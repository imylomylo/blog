---
id: 63
title: Preparing a system to be a Komodo Platform Node on KVM
date: 2017-11-14T00:57:49+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=63
permalink: /preparing-komodo-platform-node/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2017/11/komodo-platform-node-preparation.png
categories:
  - bitcoin
  - blockchain
  - komodo
  - kvm
  - systems
---
Komodo Platform? The first decentralised ICO (dICO) platform.  Intrigued, I read about it and then the dICO was postponed.  If there&#8217;s one thing Komodo Platform gets a lot of comments about, it&#8217;s their lack of suave PR.  However, the tech is amazing!  The robot trading features with the API drew me to it because I have a prospective project writing some software for betting markets, which needs automation.

Then the Komodo Platform team released their [Mock dICO Transparency Report](https://komodoplatform.atlassian.net/wiki/spaces/KPSD/blog/2017/11/12/10518596/Monaize+Mock+dICO+Transparency+Report) on why the postponement.  This happened around the weekend of the first major Bitcoin Cash rally.  The Komodo Platform team are hosting a blockchain event in Abu Dhabi, I&#8217;m presuming postponing the dICO was a good decision and to follow up my interests in the platform, thought to jump right into the tech stack.

**Warning: Work in progress!  The current question is:  is 300GB enough space?**

## Cloning KVM guest

I have a ubuntu image I use as a template.  Cloning it for a Komodo Platform node begins with

<pre class="p1"><span class="s1">virt-clone -o bunty16 -n kmd -f /var/lib/libvirt/images/kmd.img</span></pre>

It completes in a couple of minutes, the 30GB hard drive clone taking the longest.

The new kmd guest needs some first-run commands executed, like making new ssh keys for the server and changing the hostname from the template.

<pre>virt-sysprep -d kmd --hostname kmd --firstboot-command 'dpkg-reconfigure openssh-server'</pre>

## Increase KVM guest hard drive

The cloned template uses a 30GB drive.  I&#8217;d like to increase it by 300GB for this setup.

On the host:

<pre class="p1"><span class="s1">qemu-img resize /var/lib/libvirt/images/kmd.img +300G</span></pre>

Then start the new guest and resize the harddrive there.

<pre class="p1"><span class="s1">virsh start kmd</span></pre>

And then find the IP address the host-only LAN had given it:

<pre class="p1"><span class="s1">virsh net-dhcp-leases default</span></pre>

Log into the guest, and do an update and resize the filesystem to add the 300GB we&#8217;ll need for [hosting the bitcoin blockchain](https://bitcoin.org/en/full-node) (minimum 145GB space).

The partition table needs to be re-written, which requires a reboot.

So delete the extended and logical partitions and re-create them with the default values which will use entire space allocated from host.  Reboot.

If everything has worked out, the machine is up again and the guest needs to know about it&#8217;s new space.

### <span id="Guest:_Increase_the_LVM_physical_and_logical_volume_sizes" class="mw-headline">Guest: Increase the LVM physical and logical volume sizes</span>

<pre>pvs
pvresize /dev/vda5
pvs</pre>

Then look at the partition names from doing an lvs and a vgs and extend the logical with the info.

<pre>vgs
lvs</pre>

Increase the logical volume

<pre>lvextend -L +300G /dev/bunty/root</pre>

### <span id="Guest:_Increase_the_filesystem_size" class="mw-headline">Guest: Increase the filesystem size</span>

<pre>df -h
resize2fs /dev/gitlab-vg/root
df -h</pre>

Viola!

## Komodo Platform Notary Node

Komodo has a delayed proof of work algorithm for securing it&#8217;s blockchain.  How this happens is a notary node &#8220;notarises&#8221; the komodo blockchain hash into a transaction on the bitcoin blockchain &#8211; essentially securing it&#8217;s own blockchain with a notarised (and pegged) transaction on the bitcoin network.  This is a mindblowing amount of security.

Following these [instructions to setup a KMD Node](https://github.com/SuperNETorg/komodo/wiki/Setup-Komodo-Notary-Node) we&#8217;ll soon see if 300GB was enough space to allocate!