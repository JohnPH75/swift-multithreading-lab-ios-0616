# Multithreading in Swift

Multithreading may seem esoteric and dense, but it's super important. With so many apps in the App Store, the [user interface (UI) and user experience (UX)]((https://www.usertesting.com/blog/2016/04/27/ui-vs-ux/)) of your app will have to be as close to flawless as possible for it to stand out. You can hire a team of designers to create the most beautiful graphics for your photo filtering app, but it won't do any good if the whole app freezes without warning when a user attempts to process an image!

![Bluto on Ice](https://media.giphy.com/media/mbDvYG4QfMoQo/giphy.gif "Don't freeze up!")

To that end we can use multithreading to run heavy processes off the main thread of a device, thereby ensuring the user interface doesn't stutter and the user experience is maintained.

In this lab you will fix a broken photo filter app which hangs when the user tries to apply an "antique" filter.

## Goals

* When the `Antique` button is tapped, an activity indicator should be presented and animated to show the user some processing is going on. This activity indicator should stop when the image is filtered.
* We also want to allow the user to continue to pan and zoom the image while the filtration occurs in the background.

## Instructions

### Show an activity indicator
 
* Let's add an activity indicator to our filtering app. Instead of doing this in Interface Builder, we'll add it programmatically. In the `ImageViewController` class, add a property called `antiqueButton` of type `UIActivityIndicatorView!`.
* Next, in `viewDidLoad`, we'll create the actual view and set it up. Paste in the following lines of code:

```swift
activityIndicator = UIActivityIndicatorView(activityIndicatorStyle: .WhiteLarge)
activityIndicator.color = UIColor.cyanColor()
activityIndicator.center = view.center
```

* Here we instantiate a `UIActivityIndicatorView` object for the property we just created with the stile of `.WhiteLarge`. We then tint the indicator so it fits the theme of our app, and finally align it with the main view.
* If you run the app now and hit `Antique`, you'll see the activity indicator still doesn't appear. We're not done yet! The `UIActivityIndicatorView` has been created, but hasn't been added to the superview. Do this by inserting `view.addSubview(activityIndicator)` into your `viewDidLoad`. This adds our `activityIndicator` to the view controller's `view`.
* The last step we need to make our `activityIndicator` visible is to call it to start. Use the following lines to start and stop the indicator, respectively:

```swift
activityIndicator.startAnimating()  // Presents and starts the activity indicator
activityIndicator.stopAnimating()   // Hides and stops the activity indicator
```

* Add just the `startAnimating` line to your `viewDidLoad` and run your app. You should see a blue spinning activity indicator! We don't want the indicator to start as soon as the app opens, though. Let's move this start function call to the `antiqueButton` function.
* Start the activity indicator visible when the `Antique!` button is tapped and stop it when the image is filtered.

### Allow for user interaction during filtering

* Add a queue
* Add a `mainQueue` operation block around the final filtered image getting set back in the `imageView` and the call to `completion`.



### Advanced

Play around with other filters and see what you can create! Here's a [list of all available CIFilters](https://developer.apple.com/library/mac/documentation/GraphicsImaging/Reference/CoreImageFilterReference/index.html) to get you started.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/swift-multithreading-lab' title='Multithreading in Swift'>Multithreading in Swift</a> on Learn.co and start learning to code for free.</p>
