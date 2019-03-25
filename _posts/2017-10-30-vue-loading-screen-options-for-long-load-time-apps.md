---
id: 4
title: Vue Loading Screen Options For Long Load Time Apps
date: 2017-10-30T02:34:39+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=4
permalink: /vue-loading-screen-options-for-long-load-time-apps/
categories:
  - vue
tags:
  - dtt
  - slow-loading
---
I&#8217;m working on a couple too many scratch projects in 2017 but this is coming in handy as i deal with iframes and [cloud authentication](https://aws.amazon.com/cognito/) , the AWS js load times are poor (on first load) when bundling, an optimisation task next time around.

it led me to search for some stop-gap measures during development.

## #1 vue-loading-screen

First hit was <a href="https://github.com/bulv1ne/vue-loading-screen" target="_blank" rel="noopener">vue-loading screen</a> at github.

<img class="alignnone size-medium wp-image-9" src="https://i.mylomylo.com/wp-content/uploads/2017/10/vue-loading-screen-271x300.png" alt="" width="271" height="300" srcset="https://i.mylomylo.com/wp-content/uploads/2017/10/vue-loading-screen-271x300.png 271w, https://i.mylomylo.com/wp-content/uploads/2017/10/vue-loading-screen.png 651w" sizes="(max-width: 271px) 100vw, 271px" /> 

It&#8217;s cool for making ajax requests.

<pre>vue-init webpack loading #yeah bad name for a scratch project
cd loading
npm install
npm install --save vue-loading-screen
npm run dev

</pre>

Next,

## #2 Toggle Loading Component

Nicely presented at <a href="https://codepen.io/sirlancelot/full/NNdyWJ/" target="_blank" rel="noopener">codepen.</a>

<img class="alignnone size-medium wp-image-8" src="https://i.mylomylo.com/wp-content/uploads/2017/10/toggle-component-loading-300x235.png" alt="" width="300" height="235" srcset="https://i.mylomylo.com/wp-content/uploads/2017/10/toggle-component-loading-300x235.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/10/toggle-component-loading-768x601.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/10/toggle-component-loading.png 771w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-7" src="https://i.mylomylo.com/wp-content/uploads/2017/10/component-loaded-hello-300x235.png" alt="" width="300" height="235" srcset="https://i.mylomylo.com/wp-content/uploads/2017/10/component-loaded-hello-300x235.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/10/component-loaded-hello-768x601.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/10/component-loaded-hello.png 771w" sizes="(max-width: 300px) 100vw, 300px" /> 

Then,

## #3 Change iframe content

This was a slight detour, but waiting for npm install i was thinking how to integrate the slow loading into an iframe (as you do), for when the app is framed in another site.

[Finding this on jsfiddle](https://jsfiddle.net/Linusborg/ohznser9/) then opens a fountain of possibilities.  Reminds me of [RSK](http://rsk.co) from an online discussion on chains (shout out to [fish the beach bum investor](https://www.youtube.com/channel/UCXnqmbNNPv69D3GabkkLYlg)), i.e. trying to get two vue apps exchanging data via iframe (like bitcoin to ethereum).  Something for dtt

<img class="alignnone size-medium wp-image-6" src="https://i.mylomylo.com/wp-content/uploads/2017/10/iframe-vue-app-comms-300x163.png" alt="" width="300" height="163" srcset="https://i.mylomylo.com/wp-content/uploads/2017/10/iframe-vue-app-comms-300x163.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/10/iframe-vue-app-comms-768x417.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/10/iframe-vue-app-comms.png 1001w" sizes="(max-width: 300px) 100vw, 300px" /> 

## Summary

That quick 2 minute search, test and peruse yielded this blog post.  Plenty more out there, but it [saves me forking yet another repo](https://github.com/imylomylo) in my github 😀