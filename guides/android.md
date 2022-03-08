# Android Security Recommondations

### General Android Settings 	 	 
- [ ] Update operating system to the latest version
- [ ] Do not Root the device
- [ ] Do not install applications from third party app stores
- [ ] Enable device encryption
- [ ] Disable 'Developer Actions'
- [ ] Use an application/service to provide remote wipe functionality
- [ ] Enable Android Device Manager

###  Android Authentication Security
- [ ] Set a passcode and automatically lock the device when it sleeps
- [ ] Set an alphanumeric passcode
- [ ] Set Auto-Lock Timeout
- [ ] Disable 'Make Passwords Visible'
- [ ] Erase data upon excessive passcode failures

###  Android Browser Security
- [ ] Show security warnings for visited sites
- [ ] Disable 'Form Auto-Fill'
- [ ] Do not automatically remember passwords
- [ ] Disable browser plug-ins
- [ ] Turn on Do Not Track

###  Android Network Security
- [ ] Turn off Bluetooth when not in use
- [ ] Disable network notifications
- [ ] Forget Wi-Fi networks to prevent automatic rejoin

###  Android Additional Security Settings
- [ ] Turn off Location Services
- [ ] Limit the number of text (SMS) and multimedia messages (MMS) saved 
- [ ] Use encrytped chat apps rather than SMS


### DNS Security
Natively Android only supports DNS over TLS (DoT) which required port 853 and can be blocked by policy by firewall devices
- CloudFlare has [instructions](https://blog.cloudflare.com/enable-private-dns-with-1-1-1-1-on-android-9-pie/) on adding their DoT service to your device
- you can also use [apps](https://play.google.com/store/apps/details?id=com.frostnerd.smokescreen) to enable DNS over HTTPS (DoH) recommended protocol to prevent the traffic being blocked

