## New Project

```bash
flutter-elinux create <NAME> -e --platforms=elinux
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
            "deviceId": "elinux-gbm",
            "preLaunchTask": "Build Debug"
        }
    ]
}

```

Custom devices do not currently support debugging in `Profile` and `Release` modes.

### .vscode/tasks.json

```jsonc
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Build Debug",
            "command": "flutter-elinux",
            "args": ["build", "elinux", "--debug", "--target-backend-type=gbm"],
            "type": "shell",
            "problemMatcher": ["$dart-build_runner"],
        },
        {
            "label": "Build Profile",
            "command": "flutter-elinux",
            "args": ["build", "elinux", "--profile", "--target-backend-type=gbm"],
            "type": "shell",
            "problemMatcher": ["$dart-build_runner"],
        },
        {
            "label": "Build Release",
            "command": "flutter-elinux",
            "args": ["build", "elinux", "--target-backend-type=gbm"],
            "type": "shell",
            "problemMatcher": ["$dart-build_runner"],
        },
        {
            "label": "Run Profile",
            "command": "bash",
            "args": ["-c", "exec $(find build/elinux/arm64/profile/bundle -maxdepth 1 -type f) -b . -n -s 2"],
            "type": "shell",
            "problemMatcher": [],
            "dependsOn": "Build Profile"
        },
        {
            "label": "Run Release",
            "command": "bash",
            "args": ["-c", "exec $(find build/elinux/arm64/release/bundle -maxdepth 1 -type f) -b . -n -s 2"],
            "type": "shell",
            "problemMatcher": [],
            "dependsOn": "Build Release"
        }
    ]
}

```

## Configurations

### .gitignore

```ignore
.dart_tool
.flutter-plugins
.flutter-plugins-dependencies
build

```
