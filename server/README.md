Postgres setup (local)
----------------------

Quick options to get a Postgres server running locally for this project.

Docker (recommended):

```bash
docker run --name gifts-db -e POSTGRES_USER=user -e POSTGRES_PASSWORD=pass -e POSTGRES_DB=gifts -p 5432:5432 -d postgres
```

Then copy `.env.example` to `.env` and update values to match the container:

```bash
cd server
cp .env.example .env
# edit .env -> set PGUSER=user, PGPASSWORD=pass, PGDATABASE=gifts
npm start
```

Homebrew (macOS):

```bash
brew services start postgresql
psql postgres -c "CREATE USER user WITH PASSWORD 'pass';"
psql postgres -c "CREATE DATABASE gifts OWNER user;"
cp .env.example .env
# edit .env to match credentials created above
npm start
```

Verify connection:

```bash
nc -vz localhost 5432
psql -h localhost -U user -d gifts -c '\dt'
```

If you prefer a `docker-compose.yml` I can add one.
