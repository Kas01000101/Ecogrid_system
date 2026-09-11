# EcoGrid Implementation Status

## Current state

EcoGrid is a functional Flutter mobile client for environmental IoT monitoring. The current repository includes authentication screens, device configuration, a home dashboard, sensor monitoring, sensor details, image records, device-connection information, notifications, project information, historical reporting, and PDF/CSV export support.

Application version from `pubspec.yaml`:

```text
0.1.2+2
```

## Implemented screens

| Screen | Status | Responsibility |
| --- | --- | --- |
| `LoginScreen` | Implemented | Authentication entry |
| `RegisterScreen` | Implemented | Registration flow |
| `WelcomeScreen` | Implemented | Welcome experience |
| `SplashScreen` | Implemented | Splash/loading flow |
| `DeviceConfigScreen` | Implemented | Device configuration |
| `HomeScreen` | Implemented | Main application dashboard |
| `SensorDashboardScreen` | Implemented | Sensor selection and monitoring overview |
| `SensorDetailPage` | Implemented | Detailed sensor data and charts |
| `ImageGalleryScreen` | Implemented | Visual-record gallery |
| `ImageDetailScreen` | Implemented | Image detail view |
| `DeviceConnectionScreen` | Implemented | Connection information/status experience |
| `NotificationsScreen` | Implemented | Notification UI |
| `AboutScreen` | Implemented | Project/application information |
| `PDFPage` | Implemented | Historical reports and PDF/CSV export |

## Current architecture notes

- `HomeScreen` is the current application home.
- Historical documents that referenced `MainMenuScreen` describe an older UI architecture.
- `ConnectionManager` centralizes polling, state, retries, and lifecycle-aware connectivity.
- GoRouter defines the current navigation contract in `lib/main.dart`.
- Reporting is separated from live connection management.

## Dependencies of note

The project currently uses:

- GoRouter for navigation;
- SharedPreferences for local configuration;
- `http` and Dio for networking;
- `fl_chart` for charts;
- `pdf` and `printing` for PDF output;
- `csv` for CSV export;
- `path_provider` and `open_file` for local files;
- `share_plus` for sharing;
- `flutter_svg` and `google_fonts` for UI assets.

## Quality checks

Before merging behavior changes, run:

```bash
flutter pub get
flutter analyze
flutter test
```

## Maintenance notes

Older documentation included unverified performance benchmarks and several conflicting endpoint examples. Those claims are not treated as current guarantees. The maintained documentation in `docs/` follows the present Flutter code where possible and clearly marks backend behavior that must be verified outside this repository.

## Repository boundary

This repository does not contain the canonical ESP32 firmware or external hosted backend. Changes to those systems should be documented in their own repositories or deployment documentation rather than represented here as if they were part of this codebase.
