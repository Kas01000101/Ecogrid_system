# EcoGrid UI History

## Purpose

This document consolidates earlier Spanish planning files for the EcoGrid home, quick-access controls, sensor dashboard, hero image, and bottom navigation.

These notes are historical design context, not a current implementation contract. When they conflict with the Flutter code, the current code is authoritative.

## Historical dashboard refinement

An early dashboard proposal focused on improving the existing interface without introducing new product features. It targeted the active-sensor summary, quick-access controls, and last-update information.

The proposed improvements included:

- clearer text hierarchy and more consistent typography;
- larger, more accessible touch targets;
- improved card padding and vertical rhythm;
- softer shadows and consistent elevation;
- clearer visual feedback for hover and press states;
- stronger contrast and screen-reader-friendly controls;
- responsive spacing on smaller displays.

One early palette experiment used a neutral dashboard treatment with white cards, dark text, gray secondary text, and a blue accent. This was exploratory work and is not the current EcoGrid visual system.

## Historical quick-access design

Later iterations explored a green visual system for the home screen using combinations such as:

```text
#CEE2BE  light green
#98C98D  glass/mid green
#63B069  medium green
#247E5A  dark green
#0F6659  shadow green
#00444D  dark text/icon color
```

The design goals included:

- larger touch targets;
- stronger icon/text hierarchy;
- more consistent spacing;
- rounded cards and buttons;
- restrained gradients and shadows;
- responsive sizing across mobile widths.

Historical proposals targeted minimum touch areas around 44 px and recommended avoiding excessive simultaneous color tones.

## Historical sensor-dashboard button proposal

A later Sensor Dashboard proposal used the brighter EcoGrid mint palette:

```text
#00E0A6  primary mint
#009E73  secondary green
#E6FFF5  light mint surface
#6DFFF5  optional hover/highlight
```

The proposed action button was a pill-style `Show Details` control placed within each sensor card. Accessibility goals included visible focus states, sufficient contrast, and a minimum practical touch target.

The old document scoped those changes to `SensorDashboardScreen` and explicitly avoided changing Sensor Detail charts.

## Historical bottom-navigation design

The bottom navigation design evolved toward an Eco-Corporate glassmorphism treatment with:

- a rounded floating container;
- mint active state;
- dark green inactive state;
- subtle border and shadow;
- home, sensors, gallery, and settings destinations;
- accessible hit areas and small transition feedback.

The current routes are documented in [`NAVIGATION.md`](NAVIGATION.md).

## Historical main-menu image work

Several planning files described a former `MainMenuScreen` with a large `img_main_menu_screen.jpg` hero image, rounded lower corners, overlay controls, guide content, and quick-access cards.

Those plans included experiments with:

- hero heights between roughly 35% and 55% of the viewport;
- `Stack`-based layout;
- `SafeArea` for overlay controls;
- `ClipRRect` for hero-image clipping;
- responsive breakpoints;
- image precaching;
- soft shadows and translucent content cards.

`MainMenuScreen` is no longer part of the current screen tree. `HomeScreen` is the current application home, so these notes are retained only as design history.

## Historical palette experiment

One detailed proposal also explored an agricultural-green variant:

```text
#E8F3EA  light background
#3C8D2F  primary green
#A9DB80  gradient start
#6FBF73  gradient end
#2E5F3D  dark detail color
#FFD166  warm accent
```

This palette was a proposal, not a repository-wide license to replace the current Material 3 color system.

## Consolidated source files

This historical document replaces the following former root-level planning files:

- `interfaz.md`
- `ANALISIS_BOTONES_ACCESO_RAPIDO.md`
- `BOTTOM_NAVIGATION_STRUCTURE.md`
- `DOC_SENSOR_DASHBOARD_BUTTONS.md`
- `IMPLEMENTACION_IMAGEN_MAIN_MENU.md`
- `PROPUESTA_CAMBIOS_MAIN_MENU.md`
- `PROPUESTA_CAMBIOS_MAIN_MENU_DETALLADA.md`

The goal of consolidation is to keep useful design rationale without presenting obsolete Spanish planning notes as current implementation instructions.
