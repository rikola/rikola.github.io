---
layout: post
title: Breaking in EZAudio
subtitle: Integration Woes with Cocoapods
---

I recently started working with the EZAudio framework for iOS. I am using it in Swift so I ran into a whole bunch of weird problems that were hard to fix using Google-Fu.

First off, I assumed that by including EZAudio in the `Podfile` I would be able to grab the latest version with a pod update. I was wrong.  

Here was my original podfile,

```# platform :ios, '8.0'
use_frameworks!

target 'Nervana' do
	
	pod 'SWRevealViewController'
	pod 'TPCircularBuffer'
	pod 'EZAudio'
	pod 'KAProgressLabel'
	
end
```

For some reason, this was downloading the version `0.2.0` and not moving up to version `1.5.2`.

When I finally got it to jump up to the correct version, it suddenly was spitting out errors.