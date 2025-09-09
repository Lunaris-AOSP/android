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

- Enable optimized dexopt tuning (default false, Not recommend for low end device)
```bash
TARGET_OPTIMIZED_DEXOPT := true
```

- Enable BCR
```bash
WITH_BCR := true
```

# Build flages

- GMS
```bash
WITH_GMS := true
```

- Vanilla
```bash
WITH_GMS := false
```

- GMS CORE
```bash
TARGET_USES_CORE_GAPPS := true
```

- GMS OMNI
```bash
TARGET_USES_OMNI_GAPPS :=true
```

- Ship BCR
```bash
WITH_BCR := true
```

## Low ram profile
Low ram profile mode for low end devices to improve ram management 
```bash
TARGET_USE_LOWRAM_PROFILE := true
```
