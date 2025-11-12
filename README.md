# Synoboot backup

<a href="https://github.com/007revad/Synoboot_backup/releases"><img src="https://img.shields.io/github/release/007revad/Synoboot_backup.svg"></a>
![Badge](https://hitscounter.dev/api/hit?url=https%3A%2F%2Fgithub.com%2F007revad%2FSynoboot_backup&label=Visitors&icon=github&color=%23198754&message=&style=flat&tz=Australia%2FSydney)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/paypalme/007revad)
[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/007revad)
<!-- [![committers.top badge](https://user-badge.committers.top/australia/007revad.svg)](https://user-badge.committers.top/australia/007revad) -->

### Description

Back up synoboot after each DSM update so you can recover from a corrupt USBDOM

For Synology models that have a USBDOM only.

### What does it do

When you run the script, either via SSH or Task Scheduler, it backs up synoboot to the path you set at the top of the script.

It backs up synoboot, as well as synoboot1 and synoboot2.

It only creates a new backup if there are no backups with the same filename. So it will only create backups on the first run and after a DSM update.

The backup filenames include: 
1. The Synology model.
2. The Synology's serial number.
3. synoboot or synoboot1 or synoboot2.
4. The DSM version.

1 and 2 are needed so you don't accidentially try to recover a corrupted USBDOM or EEPROM with the wrong image file (in case you have more than one Synology, or migrate the drives to a new Synology).

<p align="center"><img src="/images/filenames.png"></p>

### Download the script

1. Download the latest version _Source code (zip)_ from https://github.com/007revad/Synoboot_backup/releases
2. Save the download zip file to a folder on the Synology.
3. Unzip the zip file.

### To run the script via task scheduler

Schedule the script to run at bootup to automatically create new backups after each DMS update.

See [How to run from task scheduler](https://github.com/007revad/Synoboot_backup/blob/main/how_to_run_from_scheduler.md)

### To run the script via SSH

[How to enable SSH and login to DSM via SSH](https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)

```YAML
sudo -s /volume1/scripts/synoboot_backup.sh
```

**Note:** Replace /volume1/scripts/ with the path to where the script is located.

### Troubleshooting

If the script won't run check the following:

1. Make sure you download the zip file and unzipped it to a folder on your Synology (not on your computer).
2. If the path to the script contains any spaces you need to enclose the path/scriptname in double quotes:
   ```YAML
   sudo -s "/volume1/my scripts/synoboot_backup.sh"
   ```
3. Make sure you unpacked the zip or rar file that you downloaded and are trying to run the synoboot_backup.sh file.
4. Set the script file as executable:
   ```YAML
   sudo chmod +x "/volume1/scripts/synoboot_backup.sh"
   ```

### Screenshots

<p align="center">Backing up synoboot</p>
<p align="center"><img src="/images/do_backup.png"></p>

<br>

<p align="center">synoboot already backed up for this NAS and DSM version</p>
<p align="center"><img src="/images/already_backed_up.png"></p>
