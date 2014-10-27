NGINX-Proxy
=============

A Docker build which runs a CentOS 7 container with NGINX and [docker-gen](https://github.com/jwilder/docker-gen)

```
docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock -t russmckendrick/nginx-proxy
```

and then launch your container with the `VIRTUAL_HOST` environment variable;

```
docker run -p 80 -e VIRTUAL_HOST=some.domain.com -t ...
```

or for proxied SSL support

```
docker run -d -p 80:80 -p 443:443 -v /home/containers/ssl:/etc/ssl -v /var/run/docker.sock:/tmp/docker.sock -t russmckendrick/nginx-proxy
```

and then launch your container with the `VIRTUAL_HOST` AND `SSL_PROXY` environment variables;

```
docker run -p 80 -e VIRTUAL_HOST=some.domain.com -e SSL_PROXY=1 -t ...
```

In the example above, Nginx proxy will look for `some.domain.com.crt` and `some.domain.com.key` in the `/home/containers/ssl` directory on the Docker host.
Keep in mind that all 80 traffic will redirect to 443 when SSL proxy is enabled
If you decide not to use SSL for a certain website, you can use `SSL_PROXY=0`

This is based on following by Jason Wilder ....

- [http://jasonwilder.com/blog/2014/03/25/automated-nginx-reverse-proxy-for-docker/](http://jasonwilder.com/blog/2014/03/25/automated-nginx-reverse-proxy-for-docker/)
- [https://github.com/jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)

.... the only reason why I didn't use the Docker `jwilder/nginx-proxy` container was because I wanted to build it on top of my own base image, and also [I am a operating system snob](https://media-glass.es/2014/08/03/operating-system-snob/) :smirk:
