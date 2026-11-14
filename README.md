<p align="center">
  <img src="docs/images/lemongx.png" width="200" alt="Lemon GX icon">
</p>

<h1 align="center">Lemon GX App</h1>

<p align="center">
  The Android app that installs <a href="https://github.com/MastaDaGames2/LemonGX">Lemon GX</a> into Unity games.
</p>

<p align="center">
  <a href="https://github.com/MastaDaGames2/LemonGX-App/releases/latest"><img src="https://img.shields.io/github/v/release/MastaDaGames2/LemonGX-App?label=download&style=for-the-badge&color=yellow"></a>
  <a href="https://github.com/MastaDaGames2/LemonGX-App/releases"><img src="https://img.shields.io/github/downloads/MastaDaGames2/LemonGX-App/total?label=downloads&style=for-the-badge&color=red"></a>
</p>

---

Pick an installed Unity game and the app patches it so it loads mods. Lemon GX works with games made with
Unity 6 (6000.x) and older versions. This is a fork of the
[LemonLoader installer](https://github.com/LemonLoader/MelonLoaderInstaller).

See the [Lemon GX repo](https://github.com/MastaDaGames2/LemonGX) for how to use it and where mods go.

## Changes from the LemonLoader installer

- Installs Lemon GX (MelonLoader 0.7.4) instead of LemonLoader 0.6
- The loader is built into the app, so patching works offline
- Keeps the game's own `libunity.so` instead of downloading a replacement, which crashed games with a stripped engine
- New name, icon and package (`com.lemongx`), so it installs alongside the original LemonLoader app

## Building

The app is a .NET MAUI project (`App/`). Build the loader first (see
[docs/ANDROID.md](https://github.com/MastaDaGames2/LemonGX/blob/android-0.7.4/docs/ANDROID.md) in the Lemon GX
repo), then copy its `melon_data.zip` to `App/Resources/Raw/melon_data.zip` and publish:

```
dotnet publish App/MelonLoader.Installer.App.csproj -f net8.0-android -c Release
```

Release builds are signed with `lemongx.keystore`, which isn't in this repo.

# Redesign Licensing/Credits
- [ReVanced Manager](https://github.com/ReVanced/revanced-manager) for design inspiration
- [Inter](https://fonts.google.com/specimen/Inter), under the [Open Font License](https://openfontlicense.org/)
- [ADB/Platform Tools](https://developer.android.com/tools/releases/platform-tools) and [AAPT2](https://developer.android.com/tools/aapt2), under the [Android Software Development Kit License Agreement](https://developer.android.com/tools/releases/platform-tools)

# Licensing/Credits
- [LemonLoader installer](https://github.com/LemonLoader/MelonLoaderInstaller), which this app is forked from
- [SAI](https://github.com/Aefyr/SAI), under the [GPL-3.0 license](https://github.com/Aefyr/SAI/blob/master/LICENSE)
- [SplitAPKInstall](https://github.com/nkalra0123/splitapkinstall), under the [Apache-2.0 license](https://github.com/nkalra0123/splitapkinstall/blob/master/LICENSE)
- [Apkifier](https://github.com/emulamer/Apkifier) under the [MIT license](https://github.com/emulamer/Apkifier/blob/master/LICENSE)
- [QuestPatcher](https://github.com/Lauriethefish/QuestPatcher) under the [zlib License](https://github.com/Lauriethefish/QuestPatcher/blob/main/LICENSE)
  - Changes (in accordance with the License; all used files are located in `Core/Utilities/Signing` and `Core/Utilities/Axml`)
    - Merged ApkSigner's V2 code into my APKSigner class
    - Changed namespace of helper classes to match other files and folder hierarchy position
    - QuestPatcher.Axml had no changes
