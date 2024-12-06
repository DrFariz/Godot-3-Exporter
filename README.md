# Export Godot 3.x Project

A GitHub Action to export Godot 3.x projects to multiple platforms, including Android, HTML5, Windows, Linux, and macOS.

## Features
- Export your Godot project to multiple platforms.
- Supports custom export templates.
- Generates Android keystore for signing APKs.
- Outputs exported files as GitHub Artifacts.

---

## Inputs
| **Input Name**    | **Description**                                                             | **Required** | **Default**                                                                                           |
|--------------------|-----------------------------------------------------------------------------|--------------|-------------------------------------------------------------------------------------------------------|
| `godot-link`       | URL to download the Godot Headless binary.                                 | Yes          | `https://github.com/godotengine/godot/releases/download/3.6-stable/Godot_v3.6-stable_linux_headless.64.zip` |
| `templates-link`   | URL to download the Godot export templates.                                | Yes          | `https://github.com/godotengine/godot/releases/download/3.6-stable/Godot_v3.6-stable_export_templates.tpz` |
| `platform`         | The target platform for exporting (e.g., `Android`, `HTML5`).              | Yes          | `Android`                                                                                             |
| `filename`         | The name of the exported file (without extension).                        | Yes          | -                                                                                                     |
| `path`             | The version path for the export templates (e.g., `3.6.stable`).           | Yes          | `3.6.stable`                                                                                          |
| `user`             | The user name for Android keystore signing.                               | No           | -                                                                                                     |
| `keypass`          | The password for the Android keystore (min 6 characters, letters & numbers). | No           | -                                                                                                     |

---

## Outputs
| **Output Name**     | **Description**                                          |
|----------------------|----------------------------------------------------------|
| `artifact-path`      | The path to the exported artifact.                       |

---

## Example Usage

Add the following workflow to your repository:

```yaml
name: Export Godot Project

on:
  push:
    branches:
      - main

jobs:
  export:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Export Godot Project
        uses: yourusername/export-godot-action@v1
        with:
          godot-link: "https://github.com/godotengine/godot/releases/download/3.6-stable/Godot_v3.6-stable_linux_headless.64.zip"
          templates-link: "https://github.com/godotengine/godot/releases/download/3.6-stable/Godot_v3.6-stable_export_templates.tpz"
          platform: "Android"
          filename: "MyGame"
          path: "3.6.stable"
          user: "android_user"
          keypass: "securepassword123"
```

---

## Notes
1. Ensure your project contains a pre-configured `export_presets.cfg` file in the root directory.
2. The exported file will be uploaded as an artifact and can be downloaded from the **Artifacts** section of the workflow run.

---

## Platforms Supported
- **Android**
- **HTML5**
- **Windows Desktop**
- **Linux/X11**
- **macOS**

---

Feel free to report issues or contribute to this repository to improve the action!
