cuttle-docker
=============

Cuttle is a rate-limiting HTTP proxy. See also: [cuttle](https://github.com/mrkschan/cuttle)

On Docker Hub: [rkok1/cuttle](https://hub.docker.com/r/rkok1/cuttle/)

Quick start
-----------

```
# Grab a config
wget -O config/cuttle.yml https://raw.githubusercontent.com/mrkschan/cuttle/master/cuttle.yml

# Run
docker-compose up --build
```

Extending
---------

Example usage:

1. Create cuttle.yml:
    ```
    wget -O config/cuttle.yml https://raw.githubusercontent.com/mrkschan/cuttle/master/cuttle.yml
    ```

2. Create a Dockerfile, containing:
    ```
    FROM rkok1/cuttle
    COPY cuttle.yml /opt/cuttle/config/
    ```

3. The usual:
    ```
    docker build . -t mycuttle
    docker run -p 3128:3128 mycuttle
    ```

4. Test:
    ```
    http_proxy=http://localhost:3128 curl -v http://openbsd.org
    ```