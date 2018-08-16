# Postgres docker container with postgis plugin and wale for backup

This image serves as the database for [FROST-Server](https://github.com/BowenWang29/docker-SensorThingsServer). It initalizes a postgresql database container based on [docker-postgis](https://github.com/appropriate/docker-postgis) with [WAL-E](https://github.com/wal-e/wal-e) installed for WAL archiving.

Environment variables must be pass to the container for WAL-E, or WAL-E is not configured.

This image backups at 9 am UTC and cleanups backups at 9:30 am UTC and retains up to 10 backups. These settings is found in __/scripts/setup-wale.sh__.

This image has three volumes:
- postgis_data_volume:/var/lib/postgresql/data
- postgis_backup_volume:/lib/postgresql/backup
- postgis_env_volume:/etc/wal-e.d/env
