# Quick Start Guide

## Prerequisites

- Xcode 16.0 or later
- macOS Sonoma or later
- Physical iOS 18.0+ device (AlarmKit does not work in Simulator)
- Apple Developer account (free or paid)
- iCloud account for testing sync features

## 1. Clone the Repository

```bash
git clone https://github.com/umutguden/snooze-if-you-can.git
cd snooze-if-you-can
```

## 2. Open in Xcode

```bash
open SnoozeIfYouCan.xcodeproj
```

Wait for Xcode to finish indexing.

## 3. Configure Code Signing

1. Select the **SnoozeIfYouCan** project in the navigator.
2. Select the **SnoozeIfYouCan** target.
3. Go to the **Signing & Capabilities** tab.
4. Choose your team from the dropdown.

If you get signing errors, change the bundle identifier to something unique (e.g. `com.yourname.SnoozeIfYouCan`) and repeat for all targets: SnoozeIfYouCan, SnoozeIfYouCanWatch, SnoozeAlarmWidget.

## 4. Configure Capabilities

Ensure the following are enabled:

- **Push Notifications**
- **Background Modes**: background fetch and remote notifications
- **iCloud**: CloudKit with container `iCloud.com.snoozeifyoucan.app` (or your own identifier)

To use your own iCloud container, update the identifier in `CloudKitManager.swift`:

```swift
container = CKContainer(identifier: "iCloud.YOUR-BUNDLE-ID")
```

## 5. Build and Run

1. Connect your iPhone via USB or Wi-Fi.
2. Select your device from the device menu.
3. Press Cmd+R.

Requires iOS 18.0+ and Debug configuration.

## 6. Grant Permissions

On first launch:

1. Complete the onboarding screens.
2. Tap "Enable Notifications" and allow when prompted.

For best alarm reliability, enable Critical Alerts in iPhone Settings under the app's notification settings.

## 7. Create Your First Alarm

1. Tap **+** in the top right.
2. Set your desired time.
3. Add a label and optionally select repeat days.
4. Tap **Save**.

## 8. Test the Alarm

Set an alarm one to two minutes in the future. When it fires:

1. A notification appears (if the app is in the background).
2. Tapping it opens a full-screen alarm view.
3. Choose "I'm Awake" to dismiss for free, or "Snooze" to pay and snooze for nine minutes.
4. Each snooze costs progressively more. After five, snoozing is disabled.

## Troubleshooting

**AlarmKit Not Available**: Expected in Simulator and without entitlements. The app falls back to UserNotifications automatically.

**Notifications Not Appearing**: Check notification permissions, disable Do Not Disturb or Focus modes, enable Critical Alerts and Background App Refresh. Restart the device if needed.

**Build Errors**: Change the bundle identifier and select your team. Confirm Push Notifications and iCloud are enabled in Capabilities. Ensure the device is running iOS 18+.

**Crash on Launch**: Delete the app, clean the build folder (Cmd+Shift+K), then build and run again.

## StoreKit Configuration (Optional)

To test payments:

1. Create an app record in [App Store Connect](https://appstoreconnect.apple.com).
2. Under In-App Purchases, create five consumable products:
   - `com.snoozeifyoucan.donation.tier1` ($0.99)
   - `com.snoozeifyoucan.donation.tier2` ($1.99)
   - `com.snoozeifyoucan.donation.tier3` ($2.99)
   - `com.snoozeifyoucan.donation.tier4` ($4.99)
   - `com.snoozeifyoucan.donation.tier5` ($9.99)
3. Create a sandbox tester account, sign out of the App Store on your device, and sign in with the sandbox account when prompted during a test purchase.

## Apple Watch Setup (Optional)

Pair an Apple Watch running watchOS 10 or later. Select the SnoozeIfYouCanWatch scheme in Xcode, then build and run.

## Widget Setup (Optional)

Long-press the home screen, tap **+**, find Snooze If You Can, and add a widget. It displays the next scheduled alarm.

## Further Reading

- [README.md](README.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)
- [ARCHITECTURE.md](ARCHITECTURE.md)
- [ALARMKIT_LIMITATIONS.md](ALARMKIT_LIMITATIONS.md)
