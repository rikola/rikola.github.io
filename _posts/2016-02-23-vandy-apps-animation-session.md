---
layout: post
title: VandyApps – iOS Animation Session
subtitle: Start using animations in your apps.
---

### Requirements
* OSX El Capitain
* Xcode 7+

### Set up

1. Clone or download the starter project repo from [Github](https://github.com/rikola/ios-animation-session).

---

## First – Some Closure
  
Most Computer Science majors are familiar with these as __blocks__ (Obj-C) or __lambdas__ (everything else), but to casual coders they can be scary.  

A closure is something called an **Anonymous Function**.

Normally when you have a function in Swift it looks like this:

``` swift
func sum(a: Int, b: Int) -> Int {  
	return a + b
}
```
Closures on the other hand do not have a function name (anonymous) or parameter names. This is identical to the previous sum function:  

``` swift  
{ (item1: Int, item2: Int) -> Int in  
	return item1 + item2 
}  
```

However, this session will be generally using closures with no parameters. If your closure does not take any parameters and does not need to return a value, such as with a completion handler function, you may omit the parameters and return declaration:

``` swift  
{ // Do something here }
```

Finally, if a function takes a closure as its final argument, generally as a completion handler, Swift allows the closure braces to be put outside the function call:  

``` swift
// Normal way to do it
functionThatTakesAClosure({
    // closure's body goes here
})
 
// Now with a trailing closure
functionThatTakesAClosure() {
    // trailing closure's body goes here
}
```

This makes for cleaner looking code when the closure content is large, like they will be with our animations.  


---  

## Getting Started

#### Basic UIKit Animations

It's easy as crap:

``` swift
UIView.animateWithDuration(5.0) {
	// Whatever you want to animate
}
```

`animateWithDuration(_:_:)` does all the heavy lifting here.

Now we can start animating stuff.

Open `ViewController.swift` and find `func animate()`. Change it to the following:

``` swift
func animate() {
	UIView.animateWithDuration(2.0) {
		self.someview.center.x += 10
	}
}
```

Now run the app, press the button and bask in how much you just improved this app.

Now that we have animated a `UIView` position, we can check out some of the other UIKit animation functions.

#### Taking basic UIKit animations further

You can do more customized animations with another version of `animateWithDuration:`. 

``` swift
UIView.animateWithDuration(0.5, delay: 0.4, options: [], animations: { 
	self.password.center.x += self.view.bounds.width
}, completion: nil)
```  

The `options` parameter allows you to customize certain properties about the animation. Some options you can pass in are:
* `.Repeat` – Makes the animation repeat over and over again.
* `.Autoreverse` – Causes the animation to reverse itself during the last half of the animation. Handy for making UI elements pop out and then go back to normal size. 

Another use for the `options` parameter is to pass in animation easing options. These control the animation speed curve. The default is `.EaseInOut` which brings the animation to a start and stop slowly like a real object. You can use these strategically to make your animations look less robotic. Some common easing options are:  
* `.Linear` – Robot mode. No easing on either end.
* `.CurveEaseInOut` – Easing on both ends.
* `.CurveEaseIn` – Easing only at the beginning.
* `.CurveEaseOut` – Easing only at the end.



#### Animatable Properties

As you can imagine, not every single property of views is animatable. As a general rule of thumb, view properties that are both settable and numerical can be animated.  

The following properties of UIView are animatable:

|-------------------+-------------------------------------|
| Property          | Description                         |
|-------------------|-------------------------------------|
| `frame`           | Location & size in parent container |
| `bounds`          | Area that the view can draw content |
| `center`          | Center point of the `frame`         |
| `transform`       | Used for spinning or warping        |
| `alpha`           | Transparency                        |
| `backgroundColor` | Color behind the view's content     | 
| `contentStretch`  | How the content resizes itself      |
|-------------------+-------------------------------------|


--- 

## Spring Animations

Spring animations make a cool effect of having something bounce with semi-realistic physics. They are useful for making your UI look a lot more goofy, and are particularly useful for making games and apps geared towards children or simple people. Heres an example:

``` swift
UIView.animateWithDuration(0.5, delay: 0.5, usingSpringWithDamping: 0.5, initialSpringVelocity: 0.0, options: [], animations: {
	self.loginButton.center.y -= 30.0
	self.loginButton.alpha = 1.0 
}, completion: nil)
```

#### User Interacton Animations

Now that we know how to use some basic animation functions, adding them to UI elements such as buttons is going to be a piece of cake. All you have to do is add it to the button handler function. 

---

## Transitions

#### Crossfade

abc

#### Cube Simulation

abc

#### Fade

abc

---

## Keyframes

abc


---

## Animating Constraints

#### Programatic Constraints

abc

#### IB Constraints

abc



---

Follow me on Github: [@rikola](https://github.com/rikola)  





