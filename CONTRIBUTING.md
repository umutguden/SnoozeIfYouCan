# Contributing

Contributions are welcome. By contributing, you agree to the project's licence and Code of Conduct.

> **Note**: This project is archived pending AlarmKit improvements. Contributions are still accepted, but features depending on AlarmKit may not be fully functional.

## Reporting Bugs

Check existing [issues](https://github.com/umutguden/snooze-if-you-can/issues) first. When filing a bug report:

- Use a clear, descriptive title.
- Include exact steps to reproduce the problem.
- Describe expected versus actual behaviour.
- Include your iOS version and device model.
- Attach screenshots or logs if relevant.

## Suggesting Features

Open an issue with the `enhancement` label. Describe the feature, its use case, and why it would be valuable.

## Pull Requests

1. Fork the repository.
2. Create a feature branch from `main`.
3. Make focused, minimal changes.
4. Follow existing code style and naming conventions.
5. Test on a physical device where possible.
6. Commit with clear, imperative-tense messages.
7. Open a pull request against `main` with a description of changes, testing notes, and any documentation updates.

## Code Style

- Swift style: follow the existing codebase conventions.
- Use meaningful names for types, functions, and variables.
- Keep functions focused and concise.
- Use Swift's type system and optionals properly.

## Project Structure

- `App/`: main app entry point.
- `Models/`: data models (Alarm, UserStats, Achievement, etc.).
- `Services/`: managers for alarms, payments, CloudKit, notifications.
- `Views/`: SwiftUI views organised by feature.
- `Design/`: theme, reusable components, and animations.
- `Localization/`: string catalogues and translations.
- `Intents/`: AlarmKit and Focus Mode intents.

## Areas for Contribution

- Automated tests (unit, UI, integration).
- Additional localisations.
- Accessibility improvements.
- Monitoring and documenting AlarmKit changes in new iOS betas.
- Code quality improvements and refactoring.

## Questions

Open an issue with the `question` label.
