# fileVault

A netdisk solution for cloud servers.

This docker compose file is using these images:
 -  `Nginx`
 -  `Mysql`
 -  `Filerun`
 -  `Aria-pro` (by [P3TERX](https://github.com/P3TERX/Docker-Aria2-Pro))
 -  `Aria-ng` (also by [P3TERX](https://github.com/P3TERX/Docker-Aria2-Pro))

----

## SSL

SSL is enabled by default, one needs to set his own certs in `conf/nginx/http.conf`, and store in ssl

Since I am using [Cloudflare](https://www.cloudflare.com) to protect my server, its `origin server` certifacate is set. You can also use your own cert or use [acme.sh](https://github.com/acmesh-official/acme.sh)



----

## How to use

Clone this repo

```bash
git clone https://github.com/GaryH4/fileVault
cd fileVault
```

And generate `dhparam.pem` file for security
```bash
openssl dhparam -out ./ssl/dhparam.pem -5 2048
```

Now copy the cert files to `./ssl/` directory

Then change settings in `conf/nginx/http.conf`
 - site name
 - SSL cert name

And in `docker-compose.yml`
 - RPC_SECRET

At last,

```bash
docker-compose up -d
# to see log files
docker-compose logs -f --tail="200"
# use ctrl-c to quit
```

----

## Post-configuration

Open `https://your.domain/ariang` and set your aria2 RPC path to `https://your.domain:443/aria2/jsonrpc`
