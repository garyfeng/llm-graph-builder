# Testing a local docker-compose setup
----

Per the [README.md] file, 

> If you are using Neo4j Desktop, you will not be able to use the docker-compose but will have to follow the separate deployment of backend and frontend section.

Wondering why we can't add a Neo4j in the docker. 


----
# Testing

1. Running the docker-compose as is to confirm everything works.

```sh
docker compose up
```

This builds the dockerfiles under `backend` and `frontend` folders. Taking some time.

Encountered an issue where `install==1.3.5` is not compatible with `python 3.10`.
> 12.91 ERROR: Ignored the following versions that require a different python version: 2.10.0 Requires-Python >=3.6, <3.10; 2.11.0 Requires-Python >=3.6, <3.10; 2.12.0 Requires-Python >=3.6, <3.10; 2.13.0 Requires-Python >=3.6, <3.10; 2.13.1 Requires-Python >=3.6, <3.10; 2.14.0 Requires-Python >=3.6, <3.10; 2.15.0 Requires-Python >=3.6, <3.10; 2.16.0 Requires-Python >=3.6, <3.10; 2.16.1 Requires-Python >=3.6, <3.10; 2.17.0 Requires-Python >=3.6, <3.10; 2.18.0 Requires-Python >=3.6, <3.10; 2.19.0 Requires-Python >=3.6, <3.10; 2.20.0 Requires-Python >=3.6, <3.10; 2.21.0 Requires-Python >=3.6, <3.10; 2.22.0 Requires-Python >=3.6, <3.10; 2.22.1 Requires-Python >=3.6, <3.10; 2.23.0 Requires-Python >=3.6, <3.10; 2.23.1 Requires-Python >=3.6, <3.10; 2.23.2 Requires-Python >=3.6, <3.10; 2.23.3 Requires-Python >=3.6, <3.10; 2.24.0 Requires-Python >=3.6, <3.10; 2.24.1 Requires-Python >=3.6, <3.10; 2.25.0 Requires-Python >=3.6, <3.10; 2.25.1 Requires-Python >=3.6, <3.10; 2.25.2 Requires-Python >=3.6, <3.10; 2.26.0 Requires-Python >=3.6, <3.10; 2.27.0 Requires-Python >=3.6, <3.10; 2.27.1 Requires-Python >=3.6, <3.10; 2.28.0 Requires-Python >=3.6, <3.10; 2.28.1 Requires-Python >=3.6, <3.10; 2.29.0 Requires-Python >=3.6, <3.10; 2.6.2 Requires-Python >=3.6, <3.9; 2.7.0 Requires-Python >=3.6, <3.10; 2.8.0 Requires-Python >=3.6, <3.10; 2.9.0 Requires-Python >=3.6, <3.10
12.91 ERROR: Could not find a version that satisfies the requirement install (from versions: none)
12.91 ERROR: No matching distribution found for install
>------
>failed to solve: process "/bin/sh -c pip install --upgrade pip && pip install -r requirements.txt" did not complete successfully: exit code: 1

Tried to go back to `python 3.9.9`:

>14.55 ERROR: Ignored the following versions that require a different python version: 2.6.2 Requires-Python >=3.6, <3.9
14.56 ERROR: Could not find a version that satisfies the requirement install==1.3.5 (from versions: none)
14.56 ERROR: No matching distribution found for install==1.3.5
>------
>failed to solve: process "/bin/sh -c pip install --upgrade pip && pip install -r requirements.txt" did not complete successfully: exit code: 1

I searched the repo and didn't see anywhere `import` was used. So removing it from the `requirements.txt` file and go back to `python 3.10`:


