# Wispr Flow Addons

macOS daemon that runs on the trainer's Mac alongside the workshop.

## What it does

- **CGEventTap** intercepts all key and mouse events system-wide
- **Cmd+V capture**: stores clipboard content at each paste for later cleanup
- **Cmd+Ctrl+V**: sends captured text to Claude Haiku for grammar/filler cleanup, undoes original paste, re-pastes cleaned version
- **Cmd+Ctrl+Opt+V**: same as above but adds contextual emojis
- **Mouse Button 5** (Wispr Flow dictation toggle): pauses media playback and lowers "OS Output" loopback device volume to ~silent; pressing again resumes media and restores volume
- **Escape while dictating**: also restores volume and resumes media
- Requires macOS Accessibility permission and `ANTHROPIC_API_KEY` in `wispr-addons/secrets.env`
- Run: `python3 clean.py`

## Secrets

`WISPR_CLEANUP_ANTHROPIC_API_KEY` must be set in `~/.training-assistants-secrets.env`.

## LaunchAgent

`install-startup.sh` symlinks the plist into `~/Library/LaunchAgents/` and loads it with `launchctl`, making `clean.py` auto-start at login with `KeepAlive`.

## Communication Notes

The user frequently uses a dictation tool. Messages may contain misheard or mistyped words. Use context to infer the intended meaning rather than taking words literally.
