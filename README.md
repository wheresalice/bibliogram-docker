# bibliogram-docker

Create a new Bibliogram instance in minutes using Docker

## What is included?

| Name | Description | Docker image | Dockerfile |
| --   | --          | --           | -- |
| [Caddy](https://github.com/caddyserver/caddy) | Reverse proxy (create a LetsEncrypt certificate automatically) | [caddy/caddy:2-alpine](https://hub.docker.com/_/caddy) | [Dockerfile](https://github.com/caddyserver/caddy-docker) |
| [Bibliogram](https://sr.ht/~cadence/bibliogram/) | An alternative front-end for Instagram. | [quay/pussthecatorg/bibliogram](https://quay.io/repository/pussthecatorg/bibliogram) | [Dockerfile](https://github.com/PussTheCat-org/docker-bibliogram-quay/blob/master/docker/Dockerfile) |

## How to use it
- [Install docker](https://docs.docker.com/install/)
- [Install docker-compose](https://docs.docker.com/compose/install/) (be sure that docker-compose version is at least 1.9.0)
- Get bibliogram-docker
  ```sh
  cd /usr/local
  git clone https://github.com/wheresalice/bibliogram-docker.git
  cd bibliogram-docker
  ```
- Edit the [.env](https://github.com/wheresalice/bibliogram-docker/blob/master/.env) file to set the hostname and an email- Edit the [.env](https://github.com/wheresalice/bibliogram-docker/blob/master/.env) file to set the hostname and an email
- Edit the [config.js](config.js) file as needed
- Check everything is working: `docker-compose up`
- Run Bibliogram in the background: `docker-compose up -d`

### Start Bibliogram with systemd

You can skip this step if you don't use systemd.

- `cp bibliogram-docker.service.template bibliogram-docker.service`
- Edit the content of `WorkingDirectory` if needed
- Install the systemd unit:
  ```sh
  systemctl enable $(pwd)/bibliogram-docker.service
  systemctl start bibliogram-docker.service
  ```

## How to update?

To update the stack:

```sh
docker-compose pull
docker-compose down
docker-compose up
```

To update this `docker-compose.yml` file check out the latest version on GitHub: [wheresalice/bibliogram-docker](https://github.com/wheresalice/bibliogram-docker)
