# How to Enable Qcom Atheros wifi
# Copy and paste this in terminal
# Support macOS Serria to Catalina (Not Big Sur)
# Disable system integrity protection a.k.a. SIP 
sudo mount -uw /
curl -O https://raw.githubusercontent.com/kalifans/Darwin/Driver/ar956x-drv-osx.tar.gz
tar zxvf ar956x-drv-osx.tar.gz
cd ar956x-drv-osx
./ar956x-inst.sh
# Reboot to enable Wifi
# This Script will put AirportAtheros40.kext plugin in IO80211Family.kext

# Catalina Specific
1/ mount your system volume in RW mode through Terminal
sudo mount -uw /
sudo killall Finder
2/ replace Catalina's IO80211Family kext in /S/L/E by High Sierra 10.3.6's or Mojave 10.14.6's (keep a backup of the vanilla kext somewhere). I recommend High Sierra's 10.13.6.
3/ repair permissions and rebuild your cache
sudo chmod -Rf 755 /S*/L*/E*
sudo chown -Rf 0:0 /S*/L*/E*
sudo touch -f /S*/L*/E*
sudo kextcache -i /
Then, to run those normally unsupported AR9565 Atheros cards, replace the Atheros40 plugin kext of IO80211Family kext by the patched Atheros40 kext trough the script
High Serria's IO80211Family.kext : https://osxlatitude.com/forums/topic/11138-inventory-of-supportedunsupported-wireless-cards-2-sierra-catalina/
# Troubleshooting
1. mount : permission denied. Failed with error 66
Solution; You didn't disable SIP. Disable it and try again
2. Sucessfully built kextcache and rebooted, but no Wifi
Solution; Open up a new issue 
