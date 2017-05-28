# docker-puppetmaster
puppet master docker container

_Note that in most cases you should not use this and instead use the newer puppetserver build.  - NWG, May 28, 2017_

This is a general purpose puppet master.  Run initially with the dir mounts to /tmp/etc/puppet, etc, and copy the files there for future loading from the host dir.

```
#!/bin/bash

ETCDIR="${ETCDIR:-/home/docker/puppetmaster/etc}"
LIBDIR="${LIBDIR:-/home/docker/puppetmaster/lib}"

if [ ! -d $ETCDIR ]; then mkdir -p $ETCDIR; fi
if [ ! -d $LIBDIR ]; then mkdir -p $LIBDIR; fi

docker run -d --name puppetmaster -h puppet -p 8140:8140 -v ${ETCDIR}:/etc/puppet -v ${LIBDIR}:/var/lib/puppet guyton/puppetmaster
```

