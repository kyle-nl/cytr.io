# Securely Backing Up Your Data

At the risk of sounding like an advertisement, it isn't, I've been using Backblaze to back up my computers for a long time. There are a couple reasons
- Price: $70/year for unlimited data
- Unlimited data per computer, so everything gets backed up
- You can set your own encryption key on the device
    - This means your data is never stored in the cloud in a fashion that Backblaze can read it, its encrypted before upload and you never share the key with the company
- Review their [comparison page](https://www.backblaze.com/best-online-backup-service.html) to decide for yourself

A note on the backup method, this is not an image of your system, just the files on it - so restoring this data will not restore Windows or your applications, just the documents, photos, downloads, etc you have saved. There are other backup solutions out there for doing live images of systems but not covered here.


I now use a local Synology NAS that backs up to Backblaze B2, in effect its the same thing but allows more flexibility recovery speed because of the local cache.