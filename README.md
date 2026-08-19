# OnePlus 15T fairlady TWRP device tree

## Working

- [x] Display
- [x] Touch
- [x] Decryption
- [x] Flashing
- [x] Backup & Restore
- [x] KernelSU, KernelSU Next & SukiSU Ultra Installer
- [x] MTP/OTG Storage
- [x] ADB/FastbootD
- [x] Factory Reset
- [x] Vibrator
- [x] Display & Vibration Settings
- [x] Flashlight

## Not working

- [ ] ???????

# How To Build

### Init & Sync TWRP Source
```
mkdir -p ~/TWRP && cd ~/TWRP
repo init -u https://github.com/TWRP-Test/platform_manifest_twrp_aosp.git -b twrp-16.0 -m twrp-default.xml --git-lfs --depth 1
repo sync
```
### Get the GKI prebuilt kernel
```
git clone --depth=1 https://android.googlesource.com/kernel/prebuilts/6.6/arm64 kernel/prebuilts/6.6/arm64
```
### Clone Device-tree
```
mkdir -p device/oneplus/
git clone https://github.com/Ponywka/twrp_android_device_oneplus_fairlady.git device/oneplus/fairlady
```
### Apply optional patches
```
cd ~/TWRP/bootable/recovery
git apply ../../device/oneplus/fairlady/patches/bootable_recovery/0001-virtual-ab-snapshot-aware-super-mount.patch
cd -
```
### BUILD!
```
cd ~/TWRP
source build/envsetup.sh
lunch twrp_fairlady-bp2a-eng
mka recoveryimage
```

If there is no error, `recovery.img` will be found in `out/target/product/fairlady/recovery.img`
