# self-hosted-services

This repository contains everything you need to start self-hosting a core set of privacy-preserving services that I have found helpful, all run via a common [Docker Compose](https://docs.docker.com/compose/) configuration using [Let's Encrypt](https://letsencrypt.org/) for SSL certificates.

## Requirements

- [Git](https://git-scm.com/downloads)
- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Ports `80/tcp` and `443/tcp` exposed/forwarded to the host
- DNS entries for your top-level domain and each desired sub-domain

## Included Services

- [Nextcloud](https://github.com/nextcloud/server)
  - A self-hosted server for hosting files, photos, backups, contacts, calendars, and much more
- [Uptime-kuma](https://github.com/louislam/uptime-kuma)
  - It is a self-hosted monitoring tool like "Uptime Robot"
- [Send](https://github.com/timvisee/send)
  - a fork of Mozillas's Firefox Send, which was an encrypted file sharing tool
- [Cryptpad](https://github.com/xwiki-labs/cryptpad)
  - CryptPad is a collaboration suite that is end-to-end-encrypted and open-source
- [Nitter](https://github.com/zedeus/nitter)
  - A privacy-preserving Twitter front-end
- [PrivateBin](https://privatebin.info/)
  - A privacy-preserving and encrypted-by-default pastebin

_NOTE: If you do not want to run one of the services above simply comment out or delete the relevant service section from `docker-compose.yml`._

## How does it work?

This repo relies on Docker Compose to configure and run all of the above services, leveraging Traefik to automatically expose each service, [request and maintain](https://doc.traefik.io/traefik/user-guides/docker-compose/acme-tls/) Let's Encrypt certificates for SSL, and handle all proxying.

## Updates

Automatic updates are provided by the [Watchtower](https://containrrr.dev/watchtower/) container that watches and updates base images of services when available. It will automatically search for, download, and migrate your services to updated images whenever available.

## Logging

If you find yourself in need of viewing logs for a given service, simply run the following to tail all logs:

```bash
docker-compose logs --follow
```

To view the logs of a single service, run:

```bash
docker-compose logs --follow <service_name>
```

## Getting Started

As this simply helps you get these services running, using each service is outside of the scope of this project. However, below are some links for getting started with each:

- [Nextcloud](https://docs.nextcloud.com/server/21/user_manual/en/)
- [Nitter](https://nitter.net/about)
- [PrivateBin](https://privatebin.info/)
- [CryptPad](https://docs.cryptpad.fr/en/index.html)
- [Send](https://github.com/timvisee/send/tree/master/docs)
- [Uptime-kuma](https://github.com/louislam/uptime-kuma/wiki/)

## Donations

If you decide to run this and use these services, please don't forget to donate to those people making these services a reality!

- [Nitter](https://github.com/zedeus/nitter#nitter)
- [CryptPad](https://github.com/xwiki-labs/cryptpad)
- [Uptime-kuma](https://opencollective.com/uptime-kuma)

## Additional Resources

- [Docker Compose documentation](https://docs.docker.com/compose/)

## Additional Credits

- https://github.com/containrrr/watchtower
  - Watchtower automates updating base images for other running containers
