# Project Status

**Status**: Archived
**Last updated**: January 28, 2026
**Version**: 0.1.0

## Why Archived

Apple's AlarmKit framework, announced at WWDC 2024, is not yet production-ready. See [ALARMKIT_LIMITATIONS.md](ALARMKIT_LIMITATIONS.md) for a full technical breakdown.

## Completed

- Core alarm functionality (create, edit, delete, toggle)
- Escalating snooze costs ($0.99 to $9.99) with a hard limit of five
- Full-screen alarm UI
- Donation tracking and impact dashboard
- StoreKit 2 payment integration
- iCloud sync via CloudKit
- English and Turkish localisation
- VoiceOver and high-contrast accessibility support
- Dark mode
- Onboarding flow
- Settings screen
- Basic Apple Watch and home-screen widget support
- Achievement system and social accountability features
- Focus Mode integration

## Known Limitations

### Critical

- AlarmKit authorisation is inconsistent across devices and developers.
- No simulator support for AlarmKit.
- UserNotifications fallback cannot guarantee alarm delivery when the app is terminated or under resource pressure.
- Users have no reason to trust a third-party alarm app for critical wake-ups.

### Non-Critical

- No server-side payment verification (client-side only).
- Data export limited to clipboard (should use the share sheet).
- CloudKit sync not thoroughly tested.
- Watch app and widget have basic functionality only.
- No automated tests.

## Requirements to Un-Archive

### From Apple

- Public entitlement access for AlarmKit.
- Simulator support.
- Complete API implementation with documentation.

### From This Project

- Automated test suite (unit, UI, integration).
- Server-side payment verification.
- Proper charity integration with verified payment processing.

## Contributions

Contributions are welcome despite the archive status. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Contact

HMD Developments — contact@hmddevs.org
