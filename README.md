# Block-OTA

## Method 1
Download [com.apple.MobileAsset.plist](https://github.com/Mikasa-san/Block-OTA/raw/main/com.apple.MobileAsset.plist) & copy it to /var/mobile/Managed Preferences/mobile/ then just reboot or reboot userspace & it can be added to backup folders in ManagedPreferencesDomain/mobile/

## Method 2
Go to /var/db/com.apple.xpc.launchd/ and edit disabled.plist and add com.apple.softwareupdateservicesd as key with type boolean and set value true & it can be added to backup in /DatabaseDomain/com.apple.xpc.launchd/disabled.plist

## Method 3
Copy the following command to the clipboard, then use Filza to find /usr/bin/vm_stat and click Run, then paste the following command and press Enter to run
```
killall -9 softwareupdateservicesd & killall -9 softwareupdated & killall -9 com.apple.MobileSoftwareUpdate.CleanupPreparePathService & killall -9 Preferences & chflags -R noschg,noschange,nosimmutable '/var/MobileSoftwareUpdate/MobileAsset/' & mkdir -p '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && rm -rf '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && mkdir -p '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chmod -R 0777 '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chown -R mobile:mobile '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chflags schg,schange,simmutable '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/'
```
To re-enable it later, please run the following command in Filza
```
chflags -R noschg,noschange,nosimmutable '/var/MobileSoftwareUpdate/MobileAsset/'
```
## Method 4
1. Set your device's date to any point before December 14th, 2023
2. Download [Apple TV Profile](https://static.itsnebula.net/apple/noota/17.mobileconfig)
3. Select "Allow" then Open Settings & Go to General -> Profile or Device Management
4. Tap on the tvOS Beta Profile & Tap "Install" & Restart you device
