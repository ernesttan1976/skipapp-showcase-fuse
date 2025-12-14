# Android Studio Hot-Swap Guide

You now have two Android Studio versions installed with independent Java runtimes:

- **Android Studio Flamingo** - Java 17 (for older projects)
- **Android Studio Otter** - Java 21 (for newer projects)

## Quick Switching Commands

### Switch to Flamingo (Java 17)
```bash
switch_to_flamingo
# or use the alias (in interactive shells):
as-flamingo
```

### Switch to Otter (Java 21)
```bash
switch_to_otter
# or use the alias (in interactive shells):
as-otter
```

**Note:** If you're sourcing `.zshrc` and switching in the same command line, use the function names directly:
```bash
source ~/.zshrc && switch_to_otter  # ✅ Works
source ~/.zshrc && as-otter          # ❌ Won't work (alias not expanded yet)
```

In normal interactive shells, both the functions and aliases work fine.

## How It Works

Each Android Studio version uses its own bundled Java runtime:
- **Flamingo**: `/Applications/Android Studio Flamingo.app/Contents/jbr/Contents/Home` (Java 17)
- **Otter**: `/Applications/Android Studio Otter.app/Contents/jbr/Contents/Home` (Java 21)

The switching functions update `JAVA_HOME` and `PATH` to point to the correct Java runtime.

## Default Behavior

By default, your shell starts with **Flamingo (Java 17)** for backward compatibility.

## Verifying Current Version

After switching, verify with:
```bash
echo $JAVA_HOME
java -version
```

## Opening Android Studio

You can open either version directly:
```bash
open "/Applications/Android Studio Flamingo.app"
open "/Applications/Android Studio Otter.app"
```

Or use Spotlight/Launchpad - both apps are available separately.

## Project-Specific Setup

For projects that need a specific version:

1. **Flamingo projects**: Run `as-flamingo` before working on the project
2. **Otter projects**: Run `as-otter` before working on the project

You can also add the switch command to project-specific scripts or Makefiles.

## Troubleshooting

If you encounter issues:
1. Check which version is active: `echo $JAVA_HOME`
2. Switch explicitly: `as-flamingo` or `as-otter`
3. Verify Java version: `java -version`
4. Check Gradle: `gradle -v` (should show the correct Java version)

