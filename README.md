# Zhihu Blacklist Helper

A Tampermonkey/Greasemonkey userscript that enhances Zhihu's built-in blocklist functionality by efficiently hiding blocked users' content and providing quick blocking controls.

## What This Script Does

This userscript improves your Zhihu browsing experience by:

- **Automatically syncs** your blocklist from Zhihu's API
- **Hides blocked content** on your feed with customizable visibility options
- **Adds quick "Block" buttons** to answers for one-click blocking
- **Provides a settings panel** to customize how blocked content is displayed
- **Fixes API issues** that caused the built-in block button to get stuck on loading

## Features

- Auto-syncs blocked users list from Zhihu servers
- Two display modes for blocked content:
  - **Complete hiding**: Blocked items are completely removed from view
  - **Placeholder mode**: Shows a "Blocked content" placeholder that can be clicked to reveal
- Quick block/unblock buttons on each answer
- Floating settings button for easy configuration
- Handles authentication automatically using XSRF tokens
- Monitors page for dynamic content updates

## Installation

1. **Install a userscript manager** for your browser:
   - Chrome/Edge: [Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/)
   - Firefox: [Tampermonkey](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/) or [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)
   - Safari: [Tampermonkey](https://apps.apple.com/us/app/tampermonkey/id1482490089)

2. **Install the script**:
   - Click on the Tampermonkey icon in your browser
   - Select "Create a new script"
   - Replace the default content with the contents of `Zhihu Blacklist Helper (Fixed API)-3.2.user.js`
   - Save (Ctrl+S or Cmd+S)

3. **Visit Zhihu**:
   - Navigate to [www.zhihu.com](https://www.zhihu.com)
   - The script will automatically start working

## Usage

### First Time Setup

When you first visit Zhihu after installing the script:
1. A gear icon will appear in the bottom-right corner
2. The script automatically syncs your blocklist from Zhihu
3. During sync, the icon temporarily shows hourglass

### Blocking/Unblocking Users

- Each answer on your feed will have a "Block" button next to the author's name
- Click "Block" to add the user to your blocklist
- Click "Blocked" (red button) to unblock a user
- Changes sync immediately with Zhihu's servers

### Settings Panel

Click the floating gear icon to open the settings panel:

- **Hide items completely**: When enabled, blocked content is completely removed from view
- **Show 'Blocked' placeholder**: When enabled with hiding, shows a clickable placeholder instead of removing items entirely
- **Sync**: Manually refresh your blocklist from Zhihu's servers
- **Save**: Apply your settings changes

### Settings Combinations

- **Both OFF**: Blocked content remains visible (baseline behavior)
- **Hide ON, Placeholder OFF**: Blocked items completely disappear
- **Hide ON, Placeholder ON**: Shows "Blocked content from [username]" - click to reveal
- **Hide OFF, Placeholder ON**: Same as both OFF (placeholder only works with hide enabled)

## Technical Details

- **Version**: 3.3
- **API Endpoint**: Uses Zhihu's official `/api/v4/members/{slug}/actions/block` endpoint
- **Storage**: Uses Tampermonkey's GM_getValue/GM_setValue for persistent storage
- **Authentication**: Automatically extracts XSRF token from cookies
- **Performance**: Uses MutationObserver with debouncing to handle dynamic content efficiently

## Troubleshooting

### Block button shows "Login required"
- Make sure you're logged in to Zhihu
- Refresh the page and try again

### Block button shows "Auth failed"
- Your session may have expired - try logging out and back in
- Clear cookies and log in again

### Sync shows L error
- Check your internet connection
- The Zhihu API may be temporarily unavailable
- Click the gear icon and try to Sync again

### Blocked content still appears
- Click the gear icon to open settings
- Enable "Hide items completely"
- Click "Save"
- Alternatively, click "Sync" to refresh your blocklist

## Privacy & Security

- This script only communicates with Zhihu's official API endpoints
- All data is stored locally in your browser via Tampermonkey
- XSRF tokens are read from cookies but never transmitted elsewhere
- No third-party analytics or tracking

## License

This is a userscript provided as-is for personal use.

## Support

If you encounter issues or have suggestions, please check the script's console output (press F12, go to Console tab) for error messages that might help diagnose the problem.
