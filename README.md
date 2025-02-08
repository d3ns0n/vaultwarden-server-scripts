# vaultwarden-server-scripts

Is a collection of opinionated scripts to manage backups and update of a vaultwarden instance on uberspace. This project is inspired
by the [vaultwarden article on UberLab](https://lab.uberspace.de/guide_vaultwarden/).

## Get started

```shell
git clone https://github.com/d3ns0n/vaultwarden-server-scripts.git ~/vaultwarden
mkdir -p ~/vaultwarden/backups/{data,env}
```

A short summary how to install vaultwarden on uberspace can be found [INSTALL_VAULTWARDEN.md](INSTALL_VAULTWARDEN.md).

## Backup

```shell
crontab -e
```

and add the backup script. The output will be written to `/home/username/vaultwarden/backups/backup-vaultwarden.log`. In case of an error there will still be an email.

```shell
0 0 * * * /home/username/vaultwarden/backup-vaultwarden >> /home/username/vaultwarden/backups/backup-vaultwarden.log
```

## Update vaultwarden

Subscribe to new releases on [GitHub](https://github.com/dani-garcia/vaultwarden/releases)

```shell
~/vaultwarden/update-vaultwarden
```

Check the logs and make sure that everything is up and running again.
