# LapTime User Guide (English)

## Introduction
LapTime is an iOS app for automatic lap time measurement using the device camera. The app detects motion in the camera frame, measures lap times in real time, and stores results locally. Optionally, data can be sent to a backend or transmitted over the local network to an Apple TV view (LapTimeLeaderboard). The goal is fast, stable race capture with clear live feedback and traceable results.

## Quick Start
Step 1: Open the app and switch to the "Setup" tab if you land there on first launch. Set your driver name. Alternatively, sign in with Discord to have the name filled automatically.

Step 2: Select a race from the list or create a new one. When creating, provide a name and a track code. If the code is valid, a track preview appears.

Step 3: Choose your car. The app saves your selection and uses it for all laps.

Step 4: Set the maximum lap count. Once the limit is reached, the race ends automatically and you are taken to the leaderboard.

Step 5: Switch to the "Race" tab and position the device so the finish line is in view. Tap "Start" to arm the measurement. The first movement starts the race, and each subsequent movement counts as a lap.

Step 6: Open the "Leaderboard" tab to review results per race and inspect lap details. Use the race picker at the top to switch to a different race. Tap a driver in the list to open the detailed lap times view.

## App Overview
The iOS app is organized into three main areas: Race for live capture, Leaderboard for analysis, and Setup for configuration. This keeps the workflow clear and separates capture, review, and settings.

### Race: Live Capture
In the Race area you see the camera view with measurement overlays. The app uses difference-image detection: motion within a defined region triggers the start and subsequent laps. An internal cooldown prevents immediate double counting, and a minimum lap time is enforced to reduce false triggers.

During a race, each lap is stored as its own entry. The app marks the best lap with a distinct sound and signals when the race ends after the maximum lap count. When you rotate the device, the layout adapts and shows timing and controls in a side panel.

### Leaderboard: Results and Details
The leaderboard aggregates laps per race and driver. You can select a race and view rankings by best lap and total time. A detail view shows all laps for a driver with timestamps; the best lap is highlighted.

Depending on the mode, the leaderboard shows local data only or merges local data with backend data. Entries can be deleted, with local data handled separately from backend data. This makes it clear what is stored locally versus fetched from the backend.

### Setup: Driver, Race, Car, and Network
In Setup you define your driver, select a race, and choose a car. If you are signed in with Discord, the app uses the name from your account. For local driver names, everything stays on the device.

In the Race section you can select an existing race or create a new one. Creating a race requires a name and track code. A valid track code enables a track preview.

In the Car section you choose the car that is stored with every lap. The app falls back to a default car if none is selected.

The network mode controls where data is stored. In local mode, lap times remain on the device and can optionally be sent to Apple TV. In the standard configuration, backend data is also loaded and merged with local results.

Additional settings include sound options and experimental detection visualizations, such as detection zones and debug overlays.

## Camera and Detection Logic
The app uses difference-image detection. A central region of the camera frame (ROI) is analyzed. When a significant change is detected, it is interpreted as motion. The detection threshold and the size of the observed region can be fine-tuned in the camera setup.

The first detected movement starts the race and sets the timestamp. Each further movement that exceeds the minimum lap time is saved as a lap. Time calculation is precise and displayed in seconds.

## Local Network and Apple TV (LapTimeLeaderboard)
LapTime can send lap times to an Apple TV view in real time. Once local network mode is enabled and an Apple TV is reachable on the same network, new laps are transmitted over a peer-to-peer connection. The Apple TV app shows the live leaderboard and allows switching races or deleting stored laps.

## Data Storage and Synchronization
Lap times are stored locally in a persistent database so results remain after the app is closed. In standard mode, backend data is also loaded and merged with local laps. This lets you see local measurements immediately while still accessing centrally stored results.

In local network mode, no backend connection is made. The app works entirely with local data and the optional Apple TV view.

## Tips for Better Measurements
Position the device so the finish line is stable in the frame, and avoid excessive shaking. Adjust sensitivity only if false detections occur or movement is not detected. A larger ROI captures more of the image but can be more prone to noise.

If lap counting stops unexpectedly, check Setup to confirm driver, race, and car are set correctly and that the maximum lap count has not already been reached.
