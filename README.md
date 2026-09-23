# Google Calendar Week View Widget for Android

A high-performance, production-ready Android Home Screen Widget built with **Jetpack Glance 1.1**, **Kotlin Coroutines**, and **Material You (Material 3)**. Closely replicates the native Google Calendar week widget.

## 🚀 Key Features

1. **7-Day Overlapping Grid**:
   - Header row showing day initials (M, T, W, T, F, S, S) and date numbers.
   - Solid circular pill for "Today" filled with `GlanceTheme.colors.primary` and `onPrimary` typography.
   - Pinned all-day events row at the top.
   - Flexible timed events stack with 4dp corner radius.
2. **Material You Dynamic Colors**:
   - Fully supports Android 12+ dynamic wallpaper color extraction (`GlanceTheme`).
   - Adapts automatically to Light Mode and Dark Mode.
3. **Contrast-Aware Event Color Rendering**:
   - Evaluates luminance (`ColorUtils.calculateLuminance`) of the event's calendar color.
   - Automatically switches between crisp white and dark text to ensure WCAG accessibility.
4. **CalendarContract.Instances Querying**:
   - Queries `CalendarContract.Instances` instead of raw `Events`, ensuring that all recurring instances (daily, weekly, bi-weekly, monthly) are properly calculated by the Android OS.
5. **Real-time Updates with ContentObserver**:
   - Avoids aggressive battery-draining polling (`updatePeriodMillis="0"`).
   - Uses a `ContentObserver` on `CalendarContract.Events.CONTENT_URI` to automatically refresh the widget in real time when any event is created, edited, or deleted.
6. **Native Google Calendar Interactivity**:
   - Tapping an event launches the exact native Google Calendar event detail screen via `Intent(Intent.ACTION_VIEW, ContentUris.withAppendedId(CalendarContract.Events.CONTENT_URI, eventId))`.
   - Tapping the month header jumps to today's date in Google Calendar.
7. **Permission Handling**:
   - Handles `Manifest.permission.READ_CALENDAR` gracefully with a Material 3 inline prompt and a dedicated Configuration Activity.

## 📦 How to Import into Android Studio

1. Open **Android Studio Ladybug (2024.2+)** or newer.
2. Select **File > New > Import Project...** and choose this project root.
3. Sync Gradle and run on a device or emulator running **Android 12 (API 31) or higher** to experience Material You dynamic colors.
4. Long-press on the home screen, select **Widgets**, find **Calendar Widget**, and drag the **Week View (4x3)** widget onto your home screen.