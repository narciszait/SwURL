<p align="center">
  <img src="https://imgur.com/jTPdRfJ.png" alt="SwURL"/>
</p>
<br/>
<br/>


[![Build Status](https://travis-ci.org/cmtrounce/SwURL.svg?branch=master)](https://travis-ci.org/cmtrounce/SwURL)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)

Declarative-style SwiftUI wrapper around asyncronous image views including smooth transitions and caching options.

### Currently up to date with Xcode GM 2. 

# RemoteImageView

Asyncrounously download and display images declaratively. Supports placeholders and image transitions.

Flexible caching and image fetching done in background. Currently tested with basic `List` as seen in Example

As everyone gets to understand SwiftUI more, this project will evolve and get more features.

![Fading Transition!](https://media.giphy.com/media/kFCKkcURNhI0AVG19y/giphy.gif)

## Configuration

Enable or disable debug logging 

```swift 
SwURLDebug.loggingEnabled = true
```


Choose between **global** persistent or in-memory (default) caching

 ```swift
 SwURL.setImageCache(type: .inMemory)
 ```

 ```swift
 SwURL.setImageCache(type: .persistent)
 ```
 
 ... or provide your own caching implementation by using `ImageCacheType`
 
  ```swift
 SwURL.setImageCache(type: .custom(ImageCacheType))
 ```

## Usage

`RemoteImageView` is initialised with a `URL`, placeholder `Image` (default nil)  and a `.custom` `ImageTransitionType` (default `.none`). 

Upon initialisation, a resized image will be downloaded in the background and placeholder displayed as the image is loading, transitioning to the downloaded image when complete.

`LandmarkRow` is used in a `List`

```swift
struct LandmarkRow: View {
    var landmark: Landmark
    
    var body: some View {
        HStack {
            RemoteImageView(url: landmark.imageURL,
                            placeholderImage: Image.init("user"),
                            transition: .custom(transition: .opacity,
                                                animation: .easeOut(duration: 0.5)))
            Text(verbatim: landmark.name)
            Spacer()
        }
    }
}
```

## Available Parameters

| Name | Description |
| :--- | :--- |
| url | `URL` of the remote source image. |
| placeholderImage | _(optional)_ `Image` to display whilst remote image data is being fetched and decoded. |
| transition | _(optional)_ transition to occur when showing the loaded image. |
| imageRenderingMode | _(optional)_ `TemplateRenderingMode` of the placeholder image (if provided) and loaded image. |  

# Get it

SwURL is available only through `Swift Package Manager`

* Open Xcode
* Go to `File > Swift Packages > Add Package Dependency...`
* Paste this Github Repo URL ( https://github.com/cmtrounce/SwURL ) into the search bar. 
* Select the SwURL repo from the search results.
* Choose the branch/version you want to clone. The most recent release is the most stable but you can choose branches  `master` and `develop` for the most up to date changes.
* Confirm and enjoy!

# Contact

If you want to get in touch you can email me at ctrounce94@gmail.com or follow/message me on Twitter https://twitter.com/ctrounce94
