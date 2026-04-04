# AlarmKit Limitations

> This project is archived pending a stable release of AlarmKit. See [PROJECT_STATUS.md](PROJECT_STATUS.md) for overall project status.

## Background

Apple announced AlarmKit at WWDC 2024 as a framework for third-party alarm apps to integrate with the iOS system. As of January 2026, it remains unsuitable for production use.

## Issues (January 2026)

### Entitlement Restrictions

AlarmKit requires special entitlements that are not automatically granted. Many developers report requests being denied. The criteria for approval are unclear.

### No Simulator Support

The framework is completely non-functional in the iOS Simulator. Testing requires a physical device, which makes development and debugging significantly harder.

### Incomplete Implementation

The framework appears to be in a beta state despite shipping with iOS 18. Documentation is sparse, APIs are missing, and behaviour varies across iOS versions.

### Poor System Integration

Alarms created with AlarmKit do not appear in the native Clock app. Users cannot manage alarms from both apps, resulting in a confusing experience. Dynamic Island and Lock Screen widget integration is unreliable.

## Implementation Strategy

This project uses a hybrid fallback approach:

**Primary** (iOS 18+ with entitlements):

```swift
if #available(iOS 18.0, *), AlarmKitService.shared.isAuthorized {
    try await AlarmKitService.shared.scheduleAlarm(alarm)
}
```

**Fallback** (UserNotifications with Critical Alerts):

```swift
else {
    NotificationManager.shared.scheduleAlarm(alarm)
    NotificationManager.shared.requestPermission(allowCritical: true)
}
```

An in-app full-screen `ActiveAlarmView` handles snooze and dismiss actions regardless of which delivery method is used.

## Why the Fallback Is Insufficient

- Notifications can be cleared by the user or delayed by the system.
- Background execution is not guaranteed; iOS may terminate the app.
- The device cannot be woken from deep sleep reliably.
- Users rightly expect the same reliability as the native Clock app, which has special system privileges.

## Alternatives Considered

| Approach | Outcome |
|----------|---------|
| Ship without AlarmKit | Rejected. Cannot guarantee alarm reliability. |
| Apply for health/safety exception | Not applicable to alarm apps. |
| Open-source and archive | Chosen. Preserves work and documents the challenges. |

## Advice for Other Developers

- Be honest with users about what your app can and cannot do.
- Always test on physical devices; the simulator hides AlarmKit problems.
- Keep UserNotifications as a fallback.
- Monitor WWDC and iOS betas for AlarmKit improvements.
- File feedback with Apple about specific issues.

## Contact

Open an issue with the `alarmkit-question` label for questions.

**Last updated**: January 28, 2026
