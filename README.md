# Sound Assistant 🔊

Sound Assistant is a lightweight Android utility that provides instant access to your device's native volume controls via a draggable floating button and a Quick Settings tile.

## ✨ Features

- **Quick Settings Integration**: Toggle the assistant on/off directly from your Android notification shade.
- **Floating Rounded Button**: A sleek, minimal, and fully round floating button that stays on top of other apps.
- **One-Tap Volume Control**: Instantly triggers the system's native volume slider when clicked.
- **Lag-Free Interaction**: Optimized with hardware acceleration and precision touch handling for smooth dragging.
- **Boot Persistence**: Automatically restarts after a device reboot or app update if previously enabled.
- **Battery Efficient**: Uses a sticky foreground service designed to withstand aggressive RAM management.

## 🎨 Design

The floating button features a modern, minimal aesthetic:
- **Shape**: Perfect circle (transparent background).
- **Outer Ring**: A vibrant blue-to-purple sweep gradient.
- **Center**: A clean white core.
- **Detail**: A subtle purple accent dot for a unique look.
- **Size**: Compact 40dp diameter for a non-intrusive experience.

## 🛠 Technical Implementation

### Key Components
- **`SoundAssistantTileService`**: Manages the Quick Settings tile state and service lifecycle.
- **`FloatingButtonService`**: A Foreground Service (`specialUse`) that manages the `WindowManager` overlay and touch events.
- **`BootReceiver`**: A Broadcast Receiver that listens for `ACTION_BOOT_COMPLETED` to restore service state.

### Permissions Used
- `SYSTEM_ALERT_WINDOW`: To display the floating button over other applications.
- `FOREGROUND_SERVICE` & `FOREGROUND_SERVICE_SPECIAL_USE`: To ensure the service remains active in the background.
- `POST_NOTIFICATIONS`: Required for Android 13+ to show the mandatory service notification.
- `RECEIVE_BOOT_COMPLETED`: To allow the app to restart after a device reboot.

## 🚀 How to Use

1. **Build & Install**: Run the project on an Android device (API 31+).
2. **Setup Tile**:
   - Swipe down twice to open the full Quick Settings panel.
   - Tap the Edit (pencil) icon.
   - Find **Sound Assistant** and drag it into your active tiles.
3. **Enable**: 
   - Tap the Sound Assistant tile.
   - Grant the **"Display over other apps"** permission when prompted.
   - (Android 13+) Ensure **Notification** permissions are granted.
4. **Interact**: Drag the button anywhere on your screen. Tap it to see your volume controls!

## ⚙️ Configuration
In Android Studio, if you encounter a "Default Activity not found" error when running:
1. Go to **Run > Edit Configurations**.
2. Set **Launch Options > Launch** to **Nothing**.
*(Since this app is a background utility, it does not require a traditional UI activity.)*
