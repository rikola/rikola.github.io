---
layout: post
title: How to Implement a Music Player
subtitle: With metering and more customization
---

During the course of building music playback functionality into the `Nervana` App, the `MediaPlayer` framework seemed really limited to me.

> **Reasons:**
> 
> - No audio level metering
> - No playlist support
> - Not great seeking support

I thought the default music player system offered by the `MediaPlayer` framework was not sufficiently powerful for an app I have been making, so I went off and made my own music playing service. In this guide I will walk you through the steps to make your own music playing system if you feel like the system provided version doesn't meet your needs.

----------

### Getting Started

What you'll need:  

- Xcode 7.3+
- An iPhone with a music library (Since you can't access the music library in the simulator)

1. Setup a new project with the "Single View Application" template.  
2. Name it MyMusicPlayer and make it for iPhones only. Leave CoreData and both Test checkboxes unchecked.
3. Now onto the code!

### Step 1: Building the Playlist  

First we need to lay the necessary foundation before we start playing music. It makes for cleaner code if we encapsulate the playlist functionality into its own object. Make a new empty swift file called `Playlist.swift`. Make the starting frame of the class.  

~~~ swift
import Foundation
import AVFoundation
import MediaPlayer


class Playlist<T> {
	
	private var contents: [T]
	var count: Int { return contents.count }
	var startIndex: Int { return 0 }
	var endIndex: Int { return contents.count }
	var index: Int = 0
	var nowPlaying: T? {
		return index < count ? contents[index] : nil
	}
	
	init(songs: [T], withIndex: Int = 0) {
		contents = songs
		index = withIndex
	}
	
	func insert(song: T, atIndex: Int) {
		contents.insert(song, atIndex: atIndex)
	}
	
	func remove(index: Int) -> T? {
		if index < endIndex {
			return contents.removeAtIndex(index)
		}
		return nil
	}
	
	func append(song: T) {
		contents.append(song)
	}
	
	func changeTo(index: Int) -> T? {
		assert(index >= 0, "ERROR: Cannot change to index below 0")
		if index < endIndex {
			self.index = index
			return contents[self.index]
		} else {
			self.index = endIndex
			return nil
		}
	}
	
	func next() -> T? {
		if index == endIndex {
			return nil
		}
		index++
		if index == endIndex {
			return nil
		} else {
			return contents[index]
		}
	}
	
	func previous() -> T? {
		if index > startIndex {
			index--
		}
		return contents[index]
	}
	
	subscript(i: Int) -> T {
		return contents[i]
	}
}
~~~~


