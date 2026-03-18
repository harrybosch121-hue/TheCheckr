# Railway deployment

## Required variables
Set these in Railway service variables:

- `BOT_TOKEN` — Telegram bot token
- `BOT_ADMINS` — comma-separated admin IDs
- `DATA_DIR` — set to `/data` if you attach a Railway volume

## Recommended setup
1. Create a new Railway project from this repo/folder.
2. Add a volume and mount it at `/data`.
3. Set `DATA_DIR=/data`.
4. Set `BOT_TOKEN` in Railway variables.
5. Set `BOT_ADMINS` if needed.
6. Deploy.

## Start command
Railway will use the existing Procfile:

- `worker: python bott.py`

## Important notes
- Without a mounted volume, files like `working_sites.txt`, `pending_batches.json`, `user_stats.json`, `approved.txt`, `uploads/`, and `ng/user_proxies.txt` will be ephemeral.
- With `DATA_DIR=/data`, the bot will copy initial runtime files there on first boot and then run from that directory.
- `user_agents.txt` and `addresses.txt` still load from the app directory, which is fine for static seed data.

## Python version
This project currently uses [runtime.txt](runtime.txt) with Python 3.11.
