
---

```markdown
# StepLock

**StepLock** is a motivational Android app that promotes physical activity by locking the device once the user reaches a predefined step limit. It continuously tracks steps in the background and uses Android’s Device Policy Manager to enforce the lock.

---

## Features

- Real-time step tracking (low battery usage)
- Runs in the background via a Foreground Service
- Automatic device lock when step goal is reached
- Uses the built-in **TYPE_STEP_COUNTER** sensor
- Device Admin integration for secure locking

---

## Tech Overview

| Component | Implementation |
|---------|----------------|
| Language | Kotlin |
| Minimum Android | API 26 (Android 8.0) |
| Step Tracking | `SensorManager` + `Sensor.TYPE_STEP_COUNTER` |
| Background Execution | Foreground Service |
| Lock Enforcement | `DevicePolicyManager` / Device Admin API |

---

## Project Structure

```

app/
└─ java/com/example/steplock/
├─ admin/
│   └─ StepLockDeviceAdmin.kt      # Handles device admin setup
├─ service/
│   └─ StepCounterService.kt       # Tracks steps + triggers lock
└─ MainActivity.kt                 # UI entry point / service launcher

res/
└─ xml/
└─ device_admin_receiver.xml       # Device admin configuration

````

---

## Required Permissions

```xml
<uses-permission android:name="android.permission.ACTIVITY_RECOGNITION" />
<uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
````

---

## Getting Started

1. **Clone the repository**

   ```sh
   git clone https://github.com/yourusername/steplock.git
   ```

2. **Open in Android Studio**

3. **Enable Device Admin**

   * Launch the app
   * Tap *Enable Device Admin*
   * Confirm permissions

4. **Start Tracking**

   * Tap *Start StepLock*
   * The app will continue logging steps even when minimized

---

## Customization

| Setting           | Location                              | Description                          |
| ----------------- | ------------------------------------- | ------------------------------------ |
| Step Goal         | `StepCounterService.kt` → `stepLimit` | Number of steps before lock          |
| Notification Info | `startForegroundService()`            | Adjust title/text                    |
| Lock Behavior     | `lockDevice()`                        | Uses `DevicePolicyManager.lockNow()` |

---

## Notes

* Some devices may restrict background services — disabling battery optimization improves reliability.
* Step counter values reset after device reboot unless tracked manually.
* Works with phones that include a hardware step counter.

---

## Roadmap

* User-configurable step goal
* Progress shown in notification
* Automatic restart on boot
* Daily step reset

---

## License

MIT License — free for personal and commercial use.

```



