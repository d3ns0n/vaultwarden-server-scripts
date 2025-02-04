# Install vaultwarden

For a more detailed description please refer to [https://lab.uberspace.de/guide_vaultwarden/](https://lab.uberspace.de/guide_vaultwarden/).

```shell
cd ~/vaultwarden
./docker-image-extract vaultwarden/server:alpine
```

## Configure subdomain

```shell
uberspace web domain add vault.username.uber.space
```

## Setup web backend

```shell
uberspace web backend set vault.username.uber.space --http --port 8000
```

## Configure vaultwarden

```shell
cp templates/.env.template .env
~/vaultwarden/output/vaultwarden hash
vim .env
```

Adjust the configuration from the template.

## First start and test

```shell
mkdir ~/vaultwarden/data
export ENV_FILE=$HOME/vaultwarden/.env
export DATA_FOLDER=$HOME/vaultwarden/data
~/vaultwarden/output/vaultwarden
```

If there is no error, you are good to go. You should be able to access your vault on https://vault.username.uber.space

## Setup daemon

```shell
cp ~/vaultwarden/templates/vaultwarden.ini ~/etc/services.d/vaultwarden.ini
supervisorctl reread
supervisorctl update
```

## Finishing installation

You are done. Point your Browser to your installation URL https://vault.username.uber.space and create your user. To disable registrations uncomment
the line `# SIGNUPS_ALLOWED=false` in `~/vaultwarden.env`.