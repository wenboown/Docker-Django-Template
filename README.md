# Deployment Docker of Django, PostgreSQL database, NginX, Gunicorn
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FMexsonFernandes%2FDocker-Django-NginX-PostgreSQL-Gunicorn-Deployment&count_bg=%2383DF3D&title_bg=%23000000&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

This is a [Docker][] setup for deploying your web application based on Django. It also contains tox file for testing your app.

<a href='https://ko-fi.com/Y8Y31LBT4' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://cdn.ko-fi.com/cdn/kofi3.png?v=2' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

## Requirements
You need to install [Docker][] and [Docker-Compose][].

## Production checklist
make sure your django app is configures for production use using this <a href='https://docs.djangoproject.com/en/2.1/howto/deployment/checklist/'>link</a>.

## Build
`docker-compose build` or `make build`.

## Django models in database
`docker-compose run --rm djangoapp /bin/bash -c 'cd hello; ./manage.py makemigrations'`.

## Migrate database
`docker-compose run --rm djangoapp /bin/bash -c 'cd hello; ./manage.py migrate'`.

# Database and static volumes
The static files are mounted wih the volumes of the docker-compose files! However, if you change the static files 
make sure, you remove the volumes with `docker volume prune` or run `docker compsose down -v`. Those commands remove 
the volumes and if you run `docker compose build` again the volumes will be mounted again correctly 😄 
You can inspect all listed mounted files in the menu.

## Run
Remember to pass `DJANGO_SETTINGS_MODULE` in when you run it:
`DJANGO_SETTINGS_MODULE=hello.settings.development docker compose up`.
or set it in the `config/service/.env`

## Tests
- `make checksafety`
- `make checkstyle`
- `make test`
- `make coverage`

[Docker]: https://www.docker.com/
[Django]: https://www.djangoproject.com/
[Gunicorn]: http://gunicorn.org/
[NginX]: https://www.nginx.com/
[Postgres]: https://www.postgresql.org/
[Python]: https://www.python.org/
[pipenv]: https://docs.pipenv.org/
[tox]: https://tox.readthedocs.io/en/latest/
[pytest]: https://docs.pytest.org/en/latest/
[safety]: https://pyup.io/safety/
[bandit]: https://github.com/openstack/bandit
[isort]: https://github.com/timothycrosley/isort
[prospector]: https://github.com/landscapeio/prospector
[GitLab]: https://about.gitlab.com/
[Makefile]: https://www.gnu.org/software/make/manual/make.html
[Docker-Compose]: https://docs.docker.com/compose/

## Reference
[Example using Docker, Django, multiple Postgres databases, NginX, Gunicorn, pipenv, GitLab CI and tox][post]

[post]: https://github.com/pawamoy/docker-nginx-postgres-django-example

## License
Software licensed under the [ISC license](/LICENSE).
