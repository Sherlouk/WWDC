# WWDC

Usually it is much faster to read through some bulet points instead of watching a 50 min session video. Then if you find something interesting you can still watch it.

Feel free to submit a `PR` if I got something wrong or you have an improvement suggestion.

> This is work in progress since also for me it is a lot of effort to watch all the videos. So either please be patient or just [open up an issue](https://github.com/Blackjacx/WWDC/issues/new) to make a suggestion which session notes you like to see here asap :)

## Session Notes WWDC 2019

### [What's New in Swift](https://developer.apple.com/wwdc19/402)

- **ABI Stability (Application Binary Interface):** App and Framework built by different compilers can now be used together (in the past ensured by building with same compiler)
- **Module Stability:** Swift module file and App build by different compilers can now be used together by introducing *stable and textual .swiftinterface file*
- **Binary Frameworks:** Result of ABI and Module stability. Can be shared with others.
- obsolete **return** if it is the only line in a closure / function
- auto-generated struct initializers now allow to pass only some of the aguments
- **Opaque Return Types:** Let you return the same type without leaking implementation details. Use keyword `some`
- **Property Wrappers:** Wrapper type to define custom access patterns. Property can adopt this by adding attribute to its declaration. In the case of UserDefaults you can define properties that know how to read/write from/to UserDefaults.
- **Embedded DSLs**

### [Introducing SF Symbols](https://developer.apple.com/wwdc19/206)

- **Alignment** is perfect surrounding text
- **1500** vector symbols designed by Apple in all weights available
- **Margins** of symbols can be different so they are perfectly aligned on screen
- **Scales** (small, medium, large) ensure
  - symbols maintain same weight as neighbouring text
  - symbols are vertically centered to neighbouring text
- **[SF Symbols](https://developer.apple.com/design) app** to play around and export existing symbols (as SVG template) for customization
- **UIImage(systemName: String)** is new - just copy the name from the Symbols app
- **Multiple images** with the same name in Asset Catalog are now possible. Apple first looks for symbol and then for non-symbol (ensures backwards compatibility to iOS 12: uses image in iOS 12 and symbol in iOS 13)
- **Constraining symbol images** is discouraged. Use natural size or set font size 
- **Any font** can be used with symbols via `UIImage.symbolConfiguration`
- **Vertical text alignment** works with single-lined and multi-lined text
- **Baseline alignment** to align symbol to first line of text
- **Regular images** are aligned baseline aligned by generating a new image with `image.withBaselineOffsetFromBottom(GGFloat)`
- **Prefer horizontal and vertical center alignment** instead of edge alignment
- **Buttons with symbol images** are created using `UIImage.system(image:target:action)`
- **UIButton Symbol Configuration** changed by `UIButton.setPreferredSymbolConfiguration(config:forState:)`
- **Auto-scaling UIBarButtonItems** from `SymbolScale.large` to `SymbolScale.medium` in landscape
- **No frame settings necessary for NSTextAttachment** for placing images in text
- **UIImage tint support** `image.withTintColor(UIColor)` - yeah 🥳 

### [Advances in Foundation](https://developer.apple.com/wwdc19/723)

- **Ordered Collection Diffing**
- **Compression API** to transmit resources compressed (CompressionAlgorithm.[lzfse, lz4, lzma, .zlib])
- **New Units** bits, bytes, nibbles
- **RelativeDateTimeFormatter** for get localized, relative date descriptions
- **ListFormatter** formats list contents localized
  - correct separator and localized `and` before the last element
  - specify `itemFormatter` to control how the list items are formatted
- **OperationQueue**
  - BarrierBlock lets run a completion task safely when all other tasks are finished
  - progress reporting
- **Scanner** lets you split string files in one line now: `scanner.scanUpToCharacters(CharacterSet)`
- Use `DataProtocol`instead of `UInt8`

### [What's New In App Store Connect](https://developer.apple.com/wwdc19/301)

- **AppStore for Messages** with full TestFlight capabilities
- **Transporter** Mac app for submission of IPA, PKG, ITMSP files. ApplicationLoader deprecated.
- **Build Activity View** shows all uploaded builds, download sizes for each device, detailled information for each build
- **TestFlight Feedback** 
  - lets users talke screenshots in TestFlight and send them with a description to developer
  - accessible/downloadable from ASC
  - adds a custom onboarding screen to app the first time the app is tested. 
  - can be enabled/disabled via testflight for each tester group
- **Crashes** automatically trigger the feedback dialog. Feedback viewable/downloadable in ASC.
- **App Deletions 🎉** as metric on APC. Opt-in. Only from iOS 12.3++. Only for homescreen and storage deletions. Resetting device doesn't count.
- **24h live dashboard** hourly updated statistics for all apps to better understand sales data (e.g. in-app purchase) as it is rolled out

### [Great Developer Habits](https://developer.apple.com/wwdc19/239)

- **Use groups** for project organization
- **Mirror** project and file structure
- **Large Storyboards** should be splitted
- **Update Project Settings** asap whenever Xcode prompts you
- **New Build System** should be used asap
- **Unused code** should be deleted, not commented out - we all have source control, right?
- **Warnings** resolve them immediately. Never check in code with warnings. Treat them as errors.
- **Commit small changes** a Git commit should contain only small code changes
- **Write useful commit messages** that have a shord title and a descriptive body
- **Use branches** to isolate changes that belong to a certain feature
- **Write documentation** about WHY the code has been written and WHAT it is doing
- **Use descriptive variable names** instead of `id`, `state`, etc.
- **Write Unit Tests** to avoid regressions and run them before each commit
- **Use diagnostics tools** that can be enabled in the scheme settings (Main Thread Checker, Address Sanitizer, Thread Sanitizer, Undefined Behavior Sanitizer)
- **Gauges** are very useful to see if you have problems with network, memory, disk and CPU usage
- **Network Link Conditioner** helps tracking down bugs on low connectivity
- **Do Code Reviews** to track down issues and get a common understanding of the code and its style
  - understand each changed line
  - build and run the project
  - run the tests
  - proofread comments and documentation
  - look for spelling and grammer errors
  - ensure consistency in codebase
- **Decouple your code** by creating packages and shared frameworks to reduce code size and share code between multiple app targets
- **Dependencies** should be used responsibly
  - Understand how a dependency works thoroughly
  - Read carefully the changes when it is updated
  - Have a plan when a dependency goes away or is not maintained anymore
  - Ensure privacy

### [Writing Great Accessibility Labels](https://developer.apple.com/wwdc19/254)

- **Accessibility Label** is a human understandable label
  - gives meaning to the elements of your app
  - value depends completely on the context
  - should not contain the type of the view. Automatically provided by `accessibilityType`
  - should contain context if multiple similar elements visible (multiple add buttons)
- don't add redundant context, e.g. if you're in a music player avoid `song` from the accessibility label of next, previous, ...

### [What's New in Xcode 11](https://developer.apple.com/wwdc19/401)

- **Editor splitting** is now unlimited and allowed horizontally and vertically
- **Source control log** info moved to inspector and can thus be used for *any* file any time
- **Editor Options Button** configures now every split editor seperately. 
  - Assistent and Authors are moved there
  - Holding ⌥ + ⇧ when clicking a new file shows the destination selector that lets you choose in which split editor to open the file
- **Editor and Canvas option** shows the current views preview if there is one
- **Canvas / Assistent hides automatically** if there is  othing to see for the currently selected file
- **The Minimap** is loaded with functionality
  - Landmarks, Syntax coloring, Navigation, shows symbol names on hover, highlights search results
  - Holding ⌘ shows all symbols in the file when hobvering over the minimap
- **Powered up Documentation** formats the doc block in a markdown like style
  - add missing documentation / or fill up gaps by selecting `Editor > Structure > Add Documentation`
- **Show Change** after click on change bar shows inline diff
- **Code completion** works more reliably: function overloads, enum cases, compiler control statements
- **Swift Package Manager** is now part of Xcode
  - GitHub, GitLab and BitBucket integration
  - used to integrate packages for all platforms
  - `Project Editor > Project > Swift Packages Tab` shows all personal and starred repos when logged in
  - Source browsing of packages is possible
  - helps sharing own packages with the world
- **Source Control** extendeb by `stashing` and `cherry pick`
- **Asset Catalog** can provide assets and colors for dark mode. Image assets are localizable now.
- **Environment Overrides** in the debug bar lets you change dynamic text size, appearance and accessibility settings
- **Device Conditions** in the devices window let you change network throughput and thermal state of your device
- **Test Plans** define a set of tests and are sharable via Schemes
  - describe arguments, environment variables, sanitizers, language, ...
- **Watch Simulator** is now stand alone
- **Simulator** build on top of Metal 
  - apps build in Metal can be run in the simulator with great performance
  - Apps on top of UIKit are much faster
  - 60 fps • up to 90% less battery life • warm boots are 2x as fast
- **SwiftUI** enables `Canvas previews, Code and Canvas Editors, Code Hot Swapping, Rich Preview API, Preview Pinning, Instruments Template, On-Device Previews, Action Popover Actions, Library Views and Modifiers, Canvas Editor for Code, Preview Debugging, Development Time Assets`
- **Most Awesome SwiftUI Tutorials I've Ever Seen Right In Xcode's Documentation Window**

### [What's New in Authentication](https://developer.apple.com/wwdc19/516)

- **Sign in With Apple**
  - lets choose users which information is delivered
  - creates random email and forwards it directly to your AppleID to disguise your original email 
- **Password Auto-Fill** for iPad apps on the Mac
- **Weak Password Assistant** detects weak passwords and offers you to change it
- **ASWebAuthenticationSession** provides easy OAuth workflow and deprecates SFAuthenticationSession

### [Introducing Sign In with Apple](https://developer.apple.com/wwdc19/706)

- **Secure** - backed by 2FA of the AppleID
- **Private** - not tracked by Apple
- **Fast and Easy** - user dosn't even need a keyboard
- **User controls** which data to share
- **Seamless Across Device** recognizes that already signed in on other device
- **Requires Capability** for Apple Sign In has to be added
- **Private E-Mail Relay** links random mail to your AppleID
  - Apple never retains messages
  - Can be used for any email communication liek receipts, ...
  - Two-Way Relay
- **Anti-Fraud Detection** can tell if a robot tries to sign in or not
- **Cross Platform** iOS, macOS, watchOS, tvOS, JavaScript (Android Websites)
- **ASAuthorizationAppleIDButton** creates button that has different visual styles and labels
- **Authentication Request** returns 
  - **UserID** which is unique, stable and team-scoped and can be used as the key to the user
  - **Verification Data** identity token and short-lived code to refresh token
  - **Full Name** as PersonNameComponents which contain first/last name separately
  - **Verified email** your server doesn't need to verify this email again
  - **Real User Indicator** high confidence indicator that likely real user
  - **Credential State** tells if UserID is `authorized` (let user pass), `revoked` (handle unlink) or `not Found` (show login)
- **Always check on AppStart** with `provider.getCredentialState(userID)` which runs very fast
- Listen to `NSNotification.Name.ASAuthorizationAppleIDProviderCredentialRevoked` and sign the user out if called
- **Password Autofill** integrates with Apple Sign In. Triggerd if the device detects a stored credential

### [Building Great Shortcuts](https://developer.apple.com/wwdc19/805)

- Summary of an Action should be short and only contain necessary parameter
- Best way to add shortcut is right inside the app after the action that should be added has been completed
- Offer to add shortcuts for repeatable actions
- **Activation Phrase** should be short and pronouncible
- **Suggested Shortcuts List** can be updated by app via API a often as wanted. Apple also populated this list based on device usage like recently used apps.
- **Input and Output** concept used to make actions work together. Actions can now output information for others to use, e.g. action could find a note wheas action 2 processes this. Both can be chained together.
- **Intent Editor** lets the developer modify intents

### [Designing Great Shortcuts](https://developer.apple.com/wwdc19/806)

- **Shortcut Use Cases** are `Accelerate an Action`, `Present Concise Information`, `Multi-Step Shortcuts`
- **Great Shortcuts** wrap actions the user has to to often in your app. Offer adding an action to Siri after this action has been completed
- **Provided Add to Siri Button** should be used to add an action to Siri
- **Activation Phrase** should have a great default
- **Action** should provide as much etail as possible to the user has to fill out as less as necessary
- **Prompts** can be used to collect a value from the user.
- **Minimize Disambiguation Prompts** by providing an optios list upfront
- **Pronounciation Hints** can be provided on devices lacking a display
- **Providing Synonyms** to options helps Siri to understand the user
- **The Final Confirmation Dialog** should be used to summarize everything the user has specified. Keep in mind to design a more descriptive one for devices without display!
- **Continuing in App** dialog is one big button, therefore avoid elements that look interactive.
- **Never include the App Name** this is shown automatically
- **Don't Include Users Name** since it might sound repetitive
- **Avoid first-person pronouns** use something like *There are the following options*

### [Integrating with Siri Event Suggestions](https://developer.apple.com/wwdc19/243)

- **Apps can donate information** to the system via `INInteraction` so the system can show them to the user at appropriate time, location or in related apps
- All this magic happend directly on the device
- **Intents framework** supports reservations acroll many categories like Flights, Restaurant, Movies, Ticket Events, Car Rentals, Train, Hotels, Flights
- `INReservation`, `INGetReservationDetailsIntent` and `INGetReservationDetailsIntentResponse` to donate reservation information to the system
- **NSUserActivity** is used to handle app launches from Siri suggestion throughout the iOS sytsem
  - can be used to provide web-based flow if app is not installed > `NSUserActivity.webpageURL `
- **Shortcut** appears on the lockscreen and in the search UI when specified parameters match (user is at specified location, time of the event is close, …). On tap it launches the app.
- **Reservation Details** are automatically synced across the users devices using end-to-end encryption
- **Donating Reservations**
  - If you don't have the coorindate provide `0, 0`. Siri will only use the postal address.
  - Make sure to set the correct time zone of the event location for the event
  - If no end time is available - set it nil
  - In case of multiple `INReservation` items:
    - provide `itemReference` which must be unique for each reservation
    - can be structured as you want, e.g. reservation number combined with flight number
  - Donation should be done 
    - in-app when the reservation is created
    - always when reservation viewed because it might have changed
    - from the background when the app is closed and the reservation changed
  - Donate should not be done
    - explicitly via UI elements
  - If reservation is cancelled, donate the reservation with `reservationStatus` set to `.cancelled`

### [Modern Swift API Design](https://developer.apple.com/wwdc19/415)

- **Clarity at point of use** is the most important goal as an API designer
- **No prefixes** in Swift-only frameworks
- **Prefer Structs over Classes** - Use classes only when 
  - reference counting or deinitialization is needed
  - the value is shared
- **Use private backing variables** and additionally a computed property for reference types if you need to copy them
- **Only manually copy reference types** if `isKnownUniquelyReferenced` returnes `false`. 
- **Don't start off with protocols** rather start with concrete types • discover the need for generic code • try to use existing protocols • consider generics over protocols. 
  **This will also decrease binary size and increase compile time.**
- **Get familiar with SIMD types** which are perfectly suited for geometric calculations
- **Dynamic Member Lookup** to define a single subscript operation that exposes multiple properties on a type
  - attribute type by `@dynamicMemberLookup`
  - requires implementing subscript that takes a `KeyPath` or `ReferenceWritableKeyPath`
  - any property is automatically exposed as computed property
- **Property Wrappers** offer code reuse out of computed properties by using Generics. 
  - Describe the policy behind your data access 
  - Eleminate boilerplate & get more expressive UIs
  - add the attribute `@propertyWrapper` to your generic type (requires implementing `public var value: Value` )
  - **Use Your Property Wrapper** by defining a property this way: `@YourPropertyWrapperType var name: String` which will internally expand to a private backing property as well as a computed property that uses the implementation of your generic type.
  - `@UserDefault(key: "BOOSTER_IGNITED, defaultValue: false")`
    `static var isBoosterIgnited: Bool`
  - `@ThreadSpecific var localPool: MemoryPool`
  - `@Option(shorthand: "m", documentation: "Minimum Value", defaultValue: 0)`
    `var minimum: Int`
  - Examples from SwiftUI are `@State`, `@Binding`
- Use protocols for code reuse not for classification

### [Core NFC Enhancements](https://developer.apple.com/wwdc19/715)

- Support for reading **Passports**, interacting with **smart cards** from iPhone 7 ++
- **NFCTagReaderSession** allows to scan native tags like ISO14443, ISO15693, ISO18092
- **NFCNDEFReaderSession** supports discovery of NDEF tag objects and read/write operations for those
- **Workflow to Use NFC**
  - Enable Xcode Capability
  - Use one of the sessions described abobe
  - receive tags in discovery callbacks
  - connect to tag
  - perform operations
  - invalidate session
- **Native Tag Reading** supports ISO7816
  - info.plist must contain a list of ApplicationIdentifiers (AID)
  - detect-tag callback invoked when tag is ISO7816 and AID is contains in info.plist
- **Native Tag Reading** supports also MIFARE, ISO15693, FeliCa (from Sony - heavily used by transit and payment sytems in Japan)
- Watch technical session video for implementation details to all supported **Native Tag Reading**

### [Testing in Xcode](https://developer.apple.com/wwdc19/413)

- **Testing Pyramid Refresher**
  - **Unit Tests** as foundation help to test a single piece of code - write many
  - **Integration Tests** validate larger section of code (clusters of classes). Verify that different parts behave corctly together. You need less of these than unit tests.
  - **UI Tests** oberserve the user-facing behavior of your app. Requires more maintenance, run slow. You need the least ones 
- **XCTUnwrap** is equivalent to: `assert not nil; guard let <contition> else throw`
- **XCTAssertEqual** gains an `accuracy` argument for comparing double values
- **XCTAssertThrowsError** has a closure to evaluate the thrown error. Ideal to write negative test cases.
- **UITests** property isHittable ensures that an element exists, is on the screen and you can interact with it
- **Test Plans** 
  - allow running tests more than once with different settings
  - defines all testing variants in one place
  - can be shared between multiple schemes
  - supported in Xcode and xcodebuild for CI Xcode Server
- **Test Plans** let you specify the following by using `Configurations`
  - language, region, user location, automatioc screenshots, localization screenshots, execution order, code coverage, sanitizers, API checking, memory management options, arguments and environment variables
- **Test Configuration** represents a single run of your tests with certain set of options
- **Shared Settings** are inherited by all test configurations
- **Localization Screenshots** for preserving all screenshots from all runs with different localizations 
- **Example Configurations With Different Focus Are No Problem Anymore: ** `Memory Checking` (Address Sanitizer + Zombie Objects), `Concurrency` (Thread Sanitizer, Undefined behavior Sanitizer, Random Order), `Extra Diagnostics` (ENBLE_LOGGING=1, Keep Attachments)
- **Xcode Server** is finally usable to share test configuration between different bots. The ideal (and free) solution to test a white-labelled app with lots of targets
- **Result Bundles** 
  - 4 times smaller due to optimized file format
  - viewable in Xcode
  - programmatically accessible via `xcresulttool`
  - used to get code coverage diff via `xccov diff --json Before.xcresult After.xcresult`

### [Advances in Networking, Part 1](https://developer.apple.com/wwdc19/712)

- **Low Data Mode** enables configuration per wi-fi and cellular network how `expensive` the connection is
  - delays discretionary tasks
  - disables backround app refresh
  - apps have to adopt to it by `reduce image quality (symbols vs. images)`, `reduce prefetching`, `synchronize less often`, `mark background tasks as discretionary`, `disable auto-play`, `don't block user-initiated work`
  - first try expensive prefetch by `allowConstrainedNetworkAccess = false`. On failure `error.networkUnavailableReason == .constrained` try low data alternative
  - `URLSession.allowExpensiveNetworkAccess`
  - **never check for connection type** rather check if the connection is `expensive` or `constrained`
- **DataTaskPublisher** uses Combine framework in URLSession. Useful to achieve the following in  asynchronous networking:
  - get rid of capturing self in completion handlers
  - avoid duplicate network code like checking for status code
  - achieve retry operation in just one line - since network operations are expensive: low retry count 
  - Pretty nice example of generic `low-data-mode` `adaptivePublisher` at minute `26:07`
- **WebSocket**
  - **Advantages**
    - bi-directional connection over TLS/TCP connection
    - works with firewalls / CDNs
    - proxy support
  - **URLWebSocketTask** is exciting simple! Example at `31:32`
    - NSConnection / NSListener offers client/server support for partial or complete WebSocket messages
- **Mobility Improvements** never turn off Wi-Fi anymore when walking off home with slowly fading connection
  - Improved **Wi-Fi Assit**: Cross-Layer Mobility Detection from all Frameworks `(Network.framework, URLSession, Wi-Fi, Cellular)`
  - Apps can adopt **Multipath Transport** which requires the server to do so too
  - High-Level APIs `URLSession / Network` gain benefits from improvements

### [Advances in Networking, Part 2](https://developer.apple.com/wwdc19/713)

- **Bonjour** available on EVERY native platform
  - powers wide-area service discovery
  - native browser support in Network framework via `NWBrowser` (discover)
  - `NWListener` provides advertising support
  - `NSConnection` handles the connection
- **Building Framing Protocols**
  - Developers can write their own framing protocol that runs in the same networking thread as TCP
  - encapsulate or encode application messages
  - used to write common code across TCP/UDP transports
- **Collecting Metrics** more metrics for URLSession and newly created ones for Network
- **Optimistic DNS** enabled by default and improves performance for answers with short time-to-live
- **Request and Response Metrics** extended
  - byte counts, packet counts, round-trip-times
  - start and end reports to correspond to application activity
  - multiple reports simultaneously
  - per-path breakdown for mlti-path protocols
- **iPad Apps For Mac** opt-in to allow incoming conections - outgoing on by default
- **CNCopyCurrentNetworkInfo** needs capability `Access Wi Fi Information` & must meet at least 1 of:
  - permission to location
  - VPN enabled
  - if app is hotspot configurator it can access the info for networks it configured
- **Never switch on the current network device** but rather do:
  - `allowsExpensiveNetworkAccess = false`
  - `waitsForConnectivity = true`
  - `taskIsWaitingForConnectivity` delegate is called where you can switch to cellular data
- **Deprecations**
  - PAC files for schemes `file://` and `ftp://`
  - SPDY replaced by HTTP/2
  - Secure transport doesn't support TLS 1.3 / Use URLSession / Network.framework instead

### [Getting Started with Xcode](https://developer.apple.com/wwdc19/404)

- 1h presentation about all the power Xcode offers
- You learn about all the UI elements and functionality of Xcode
  - how to compile
  - fix issues in SwiftUI
  - add capabilities
  - create Swift Packages
  - how to add dependencies via Swpft Package Manager
  - unit testing
  - target memberships
  - running and debugging
  - documentation
  - and many more...
- It is perfectly suited for new developers that have never worked with Xcode, but also for experienced ones to get to know the new UI of Xcode 11

### [Modernizing Your UI for iOS 13](https://developer.apple.com/wwdc19/224)

- **Deprecation of LaunchImages** use Launch Storyboards instead
- **New App Store Requirement** Any app linking to iOS 13 must ensure correct layout at any size 
- **Split Screen Multitasking** is required for iPad Apps
- **UINavigationBarAppearance** customize `.standardAppearance` (iPhone portrait), `.compactAppearance` (iPhone landscape), `.scrollEdgeAppearance` (if attached to scrollView and scrolled to top, bar uses this one)
  - settable per `navigationItem` so customization per view controller possible (including color, transparency, …)
    `let appearance = navigationBar.standardAppearance.copy()`
    `/* configuration */`
    `navigationItem.standardAppearance = appearance`
- **UIBarButtonAppearance, UIToolBarAppearance**
- **UITabBarAppearance** customize `.stackedLayoutAppearance` (text below icon), `.inlineLayoutAppearance` (text right to icon; iPads), `.compactInlineLayoutAppearance` (text right to icon; landscape; smaller phones)
- **UIModalPresentationStyle.[automatic | formSheet | pageSheet]** are able to stack behind each other
  - `.automatic` is the new default; gets resolved at presentation time
  - get the old behavior by `viewController.modalPresentationStyle = .fullScreen`
  - sheets get gesture recognizer aded automatically to support `pull-to-dismiss` - opt-out possible (see link in description for example project)
  - **Appearance Callbacks Not Called for .PageSheet and .FormSheet** on presentingViewController:
    `viewWillAppear`, `viewDisappear`, `viewWillDisappear`, `viewDidDisappear`
- **Search UI** 
  - offers possibility to hide cancel button and scope control
  - expose `UISearchTextField` on `UISearchBar` so customization becomes possible
  - `Search Tokens` that represent complex searches
    - are copy&pastable and support drag&drop
    - can be created by user/developer from selected text in UISearchTextField
- **UITextInteraction** the new & easy way to control selection UI
- **Multi Selection in Table-/Collection Views** simply by Two-Finger-Swipe 
  - opt-in by implementing only 1 new delegate method for Tables and Collections
- **New Editing Gestures**
  - `pinch 3 fingers in`: copy selected text
  - `pinch 3 fingers out` paste copied text
  - `3 finger tap || 3 finger swipe back` undo
  - `3 finger swipe forward` redo
  - opt out by `responder.editingInteractionConfiguration = .none`
- **UIContextMenuInteraction** context menus with `rich preview`, `nested menus`, `in-line sections`
  - transform to context menus on macOS
  - `UIMenu` & `UIInteraction` provide hierarichal menu construction system
  - adopt by `view.addInteraction(UIContextMenuInteraction(delegate: self))`
  - customize how  view and menu will be presented: `UITargetedPreview & UITargetedDragPreview`
  - convenience delegate methods for context menus on UITableView & UICollectionView
  - `UIViewControllerPreviewing` (peek & pop) is deprecated for sake of this new API
  - replace long-press driven behavior/menus by this new API

### [What's New in Safari](https://developer.apple.com/wwdc19/515)

- **Desktop-class website browsing**
- **Legacy Safrai Extension Support** dropped for sake of `Content Blockers`, `Share Extensions`, `Safari App Extensions`
- **Safari Extensions**
  - deliver bundles with app OR after notarization via web site
  - Get the visible content of the web page (screenshot)
  - show and dismiss popovers
  - delegate informs about navigating/redirect to new site
- **Content Blocker**
  - associate content blocker with safari extension to get notified when content is blocked
- **UNiversal Links** for macOS so ordinary https links open app if installed

### [What's New in Safari Extensions](https://developer.apple.com/wwdc19/720)

- **Distributable** via 
  - App on AppStore (show up immediately in Safari)
  - App on your web site after running through the notarization service (show up in Safari after first launch of the app)
- **Unsigned Extensions** must be allowed each time Safari is run from the Developer menu
- **ContentBlocker** can now tell Safari App Extensions bout its activity
- **Page Naviagtion Delegate** informs about navigating/redirect to new site
- Adopting ContentBlocker and PageNavigation extensions allows 
  - replacing arbitrary contentent on websites
  - updating toolbar icon badge, e.g. with content items blocked count
  - blocking certain content from web sites you browse on
- **Screenshots** of web sites are now possible
- **Tab, Window, Page management**
  - Get base URI from native code without injection of script
  - Directly navigate to certain tabs without scripting from the extension
  - All open tabs and windows are visible from an extension
- **Popovers** can be shown/dismissed programmatically

- **Communication between App and Extension**
  - Possible by NSXPCConnection (extension and app must be part of the same app group)
  - Share data by using `UserDefaults(suiteName:)`
  - Sending messages from app >>> extension: `SFSafariApplication.dispatchMessage` 
  - Receive message in extension by implementing `SFSafariExtensionHandling.messageReceivedFromContainingApp` (Possible also when safari is not running - launched eventually)

### [Designing Audio-Haptic Experiences](https://developer.apple.com/wwdc19/810)

- **Core Haptics** allows to use taptic engine fully in **iPhone**
-  Developers can change the *Haptic Intensity* and the *Haptic Sharpness*
- 3 Guiding principles: *Causality*, *Harmony*, *Utility*
- **Causality** means that haptic feedback and the event causing it must match our expectations
- **Harmony** means how sound/haptic/visuals work together 
- **Utility** add audio/haptics that provide clear value to your UX
- **Work with Primitives** Transient (short) and Continuous (long)
  - both can be modulated by haptic intensity/sharpness which work different with the 2 primitives
- use transient building blocks for *sharp, crisp and short sounds*
- use continuous primitives for *smooth, extended sounds*

### [Introducing Core Haptics](https://developer.apple.com/wwdc19/520)

- Event based audio-/haptic rendering API - a synthesizer
- same feel on iPhone 8, 8 Plus, X, XS, XR, XS Max
- Not a replacement for UIFeedbackGenerator! Continue using it for `impact`, `selection` and `notification`
- Use **Core Haptics** for custom haptics and audio patterns
- Content  Classes: `CHHapticPattern`, `CHHapticEvengt`, `CHHapticParameter`
- Playback Classes: `CHHapticEngine`, `CHHapticPatternPlayer`, `CHHapticAdvancedPatternPlayer`
- Haptics can be coded inside the app or delivered as AHAP (Apple Haptic Audio Pattern) resource file
  - AHAP describes pattern as text
  - schema for JSON
  - Can use Swift Codable
  - Separate content from code
- Read more at the updated [Human Interface Guidelines (HIG) for haptics](https://developer.apple.com/design/human-interface-guidelines/ios/user-interaction/haptics/)

### [Expanding the Sensory Experience with Core Haptics](https://developer.apple.com/wwdc19/223)

- This is basically a merge of sessions [Designing Audio-Haptic Experiences](https://developer.apple.com/wwdc19/810) and [Introducing Core Haptics](https://developer.apple.com/wwdc19/520)
- For an in-depth example scroll the video to 40:10

### [Cryptography and Your Apps](https://developer.apple.com/wwdc19/709)

- **Cryptography is hard to get right** don't do it yourself unless you are an cryptography expert
- **Use [Data Protection](https://developer.apple.com/documentation/uikit/protecting_the_user_s_privacy/encrypting_your_app_s_files)** to protect your data on the device: `try data.write(to: fileURL, options: .completeFileProtection)` if you don't do so yet
- **Use Keychain** for Credentials and Keys. Never write them to the UserDefaults!
- **Apple Watch** can now be used to authenticate operations done on macOS
- **Use CloudKit** to share data across devices/users by encrypting assets in private CK DB
- **Use TLS 1.3** (Transport Layer Security) to ensure a secure network connection. Usage is ensured by using Network.framework or URLSession
- **Use SecTrust** to verify remote parties.
- **Adopt CryptoKit**
  - AES encryption inn just one line
  - strongkly typed interfaces
  - memory management
  - equatable conformances
  - generics
  - Hash Functions (`SHA-256`, `SHA-384`, `SHA-512`), Symmetric Key Cryptography (`HMAC`, `AES-GCM`), Public-Key Cryptography (`Curve25519`: `P-256`, `P-384`, `P-512`), Insecure Module (`MD5`, `SHA1`)
-  Using a signature to authorize an operation: `try P256.Signing.PrivateKey()`
- Constrain key usage by generating them with the SecureEnclave, e.g. only usable when unlocked `try SecureEnclave.P256.Signing.PrivateKey(accessControl:)`
- Customizing Authentication Context with `LAContext`: `try SecureEnclave.P256.Signing.PrivateKey(accessControl:authenticationContext:)`

- **Performant** through usage of CoreCrypto, hand-tuned assembly code and usage of the A12 Bionic
