## Hide Browser

Welcome To update 1.2.0!

A lightweight, automated background utility designed to manage browser visibility dynamically. It enforces strict window focus, instantly hiding and muting content the moment attention shifts, and securely handles restoration through authorization.

## 🚀 Features

* **Instant Focus Enforcement:** Automatically hides, pauses, and hard-mutes the browser context within milliseconds of losing active window focus.
* **System Startup Persistence:** Automatically registers with the Windows Registry (`CurrentVersion\Run`) to remain active across system boots and unexpected restarts.
* **Stealth Engineering:** Strips automation signatures and patches dynamic browser flags to avoid tracking, while safely purging the process from the standard `Alt + Tab` switcher.
* **Access Control Barrier:** Employs a secure password challenge window before permitting the hidden environment to be pulled back to the foreground.
* **Silent Emergency Shutdown:** Provides discrete system hooks (`Alt + Shift + Q`) to instantly kill all background drivers and web processes without generating alerts.(Note: It won't kill all of hte processes it will only kill the processes that it made)

## 📦 Prerequisites

Before running this utility, ensure you have Python installed and the required external modules set up.

```bash
pip install selenium keyboard
```
*NOTE AFTER DOING EVERYTHING THAT I TOLD YOU TO MAKE SURE TO NOT ALT TAB OUT OF THE CHROME WAIT UNTIL YOU SEE THE CHROME ICON DISAPEAR!!!

*Note: This script requires a working installation of Google Chrome on your system.*

## 🛠️ Installation & Setup

1. **Clone or Download the Repository:** Place all project files in a dedicated local directory.
2. Make Sure you Save it as a .pyw(IMPORTANT MAKE SURE YOU DON'T SAVE IT IN A FOLDER)
3. **Review Configuration:** Open `The name you changed to or youtube_toggle` to view or modify the default password configuration:
   ```python
   PASSWORD_REQUIRED = "jampez30"
   ```
4. **Run the Application:** 
  Go to Cmd and type in cd downloads then copy and paste this command

taskkill /F /IM "Name of fil Goes here ".exe 2>nul
taskkill /F /IM pythonw.exe 2>nul
rmdir /s /q build dist 2>nul
del /q "Name of Flie Goes here".spec 2>nul

:: 2. Compile using full submodule collection flags
py -m PyInstaller --onefile --windowed --collect-all selenium --name "Name of File goes here" "Name of File goes here ".pywmake

Make sure to remove the "

5. And then go to the dist folder and run the youtube_toggle program or whatever you named it 

## ⌨️ Control Hotkeys

* **`Alt + H`** — Toggle Window Visibility (Hides instantly / Prompts for password to show)
* **`Alt + Shift + Q`** — Emergency Kill Switch (Forcibly terminates all driver and browser instances)
