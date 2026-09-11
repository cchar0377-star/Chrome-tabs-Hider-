[CHANGELOG (1).md](https://github.com/user-attachments/files/32084174/CHANGELOG.1.md)# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.2.0] - 2026-09-11

### Added
- **Main-Thread UI Processing Relay:** Introduced a thread-safe signaling flag (`unhide_requested = threading.Event()`) to decouple user interface creation from background hooks. Hotkeys now pass execution requests safely across thread boundaries, completely eliminating Tkinter UI deadlocks and window freezes.
- **UUID Window Isolation:** Implemented a dynamic runtime title-injection mechanism using `uuid.uuid4()`. The automated browser temporarily signs its desktop window with a unique random hash token during startup, ensuring `user32.FindWindowW` locks onto the exact automation node and ignores standard Chrome tabs or YouTube windows.
- **Dynamic Startup Latency Guard:** Upgraded the rigid initialization timer to an active checking loop tied to `driver.title`, allowing the framework to proceed the exact millisecond the DOM layer clears regardless of local network speeds.
- **Proactive Garbage Collection:** Integrated manual scope pruning (`del active_hwnd`) paired with explicit `gc.collect()` cycling directly inside the asynchronous event loop to actively flush temporary system call records from the memory heap.
- **Thread-Safe Event Logger:** Built a silent diagnostic logging backend (`automation_runtime.log`) that indexes operational milestones, startup data, and runtime execution errors to allow seamless auditing while running in hidden modes.
- **Automated Engine Health Probe:** Embedded a high-speed checkpoint utility (`check_browser_health`) inside the main loop that continuously pings the browser's internal JavaScript engine, letting the program instantly detect crashes or manual browser closures and execute clean shutdown hooks.

### Fixed
- **Background Thread GUI Freeze (Main Fix):** Resolved a structural crash caused by spawning Tkinter input dialogs directly inside the asynchronous `keyboard` hook thread. Forcing the password prompt onto the main thread loop ensures it initializes reliably every time.
- **`InvalidSessionIdException` Connection Crash:** Placed an active JavaScript engine heartbeat test inside the background monitoring loop. The script now intercepts sudden disconnections (such as a user closing Chrome manually) and executes an orderly shutdown instead of triggering a fatal unhandled script error window.
- **Permanent Window Layer Lock:** Fixed an issue where the application became trapped behind other desktop layers or completely locked out interaction with other tools. Replacing the endless `HWND_TOPMOST` status loop with a temporary focus pull followed immediately by an `HWND_NOTOPMOST` release restores normal multitasking behaviors.
- **Thread Loop CPU Starvation:** Resolved a structural logic flaw where the focus monitor loop completely bypassed its timing delay when the window flag shifted to hidden. Repositioned the `time.sleep(0.1)` interval to lower idle CPU overhead from a 100% core lock down to a stable **1.8% – 2.1%** profile.
- **Double-Launch / Process Bloat:** Consolidated conflicting setup parameters that were causing the script to initialize two separate browser sessions consecutively, which previously left orphaned browser processes trailing invisibly in the background.
- **Transient OS API Exceptions:** Wrapped low-level desktop window queries inside robust try-except blocks, preventing background tracking workers from crashing if Windows security prompts (UAC) or full-screen application alerts temporarily interrupt the desktop window hierarchy.
- **PyInstaller Build Interruption:** Corrected compiler automation scripts to prevent manual cleanup calls from prematurely terminating PyInstaller's packaging engine, ensuring monolithic standalone executables build cleanly.

### Changed
- **Main Keep-Alive Architecture:** Reconfigured the fundamental execution loop from an idle sleep cycle to an active operational supervisor that monitors incoming hotkey event signals and performs proactive Selenium driver validation.
- **Unified Profile Hardening:** Merged anti-bot tracking bypass arguments with aggressive memory-saving parameters (blocking graphic rendering layers, hardware acceleration modules, and background syncing tools), stabilizing the active application footprint at a **~40.8MB baseline**.
- **Registry Endpoint Alignment:** Synchronized internal registry auto-start values within the persistence helper engine to match the updated PyInstaller compilation target output parameters.

---

## [1.1.0] - 2026-09-09

### Fixed
- **Window Handle Lookup Failure:** Resolved a critical bug where the focus monitoring loop and visibility toggles failed to find the browser window. Replaced the unreliable ChromeDriver PID-matching routine with a direct OS-level window title query (`FindWindowW`) tied to the active Selenium driver instance.
- **Variable Overwrite Conflict:** Eliminated a redundant window enumeration callback sequence (`enum_windows_callback`) that was resetting the `hwnd` handle variable to `None` immediately after a successful lookup.
- **Redundant Fallback Logic:** Cleaned up duplicate `GetForegroundWindow` fallback assignments to streamline script execution flow.

### Changed
- **Initialization Sequence:** Restructured the startup flow so window style modification flags (`WS_EX_TOOLWINDOW`) are applied immediately following a confirmed handle match, ensuring predictable behavior during automated UI focus tests.
