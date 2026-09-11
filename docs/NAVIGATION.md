# EcoGrid Navigation

## Current router

EcoGrid uses GoRouter. The route configuration lives in `lib/main.dart`.

The current initial location is:

```text
/login
```

## Route map

| Route | Screen | Purpose |
| --- | --- | --- |
| `/login` | `LoginScreen` | Authentication entry screen |
| `/register` | `RegisterScreen` | Registration flow |
| `/` | `WelcomeScreen` | Welcome screen |
| `/splash` | `SplashScreen` | Splash/loading screen |
| `/ip` | `DeviceConfigScreen` | Device configuration |
| `/app-home` | `HomeScreen` | Main application home/dashboard |
| `/home` | `SensorDashboardScreen` | Environmental sensor dashboard |
| `/sensor-detail` | `SensorDetailPage` | Detailed sensor view and charting |
| `/image-gallery` | `ImageGalleryScreen` | Visual-record gallery |
| `/image-detail` | `ImageDetailScreen` | Selected image detail |
| `/device-connection` | `DeviceConnectionScreen` | Device connection information |
| `/about` | `AboutScreen` | Project/application information |
| `/notifications` | `NotificationsScreen` | Notification list |

`SensorDetailPage` receives sensor context through GoRouter `state.extra`, including the IP/address context, sensor type, and display title.

`ImageDetailScreen` receives an `ImageData` object through `state.extra`.

## Main navigation model

The current project uses `HomeScreen` as the principal application home. Earlier documentation referred to a `MainMenuScreen`, but that screen is no longer present in the current `lib/screens/` tree.

This distinction matters when reading historical design notes: references to `main_menu_screen.dart` are legacy references and must not be treated as current architecture.

## Bottom navigation

The visual navigation system follows the EcoGrid green/mint identity. Historical design notes defined a floating, rounded navigation bar with routes to home, sensors, gallery, and device settings.

The exact current behavior is defined by the Flutter widgets and route configuration, not by old planning documents. Changes to bottom navigation should preserve route compatibility and accessible touch targets.

## Navigation principles

- prefer GoRouter route changes over manual screen replacement when the route already exists;
- keep route names and `state.extra` contracts synchronized with the destination screen;
- do not add authentication or data assumptions to a navigation-only screen;
- test sensor-detail and image-detail routes whenever their payload contracts change;
- keep the home, sensor, reporting, gallery, and configuration flows clearly separated.
