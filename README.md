# Portra Camera — prototype 0.1.0

Android camera prototype targeting Google Pixel 7a.

## What this first build does
- CameraX preview and still capture.
- Uses CameraX `CAPTURE_MODE_MAXIMIZE_QUALITY` and JPEG quality 100.
- Saves two files in `Pictures/PortraCamera`:
  - `Portra_Original_*.jpg`: untouched camera JPEG.
  - `Portra_WarmCinema_*.jpg`: deterministic, non-AI warm cinematic grade.
- Processing is local on-device. No network permission or analytics SDK is included.

## Important limitations
- This is a first technical prototype, not a finished film-emulation product.
- The warm profile is an initial hand-authored transform, not a calibrated Kodak Portra 400 reproduction.
- This version does not yet capture RAW/DNG, expose manual Camera2 controls, record video, or provide a live graded viewfinder.
- CameraX output quality and available resolutions depend on the device camera implementation.
- Pixel 7a testing is required before treating image quality or compatibility as verified.

## Build
Open this folder in Android Studio (JDK 17; Android SDK 35), allow Gradle sync, then:
`Build > Build Bundle(s) / APK(s) > Build APK(s)`

The generated APK will be under `app/build/outputs/apk/debug/`.

## Next engineering milestones
1. Pixel 7a device test; verify output dimensions, orientation, metadata and gallery saving.
2. Add Camera2 interop for exposure compensation, focus, white balance and lens selection where supported.
3. Add RAW/DNG capture when the selected camera advertises RAW capability.
4. Replace the first-pass RGB transform with a higher-fidelity color pipeline (linear-light processing, 3D LUT, highlight handling and optional grain).
5. Add video capture and a real-time GPU color pipeline with matched still/video rendering.
