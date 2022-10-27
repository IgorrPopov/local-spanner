# Local GCP Spanner

This project helps you to run GCP Spanner for local development purposes.

This is Spanner emulator, and it's not intended for production.

If you use **Node.js** you run these scripts from the package.json file (or you can just run **docker-compose** commands directly)

```
  "scripts": {
    "spanner:up": "docker-compose -f ./spanner.docker-compose.yaml up --build spanner gcloud",
    "spanner:down": "docker-compose -f ./spanner.docker-compose.yaml down --remove-orphans",
    "spanner:cli": "docker-compose -f ./spanner.docker-compose.yaml up -d spanner-cli && docker attach spanner-cli",
    "spanner:cli:stop": "docker-compose -f ./spanner.docker-compose.yaml stop spanner-cli"
  }
```

Put your valid DML and DDL scripts into corresponding directories in the migration directory.

**IMPORTANT!** Before using please visit these links in order to have overall info about Spanner emulator (how it works, and what restrictions it has)

- https://cloud.google.com/spanner/docs/emulator
- https://cloud.google.com/spanner/docs/emulator#client-libraries
- https://github.com/GoogleCloudPlatform/cloud-spanner-emulator