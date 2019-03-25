---
id: 101
title: First time GravCMS Developer
date: 2017-12-12T07:35:54+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=101
permalink: /first-time-gravcms-developer/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2017/12/gravcms-developer-first-time.png
categories:
  - front-end
  - systems
---
For an upcoming project I had to put my GravCMS Developer hat on and because I hadn&#8217;t used PHP recently on my dev virtual box was starting from nearly nothing.  It is easier to install PHP composer globally whilst doing dev.  I ran GravCMS on port 80 for dev and used the sudo command &#8211; in production, I guess you would proxy to grav using apache or nginx and use a port above 1024 so you don&#8217;t have to be root.

There are other ways to begin, but I thought I would install PHP composer globally&#8230;for giggles&#8230;

<pre class="p1"><span class="s1">php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"</span>

<span class="s1">php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"</span>

<span class="s1">php composer-setup.php --filename=composer --install-dir=/usr/local/bin</span></pre>

Install some php extensions

<pre class="p1"><span class="s1">sudo </span><span class="s2">apt</span><span class="s1">-get install php7.0-gd </span><span class="s1">php7.0-curl php7.0-openssl </span><span class="s1">php7.0-curl </span><span class="s1">php7.0-zip php7.0-mbstring php7.0-xml</span></pre>

And to continue a [GravCMS](https://getgrav.org) installation,

<pre class="p1"><span class="s1">composer create-project getgrav/grav ~/webroot/grav</span></pre>

If there&#8217;s a permission problem with this error

<pre>bin/grav install handling the post-create-project-cmd event returned with error code 126</pre>

Just cd webroot/grav and run the grav executable with php

<pre class="p1"><span class="s1">php bin/grav install</span></pre>

And then run grav (on the interfaces to listen on, if you&#8217;re on a virtual machine, use that IP address and not localhost) sudo php -S 192.168.80.84:80 system/router.php

<pre class="p1"><span class="s1">mylo@proxy</span><span class="s2">:</span><span class="s3">~/webroot/grav</span><span class="s2">$ sudo php -S 192.168.80.84:80 system/router.php </span>

<span class="s2">PHP 7.0.22-0ubuntu0.16.04.1 Development Server started at Wed Dec<span class="Apple-converted-space">  </span>6 18:18:28 2017</span>

<span class="s2">Listening on http://192.168.80.84:80</span>

<span class="s2">Document root is /home/mylo/webroot/grav</span>

<span class="s2">Press Ctrl-C to quit.</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56967 [200]: /</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56968 [200]: /user/themes/antimatter/css/pure-0.5.0/grids-min.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56970 [200]: /user/themes/antimatter/css-compiled/nucleus.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56972 [200]: /user/themes/antimatter/css-compiled/template.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56974 [200]: /user/themes/antimatter/css/font-awesome.min.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56976 [200]: /user/plugins/markdown-notices/assets/notices.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56978 [200]: /user/themes/antimatter/css/slidebars.min.css</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56980 [200]: /system/assets/jquery/jquery-2.x.min.js</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56982 [200]: /user/themes/antimatter/js/modernizr.custom.71422.js</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56984 [200]: /user/themes/antimatter/js/antimatter.js</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56986 [200]: /user/themes/antimatter/js/slidebars.min.js</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:31 2017] </span><span class="s2">192.168.80.82:56991 [200]: /user/themes/antimatter/fonts/fontawesome-webfont.woff2?v=4.7.0</span>

<span class="s4">[Wed Dec<span class="Apple-converted-space">  </span>6 18:18:32 2017] </span><span class="s2">192.168.80.82:56998 [200]: /user/themes/antimatter/images/favicon.png</span></pre>

<img class="aligncenter wp-image-111 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-038-Home-I-Grav-http___localhost_8480_-581x1024.png" alt="gravcms-developer" width="581" height="1024" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-038-Home-I-Grav-http___localhost_8480_-581x1024.png 581w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-038-Home-I-Grav-http___localhost_8480_-170x300.png 170w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-038-Home-I-Grav-http___localhost_8480_-768x1355.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-038-Home-I-Grav-http___localhost_8480_.png 1046w" sizes="(max-width: 581px) 100vw, 581px" /> 

## GravCMS Developer: Install Admin Panel

These are the summary steps from the [admin panel intro pages](https://learn.getgrav.org/admin-panel/introduction).

Go to the webroot

<pre class="p1"><span class="s1">mylo@proxy</span><span class="s2">:</span><span class="s3">~/webroot/grav</span><span class="s2">$ php bin/gpm version -f</span>

<span class="s2">You are running </span><span class="s4">Grav</span><span class="s2"> v</span><span class="s5">1.3.10</span></pre>

Then do the install (dev mode I&#8217;m using sudo for quick port 80 access, and have directories with permissions created as such)

<pre class="p1"><span class="s1">mylo@proxy</span><span class="s2">:</span><span class="s3">~/webroot/grav</span><span class="s2">$ sudo php bin/gpm install admin</span>

<span class="s2">GPM Releases Configuration: </span><span class="s4">Stable</span>

<span class="s2">The package </span><span class="s5">admin</span><span class="s2"> is already installed, overwrite? [y|N] y</span>

<span class="s2">Preparing to install </span><span class="s5">Admin Panel</span><span class="s2"> [v1.6.7]</span>

<span class="s2"><span class="Apple-converted-space">  </span>|- Downloading package... <span class="Apple-converted-space">  </span>100%</span>

<span class="s2"><span class="Apple-converted-space">  </span>|- Checking destination...<span class="Apple-converted-space">  </span></span><span class="s1">ok</span>

<span class="s2"><span class="Apple-converted-space">  </span>|- Installing package...<span class="Apple-converted-space">    </span></span><span class="s1">ok</span><span class="s2"><span class="Apple-converted-space">                             </span></span>

<span class="s6"><span class="Apple-converted-space">  </span>'- </span><span class="s2">Success!</span><span class="s6"> </span>

<span class="s2">Clearing cache</span>

<span class="s7">Cleared:<span class="Apple-converted-space">  </span></span><span class="s2">/home/mylo/webroot/grav/cache/twig/*</span>

<span class="s7">Cleared:<span class="Apple-converted-space">  </span></span><span class="s2">/home/mylo/webroot/grav/cache/doctrine/*</span>

<span class="s7">Cleared:<span class="Apple-converted-space">  </span></span><span class="s2">/home/mylo/webroot/grav/cache/compiled/*</span>

<span class="s7">Touched: </span><span class="s2">/home/mylo/webroot/grav/user/config/system.yaml</span></pre>

<img class="aligncenter wp-image-112 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin-1024x685.png" alt="GravCMS Developer - Admin Panel" width="640" height="428" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin-1024x685.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin-300x201.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin-768x514.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin-900x600.png 900w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-039-Grav-Register-Admin-User-I-Grav-http___localhost_8480_admin.png 1046w" sizes="(max-width: 640px) 100vw, 640px" /> 

And after admin user creation you get to your GravCMS Developer Dashboard.

<img class="aligncenter wp-image-113 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-042-Dashboard-I-Grav-http___localhost_8480_admin-1024x619.png" alt="GravCMS Developer Dashboard" width="640" height="387" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-042-Dashboard-I-Grav-http___localhost_8480_admin-1024x619.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-042-Dashboard-I-Grav-http___localhost_8480_admin-300x181.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-042-Dashboard-I-Grav-http___localhost_8480_admin-768x464.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-042-Dashboard-I-Grav-http___localhost_8480_admin.png 1216w" sizes="(max-width: 640px) 100vw, 640px" /> 

## GravCMS Developer: Install a theme close to what you will use

Get to the themes part of the admin panel and at the top of the screen &#8220;Add+&#8221;.   I&#8217;m roughly looking at doing a single landing page for a crypto project.  The landio theme is quite close from memory.

<img class="aligncenter wp-image-114 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-043-Themes-I-Grav-http___localhost_8480_admin_themes_install-1024x619.png" alt="add landio theme to GravCMS" width="640" height="387" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-043-Themes-I-Grav-http___localhost_8480_admin_themes_install-1024x619.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-043-Themes-I-Grav-http___localhost_8480_admin_themes_install-300x181.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-043-Themes-I-Grav-http___localhost_8480_admin_themes_install-768x464.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/FireShot-Capture-043-Themes-I-Grav-http___localhost_8480_admin_themes_install.png 1216w" sizes="(max-width: 640px) 100vw, 640px" /> 

And that&#8217;s where we end&#8230;.abruptly &#8211; I&#8217;ve fallen into a development hole of 15 or so tabs&#8230;and the flow is gone 😀 It was easier to download a skeleton and just use that from scratch rather than try to install a theme.

This is a [useful must-have-gravs-plugin page](https://www.sitepoint.com/8-must-have-grav-plugins-to-round-off-your-blogs-installation/).