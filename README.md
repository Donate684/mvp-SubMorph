# SubMorph for mpv
SubMorph is part of project **[mpv anime](https://github.com/Donate684/mpv-anime)**. It's a powerful Lua script for mpv that intelligently restyles ASS/SSA subtitles to provide a consistent and predictable viewing experience across all your media.

It solves the common problem of subtitles appearing too large or too small by scaling them relative to a fixed reference height (e.g., 720p), ensuring your custom style looks perfect regardless of the video's or subtitle's original resolution.

![preview](preview.png?raw=true)

## 📋 Key Features

* **Unified Style Scaling:** Forget tweaking styles for every file. Set your preferred look once against a `reference_height`, and SubMorph handles the rest.
* **Smart Dialogue Detection:** A heuristic engine identifies which subtitle styles are used for dialogue, applying your custom style only where it's needed and preserving the original look of signs, titles, and karaoke.
* **Embedded & External Subtitle Support:** Seamlessly processes both external `.ass`/`.ssa` files and embedded subtitle tracks (requires `ffmpeg`).
* **Clean & Temporary:** Works by creating temporary subtitle files in a dedicated folder, which is automatically cleaned up on exit. Your original files are never modified.
* **Fully Configurable:** Fine-tune every aspect of your target style—from font and colors to outlines and margins—via a simple `.conf` file.

## ⚙️ Requirements

* **[mpv](https://mpv.io/)**: The video player.
* **[ffmpeg](https://ffmpeg.org/)**: Required for processing embedded subtitle tracks. It must be available in your system's `PATH` or mpv folder.

## 🚀 Installation

1.  Download the `SubMorph.lua` file from this repository.
2.  Place it in your `mpv` scripts folder.
3.  (Optional but Recommended) To configure the script, create a file named `SubMorph.conf` and place it in the `script-opts` folder.

## 🛠️ Configuration
You can customize the script's behavior by editing SubMorph.conf. Here are some of the key options:

```
# SubMorph.conf

# Enable mode: 'always', 'manual', or 'no'.
enable=always

# The script will scale styles as if you were watching a video
# at this reference height (in pixels).
reference_height=720

# --- Define your target style for the reference_height ---

# Font name and size.
font_name=Candara
font_size=65

# Outline thickness and shadow distance.
outline=2.5
shadow=1.0

# Main text color in &HBBGGRR format.
primary_colour=&H00FFFFFF

# Outline color.
outline_colour=&H00000000
```

You can find a complete, commented configuration file in this repository.

## ▶️ Usage
The script has two primary modes of operation, set by the enable option in SubMorph.conf.

**Automatic Mode (Default)**
With ```enable=always```, the script runs automatically whenever a new file is loaded or the subtitle track is changed. No user interaction is required.

**Manual Mode**
With ```enable=manual```, the script will only run when you explicitly trigger it. You can do this by binding a key in your ```input.conf``` file.

Add the following line to input.conf to bind the action to Q:

```Q script-message run-submorph```

Pressing Q will now apply the SubMorph style to the currently active subtitle track.


### 📜 License
This project is licensed under the MIT License. See the LICENSE file for details.
