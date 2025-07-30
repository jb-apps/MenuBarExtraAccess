# MenuBarExtraAccess

[![Platforms - macOS 13.0](https://img.shields.io/badge/platforms-macOS%2013.0-blue.svg?style=flat)](https://developer.apple.com/swift) [![](https://img.shields.io/endpoint?url=https%3A%2F%2Fswiftpackageindex.com%2Fapi%2Fpackages%2Forchetect%2FMenuBarExtraAccess%2Fbadge%3Ftype%3Dswift-versions)](https://swiftpackageindex.com/orchetect/MenuBarExtraAccess) [![Xcode 14](https://img.shields.io/badge/Xcode-14-blue.svg?style=flat)](https://developer.apple.com/swift) [![License: MIT](http://img.shields.io/badge/license-MIT-lightgrey.svg?style=flat)](https://github.com/orchetect/MenuBarExtraAccess/blob/main/LICENSE)

#### **Gives you *Extra* access to SwiftUI `MenuBarExtra`.**

- Programmatically hide, show, or toggle the menu (by way of a `Bool` binding)
- Programmatically enable or disable the menubar extra (by way of a `Bool` binding)
- Access to the underlying `NSStatusItem`
- Access to the underlying `NSWindow` (when using the `.window` style)
- Works with one or [multiple](#Multiple-MenuBarExtra) `MenuBarExtra`
- Works with both [`menu`](#Standard-Menu-Style) and [`window`](#Window-Style) based styles (see [Known Issues](#Known-Issues))

## Why?

There is no 1st-party `MenuBarExtra` API to get or set the menu presentation state, disable the menubar extra, access the `NSStatusItem`, or access the popup's `NSWindow`. (Still as of macOS 26 beta 4)

## Library Features

- A new `.menuBarExtraAccess(isPresented:, isEnabled:) { statusItem in }` scene modifier with
  - a binding to hide/show/toggle the menu
  - a binding to enabled/disable the menubar extra
  - direct access to the `NSStatusItem` if needed
- A new `.introspectMenuBarExtraWindow { window in }` view modifier passing in the `NSWindow` reference
- Window-based menu extra status items now remain highlighted while the window is open so it feels more like a native menu
- No private API used, so it's Mac App Store safe

## Getting Started

The library is available as a Swift Package Manager (SPM) package.

Use the URL `https://github.com/orchetect/MenuBarExtraAccess` when adding the library to a project or Swift package.

Check out the [Examples](Examples) folder for a demonstration of the package's usage.

## Future

The hope is that Apple implements native versions of these features (and more) in future iterations of SwiftUI!

Until then, a radar has been filed as a feature request: [FB11984872](https://github.com/feedback-assistant/reports/issues/383)

## Menu Builder

Check out [MacControlCenterUI](https://github.com/orchetect/MacControlCenterUI), a SwiftUI package built on MenuBarExtraAccess for easily building Control Center style menus.

## Known Issues

- When using `.menuBarExtraStyle(.menu)`, SwiftUI causes the popup menu to block the runloop while the menu is open, which means:
  - Observing the `isPresented` binding will not work as expected.
  - Setting the `isPresented` binding to `false` while the menu is presented has no effect.
  - The user must dismiss the menu themself to allow event flow to continue. We have no control over this until Apple decides to change the MenuBarExtra behavior.

## Author

Coded by a bunch of 🐹 hamsters in a trenchcoat that calls itself [@orchetect](https://github.com/orchetect).

## License

Licensed under the MIT license. See [LICENSE](https://github.com/orchetect/MenuBarExtraAccess/blob/master/LICENSE) for details.

## Community & Support

Please do not email maintainers for technical support. Several options are available for issues and questions:

- Questions and feature ideas can be posted to [Discussions](https://github.com/orchetect/MenuBarExtraAccess/discussions).
- If an issue is a verifiable bug with reproducible steps it may be posted in [Issues](https://github.com/orchetect/MenuBarExtraAccess/issues).

## Sponsoring

If you enjoy using MenuBarExtraAccess and want to contribute to open-source financially, GitHub sponsorship is much appreciated. Feedback and code contributions are also welcome.

## Contributions

Contributions are welcome. Posting in [Discussions](https://github.com/orchetect/MenuBarExtraAccess/discussions) first prior to new submitting PRs for features or modifications is encouraged.
