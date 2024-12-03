PGAdmin highly recommended for those not familiar with PostgreSQL:
- PGAdmin: https://www.pgadmin.org/download/

## Deploying

- Ensure there exists a .env file in the backend directory with the following fields:
  - `DB_NAME=placenet`
  - `DB_USER=postgres`
  - `DB_PASSWORD=yourpostgrespasswordhere`
  - `DB_HOST=127.0.0.1`
  - `DB_PORT=5432`
  - `PORT=3000`
  - `JWT_SECRET=bat00bataupwcpsEQLbat00bat`
  - `AWS info will also be needed. Create an S3 bucket and add the AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_REGION, and AWS_BUCKET_NAME like with the other properties above.`
    
- Run the backend with `node startServer.js backend`
- Quit the server with "Ctrl/Cmd + C".
- The server won't run if the database isn't online and operational.
