# n8n on fly.io for Byrdson Services

1. Create a Supabase Postgres database.
1. Comment out `DB_POSTGRESDB_SSL_CA_FILE`.
2. `fly launch --copy-config --no-deploy --org byrdson-services`
3. `fly secrets import --app n8n-byrdson < .env`
4. `fly deploy --ha=false`
5. Install Supabase SSL CA using n8n execute command node. `wget -P /home/node/.n8n https://supabase-downloads.s3-ap-southeast-1.amazonaws.com/prod/ssl/prod-ca-2021.crt`.
6. Uncomment `DB_POSTGRESDB_SSL_CA_FILE`.