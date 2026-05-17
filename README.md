# CustomNavigationTitle

[![Swift Package Manager](https://img.shields.io/badge/Swift%20Package%20Manager-compatible-brightgreen.svg)](https://github.com/apple/swift-package-manager)

[日本語はこちら](README-ja.md)

CustomNavigationTitle is a simple SwiftUI package that animates the display and hiding of the navigation title based on scrolling. (This effect is used in Apple's native Settings, Mail, and App Store apps.)

![Demo](Assets/demo01.gif)

## Features
- The title fades in and out based on scrolling.
- Easily integrated with your existing code using a simple API.
- Compatible with SwiftUI's `ScrollView`, `List`, and `Form`.

## Requirements
- iOS 16.0+
- MacCatalyst 16.0+
- macOS 13.0+

## Installation
Install using Swift Package Manager (SPM).

1. Open your project in Xcode.
2. Select **File > Add Package Dependency...**.
3. Enter `https://github.com/Chronos2500/CustomNavigationTitle.git`.
4. Configure the version requirements and click **Add Package**.

## Usage

### Basic Usage
1. Add the `.scrollAwareTitle("CustomTitle")` modifier to one of your ScrollView, List, or Form.
2. Then, add the `titleVisibilityAnchor()` modifier to the view that triggers the title's appearance and disappearance. When this view moves out of the visible area, the title is displayed.
* If the view is wrapped in a NavigationStack (or similar), this is all you need.
* Although `.scrollAwareTitle()` takes precedence over `.navigationTitle()`, it is recommended to also set `.navigationTitle()` for Navigation History Stack functionality.
* For a detailed example, [see the project in the Examples folder](Examples/CustomNavigationTitleExample/CustomNavigationTitleExample/ContentView.swift).

```swift
import SwiftUI
import CustomNavigationTitle

struct ContentView: View {
    var body: some View {
        NavigationStack {
            ScrollView {
                Text("First")
                    .font(.largeTitle)
                    .padding()
                Text("Second")
                    .font(.largeTitle)
                    .padding()
                    .titleVisibilityAnchor()
                Text("Third")
                    .font(.largeTitle)
                    .padding()
            }
            .scrollAwareTitle("CustomTitle")
        }
    }
}
```

### Using a Custom Title View
```swift
.scrollAwareTitle {
    HStack {
        Image(systemName: "star.fill")
        Text("Favorites")
    }
}
```

## License
Provided under the MIT License.

Chronos2500 © 2025

