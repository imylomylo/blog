---
id: 349
title: KVM routed network for new komodo feature testing
date: 2018-08-28T03:23:19+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=349
permalink: /kvm-routed-network-for-new-komodo-feature-testing/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2018/08/800px-Set_of_Poker_Chips_in_Case.jpg
categories:
  - komodo
  - kvm
tags: [featured]
---
The new komodo features include [testing Crypto Conditions (UTXO smart contracts)](https://blog.komodoplatform.com/pre-alpha-komodo-utxo-smart-contracts-notes-7c5e8f49206), independent blockchain customization, [a community news site and integrated discourse forum](https://www.reddit.com/r/komodoplatform/comments/87l636/a_new_komodo_news_site_what_do_you_want_to_see/?st=jld426a2&sh=430bc10a), and finally the one that pushed me over the edge to order a new dedicated server&#8230;.erc20 bridging to komodo.  Between trying to finish a [komodo rpc lib in javascript](https://github.com/imylomylo/komodo-rpc-lib) (first, then maybe go and python) and picking up more docker related workflows to emulate what it would be like for a new dev to use komodo in the quickest amount of time, I feel comfortable having a few more machines &#8211; and this is where a KVM routed network gives me full advantage of having 2-10 underutilised virtual machines per dedicated server.  From these virtual machines, running a few docker containers in each virtual machine makes for pretty effective utilisation, although virtualization is not my expertise, a KVM routed network helps me keep tasks and goals fairly independent from each other.

&nbsp;

## Background: My First KVM Routed Network

My first KVM routed network configuration was in late 2017 when I was a community member of Komodo.  There was a lot of moving parts and I was new &#8211; and as I learned one aspect of Komodo I didn&#8217;t want it to blow up in my face and stop progress in another part.  I was at a crossroads in my career and not in front of a powerful machine a lot of the time.  I worked at a fantastic organic health food store part-time to make ends meet whilst I delved into blockchain tech.

This is how I came across [some dude&#8217;s website about KVM configurations](https://jamielinux.com/docs/libvirt-networking-handbook/) &#8211; it seemed to be the only site which was clear&#8230;on the whole internet!  Hopefully this quick note plus &#8220;Jamie&#8217;s&#8221; site make things clearer.  Doing a search for &#8220;jamie linux kvm networking&#8221; and you see the results.  I visited his notes enough to remember his name 🙂

<img class="aligncenter wp-image-354 size-large" src="https://i.mylomylo.com/wp-content/uploads/2018/08/jamie-linux-kvm-networking-1024x936.png" alt="step by step kvm routed network guru" width="640" height="585" srcset="https://i.mylomylo.com/wp-content/uploads/2018/08/jamie-linux-kvm-networking-1024x936.png 1024w, https://i.mylomylo.com/wp-content/uploads/2018/08/jamie-linux-kvm-networking-300x274.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/08/jamie-linux-kvm-networking-768x702.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/08/jamie-linux-kvm-networking.png 1082w" sizes="(max-width: 640px) 100vw, 640px" /> 

## KVM Routed Network Cheatsheet

  1. ssh to host
  2. become root and create a bridge interface for your public addresses to be advertised on the host and then routed to the guest (if in doubt, refer to Jamie&#8217;s website for clearer instructions)
  3. download your iso (e.g. ubuntu-16.04-5)
  4. Create the virtual machine and start it with VNC 
```
  virt-install --name erc20bridge --ram 4096 --disk path=/var/lib/libvirt/images/erc20bridge.img,bus=virtio,size=300 --cdrom /opt/ubuntu-16.04.5-server-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0,password=protectme --vcpus 4 --noautoconsole -v
```

  5. log out OR ssh tunnel your vnc connection 
```
ssh -L5900:localhost:5900 user@kvmhost
```
  6. Finish the install VNC as if you were in front of the machine  
<img class="aligncenter size-full wp-image-356" src="https://i.mylomylo.com/wp-content/uploads/2018/08/kvm-vnc-install-ubuntu.png" alt="vnc install ubuntu as kvm guest" width="912" height="734" srcset="https://i.mylomylo.com/wp-content/uploads/2018/08/kvm-vnc-install-ubuntu.png 912w, https://i.mylomylo.com/wp-content/uploads/2018/08/kvm-vnc-install-ubuntu-300x241.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/08/kvm-vnc-install-ubuntu-768x618.png 768w" sizes="(max-width: 912px) 100vw, 912px" /> 
  7. After it shuts down, remove the vnc config from your guest configuration.  Firstly dump the definition of your guest, modify the XML definition, then redefine it with the host.  (keep an original file in case of errors).
   
```
virsh dumpxml erc20bridge &gt; erc20bridge.orig
cp erc20bridge.orig erc20bridge
vi erc20bridge
```
optionally remove
```  
<graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
<listen type='address' address='0.0.0.0'/>
</graphics>
```
  8. Whilst we are still editing the machine definition, let&#8217;s define a new network interface which will have the public ip for our routed network. 
```

From 1 card:
    <interface type='network'>
      <mac address='52:54:00:d9:68:1d'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

To 2 cards (slot 3 & slot 7):
    <interface type='network'>
      <mac address='52:54:00:d9:68:1d'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <interface type='bridge'>
      <mac address='52:54:00:55:f6:89'/>
      <source bridge='virbr10'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </interface>


``` 
    vnetXXX on my systems is an odd number.  e.g. vnet1, vnet3, vnet5 because each guest has two interfaces.  The first interface is internal KVM NAT network, the second is the one used for the KVM Routed Network.</li> 
    
      * You then want to boot up the guest and make sure the NAT network is ok and that if you run ifconfig on the host there are no conflicts and both guest network cards are shown.  vnetX and vnetX+1
      * ssh to the guest using it&#8217;s internal address, something like ssh mylo@192.168.122.XXX will get you in.  And then make a definition for the second network card in /etc/network/interfaces 
```
      # The secondary network interface

    
```
      *  Reboot the guest.
      * On the host, configure the firewall (iptables) and routing (ip r) <pre class="p1"><span class="s1">root</span><span class="s2">@</span><span class="s3">host </span><span class="s2">~ </span><span class="s4"># </span><span class="s5">iptables -A FORWARD -d GUEST_EXTERN_IP/32 -o virbr10 -j ACCEPT</span>
<span class="s1">root</span><span class="s2">@host</span><span class="s3"> </span><span class="s2">~ </span><span class="s4"># </span><span class="s5">iptables -A FORWARD -s GUEST_EXTERN_IP/32 -i virbr10 -j ACCEPT</span>
<span class="s1">root<span class="s2">@host</span><span class="s3"> </span><span class="s2">~ </span><span class="s4"># </span>ip r add GUEST_EXTERN_IP/32 dev virbr10</span></pre>
    
      * To make this routing permanent on the host on reboots, add to the host networking configs (again refer to Jamie&#8217;s website for details) <pre class="p1"><span class="s1">#KVM bridge stuff for custom routed network</span>

<span class="s1">auto virbr10-dummy</span>
<span class="s1">iface virbr10-dummy inet manual</span>
<span class="s1"><span class="Apple-converted-space">  </span>pre-up /sbin/ip link add virbr10-dummy type dummy</span>
<span class="s1"><span class="Apple-converted-space">  </span>up /sbin/ip link set virbr10-dummy address 52:54:00:da:ba:5e</span>

<span class="s1">auto virbr10</span>
<span class="s1">iface virbr10 inet static</span>
<span class="s1"><span class="Apple-converted-space">  </span>#make sure bridge-utils is installed!</span>
<span class="s1"><span class="Apple-converted-space">  </span>bridge_ports virbr10-dummy</span>
<span class="s1"><span class="Apple-converted-space">  </span>bridge_stp on</span>
<span class="s1"><span class="Apple-converted-space">  </span>bridge_fd 2</span>
<span class="s1"><span class="Apple-converted-space">  </span>address HOST_EXTERN_IP</span>
<span class="s1"><span class="Apple-converted-space">  </span>netmask 255.255.255.224</span>
<span class="s1"><span class="Apple-converted-space">  </span>up route add -host GUEST_EXTERN_IP_1/32 dev virbr10</span>
<span class="s1"><span class="Apple-converted-space">  </span>up route add -host GUEST_EXTERN_IP_2/32 dev virbr10
</span></pre>
    
      *  Make your guest come up on host machine reboots <pre class="p1"><span class="s1">virsh </span><span class="s2">autostart erc20bridge
</span></pre></ol> 
    
    ## Next step, Use existing work in new servers
    
    So once you can ssh to your guest from anywhere in the world, you can start to [build komodo from source](https://i.mylomylo.com/build-komodo-source/) on one machine, use another machine for playing around with [docker images and smart contracts](https://i.mylomylo.com/pre-alpha-komodo-utxo-smart-contracts/) or even running through some [preparation to become a Komodo Notary Node](https://i.mylomylo.com/preparing-komodo-platform-node/) etc.  About as limitless as crypto conditions utxo based smart contracts!
    
    All the best!
