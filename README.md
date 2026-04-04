# Snooze If You Can

> **Archived.** This project is archived pending a stable release of Apple's AlarmKit framework. See [ALARMKIT_LIMITATIONS.md](ALARMKIT_LIMITATIONS.md) for details.

[![Swift](https://img.shields.io/badge/Swift-6.0-orange.svg)](https://swift.org)
[![Platform](https://img.shields.io/badge/Platform-iOS%2018.0+-blue.svg)](https://developer.apple.com/ios/)
[![Licence](https://img.shields.io/badge/Licence-MIT-green.svg)](LICENSE)

An iOS alarm app that turns snoozing into charitable donations. Each time you hit snooze, a small payment goes to [Darussafaka](https://www.darussafaka.org), supporting education for children in need.

## Features

- **Alarms**: repeating or one-time, with custom labels and sounds
- **Escalating snooze costs**: each snooze is progressively more expensive ($0.99 to $9.99)
- **Hard limit**: after five snoozes you must wake up
- **Charitable impact**: 100% of snooze payments support education
- **Impact dashboard**: track donations, streaks, and wake-up statistics
- **Achievements**: earn badges for wake-up milestones
- **iCloud sync**: alarms and stats sync across devices
- **Accessibility**: full VoiceOver support and high-contrast mode

## Current Limitations

Apple announced AlarmKit at WWDC 2024 for iOS 18, but as of January 2026 the framework is not production-ready. Key issues include restricted entitlements, no simulator support, and incomplete system integration.

The app uses a hybrid approach: AlarmKit when available, falling back to UserNotifications with Critical Alerts. **This is not a replacement for the native Clock app.** See [ALARMKIT_LIMITATIONS.md](ALARMKIT_LIMITATIONS.md) for a full technical breakdown.

## Architecture

| Component | Technology |
|-----------|------------|
| Language | Swift 6.0 |
| UI | SwiftUI |
| Minimum iOS | 18.0 |
| Architecture | MVVM with ObservableObject |
| Persistence | UserDefaults (local) + CloudKit (sync) |
| Payments | StoreKit 2 (consumable in-app purchases) |
| Alarm delivery | AlarmKit (iOS 18+) with UserNotifications fallback |

See [ARCHITECTURE.md](ARCHITECTURE.md) for detailed system design.

## Getting Started

### Prerequisites

- Xcode 16.0 or later
- Physical iOS 18.0+ device (AlarmKit does not work in Simulator)
- Apple Developer account
- iCloud container configured for sync
- App Store Connect products configured for donations

### Build and Run

```bash
git clone https://github.com/umutguden/snooze-if-you-can.git
cd snooze-if-you-can
open SnoozeIfYouCan.xcodeproj
```

1. Select your development team in Signing & Capabilities.
2. Enable Push Notifications, Background Modes (fetch + remote notifications), and iCloud (CloudKit).
3. Select a physical device and press Cmd+R.

See [QUICKSTART.md](QUICKSTART.md) for detailed setup instructions including StoreKit configuration.

## How It Works

1. Set an alarm with a custom time and label.
2. When the alarm fires, a full-screen view presents two options:
   - **I'm Awake** dismisses the alarm for free and extends your streak.
   - **Snooze** charges a fee and reschedules for nine minutes.
3. Each successive snooze costs more. After five snoozes, the option is disabled.
4. All snooze payments go to Darussafaka.

| Snooze | Cost |
|--------|------|
| 1st | $0.99 |
| 2nd | $1.99 |
| 3rd | $2.99 |
| 4th | $4.99 |
| 5th | $9.99 |

## Contributing

Contributions are welcome, though the project is archived pending AlarmKit improvements. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Licence

MIT. See [LICENSE](LICENSE).

## Acknowledgements

- [Darussafaka Society](https://www.darussafaka.org) for their work supporting education in Turkey.
- Apple for the AlarmKit framework vision.

## Contact

HMD Developments, contact@hmddevs.org
