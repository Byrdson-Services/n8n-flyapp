# n8n on fly.io for Byrdson Services
An n8n self-hosted instance hosted on fly.io made especially for Byrdson Services' Robotic Process Automation (RPA) team.

## fly.io Deployment
1. Create a Supabase Postgres database.
2. Comment out `DB_POSTGRESDB_SSL_CA_FILE` on fly.toml.
3. `fly launch --copy-config --no-deploy --org byrdson-services`
4. `git restore fly.toml`
5. On .env repo: `fly secrets import --app n8n-byrdson < .env`
6. `fly deploy --ha=false`
7. Install Supabase SSL CA using n8n execute command node. `wget -P /home/node/.n8n https://supabase-downloads.s3-ap-southeast-1.amazonaws.com/prod/ssl/prod-ca-2021.crt`
8. Uncomment `DB_POSTGRESDB_SSL_CA_FILE` on fly.toml.
9. `fly deploy`

## Change server configuration
1. `fly deploy`