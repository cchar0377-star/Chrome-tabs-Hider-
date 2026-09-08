## Hide Browser

A lightweight, automated background utility designed to manage browser visibility dynamically. It enforces strict window focus, instantly hiding and muting content the moment attention shifts, and securely handles restoration through authorization.

## 🚀 Features

* **Instant Focus Enforcement:** Automatically hides, pauses, and hard-mutes the browser context within milliseconds of losing active window focus.
* **System Startup Persistence:** Automatically registers with the Windows Registry (`CurrentVersion\Run`) to remain active across system boots and unexpected restarts.
* **Stealth Engineering:** Strips automation signatures and patches dynamic browser flags to avoid tracking, while safely purging the process from the standard `Alt + Tab` switcher.
* **Access Control Barrier:** Employs a secure password challenge window before permitting the hidden environment to be pulled back to the foreground.
* **Silent Emergency Shutdown:** Provides discrete system hooks (`Alt + Shift + Q`) to instantly kill all background drivers and web processes without generating alerts.

## 📦 Prerequisites

Before running this utility, ensure you have Python installed and the required external modules set up.

```bash
pip install selenium keyboard
```

*Note: This script requires a working installation of Google Chrome on your system.*

## 🛠️ Installation & Setup

1. **Clone or Download the Repository:** Place all project files in a dedicated local directory.
2. Make Sure you Save it as a .pyw
3. **Review Configuration:** Open `youtube_toggle` to view or modify the default password configuration:
   ```python
   PASSWORD_REQUIRED = "jampez30"
   ```
4. **Run the Application:** 
   Double-click `.pyw`. Running it as a `.pyw` file ensures the script executes entirely in the background without launching a black command prompt console.

## ⌨️ Control Hotkeys

* **`Alt + H`** — Toggle Window Visibility (Hides instantly / Prompts for password to show)
* **`Alt + Shift + Q`** — Emergency Kill Switch (Forcibly terminates all driver and browser instances)
