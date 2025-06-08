## New Project

```bash
flutter create <NAME> -e --platforms=web
```

## VS Code Settings

### .vscode/launch.json

```jsonc
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug",
            "request": "launch",
            "type": "dart",
            "flutterMode": "debug",
            "deviceId": "chrome"
        }
    ]
}

```

## Build

```bash
flutter build web --wasm
```

## "No Device" when using non-standard versions of Chrome

### \> Preferences: Open User Settings (JSON)

```diff
    ...
+   "dart.env": {
+     "CHROME_EXECUTABLE": "/Applications/<CHROME_EXECUTABLE>.app/Contents/MacOS/<CHROME_EXECUTABLE>"
+   },
```
