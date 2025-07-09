# F.A.Q. and limitations

## What is the correct command to use in Aseprite Command Path

The plugin uses one of the default commands bellow depending on the Operational System:

- Windows: `C:\\Steam\steamapps\common\Aseprite\aseprite.exe`.
- MacOS: `/Applications/Aseprite.app/Contents/MacOS/aseprite`.
- Linux: `aseprite`.

If you are using a different path you can edit it via Editor Settings.

## Linux: Path is correct but Aseprite not found

Some distros install Godot via Flatpak. By default, flatpak apps are sandboxed not having access to the host's file system. This will make Godot show "command not found" even when the right path is set.

At the time I'm writing this, people recommend using a program called Flatseal which is able to give flatpak apps permission to access parts of the file system.

## MacOS: Path is correct but Aseprite not found

If you are copying the path from the Finder, it's very likely you are copying the wrong one. MacOS apps are just special folders ending on `.app`. The real executable is located inside it, in the `Contents/MacOS/` folder.

Check the default command for an example. Usually what you want is for your aseprite path to end on `Aseprite.app/Contents/MacOS/aseprite`.

## Non-looping animations

From Aseprite 1.3 you can control loops by setting the `repeat` property under `Tag properties` in Aseprite. There's no extra steps required in the plugin.

Older versions have no option for loops so this plugin handles that via a configured convention.

By default, all animations are imported with loop = true. Any animation starting with `_` (the exception prefix), will be imported with loop = false.

Both the default configuration and the exception prefix can be changed in the configuration window.

## Import overwrite previous files

This is expected behaviour, import overwrites previously imported files. Any manual modification in the previous resource file will be lost.

## Why Libresprite doesn't work with this plugin?

Libresprite is an open source alternative to Aseprite that was forked from the last version of Aseprite with a GPL license. A lot changed in Aseprite since the fork,
and Libresprite hasn't kept up with it (and I don't think that's even its goal).

At the time of writing this, Libresprite hasn't had a new release since around 2 years ago, and the only other version released was published 2 years before that.
Keeping this plugin compatible with such an old implementation would require more effort and time, and given how little progress Libresprite is having, I can't justify that.

Here are a few alternatives I can recommend if you can't afford Aseprite:

- If you don't mind using an outdated version, you can downlod [Aseprite Wizard version 7.2.0](https://github.com/viniciusgerevini/godot-aseprite-wizard/releases/tag/v7.2.0-4), which is the last version without major incompatibilities with Libresprite. Keep in mind a lot of bug fixes and improvement happened since then, so it might not be the best experience.
- Even though Aseprite is not free, it allows you to compile it from the source and use it with no cost, even for commercial games. This does take time and effort, but it's a good alternative for the tech savvy.
