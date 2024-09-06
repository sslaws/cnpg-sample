# Sample CloudNativePG cluster creation and restore

## Cluster Creation

The hg.yaml file has a few [PLACE HOLDERS] but is otherwise a complete sample and can be run with kubectl apply.

It will create a HA instance with 2 replicas and 3 PGBouncer instances.  An application DB will be created along with a YAML specified app credentials.  SuperUser access can be enabled and if so will automatically create a secret containing the password.

The WAL files will be shipped to Object Storage every 5 minutes and the database will be backed up nightly at 3am UTC.

SuperUser access can be enabled/disabled at anypoint and reapplied.

## Restore Cluster

The restore.yaml has a similar structure with S3 and application credentials being YAML specified.  The intent here was that a restore may happen in an alternate namespace which is why these are duplicated.

The restore will recover the DB from Object Storage all the way to the latest WAL.
