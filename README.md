# Initialize local repository
```
repo init -u https://github.com/Lunaris-AOSP/android -b 16 --git-lfs
```

# Sync up
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

# Build

- Set up the build environment
```bash
. b*/env*
```

- Lunch a target
```bash
lunch lineage_codename-bp2a-user
```

- To start compiling
```bash
m lunaris
```
- Bringup about
```bash
https://github.com/Lunaris-AOSP/packages_apps_Settings/blob/0acd6251e20bacd8db589beb483d6138f553f02c/res/values/lunaris_strings.xml#L338
```

- Maintainer flag
```bash
ro.paranoid.maintainer=GHOST
```

- Enable optimized dexopt tuning (default false)
```bash
TARGET_OPTIMIZED_DEXOPT := true
```

- Enable BCR
```bash
WITH_BCR := true
```

# Additional  
Remove all cpuset configurations from the device tree under init/ and rootdir/.
The ROM will handle CPU set management more efficiently.

For example, remove any lines referencing paths like:
/dev/cpuset/background/cpus or /dev/cpuset/restricted/cpus.
```bash
grep -r "/dev/cpuset/" .
```
Delete or clean up any related entries accordingly

## Setup Efficient freq hint(if using libpref)

How the Boost Works
When a fling gesture or animation-heavy action (e.g., entering Quick Settings) is detected:

The system enters a combined LAUNCH + FIXED_PERFORMANCE mode.
These modes persist throughout the fling/animation duration, plus an additional 160ms buffer (for fling).
Once the fling/animation ends, both hints are disabled.

```bash
https://github.com/AxionAOSP-devices/android_device_google_raviole/commit/cee1e28a7fdebfe4327d4e70a14e71c663f94ce8
https://github.com/Pong-Development/device_nothing_Pong/commit/38ef69f5e90f11750141bffe43e5549c9d429db7
```
