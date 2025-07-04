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
https://github.com/Lunaris-AOSP/packages_apps_Settings/blob/f6c1759b737cd0ef835a5f34181c865bf25f13d2/res/values/lunaris_strings.xml#L335
```

- Maintainer flag
```bash
ro.paranoid.maintainer=GHOST
```

- Enable optimized dexopt tuning (default false)
```bash
TARGET_OPTIMIZED_DEXOPT := true
```
