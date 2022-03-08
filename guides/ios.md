# iOS Security Recommondations

### General iOS Settings
- [ ] Update device to the latest iOS
  - Ensuring the device is up to date keeps known vulnerablities from being exploited.
- [ ] Require a complex passcode
  - Complex passcodes prevent other users from accessing your device, features like FaceID & TouchID reduce the burden for users in entering these passcodes.
- [ ] Set auto-lock timeout 
  - This ensures the device locks when not being used
- [ ] Disable grace period
  - This feature ensures the device locks during the 
- [ ] Set the device to erase data upon excessive passcode failures
- [ ] Ensure Data Protection is Enabled
- [ ] Turn off “Ask to Join Networks”
- [ ] Forget unused Wi-Fi networks
- [ ] Enable remote wipe functionality 
- [ ] Check your device name so it is not personally identifiable (shows up in Bluetooth and AirDrop advertisements)

### Privacy Enhancements
- [ ] [Use encrypted DNS (iOS 14 and newer)](#encrypted-dns)
- [ ] Use full VPN Service


### Check your call forwarding
While not exhaustive, some basic checks can help you catch low-sophistication forwarding attacks
[Codes to Check If Your Phone Is Tapped](https://clario.co/blog/code-to-check-if-phone-is-hacked/)

## Step-by-Step Instructions

### Encrypted DNS
By default, DNS is sent over a plaintext connection. DNS over TLS (DoT) is one way to send DNS queries over an encrypted connection. With DoT, the encryption happens at the transport layer, where it adds TLS encryption on top of the user datagram protocol (UDP).

**Starting with iOS 14, Apple natively supports encrypted DNS. However, if you try searching through the Settings app, you will find no mention of it anywhere. The support for encrypted DNS is there, but the setting is not. In order to actually use a different (secure) DNS server, you will have to download a third-party app, or install a third-party configuration profile.**

We suggest using DoH over DoT (TLS) because DNS over TLS uses port 853 which can indicate use of DNS security wheras DoH uses port 443, the same port that all HTTPS (web) traffic uses making this much more challenging to detect and block while still offering workng internet access.

Signed Profiles:
- [OpenDNS](https://github.com/paulmillr/encrypted-dns/blob/master/signed/opendns-familyshield.mobileconfig?raw=true) - DoH, Malware & Family Filter
- [Cloudflare](https://github.com/paulmillr/encrypted-dns/blob/master/signed/cloudflare-malware-https.mobileconfig?raw=true) - DoH, Malware Filter
- [Quad9](https://github.com/paulmillr/encrypted-dns/blob/master/signed/quad9-https.mobileconfig?raw=true) - DoH
- [Google](https://github.com/paulmillr/encrypted-dns/blob/master/signed/google-https.mobileconfig?raw=true) - DoH

[Source](https://github.com/paulmillr/encrypted-dns)
[Further Reading](https://paulmillr.com/posts/encrypted-dns/)