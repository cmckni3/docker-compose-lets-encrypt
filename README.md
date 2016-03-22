# Let's Encrypt Docker Example

Examples of how to manually generate [Let's Encrypt](https://letsencrypt.org)
certificates manually using docker and docker-compose.

This method is *not* recommended if a stable plugin can automate this
process on the web server.

## Usage

* Create a certificate using [manual domain verification](https://letsencrypt.readthedocs.org/en/latest/using.html#manual)

```bash
# docker compose
docker-compose run --rm --entrypoint 'letsencrypt certonly --manual -d example.com -d www.example.com' letsencrypt
# docker
docker run --rm --entrypoint 'letsencrypt certonly --manual -d example.com -d www.example.com' letsencrypt
```

* Create a certificate using the [Let's Encrypt standalone server](https://letsencrypt.readthedocs.org/en/latest/using.html#standalone)

```bash
# docker compose
docker-compose run --rm --service-ports --entrypoint 'letsencrypt certonly --standalone -d example.com -d www.example.com' letsencrypt
# docker
docker run --rm -p 80:80 -p 443:443 --entrypoint 'letsencrypt certonly --standalone -d example.com -d www.example.com' letsencrypt
```

* Start a container interactively (useful for debugging or fixing dependencies)

```bash
# docker-compose
docker-compose run --rm --entrypoint /bin/bash letsencrypt
# docker
docker run -it --rm --entrypoint /bin/bash letsencrypt
```

## Questions about the [Let's Encrypt](https://letsencrypt.org) client?

The full documentation can be found at [Read the Docs](https://letsencrypt.readthedocs.org/en/latest/intro.html)
