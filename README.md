# Postgres docker container with wale

Based on https://github.com/docker-library/postgres with [WAL-E](https://github.com/wal-e/wal-e) installed.

Environment variables to pass to the container for WAL-E, all of these must be present or WAL-E is not configured.

Create an IAM user in a group with GetObject, ListBucket and PutObject on the bucket you want to use (and that it's not public).

Use the to set the ENV variables

| ENV | Default | Description |
|------------- | -------------|------------- |
| AWS_SECRET_KEY | None | from IAM user's credentials, used to authenticate with S3 |
| AWS_ACCESS_KEY` | None | from IAM user's credentials, used to authenticate with S3 |
| WALE_S3_PREFIX="s3://{bucketname}/{path}" | s3://postgres-backups/ | from S3 bucket, used as the destination for database backups |
| RETAIN_BACKUP_COUNT | 7 | Total number of backups to keep in S3 |
| BACKUP_CLEANUP_CRON | 0 4 * * * | Perform backup cleanup everyday at 4 am. |
| BACKUP_CRON | 0 3 * * * | Perform database backups everyday at 3 am. |