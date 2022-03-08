Credit to [DecentSecurity.com](https://decentsecurity.com/#/securing-your-computer/) for the basis of this guide, I have updated some parts of this 2+ year old document

# Windows
Windows is an enterprise-ready, highly configurable operating system and as such can take a long time to properly manage and configure.

From Microsoft's own [security documentation](https://docs.microsoft.com/en-us/windows/security/):

> Security baselines are an essential benefit to customers because they bring together expert knowledge from Microsoft, partners, and customers.

> For example, there are over 3,000 Group Policy settings for Windows 10, which does not include over 1,800 Internet Explorer 11 settings. Of these 4,800 settings, only some are security-related. Although Microsoft provides extensive guidance on different security features, exploring each one can take a long time. You would have to determine the security impact of each setting on your own. Then, you would still need to determine the appropriate value for each setting.


## Start Fresh
The best thing to do is start from the bare hardware and install Windows 10 from scratch with UEFI, TPM, and SecureBoot turned on. If you don't want to do that, skip to Section B. Any retail computer purchased with Windows 8.1 will already have these turned on.

1. Update BIOS
   - For best compatibility and security you should update your computer's BIOS. A modern BIOS (really UEFI) is a full operating system that runs below and at the same time as Windows, and needs patches too! People who built computers in the early 2000's will tell you BIOS updates are risky - and they were - but not anymore. These updates deliver fixes, features, and security updates you won't ever hear on the news.

   - Even new computers/motherboards need updates. If you're starting from scratch, do the BIOS update after installing Windows 10.

   - You can find the BIOS update tool on your manufacturer's driver page for your computer model. You will need to reboot for it to take effect. If you have a Surface, BIOS updates are delivered through Windows Update.

2. Prepare Windows Bootable Media
   - To get ready to install Windows 10 64 bit on the bare hardware, use Microsoft's Media Creation Tool to create a bootable DVD or USB stick.

   - Make sure everything is backed up before proceeding. The following changes will wipe your Windows installation.

3. Configure BIOS
    > **This part is important and something few guides discuss.**

   - From the boot of your computer, press the setup hotkey. It may be F1, F2, F8, F10, Del, or something else to get into SETUP mode. Again, **BACKUP YOUR DATA**.

   - In the BIOS:

     - Set a BIOS password. It can be simple, password managers don't work here, so don't lock yourself out. This is only to prevent malicious modification by someone in front of the computer or by a program trying to corrupt it.

     - Change boot to/prioritize UEFI. Disable everything except UEFI HDD and UEFI DVD (or USB UEFI if you plan on using a USB stick to install Windows) - disable all but your primary boot device after install.

     - Enable the TPM (if available) and SecureBoot (if available) options. This is important, as it is the underpinnings of the chain of trust in the boot process.

     - Disable 1394 (FireWire) and ExpressCard/PCMCIA (if you're on a laptop) as a layer to further mitigate DMA attacks. This isn't as important anymore, but if you don't use them you might as well turn them off.

     - If you want - and if the computer offers it - you can enable a System and HDD password. We will be using BitLocker to protect the disk, but this is an extra layer you can add if you want. I don't do this.

     - If you don't use the webcam or microphone, you may be able to turn them off in the BIOS.

     - Save settings and shut down.

 1. Install Windows 10
    - Insert your DVD/USB. Boot the computer and use the boot menu hotkey to boot to your UEFI DVD or UEFI USB. The hotkey is often F10 or F12. Search the web or manufactuer's documentation if you can’t figure out how to get to the boot menu.

    - Follow the prompts and install Windows. If it gives you an option of where to install Windows to, and there's already a partition, delete the partition first.


4. Update Windows 10
   - In Start > Settings > Update, continue updating and rebooting Windows until there's nothing left to update. Wait until this is done before intalling anything else. 

5. Set UAC to full
    > User Account Control (UAC) is a fundamental component of Microsoft's overall security vision. UAC helps mitigate the impact of malware. Each app that requires the administrator access token must prompt for consent. The one exception is the relationship that exists between parent and child processes.

    - This means if a piece of malware attempts to use administrative priveleges to do something nasty, it has to prompt for consent. Ther are bypasses, but its still smarter to turn it on than be nihilistic about it.
  
   - Follow [these instructions](https://www.tenforums.com/tutorials/3577-change-user-account-control-uac-settings-windows-10-a.html) to set UAC to the highest option, "Always notify me." Anything less allows any malware to instantly elevate to administrator level permissions. UAC isn't magic, but it's a layer you want to use.

6. Enable Drive Encryption
   - If you have Windows 10 Home:

      - Start > Settings > System > About
      - Look for the "Device encryption" setting at the bottom of the About pane. If it's not there, your computer does not support the limited encryption feature that Home supports. You should upgrade to Windows 10 Pro or set a HDD password in your BIOS if your computer supports it. Depending on model of drive, HDD password will provide less protection than BitLocker.

   - If you have Windows 10 Pro (best option):

     - Right-click on Start > Control Panel > BitLocker Drive Encryption > Turn on BitLocker

     - If it says you don't have a TPM: [how to use BitLocker without a TPM](https://www.howtogeek.com/howto/6229/how-to-use-bitlocker-on-drives-without-tpm/).

   - Why not use TrueCrypt/Veracrypt?

     - With SecureBoot, before your computer boots to Windows it verifies the OS hasn't been corrupted with a bootkit that modifies Windows that lets a virus run hidden. 3rd party encryption tools break this chain of trust that flows from UEFI to Windows bootloader to BitLocker. This chain of trust is critical for preventing an entire category of attacks against Windows. This is not theoretical, chain-of-trust in the boot process stops real-world attacks.

## Anti-Virus / Anti-Malware
I am asked quite frequently by friends which software to use for anti-malware on Windows. This question is much easier to answer than ever before as Microsoft now has the best built-in anti-malware it has ever had, and its included with your Windows license. Windows Defender's performance is comparable to the best products on the market. With some configuration settings and additional business features like Defender for Endpoint, Azure Sentinel, etc. (license required) it easily competes with the best enterprise tools out there. 

- Don't disable Windows Defender via settings or by installing some bundled or free anti-malware tool
- Enable all of the [security features](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-microsoft-defender-antivirus-features?view=o365-worldwide) you are comfortable with. I say "comfortable with" because if suspicious or malicious files are detected Defender may upload samples to Microsoft's servers for further evaluation - some people may be concerned for their data privacy using this feature. See the [Cloud Protection Documentation](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission?view=o365-worldwide) for more information

## Web Browser Security
This section is dedicated to installing and configuring a web browser. Chromium based browsers remains the standard with impressive security. Mozilla has spent years completely revamping the security model and reliability code of Firefox, it’s an extremely fast, secure choice.

Microsoft Edge, based on Chromium, is built into Windows and works well with system security controls. Personally I still prefer Brave or Firefox but Microsoft has done a good job on this new browser.

Options are great, install whichever you prefer or both:

8.1 Install [Brave](https://brave.com) 64 bit
Make sure Brave installs for all users so it is in a directory that requires administrative permissions to modify and is able to auto-update.

8.2 Install Firefox 64 bit
Again, Firefox is a great choice for a browser. You should ensure you’re using Firefox 64-bit.

- Consider a content blocker like uBlock Origin
  - The majority of threats to users come through malicious advertisements displayed on mainstream websites. Fake pop-ups saying your computer is infected also target less technically proficient users that get tricked into calling a scam tech support company.

  - uBlock Origin is a fast, effective, and reputable “ad-blocking” software

## Other Software
- Adobe Reader DC
    - Adobe Reader is pretty safe if you have the full suite of security settings turned on. In the case of Adobe Reader DC, there's just one setting you need to change:
      - Edit > Preferences > Security (Enhanced) > Protected View > Files from potentially unsafe locations

- Microsoft Office
  - Follow this [guide](https://www.gpetrium.com/increase-ms-security/) for reducing the attack surface of Microsoft Office

- General Recommendations
  - Don't install random software from unknown vendors
  - Don't install games, browser plugins, or any other add-ons you aren't familiar with (if in doubt ask a professional)
  - If software is "free", your data is likely the cost
  - Don't steal software, pirated software invariably has a virus
  - Don't click links or open documents you aren't expecting, even if they are from someone you recognize - email can be spoofed and accounts compromised


## More Settings
- I'd like to get deeper into the weeds on things to configure like disabling like the Guest Account, LLMNR, NETBIOS, SMBv1/v2 - but, this is a huge task (300+ controls) requiring a more complex explanation of why and guides on how, so this will have to do for now
    - Most of these settings are included in the Microsoft Security Baselines available [here](https://www.microsoft.com/en-us/download/details.aspx?id=55319)
- To protect against some password brute-forcing attacks, ensure your password is long (13+ chars) and complex