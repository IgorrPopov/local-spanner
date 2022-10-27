# Local GCP Spanner

This project helps you to run GCP Spanner for local development purposes.

This is Spanner emulator, and it's not intended for production.

If you use **Node.js** you can run these scripts from the package.json file (or you can just run **docker-compose** commands directly)

```JSON
  "scripts": {
    "spanner:up": "docker-compose -f ./spanner.docker-compose.yaml up --build spanner gcloud",
    "spanner:down": "docker-compose -f ./spanner.docker-compose.yaml down --remove-orphans",
    "spanner:cli": "docker-compose -f ./spanner.docker-compose.yaml up -d spanner-cli && docker attach spanner-cli",
    "spanner:cli:stop": "docker-compose -f ./spanner.docker-compose.yaml stop spanner-cli"
  }
```

#####Environment variables

```bash
    PROJECT_ID=test-project-id
    INSTANCE_NAME=test-instance-name
    DATABASE_NAME=test-database-name
    SPANNER_EMULATOR_HOST=localhost:9010
```

Use **PROJECT_ID**, **INSTANCE_NAME**, and **DATABASE_NAME** for Spanner connection (local and in the cloud).

In order to switch between cloud and local Spanner provide **SPANNER_EMULATOR_HOST** variable to your app, and Spanner [client libraries will connect not to the cloud but to the local emulator.](https://cloud.google.com/spanner/docs/emulator#client-libraries)

Put your valid DML and DDL scripts into corresponding directories in the **/migrations** directory.

You can start **spanner-cli** service and interact with the locally running Spanner emulator directly from the terminal or you can also connect to it via SQL Clients like DBeaver and DataGrip. The only thing you need to do is to set up **autoConfigEmulator** flag from false to true for the GCP Spanner driver.

**IMPORTANT!** Before using please visit these links in order to have overall info about Spanner emulator (how it works, and what restrictions it has)

- https://cloud.google.com/spanner/docs/emulator
- https://cloud.google.com/spanner/docs/emulator#client-libraries
- https://github.com/GoogleCloudPlatform/cloud-spanner-emulator