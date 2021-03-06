# Maintenance Page
A simple static maintenance page in a docker-compose

`master` branch on this repo will not run locally, it attempts to set up SSL certs with certbot, this requires an active domain pointing at your machine and open ports.

The `local` branch exposes port 8080 and does not set up SSL, use this for local dev.

If you don't want/need certs in your live environment; use the local branch, and just change the `ports` in `docker-compose.yml` from `8080:80` to `80:80`

## Dependencies
docker-compose or compatible alternative

## Usage
- Adjust the static html in this repo's `/webroot` to your liking (you can also do this while it's running)
- change `server_name localhost` in `conf.d/nginx.conf` to your domain i.e. `server_name example.com`
- similarly, change the `ssl_certificate` and `ssl_certificate_key` lines to replace `server.company.com` with your domain `example.com`
- set `CERTBOT_EMAIL` env variable, many ways to do this, but you can just `echo "CERTBOT_EMAIL=user@example.com" >> .env` in the root of this directory (with your own email address obviously)
- run with `docker-compose up` or `docker-compose up -d` for detached mode once you're ready.
- stop with `docker-compose down`


[Photo by Arthur Brognoli from Pexels](https://www.pexels.com/photo/high-angle-shot-of-mountain-2327372)
