# Gemini Work Profile Patches

Patches for use with [Morphe](https://morphe.software) that make the **Gemini app work inside an Android work
profile** (Shelter, Island, Insular, Samsung Secure Folder, …) — signing in with **microG** instead of Google Play
services.

Normally the Google app refuses to run Gemini in a managed profile ("use your personal profile", errors 19 / 900009)
or sends you to the web app. These patches install the Google app and the Gemini app as **separate clones**
("Google (Morphe)" and "Gemini (Morphe)") that work in the profile, next to the original apps.

The patches find their targets by stable strings and code structure, not by obfuscated names, so they are expected
to keep working with new app versions. If Google changes something, a patch fails with an error instead of producing
a broken app.

### How to use these patches

Click the button below, or manually add this repo url to Morphe Manager: https://github.com/Johannes7k75/gemini-work-profile-patches

<a href="https://morphe.software/add-source?github=Johannes7k75/gemini-work-profile-patches">
  <img src=".github/assets/add-to-morphe.svg" alt="Add to Morphe" height="48">
</a>

## 📋 Requirements

- [MicroG-RE](https://github.com/MorpheApp/MicroG-RE) (`app.revanced.android.gms`) installed **in the work profile**,
  with your Google account added in microG.
- The original **Google** app and **Gemini** app (they stay installed; they are only the source for patching).
- Morphe Manager (or Morphe Desktop).

## 🚀 Setup

1. In Morphe Manager, patch the **Google** app with this bundle (all default patches).
   Do **not** additionally enable the official "Clone app" patch — cloning is already included.
2. Patch the **Gemini** app with this bundle.
3. Install both, then make them available in the work profile (e.g. Shelter → "Clone to work profile").
   microG must be present in the same profile.
4. In the work profile, open **Gemini (Morphe)** and sign in. Allow the account / microG permissions when asked.

Always open **Gemini (Morphe)**. Opening "Google (Morphe)" directly crashes — use the optional
*Hide launcher icon* patch to remove its icon.

## 🔄 Updating

When the original Google or Gemini app gets updated, patch it again in Morphe Manager and install it as an update of
the clone. Keep the same Manager signing key (back it up: Manager → Settings → export keystore); with another key the
clone has to be uninstalled first and you have to sign in again.

## 🩹 Patches list

<!-- PATCHES_START EXPANDED -->

#### A list of the patches will automatically be shown here after the first release.

<!-- PATCHES_END -->

## ⚠️ Known issues

- "Google (Morphe)" opened directly crashes (it is meant to be started by Gemini).
- Assistant features outside the Gemini app (overlay, "Hey Google", assist gesture) are not covered.
- Android 10+ may show an "app info" placeholder icon for apps without launcher icon; turn it off with
  `adb shell settings put global show_hidden_icon_apps_enabled 0`.

## 🙏 Credits

- [ryuya0124/gemini-microg-patches](https://github.com/ryuya0124/gemini-microg-patches) — the original research on
  running Gemini with microG in a Samsung Secure Folder: which checks block work profiles and how the cloned Google app
  can use microG. This project is an independent implementation built on that research.
- [Morphe Patches](https://github.com/MorpheApp/morphe-patches) — the "Clone app" patch is adapted from it (GPLv3).
- [MicroG-RE](https://github.com/MorpheApp/MicroG-RE) / [microG](https://github.com/microg/GmsCore).

This project is not affiliated with Google or the Morphe project.

## 📜 Licence

Gemini Work Profile Patches are licensed under the [GNU General Public License v3.0](LICENSE), with the additional
GPL section 7 terms of the [NOTICE](NOTICE).
