# MacOS

- [ ] Consider installing a fresh copy of macOS
    - Optionally, start clean, avoid previous misconfigurations
    - Follow [this](https://support.apple.com/en-us/HT204904) Apple Support guide
    - This step cannot be undone!
  
- [ ] Install all Apple Software Updates
  - [ ] Enable automatic software updates (recommended)
    - Go to System Preferences > Software Update > Advanced, check all.

- [ ] Enable password-protected sleep
  - Go to System Preferences > Security & Privacy > General, check “Require password 5 seconds after sleep or screen saver begins”.

- [ ] Forbid unsigned software
  - Go to System Preferences > Security & Privacy > General, select “Allow apps downloaded from App Store and identified developers” at most.

- [ ] Disable guest user access
  - Go to System Preferences > Users & Groups > Guest User, uncheck all.

- [ ] Enable disk encryption
  - Go to System Preferences > Security & Privacy > FileVault, if disabled, click “Turn On FileVault” and follow the procedure.

- [ ] Enable the inbound network firewall
  - Go to System Preferences > Security & Privacy > Firewall, if disabled, click “Turn On Firewall”.

- [ ] Disable network services
  - Go to System Preferences > Sharing, uncheck all.

- [ ] Disable unnecessary application access
  - Go to System Preferences > Security & Privacy > Privacy > Location Services, uncheck all unnecessary access. Repeat these steps for other permissions like Microphone, Input Monitoring, Full Disk Access and Screen Recording access as well.

- [ ] Prevent Safari from opening downloads automatically
  - Go to Safari > Preferences > General, uncheck “Open safe files after downloading”.

- [ ] Show all filename extensions
  - Go to Finder > Preferences > Advanced, check “Show all filename extensions”.

- [ ] Disable radios when unused
  - When not in use, disable Wi-Fi and/or Bluetooth

- [ ] Check your computer name and maybe change
  - Go to System Preferences > Sharing, Computer Name - if your computer name includes personally identifiable information, consider changing it


### More Advanced Stuff
For the security enthusiast, who wants to go the extra mile.


- [ ] Consider the risks of browser extensions
  - Browser extensions such as adblockers or grammar checkers require full read-write access to everything you do on the web. Yes, this includes your passwords. This is not malicious per se, but is the reward worth the risk?
  - Go through your browser’s installed extensions and assess their value to you, and whether the risk trade-off is worth it or not

- [ ] Run an outbound network firewall
  - For visibility and control about the traffic leaving your system.
  - Install Little Snitch (paid) or LuLu (open-source)

- [ ] Use DNS encryption with malicious domain filtering
  - Mitigates potential DNS poisoning
  - Using a filtered DNS provider removes known-malicious domains as an additional layer of protection

- [ ] Run an outbound network firewall
  - For visibility and control about the traffic leaving your system.
  - Install Little Snitch (paid) or LuLu (open-source)


#### Additional Tools
- Objective See Tools - Patrick Wardle, a pioneer in Mac security, offers a wealth of free tools to improve your Mac's security. If you would like further assurance or awareness of what is going on behind the scenes of your Mac, you can trust his tools. Availble at the [Objective-See](https://objective-see.com/products.html) website.

- Google's [Santa](https://github.com/google/santa) Project
    > Santa is a binary authorization system for macOS. It consists of a system or kernel extension (depending on the macOS version) that monitors for executions, a daemon that makes execution decisions based on the contents of a local database, a GUI agent that notifies the user in case of a block decision and a command-line utility for managing the system and synchronizing the database with a server.


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