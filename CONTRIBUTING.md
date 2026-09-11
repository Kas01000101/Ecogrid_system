# Contributing to EcoGrid

Thank you for your interest in contributing to EcoGrid.

## Development setup

Before making changes:

```bash
flutter pub get
flutter analyze
flutter test
```

Use a supported Flutter SDK and keep the project compatible with the Dart SDK constraint declared in `pubspec.yaml`.

## Pull requests

A pull request should:

- explain what changes and why;
- keep unrelated refactors out of the same change when possible;
- include or update tests when behavior changes;
- pass `flutter analyze` and `flutter test`;
- preserve existing navigation and connection behavior unless the change intentionally modifies it;
- document new dependencies and their purpose.

## IoT and networking changes

Changes to ESP32 or API communication should consider:

- request timeouts;
- application foreground/background lifecycle;
- retry behavior;
- connection-state reporting;
- local-network reachability;
- failure handling when the external API or device is unavailable.

Avoid hard-coding private credentials or environment-specific secrets.

## Reports and files

Changes to PDF or CSV generation should preserve readable output, file portability, and platform-safe file handling. Add tests for date ranges, generated data, or file behavior when appropriate.

## Security and private data

Never commit:

- API secrets or tokens;
- ESP32 credentials;
- Android signing keys or keystores;
- `key.properties` containing secrets;
- personal information;
- private datasets;
- production-only environment configuration.

## Licensing

Source-code contributions are distributed under the repository's MIT License unless a file explicitly states otherwise. Only contribute code or assets that you have the right to submit.
