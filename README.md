# OneDrive compose

Docker compose configuration for OneDrive client

Making the assumption that the OneDrive folder is located in the home folder.

You need to create `.env` file with `VERSION=x.x.x`

First run
```bash
export ONEDRIVE_DATA_DIR="${HOME}/OneDrive"
export ONEDRIVE_UID=`id -u`
export ONEDRIVE_GID=`id -g`
mkdir -p ${ONEDRIVE_DATA_DIR}
docker run -it --name onedrive -v onedrive_conf:/onedrive/conf \
    -v "${ONEDRIVE_DATA_DIR}:/onedrive/data" \
    -e "ONEDRIVE_UID=${ONEDRIVE_UID}" \
    -e "ONEDRIVE_GID=${ONEDRIVE_GID}" \
    driveone/onedrive:edge
```

Then you can run `docker compose up -d`