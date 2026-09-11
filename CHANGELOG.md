# Changelog

All notable changes to this project will be documented in this file.

## [1.1.0] - 2026-09-09
Update 1.2.0- 2026-9/11/2026 12:00PM Adelaide Time 

### Fixed
- **Window Handle Lookup Failure:** Resolved a critical bug where the focus monitoring loop and visibility toggles failed to find the browser window. Replaced the unreliable ChromeDriver PID-matching routine with a direct OS-level window title query (`FindWindowW`) tied to the active Selenium driver instance.
- **Variable Overwrite Conflict:** Eliminated a redundant window enumeration callback sequence (`enum_windows_callback`) that was resetting the `hwnd` handle variable to `None` immediately after a successful lookup.
- **Redundant Fallback Logic:** Cleaned up duplicate `GetForegroundWindow` fallback assignments to streamline script execution flow.

### Changed
- **Initialization Sequence:** Restructured the startup flow so window style modification flags (`WS_EX_TOOLWINDOW`) are applied immediately following a confirmed handle match, ensuring predictable behavior during automated UI focus tests.
- 
  
