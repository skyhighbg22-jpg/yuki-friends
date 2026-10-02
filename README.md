# Yuki for friends (Windows x64)

## Paste into a new PowerShell (install or update)

Close Yuki before updating. Paste all three lines:

```powershell
cd "$env:USERPROFILE\Downloads"
Invoke-WebRequest 'https://github.com/skyhighbg22-jpg/yuki-friends/releases/latest/download/install-friends.ps1' -OutFile '.\install-yuki.ps1' -UseBasicParsing
powershell -NoProfile -ExecutionPolicy Bypass -File .\install-yuki.ps1 -Source 'https://github.com/skyhighbg22-jpg/yuki-friends/releases/latest/download/Yuki-setup.exe'
```

Then open **Yuki Companion** from the Start menu. The same commands install the latest published build on future runs.

Download page: https://github.com/skyhighbg22-jpg/yuki-friends/releases/latest

## ZIP alternative

Extract `Yuki-friends.zip`, open PowerShell in the extracted folder, and run:

```powershell
cd "$env:USERPROFILE\Downloads\Yuki-friends"
powershell -NoProfile -ExecutionPolicy Bypass -File .\install-friends.ps1
```

Open **Yuki Companion** from the Start menu. No Git, Rust, or npm needed for the base app. Setup installs WebView2 if it is missing (internet required).

For updates: close Yuki, extract the new ZIP, and run the same command. Setup replaces the app; it does not uninstall it or clear your preferences. This is a manual friends build, with no automatic update checks.

If your friend provides a direct HTTPS download link to `Yuki-setup.exe`, the script can also download and install it:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\install-friends.ps1 -Source "https://YOUR-HOST/Yuki-setup.exe"
```

Voice and AI chat need the Python voice environment and a configured provider; Python and models are not included. Advanced Spotify controls need Node.js. Browser tab audio controls need the bundled browser extension. These are optional extras and have separate setup instructions in the project documentation.

## Making the next friends build (developer only)

From the project folder:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\scripts\build-friends.ps1
```

Share `.test-output/friends/Yuki-friends.zip` again. The ZIP includes the latest built app, the install/update script, and these instructions. You can keep sharing ZIPs without setting up a release server.

To build and publish the next update to GitHub instead, add `-Publish` to that command. Requires the GitHub CLI signed in to an account with write access to `skyhighbg22-jpg/yuki-friends`. Your friends keep using the same download page and commands.
