# Karabiner-Shortcuts

A collection of [Karabiner-Elements](https://karabiner-elements.pqrs.org/) complex modifications for macOS, built around a workflow of juggling multiple Claude Code / Codex CLI sessions inside [GNU Screen](https://www.gnu.org/software/screen/) on iTerm2.

If you've ever had 6+ AI coding sessions running in Screen windows and wished you could flip between them with a single key instead of `Ctrl+a n` ... `Ctrl+a n` ... `Ctrl+a n`, these are for you.

## Getting Started

1. **Install Karabiner-Elements** from [karabiner-elements.pqrs.org](https://karabiner-elements.pqrs.org/) (or `brew install --cask karabiner-elements`).
2. **Copy the JSON files** you want into Karabiner's complex modifications directory:
   ```bash
   cp *.json ~/.config/karabiner/assets/complex_modifications/
   ```
3. **Open Karabiner-Elements** and navigate to **Complex Modifications**.
4. Click **Add Predefined Rule**, find the rules you just copied, and click **Enable**.

## Bindings

### `iterm_media_to_ctrl_a_pn.json` — GNU Screen navigation via media keys

Remaps the media keys (F7/F8/F9 on Apple keyboards) to GNU Screen commands, but **only** when iTerm2 is focused. Music playback stays untouched everywhere else.

| Key | Action | Screen Command |
|-----|--------|----------------|
| F7 (Prev Track) | Previous Screen window | `Ctrl+a p` |
| F9 (Next Track) | Next Screen window | `Ctrl+a n` |
| F8 (Play/Pause) | Enter copy/scrollback mode | `Ctrl+a [` |

### `kinesis_iterm2_f10_f11_f12.json` — GNU Screen navigation for Kinesis Advantage2

Same idea as above, but scoped to a **Kinesis Advantage2** keyboard (vendor 10730, product 258) using F10-F12 instead of the media keys. Useful if you have a Kinesis at your desk and want dedicated Screen-switching keys that don't conflict with media controls.

| Key | Action | Screen Command |
|-----|--------|----------------|
| F10 | Previous Screen window | `Ctrl+a p` |
| F11 | Enter copy/scrollback mode | `Ctrl+a [` |
| F12 | Next Screen window | `Ctrl+a n` |

### `iterm_f3_f4_git_commands.json` — Quick git shortcuts

One-key git commands in iTerm2. F3 types the command (without pressing Enter) so you can review it; F4 runs immediately.

| Key | Action |
|-----|--------|
| F3 | Types `git diff` (no Enter — you can name specific files or just hit Enter when ready) |
| F4 | Types `git status` and presses Enter |

### `capslock_app_switcher.json` — Caps Lock as app switcher

Turns Caps Lock into a one-key `Cmd+Tab`. Works globally across all apps.

| Key | Action |
|-----|--------|
| Caps Lock | Open macOS app switcher (`Cmd+Tab`) |

### `chrome_tab_switching.json` — Chrome tab switching via F7/F9

Remaps F7/F9 to switch Chrome tabs, keeping the same "previous/next" muscle memory as the Screen navigation above.

| Key | Action | Chrome Shortcut |
|-----|--------|-----------------|
| F7 (Prev Track) | Previous tab | `Cmd+Opt+Left` |
| F9 (Next Track) | Next tab | `Cmd+Opt+Right` |

## Notes

- All iTerm2 rules are scoped with `frontmost_application_if` so they only fire when iTerm2 is the active app.
- The Chrome rule similarly only fires when Chrome is in front.
- The Kinesis rule adds a `device_if` condition so it won't affect your laptop keyboard or other external keyboards.
- The Caps Lock rule is global and fully replaces the Caps Lock toggle. If you still need Caps Lock occasionally, consider adding a Shift+Caps Lock escape hatch.
- If you use both the media-key and Kinesis rules, Karabiner applies whichever matches first based on rule order and conditions.
