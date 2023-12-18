# Introduction

Receipt Wrangler has one main configuration file to set up named `config.prod.json`. The details of what everything does will be detailed below.

# Unraid users
For those users installing the Receipt Wrangler in UnRaid here is a quick breakdown of options to consider while installing.

**Network Type**:
You should set your network to match the general docker network.  If configuring your installation for MariaDB or PostgreSQL please make sure that Receipt Wrangler is on the same network as your Database.

**Database Options**:
Modify these settings as appropriate for your database installation.  You will need to pre-configure your Receipt Wrangler database and then complete the fields as appropriate.  DB_ENGINE options are: mariadb, postgresql, sqlite.  If using an SQLite database it is recommended you place the file somewhere that space won't be an issue.

**Config Path**:
You should set up the folder location where you want the Receipt Wrangler configuration files to live.  I recommend `/mnt/user/appdata/ReceiptWrangler` (or something similar).  The installation of the docker container will not create a `config.prod.json` file.  

To manually create one after installation open the terminal from UnRaid and type the following commands:

`cd /mnt/user/appdata/ReceiptWrangler` - this moves you to the folder you created for the configuration file.

`touch config.prod.json` - creates the configuration file.  This is adequate to get the Receipt Wrangler docker to start, however it won't actually do anything outside of allowing you to manually upload receipts until you edit the file.

**Data Path**:

This can be anyplace you would like Receipt Wrangler to store images of the reciepts it keeps.  I recommend storing the images someplace where space won't be an issue.

**Additional Port Mapping**:
If you plan to use email integration, it may be necessary in some network environments to forward the IMAP port from your general network into your docker network.  This can be accomplished during setup by clicking on "Add another Path, Port, Variable, Label, or Device" and adding TCP port 993 from the host network to the docker network.

# Configuration

Sample config:

```json
{
  "aiSettings": {
    "type": "type",
    "url": "url",
    "key": "key"
  },
  "secretKey": "randomlyGeneratedSecureString"
}
```

- aiSettings: These settings are used to configure the AI Integration. These values are detailed [here](https://github.com/Receipt-Wrangler/.github/tree/main/integrations/ai.md).
- secretKey: This key is used to sign jwts generated from the server.
