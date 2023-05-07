# OpenGL OSX Template

This project is a simple C++ project for creating an empty OpenGL 3 window on OSX.

## Prerequisites

First, you'll want to install [Homebrew](https://brew.sh/).  This will make it a cinch to install the necessary dependencies to build the project.

Open up a Terminal and run,

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

This will install Homebrew onto your Mac.

Next, we need to install the project dependencies.  You'll want both `glfw` and `glm`.

```shell
brew install glfw glm
```

We also use `cmake` to simplify the build process, so install that too.

```shell
brew install cmake
```

## Configuring VS Code

Open up the root direcotry in VSCode.  If you don't have the `CMake Tools` extension installed, install that now.

Hit cmd+shift+p and select "CMake: Configure". You'll have to do this any time you change your CMake project setup (add a file, change a library, etc). This should create a `build/` directory with your actual `Makefile` in it.

If you are seeing squiggly lines in VSCode complaining that it can't find the GLFW headers, you'll need to add the header paths to your intellisense settings.

Open up `C/C++ Configurations` and scroll down to "Include path". You'll need to add an entry to this box (one per line) for each external library you want to include.

To find the include path, in your terminal type,

```shell
brew info glfw
```

You should see something like this,

```text
==> glfw: stable 3.3.8 (bottled), HEAD
Multi-platform library for OpenGL applications
https://www.glfw.org/
/opt/homebrew/Cellar/glfw/3.3.8 (14 files, 490.4KB) *
  Poured from bottle using the formulae.brew.sh API on 2023-05-07 at 16:17:35
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/glfw.rb
License: Zlib
==> Dependencies
Build: cmake ✔
==> Options
--HEAD
	Install HEAD version
==> Analytics
install: 284 (30 days), 2,967 (90 days), 46,730 (365 days)
install-on-request: 283 (30 days), 2,701 (90 days), 40,678 (365 days)
build-error: 0 (30 days)
```

Notice the path there, `/opt/homebrew/Cellar/glfw/3.3.8`. That's the location on your computer where the library is actually stored.  Back in the "Include path" box in VS Code, add the path followed by `/include`. So in this case, `/opt/homebrew/Cellar/glfw/3.3.8/include`.

You'll want to do this same thing for the `glm` library as well.

## Building

To build your project, type cmd+shift+p and select "CMake: Build". If everything goes well, you'll have an `opengl-template` executable file in your `build/bin/` directory.