# Information Security Configuration Recommendations

For less tech-savy users it can be hard to know where to start to get a good security baseline set for your devices. These guides are an attempt to cover the basics for all the major platforms without getting too deep into the weeds of the technical jargon. 

**Some of the jargon is defined [here](terms.md)**

These guides are not meant to be complete, but a start to implementing stronger security for your devices. The recommendations will change over time, and without updates, will become stale. Please file PRs as needed. [GitHub Link](https://github.com/kyle-nl/cytr.io/)

# Why should I trust you?
Thats a good start, you shouldn't trust these guides alone - do your own research but make sure its from knowlegable sources. Random internet guides are not always deeply knowlegable on modern attacks or up to date. The authors of these guides have worked in the infosec community for over a decade in various roles from defensive security to offensive security and have tried to distill the most high value recommendations 


# Security Recommendations by Platform
No matter which platform you use, keep your devices backed up in a secure fashion so others can't access the data, and be aware of how to wipe your device if you are concerned for your safety or the safety of others if the data on the device were to be exposed.

## Mobile ##
[![iOS](icons/406080_apple_ios_ipad_round_icon.png)](guides/ios.html)  [![Android](icons/1269841_android_google_material_mobile_os_icon.png)](guides/android.html)

## Desktop ##
[![macOS](icons/652586_apple_ios_mac_os_platform_icon.png)](guides/macos.html) [![Windows](icons/1296843_metro_microsoft_os_pc_system_icon.png)](guides/windows.html)

## Communication Privacy ##
Privacy includes not just data encryption, but anonymity both in who you are and who you are communicating with and when. We reccomend both Signal and Wickr (comparison below). There may be others that work well, but we haven't tested or evaluated them. See below for why you should stick to these apps. They both support all the major platforms.
- [Wickr](https://pro-download.wickr.com/#/version/pro) (we reccommend the Pro version (free) for features like screen sharing)
- [Signal](https://signal.org/download/)


### What NOT to use:
- **Telegram** - [Chats are not encrypted by default](https://www.howtogeek.com/710344/psa-telegram-chats-arent-end-to-end-encrypted-by-default/)
- **WhatsApp** - [Unencrypted Metadata](https://arstechnica.com/gadgets/2021/09/whatsapp-end-to-end-encrypted-messages-arent-that-private-after-all/)
- **Social Media Chat Apps** - These apps generally have your chat content mined for advertising purposes, meaning privacy is not the focus of the application. The app was built for the social aspect, not for security. There are various justifications depending on which app, we reccomend using a chat app built from the ground up with security in mind.
- **Anything other than our recommendations** - Apps that have not been evaluated by security professionals may not have any public vulnerabilities and therefore may *appear* to be more secure, but this couldn't be further from the truth. The security of the app is only improved by security professionals reviewing and submitting bugs to be fixed.

### Signal vs Wickr Comparison
Signal and Wickr are both designed from the ground up with security in mind, and therefore we can recommend using either of these apps; they both come with caveats to use them more securely, here we will discuss some of these
 - To use Signal you must have an active cell phone contract and be able to receive an unsecure SMS
 - To use the Signal desktop app, Signal must first be installed on your phone, this limits usablity to having a working phone and cellular network, and be able to recieve an unsecured SMS to set up the account
 - Be aware that the Signal risk model doesn't seem to include a device being confiscated, see this [DoD bulletin](https://content.govdelivery.com/accounts/USDODDC3/bulletins/2e03518) which describes the problems they identified
   - Moxie, Signal's brilliant founder, has a related [blog post](https://signal.org/blog/cellebrite-and-clickbait/) which describes their risk model and explains how Signal accomodates users with an elevated risk model. Users should still be be **aware** of these assumptions.

     > If you are concerned about a situation where someone else might end up physically holding your device with the screen unlocked in their hands, Signal can still help. Features like [disappearing messages](https://signal.org/blog/disappearing-by-default/) and view-once media messages allow you to communicate more ephemerally and keep your conversations tidy.
- Wickr tends to be configured for an increased risk model by default, to include automatically disappearing messages which is one reason we prefer it; Wickr also doesn't require a cellular contract or leverage unsecure SMS for account setup; it doesn't require you have a phone at all which makes it more usable for more people

### Configuration Recommendations and Features to be Aware of
- Disappearing message time can be set, regardless of read status (Wickr only)
  - Note that Signal's "disappearing messages" feature is dependent on the message being read, and  would more accurately be called a "burn on read timer" (small terminology difference)
- Burn-on-read timer can be set to remove messages that have been read by users after a configurable time period (both Wickr and Signal)
- Link previews are disabled by default, and should be left disabled (Wickr and Signal)
- Key Validation should be done for your contacts (Wickr and Signal)
  - This feature allows you to validate you are speaking to the person you expect to be speaking to and reduces the risk of a man-in-the-middle attack; it relies on an out-of-band communication method (in person for instance)
  - Wickr calls this "[Security Verification](https://support.wickr.com/hc/en-us/articles/115005092548-Security-Verification)"
  - Signal calls this a "[Safety Number](https://support.signal.org/hc/en-us/articles/360007060632-What-is-a-safety-number-and-why-do-I-see-that-it-changed-)"
- [Signal PIN](https://support.signal.org/hc/en-us/articles/360007059792-Signal-PIN) - Your Signal PIN is a code used to support features like non-phone number based identifiers. This means that your PIN can recover your profile, settings, contacts, and who you’ve blocked if you ever lose or switch devices; use this (Signal Only) 
- [Registration Lock](https://support.signal.org/hc/en-us/articles/360007059792-Signal-PIN#manage_registration_lock) - Enabling a Registration Lock will require the Signal PIN to register your phone number with Signal again; use this (Signal Only)
- Anti-Censorship
  - This feature is used to circumvent government monitoring that could block Wickr/Signal by using network proxies (techniques vary)
  - Signal calls this "[Censorship Circumvention](https://signal.org/blog/doodles-stickers-censorship/)" - unsure of exactly how it works since Moxie's [blog post](https://signal.org/blog/looking-back-on-the-front/) saying AWS would suspend them for using domain fronting but I would expect its a similar method but not as public about it
  - Wickr calls this "[Open Access](https://wickr.com/product-feature-wickr-open-access/)" which relies on a network of proxy servers
- Screen Lock - require FaceID, passcode, or biometric to be supplied prior to opening the app or showing new messages; on by default in Wickr, off by default in Signal (recommend you use this)


## Internet Privacy ##
We often think of privacy in terms of advertisers knowing too much about us, but the reality is that some governments monitor the internet traffic of their citizens to look for dissident opinions for persecution. This is a much more serious risk model and requires more careful attention to online behavior. Let's discuss the basics, as this is a highly complex topic; and, for the moment, ignore the attacks that will make even the basics very complex.

What you need to be aware of is the difference between encrypted and unencrypted communications. Modern secure encryption is far too time consuming to break for low priority targets like dissidents, what we need to look out for first is the unencrypted communications. 

Google's [transparency report](https://transparencyreport.google.com/https/overview?hl=en) outlines the trend in websites supporting and enforcing secure web browsing, often denoted by the "https" in your browser's address bar. The summary is that most website support or encorce secure communications at this point. There are also features in modern browsers to force the remaining traffic to use encryption even if the upstream host does not support it (this has its own security ramifications as well).

Most other web traffic is already secured by Transport Layer Security (TLS), with one of the last internet critical protocols to support this being DNS, which now supports TLS and DNS of HTTPS. These are referred to as DoT and DoH respectively.

There are a few ways to secure these last few protocols and websites: 
- use a VPN: [instructions](https://openvpn.net/download-open-vpn/) to run your own on various cloud services, you could also use a trusted 3rd party VPN provider (look elsewhere for these guides)
- use encrypted DNS (see platform hardening guides)
- use [Tor](https://www.torproject.org) 
  - note if you only run the Tor Browser it only protects the traffic from the browser, its also obvious to anything upstream that you are using Tor




## Password Management ##
One of the most common attack methods relies on users reusing their passwords. 

Let's say your BookFace password is "Siegfried1999!" If there is a BookFace breach that leaks your email address and password, attackers will re-use this information on every other web service available. If you have ever reused it on another site, like LankedOn, your account would be compromised. 

Password managers create and store unique passwords very every service, so not only are they harder to guess, but they are also never reused. 

Even with the length and complexity of the above password, its honestly a pretty easy-to-brute-force password being a word (or proper noun), a year, and a symbol. This is one of the most common password formulas we see and well known by attackers.

Use a password manager, protect the data and the datastore as well as the devices you use it on.

### Password Managers:
- [1Password](https://1password.com/)
- [LastPass](https://www.lastpass.com/)
- [KeePass](https://keepass.info/)
- [BitWarden](https://bitwarden.com/)

## Account Security
- **Use Multi-Factor Authentication** if possible; I perfer hardware-based tokens like the venerable [YubiKey](https://www.yubico.com/products/) but TOTP and App-based factors are better than nothing
  - Hardware tokens using modern authentication ensures that even with a spoofed credential-relaying website the credentials won't work as they are signed for only the destination website, this is the strongest authentication mechanism available because it can protect against Social Engineering/user mistakes
  -  SMS is not recommended due to the range of attacks like SIM swapping, Social Engineering, and lack of transport security on SMS which are sent unencrypted and are fairly easy for a nation state to gain access to
  -  Password managers will generate TOTP codes for you which makes them easy to enter and allows a streamlined backup strategy for these credentials
  -  If you use a hardware token, enroll two in case you lose the first one!
  -  If one of your accounts is ever compromised, or you want to be extra careful, make sure no backup authentication devices have been added, forwarding addresses (like for email), or account information has bene changed - attackers will use these methods to leave themselves a backdoor into your accounts even if you change the password!