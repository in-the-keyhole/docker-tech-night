first, a little housekeeping -

copy these notes into a newly-created file /mynotes.txt

---

export PS1="\W$ "
while true ; do nc -l 9999 <<<MYNAMEGOESHERE ; done
while true ; do nc -l 9999 < myfile.txt ; done

links:



---

open up a couple terminals, set prompt, navigate into /sandbox

---


## my setup for projector-friendly ide and terminal

- zoom - 125%
- theme - white
- terminal: theme - man_page


---

# `docker help`

is docker installed?

we'll cover blah, blah and blah

```
sandbox$ docker help                                                                                                                                                                               
Usage: docker [OPTIONS] COMMAND [arg...]                                                                                                                                                           
 -H=[unix:///var/run/docker.sock]: tcp://host:port to bind/connect to or unix://path/to/socket to use                                                                                              
                                                                                                                                                                                                   
A self-sufficient runtime for linux containers.                                                                                                                                                    
                                                                                                                                                                                                   
Commands:                                                                                                                                                                                          
    attach    Attach to a running container                                                                                                                                                        
    build     Build an image from a Dockerfile                                                                                                                                                     
    commit    Create a new image from a container's changes                                                                                                                                        
    cp        Copy files/folders from a container's filesystem to the host path                                                                                                                    
    diff      Inspect changes on a container's filesystem                                                                                                                                          
    events    Get real time events from the server                                                                                                                                                 
    export    Stream the contents of a container as a tar archive                                                                                                                                  
    history   Show the history of an image                                                                                                                                                         
    images    List images                                                                                                                                                                          
    import    Create a new filesystem image from the contents of a tarball                                                                                                                         
    info      Display system-wide information                                                                                                                                                      
    inspect   Return low-level information on a container                                                                                                                                          
    kill      Kill a running container                                                                                                                                                             
    load      Load an image from a tar archive                                                                                                                                                     
    login     Register or log in to a Docker registry server                                                                                                                                       
    logout    Log out from a Docker registry server                                                                                                                                                
    logs      Fetch the logs of a container                                                                                                                                                        
    port      Lookup the public-facing port that is NAT-ed to PRIVATE_PORT                                                                                                                         
    pause     Pause all processes within a container                                                                                                                                               
    ps        List containers                                                                                                                                                                      
    pull      Pull an image or a repository from a Docker registry server                                                                                                                          
    push      Push an image or a repository to a Docker registry server                                                                                                                            
    restart   Restart a running container                                                                                                                                                          
    rm        Remove one or more containers                                                                                                                                                        
    rmi       Remove one or more images                                                                                                                                                            
    run       Run a command in a new container                                                                                                                                                     
    save      Save an image to a tar archive                                                                                                                                                       
    search    Search for an image on the Docker Hub                                                                                                                                                
    start     Start a stopped container                                                                                                                                                            
    stop      Stop a running container                                                                                                                                                             
    tag       Tag an image into a repository                                                                                                                                                       
    top       Lookup the running processes of a container                                                                                                                                          
    unpause   Unpause a paused container                                                                                                                                                           
    version   Show the Docker version information                                                                                                                                                  
    wait      Block until a container stops, then print its exit code                          
```



what version are we using?
# `docker version`

```
vagrant$ docker version                                                                                             
Client version: 1.2.0                                                                                               
Client API version: 1.14                                                                                            
Go version (client): go1.3.1                                                                                        
Git commit (client): fa7b24f                                                                                        
OS/Arch (client): linux/amd64     
Server version: 1.2.0                                                                                                           
Server API version: 1.14                                                                                                        
Go version (server): go1.3.1                                                                                                    
Git commit (server): fa7b24f
```

what's containers are running?
# `docker ps`

```
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES                              
vagrant$     
```

nothing, so what images are available to run?
# `docker images`

```
vagrant$ docker images                                                                                                                                     
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE                                                               
ubuntu              14.04               96864a7d2df3        5 days ago          205.1 MB                                                                   
java                8u40                c64588070549        7 days ago          607.2 MB                                                                   
centos              centos7             70214e5d0a90        2 weeks ago         224 MB                                                                     
mongo               2.7.5               5cecf32bbdbb        5 weeks ago         378.8 MB                                                                   
mysql               5.7.4               77ef40ef4fa6        5 weeks ago         252.2 MB                                                                   
node                0.10.30             32b8e915efd9        5 weeks ago         864.9 MB                                                                   
wordpress           3.9.2               30988b0c2902        6 weeks ago         203.7 MB    
```

pick one, let's run
# `docker run`

```
vagrant$ docker run mongo:2.7.5                                                                                                                            
mongod --help for help and startup options                                                                                                                 
2014-09-23T16:47:43.585+0000 I          [initandlisten] MongoDB starting : pid=1 port=27017 dbpath=/data/db 64-bit host=c7ec8f09e735                       
2014-09-23T16:47:43.585+0000 I          [initandlisten]                                                                                                    
2014-09-23T16:47:43.585+0000 I          [initandlisten] ** NOTE: This is a development version (2.7.5) of MongoDB.                                         
2014-09-23T16:47:43.585+0000 I          [initandlisten] **       Not recommended for production.                                                           
2014-09-23T16:47:43.585+0000 I          [initandlisten]                                                                                                    
2014-09-23T16:47:43.585+0000 I          [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.                               
2014-09-23T16:47:43.585+0000 I          [initandlisten] **        We suggest setting it to 'never'                                                         
2014-09-23T16:47:43.586+0000 I          [initandlisten]                                                                                                    
2014-09-23T16:47:43.586+0000 I          [initandlisten] db version v2.7.5                                                                                  
2014-09-23T16:47:43.586+0000 I          [initandlisten] git version: 2966c35b20416d55c3d481e5f254a9befb1b2338                                              
2014-09-23T16:47:43.586+0000 I          [initandlisten] build info: Linux build16.nj1.10gen.cc 2.6.32-431.3.1.el6.x86_64 #1 SMP Fri Jan 3 21:39:27 UTC 2014
 x86_64 BOOST_LIB_VERSION=1_49                                                                                                                             
2014-09-23T16:47:43.586+0000 I          [initandlisten] allocator: tcmalloc                                                                                
2014-09-23T16:47:43.586+0000 I          [initandlisten] options: {}                                                                                        
2014-09-23T16:47:43.588+0000 I JOURNAL  [initandlisten] journal dir=/data/db/journal                                                                       
2014-09-23T16:47:43.588+0000 I JOURNAL  [initandlisten] recover : no journal files present, no recovery needed                                             
2014-09-23T16:47:43.665+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.ns, filling with zeroes...                                  
2014-09-23T16:47:43.665+0000 I STORAGE  [FileAllocator] creating directory /data/db/_tmp                                                                   
2014-09-23T16:47:43.670+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.ns, size: 16MB,  took 0.002 secs                           
2014-09-23T16:47:43.674+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.0, filling with zeroes...                                   
2014-09-23T16:47:43.677+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.0, size: 64MB,  took 0.002 secs                            
2014-09-23T16:47:43.684+0000 I NETWORK  [initandlisten] waiting for connections on port 27017       
```

is it running... (in another terminal)
(ps == process status)

```
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS               NAMES                           
c7ec8f09e735        mongo:2.7.5         "/entrypoint.sh mong   9 minutes ago       Up 9 minutes        27017/tcp           naughty_elion 
```

it's listening on port 27017, can we access it? well, not on localhost at least...

```
vagrant$ curl localhost:27017                                                                                                                              
curl: (7) Failed to connect to localhost port 27017: Connection refused  
```

try robomongo too

let's stop it
# `docker stop`


```
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS               NAMES                           
357005e56062        mongo:2.7.5         "/entrypoint.sh mong   5 seconds ago       Up 5 seconds        27017/tcp           compassionate_tesla             
vagrant$ docker stop 357                                                                                                                                   
357                                                                                                                                                        
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES                              
vagrant$      
```

let's start it back up
# `docker start`

```
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES                              
vagrant$ docker start 357                                                                                                                                  
357                                                                                                                                                        
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS               NAMES                           
357005e56062        mongo:2.7.5         "/entrypoint.sh mong   37 seconds ago      Up 3 seconds        27017/tcp           compassionate_tesla             
vagrant$     
```

can we inspect the running app?
# `docker inspect`

```
vagrant$ docker inspect 357
...
```

what does the app look like to the os?

```
htop

find the app with kill -9 the app
```

docker ps to see that it is gone





or we can also stop it via ctrl-c, assuming the container isn't catching those keys (e.g. a shell)

```
vagrant$ docker run mongo:2.7.5                                                                                                                            
mongod --help for help and startup options                                                                                                                 
2014-09-23T17:03:59.809+0000 I          [initandlisten] MongoDB starting : pid=1 port=27017 dbpath=/data/db 64-bit host=a838cb4d3b4d                       
2014-09-23T17:03:59.809+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:03:59.809+0000 I          [initandlisten] ** NOTE: This is a development version (2.7.5) of MongoDB.                                         
2014-09-23T17:03:59.809+0000 I          [initandlisten] **       Not recommended for production.                                                           
2014-09-23T17:03:59.810+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:03:59.810+0000 I          [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.                               
2014-09-23T17:03:59.810+0000 I          [initandlisten] **        We suggest setting it to 'never'                                                         
2014-09-23T17:03:59.810+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:03:59.810+0000 I          [initandlisten] db version v2.7.5                                                                                  
2014-09-23T17:03:59.810+0000 I          [initandlisten] git version: 2966c35b20416d55c3d481e5f254a9befb1b2338                                              
2014-09-23T17:03:59.810+0000 I          [initandlisten] build info: Linux build16.nj1.10gen.cc 2.6.32-431.3.1.el6.x86_64 #1 SMP Fri Jan 3 21:39:27 UTC 2014
 x86_64 BOOST_LIB_VERSION=1_49                                                                                                                             
2014-09-23T17:03:59.810+0000 I          [initandlisten] allocator: tcmalloc                                                                                
2014-09-23T17:03:59.810+0000 I          [initandlisten] options: {}                                                                                        
2014-09-23T17:03:59.813+0000 I JOURNAL  [initandlisten] journal dir=/data/db/journal                                                                       
2014-09-23T17:03:59.814+0000 I JOURNAL  [initandlisten] recover : no journal files present, no recovery needed                                             
2014-09-23T17:03:59.890+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.ns, filling with zeroes...                                  
2014-09-23T17:03:59.890+0000 I STORAGE  [FileAllocator] creating directory /data/db/_tmp                                                                   
2014-09-23T17:03:59.894+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.ns, size: 16MB,  took 0 secs                               
2014-09-23T17:03:59.900+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.0, filling with zeroes...                                   
2014-09-23T17:03:59.907+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.0, size: 64MB,  took 0.006 secs                            
2014-09-23T17:03:59.913+0000 I NETWORK  [initandlisten] waiting for connections on port 27017                                                              
^C2014-09-23T17:04:05.615+0000 I          [signalProcessingThread] got signal 2 (Interrupt), will terminate after current cmd ends                         
2014-09-23T17:04:05.616+0000 I COMMANDS [signalProcessingThread] now exiting                                                                               
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] shutdown: going to close listening sockets...                                             
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] closing listening socket: 7                                                               
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] closing listening socket: 8                                                               
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] removing socket file: /tmp/mongodb-27017.sock                                             
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] shutdown: going to flush diaglog...                                                       
2014-09-23T17:04:05.617+0000 I NETWORK  [signalProcessingThread] shutdown: going to close sockets...                                                       
2014-09-23T17:04:05.617+0000 I STORAGE  [signalProcessingThread] shutdown: waiting for fs preallocator...                                                  
2014-09-23T17:04:05.617+0000 I STORAGE  [signalProcessingThread] shutdown: final commit...                                                                 
2014-09-23T17:04:05.621+0000 I STORAGE  [signalProcessingThread] shutdown: closing all files...                                                            
2014-09-23T17:04:05.622+0000 I STORAGE  [signalProcessingThread] closeAllFiles() finished                                                                  
2014-09-23T17:04:05.622+0000 I JOURNAL  [signalProcessingThread] journalCleanup...                                                                         
2014-09-23T17:04:05.622+0000 I JOURNAL  [signalProcessingThread] removeJournalFiles                                                                        
2014-09-23T17:04:05.623+0000 I STORAGE  [signalProcessingThread] shutdown: removing fs lock...                                                             
2014-09-23T17:04:05.623+0000 I COMMANDS [signalProcessingThread] dbexit:  rc: 0                                                                            
vagrant$     
```

ok, so how can we access the app externally?, let's 'publish' a port, 

```
vagrant$ docker run --publish 27017:27017 mongo:2.7.5                                                                                                      
mongod --help for help and startup options                                                                                                                 
2014-09-23T17:20:33.130+0000 I          [initandlisten] MongoDB starting : pid=1 port=27017 dbpath=/data/db 64-bit host=d4e1b5db7e8e                       
2014-09-23T17:20:33.130+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:20:33.130+0000 I          [initandlisten] ** NOTE: This is a development version (2.7.5) of MongoDB.                                         
2014-09-23T17:20:33.130+0000 I          [initandlisten] **       Not recommended for production.                                                           
2014-09-23T17:20:33.130+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:20:33.131+0000 I          [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.                               
2014-09-23T17:20:33.131+0000 I          [initandlisten] **        We suggest setting it to 'never'                                                         
2014-09-23T17:20:33.131+0000 I          [initandlisten]                                                                                                    
2014-09-23T17:20:33.131+0000 I          [initandlisten] db version v2.7.5                                                                                  
2014-09-23T17:20:33.131+0000 I          [initandlisten] git version: 2966c35b20416d55c3d481e5f254a9befb1b2338                                              
2014-09-23T17:20:33.131+0000 I          [initandlisten] build info: Linux build16.nj1.10gen.cc 2.6.32-431.3.1.el6.x86_64 #1 SMP Fri Jan 3 21:39:27 UTC 2014
 x86_64 BOOST_LIB_VERSION=1_49                                                                                                                             
2014-09-23T17:20:33.131+0000 I          [initandlisten] allocator: tcmalloc                                                                                
2014-09-23T17:20:33.131+0000 I          [initandlisten] options: {}                                                                                        
2014-09-23T17:20:33.135+0000 I JOURNAL  [initandlisten] journal dir=/data/db/journal                                                                       
2014-09-23T17:20:33.135+0000 I JOURNAL  [initandlisten] recover : no journal files present, no recovery needed                                             
2014-09-23T17:20:33.214+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.ns, filling with zeroes...                                  
2014-09-23T17:20:33.214+0000 I STORAGE  [FileAllocator] creating directory /data/db/_tmp                                                                   
2014-09-23T17:20:33.219+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.ns, size: 16MB,  took 0.001 secs                           
2014-09-23T17:20:33.224+0000 I STORAGE  [FileAllocator] allocating new datafile /data/db/local.0, filling with zeroes...                                   
2014-09-23T17:20:33.227+0000 I STORAGE  [FileAllocator] done allocating datafile /data/db/local.0, size: 64MB,  took 0.002 secs                            
2014-09-23T17:20:33.231+0000 I NETWORK  [initandlisten] waiting for connections on port 27017         
```

```
vagrant$ curl localhost:27017                                                                                                                              
It looks like you are trying to access MongoDB over HTTP on the native driver port. 
```

also show in browser, then stop mongo


ok, let's make an 'app', the cheesiest example

run directly on vm

`while true ; do nc -l 9999 <<<luke ; done`

```
vagrant$ curl localhost:9999                                                                                                                               
luke  
```

```
vagrant$ while true; do nc -l 9999 <<<luke ; done                                                                                                         
GET / HTTP/1.1                                                                                                                                             
Host: 192.168.169.170:9999                                                                                                                                 
Connection: keep-alive                                                                                                                                     
Cache-Control: max-age=0                                                                                                                                   
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8                                                                         
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2062.122 Safari/537.36                       
Accept-Encoding: gzip,deflate,sdch                                                                                                                         
Accept-Language: en-US,en;q=0.8                                                                                                                            
Cookie: autoAuth=true; sess.0643072C=s%3Aj%3A%7B%22userId%22%3A%22noreply%40keyholesoftware.com%22%7D.FtPXg1ybCVtphmRrUh%2By42iGH9ggWioTkYYKsMqKR6g; email=
noreply%40keyholesoftware.com; token=82oahjv2t9  
```

ok, so let's make an 'image' out of our 'app', so we can 'run' it

so, which 'base image' to start with?

```
vagrant$ docker images                                                                                                                                     
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE                                                               
ubuntu              14.04               96864a7d2df3        5 days ago          205.1 MB                                                                   
java                8u40                c64588070549        7 days ago          607.2 MB                                                                   
centos              centos7             70214e5d0a90        2 weeks ago         224 MB                                                                     
mongo               2.7.5               5cecf32bbdbb        5 weeks ago         378.8 MB                                                                   
mysql               5.7.4               77ef40ef4fa6        5 weeks ago         252.2 MB                                                                   
node                0.10.30             32b8e915efd9        5 weeks ago         864.9 MB                                                                   
wordpress           3.9.2               30988b0c2902        6 weeks ago         203.7 MB 
```

well, we're running in ubuntu now, so let's go with that..., what command would we run if we wanted to explore and dig around in the container? almost like we'd want to use what we're using in this vm, like bash or something


```
vagrant$ docker run --interactive --tty ubuntu:14.04 /bin/bash                                                                                             
root@9fab8c6bbdec:/#   
```

we're in, but let's exit out right quick

```
root@9fab8c6bbdec:/# exit                                                                                                                                  
exit                                                                                                                                                       
vagrant$ docker ps -l                                                                                                                                      
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS                     PORTS               NAMES                      
9fab8c6bbdec        ubuntu:14.04        "/bin/bash"         About a minute ago   Exited (0) 6 seconds ago                       silly_lumiere              
vagrant$   
```

actually, let's stop back and see how these containers are isolated and one-off 

```
vagrant$ docker run --interactive --tty ubuntu:14.04 /bin/bash                                                                                             
root@25f7b01338b8:/# ls                                                                                                                                    
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var                                                     
root@25f7b01338b8:/# touch myfiiiiiiiiile                                                                                                                  
root@25f7b01338b8:/# exit                                                                                                                                  
exit                                                                                                                                                       
vagrant$ docker run --interactive --tty ubuntu:14.04 /bin/bash                                                                                             
root@d9501c8210b9:/# ls                                                                                                                                    
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var                                                     
root@d9501c8210b9:/#    
vagrant$ docker run --interactive --tty ubuntu:14.04 ls                                                                                                    
bin   dev  home  lib64  mnt  proc  run   srv  tmp  var                                                                                                     
boot  etc  lib   media  opt  root  sbin  sys  usr   
vagrant$ docker run --interactive --tty ubuntu:14.04 /bin/bash
tree

    `-- tmp                                                                                                                                                                                        
                                                                                                                                                                                                   
4544 directories, 24325 files                                                                                                                                                                      
root@caf547d2063b:/# exit                                                                                                                                                                          
exit                                                                                                                                                                                               
vagrant$ docker run --interactive --tty ubuntu:14.04 /bin/bash                                                                                                                                     
root@44ecb7964ea5:/# apt-get update                                                                                                                                                                
Ign http://archive.ubuntu.com trusty InRelease                                                                                                                                                     
Ign http://archive.ubuntu.com trusty-updates InRelease                                                                                                                                             
Ign http://archive.ubuntu.com trusty-security InRelease                                                                                                                                            
Ign http://archive.ubuntu.com trusty-proposed InRelease                                                                                                                                            
Get:1 http://archive.ubuntu.com trusty Release.gpg [933 B]                                                                                                                                         
Get:2 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]                                                                                                                                 
Get:3 http://archive.ubuntu.com trusty-security Release.gpg [933 B]                                                                                                                                
Get:4 http://archive.ubuntu.com trusty-proposed Release.gpg [933 B]                                                                                                                                
Get:5 http://archive.ubuntu.com trusty Release [58.5 kB]                                                                                                                                           
Get:6 http://archive.ubuntu.com trusty-updates Release [59.7 kB]                                                                                                                                   
Get:7 http://archive.ubuntu.com trusty-security Release [59.7 kB]                                                                                                                                  
Get:8 http://archive.ubuntu.com trusty-proposed Release [110 kB]                                                                                                                                   
Get:9 http://archive.ubuntu.com trusty/main Sources [1335 kB]                                                                                                                                      
Get:10 http://archive.ubuntu.com trusty/restricted Sources [5335 B]                                                                                                                                
Get:11 http://archive.ubuntu.com trusty/universe Sources [7926 kB]                                                                                                                                 
Get:12 http://archive.ubuntu.com trusty/main amd64 Packages [1743 kB]                                                                                                                              
Get:13 http://archive.ubuntu.com trusty/restricted amd64 Packages [16.0 kB]                                                                                                                        
Get:14 http://archive.ubuntu.com trusty/universe amd64 Packages [7589 kB]                                                                                                                          
Get:15 http://archive.ubuntu.com trusty-updates/main Sources [155 kB]                                                                                                                              
Get:16 http://archive.ubuntu.com trusty-updates/restricted Sources [1250 B]                                                                                                                        
Get:17 http://archive.ubuntu.com trusty-updates/universe Sources [105 kB]                                                                                                                          
Get:18 http://archive.ubuntu.com trusty-updates/main amd64 Packages [410 kB]                                                                                                                       
Get:19 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [6341 B]                                                                                                                 
Get:20 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [266 kB]                                                                                                                   
Get:21 http://archive.ubuntu.com trusty-security/main Sources [54.1 kB]                                                                                                                            
Get:22 http://archive.ubuntu.com trusty-security/restricted Sources [40 B]                                                                                                                         
Get:23 http://archive.ubuntu.com trusty-security/universe Sources [11.4 kB]                                                                                                                        
Get:24 http://archive.ubuntu.com trusty-security/main amd64 Packages [182 kB]                                                                                                                      
Get:25 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [40 B]                                                                                                                  
Get:26 http://archive.ubuntu.com trusty-security/universe amd64 Packages [59.8 kB]                                                                                                                 
Get:27 http://archive.ubuntu.com trusty-proposed/main amd64 Packages [169 kB]                                                                                                                      
Get:28 http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages [40 B]                                                                                                                  
Fetched 20.3 MB in 25s (799 kB/s)                                                                                                                                                                  
Reading package lists... Done                                                                                                                                                                      
root@44ecb7964ea5:/# apt-get install tree                                                                                                                                                          
Reading package lists... Done                                                                                                                                                                      
Building dependency tree                                                                                                                                                                           
Reading state information... Done                                                                                                                                                                  
The following NEW packages will be installed:                                                                                                                                                      
  tree                                                                                                                                                                                             
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.                                                                                                                                     
Need to get 37.8 kB of archives.                                                                                                                                                                   
After this operation, 109 kB of additional disk space will be used.                                                                                                                                
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/universe tree amd64 1.6.0-1 [37.8 kB]                                                                                                               
Fetched 37.8 kB in 0s (104 kB/s)                                                                                                                                                                   
Selecting previously unselected package tree.                                                                                                                                                      
(Reading database ... 11518 files and directories currently installed.)                                                                                                                            
Preparing to unpack .../tree_1.6.0-1_amd64.deb ...                                                                                                                                                 
Unpacking tree (1.6.0-1) ...                                                                                                                                                                       
Setting up tree (1.6.0-1) ...                                                                                                                                                                      
root@44ecb7964ea5:/#               

```



even another backtrace, so where are those containers, are they gone?
no, for a couple reasons  - 1, we didn't delete them, we only stopped them / they stopped, 2 - we didn't specify the --rm flag when we ran them
so,

```
vagrant$ docker ps --all                                                                                                                                      
CONTAINER ID        IMAGE               COMMAND                CREATED              STATUS                            PORTS               NAMES            
d9501c8210b9        ubuntu:14.04        "/bin/bash"            37 seconds ago       Exited (0) 6 seconds ago                              sleepy_euclid    
25f7b01338b8        ubuntu:14.04        "/bin/bash"            46 seconds ago       Exited (0) 38 seconds ago                             thirsty_lovelace 
ce73adfc4f32        ubuntu:14.04        "/bin/bash"            About a minute ago   Exited (0) 49 seconds ago                             hungry_bohr                                                                                                                                                           
0d76a50d60ff        ubuntu:14.04        "/bin/bash"            About a minute ago   Exited (127) About a minute ago                       cranky_einstein  
d9a83d01ee9a        ubuntu:14.04        "/bin/bash"            2 minutes ago        Exited (0) 2 minutes ago                              stoic_wright     
d9c693db8415        ubuntu:14.04        "/bin/bash"            3 minutes ago        Exited (0) 2 minutes ago                              condescending_ard
9fab8c6bbdec        ubuntu:14.04        "/bin/bash"            6 minutes ago        Exited (0) 5 minutes ago                              silly_lumiere    
14e8d69da0a3        ubuntu:14.04        "/bin/bash"            7 minutes ago        Exited (130) 6 minutes ago                            insane_blackwell 
d4e1b5db7e8e        mongo:2.7.5         "/entrypoint.sh mong   34 minutes ago       Exited (0) 28 minutes ago                             lonely_feynman   
```

ok, so enough of that, we are trying to create an app

```
vagrant$ docker run --interactive --tty --publish 9999:9999 ubuntu:14.04 /bin/bash                                                                         
root@d444453bdfc2:/# while true; do nc -l 9999 <<<luke ; done                                                                                             
GET / HTTP/1.1                                                                                                                                             
Host: 192.168.169.170:9999                                                                                                                                 
Connection: keep-alive                                                                                                                                     
Cache-Control: max-age=0                                                                                                                                   
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8                                                                         
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2062.122 Safari/537.36                       
Accept-Encoding: gzip,deflate,sdch                                                                                                                         
Accept-Language: en-US,en;q=0.8                                                                                                                            
Cookie: autoAuth=true; sess.0643072C=s%3Aj%3A%7B%22userId%22%3A%22noreply%40keyholesoftware.com%22%7D.FtPXg1ybCVtphmRrUh%2By42iGH9ggWioTkYYKsMqKR6g; email=
noreply%40keyholesoftware.com; token=82oahjv2t9                                                                                                                                                                                                                                                                       
```

```
vagrant$ curl localhost:9999                                                                                                                               
luke  
```

ok, so we know we can serve up our 'app' from a container, so let's ctrl-c to kill netcat, and 'exit' the container,...

we have a container, but the problem is, we want our app to automatically run that netcat command, see out command below?

```
vagrant$ docker ps -l                                                                                                                                      
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                       PORTS               NAMES                     
d444453bdfc2        ubuntu:14.04        "/bin/bash"         5 minutes ago       Exited (130) 4 seconds ago                       sleepy_hawking            
```

remember when we added 'ls' as a command earlier?


```
vagrant$ docker run --publish 9999:9999 ubuntu:14.04 /bin/bash -c 'while true; do nc -l 9999 <<<luke ; done'                          
GET / HTTP/1.1                                                                                                                                             
Host: 192.168.169.170:9999                                                                                                                                 
Connection: keep-alive                                                                                                                                     
Cache-Control: max-age=0                                                                                                                                   
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8                                                                         
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2062.122 Safari/537.36                       
Accept-Encoding: gzip,deflate,sdch                                                                                                                         
Accept-Language: en-US,en;q=0.8                                                                                                                            
Cookie: autoAuth=true; sess.0643072C=s%3Aj%3A%7B%22userId%22%3A%22noreply%40keyholesoftware.com%22%7D.FtPXg1ybCVtphmRrUh%2By42iGH9ggWioTkYYKsMqKR6g; email=
noreply%40keyholesoftware.com; token=82oahjv2t9                                                                                                            
```

```
vagrant$ curl localhost:9999                                                                                                                               
luke  
```

so, we stop in the other terminal
we've been running these containers blocking, i.e. our terminal is taken over 
but most of the time, we run non-interactively, or not attached


```
vagrant$ docker run --detach --publish 9999:9999 ubuntu:14.04 /bin/bash -c 'while true; do nc -l 9999 <<<luke ; done'                                     
11499f12867c133c00113c12b22bf82f5a84fb0f08a4863ce79bb543ce049a62                                                                                           
vagrant$ docker ps                                                                                                                                 
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS                    NAMES                      
11499f12867c        ubuntu:14.04        "/bin/bash -c 'while   26 seconds ago      Up 25 seconds       0.0.0.0:9999->9999/tcp   tender_sinoussi     
vagrant$ curl localhost:9999                                                                                                                               
luke 
vagrant$ docker stop 114                                                                                                                                   
114                                                                                                                                                        
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES                              
vagrant$ curl localhost:9999                                                                                                                               
curl: (7) Failed to connect to localhost port 9999: Connection refused                                                                                     
vagrant$ docker start 114                                                                                                                                  
114                                                                                                                                                        
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS                    NAMES                      
11499f12867c        ubuntu:14.04        "/bin/bash -c 'while   3 minutes ago       Up 2 seconds        0.0.0.0:9999->9999/tcp   tender_sinoussi            
vagrant$ curl localhost:9999                                                                                                                               
luke                                     
vagrant$ docker stop 114                                                                                                                                   
114                                                                                                                                                        
vagrant$   
```

# `docker top`
so what's running inside it?

```
vagrant$ docker top 79c                                                                                                                                    
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD            
root                30877               651                 0                   19:37               ?                   00:00:00            /bin/bash -c wh
ile true; do nc -l 9999 <<<luke ; done                                                                                                                    
root                30922               30877               0                   19:38               ?                   00:00:00            nc -l 9999     
vagrant$   
```


# `docker logs`
so, it's detached, and it doesn't block, but where are the logs (we're just talking about standard out stream now)

```
vagrant$ docker logs 79c                                                                                                                                 
GET / HTTP/1.1                                                                                                                                             
Host: 192.168.169.170:9999                                                                                                                                 
Connection: keep-alive                                                                                                                                     
Cache-Control: max-age=0                                                                                                                                   
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8                                                                         
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2062.122 Safari/537.36                       
Accept-Encoding: gzip,deflate,sdch                                                                                                                         
Accept-Language: en-US,en;q=0.8                                                                                                                            
Cookie: autoAuth=true; sess.0643072C=s%3Aj%3A%7B%22userId%22%3A%22noreply%40keyholesoftware.com%22%7D.FtPXg1ybCVtphmRrUh%2By42iGH9ggWioTkYYKsMqKR6g; email=
noreply%40keyholesoftware.com; token=2fyrs5rk9                                                                                                             
vagrant$ docker logs --follow 79c 
```




# `docker commit`
so, we have a startable and stoppable container, great, but how can we distrubute our docker app? 
how can others 'run' it? we have to make it an 'image' so they can run it?

```
vagrant$ docker commit 114                                                                                                                                 
87549b9a04589dd26b370a5c002c0f99d332f9cc60c70af454bc4bcda447b420                                                                                           
vagrant$ docker images                                                                                                                                     
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE                                                               
<none>              <none>              87549b9a0458        10 seconds ago      205.1 MB                                                                   
ubuntu              14.04               96864a7d2df3        5 days ago          205.1 MB                                                                   
java                8u40                c64588070549        7 days ago          607.2 MB                                                                   
centos              centos7             70214e5d0a90        2 weeks ago         224 MB                                                                     
mongo               2.7.5               5cecf32bbdbb        5 weeks ago         378.8 MB                                                                   
mysql               5.7.4               77ef40ef4fa6        5 weeks ago         252.2 MB                                                                   
node                0.10.30             32b8e915efd9        5 weeks ago         864.9 MB                                                                   
wordpress           3.9.2               30988b0c2902        6 weeks ago         203.7 MB                                                                   
vagrant$      
```


now let's 'run' it

```
vagrant$ docker run --detach --publish 9999:9999 875                                                                                                       
a7191d2ce60ff904841f8028993349b1e03990c942d8ebad5676eb57c036aef0                                                                                           
vagrant$ docker ps                                                                                                                                         
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS                    NAMES                      
a7191d2ce60f        87549b9a0458        "/bin/bash -c 'while   10 seconds ago      Up 10 seconds       0.0.0.0:9999->9999/tcp   sick_mestorf               
vagrant$ curl localhost:9999                                                                                                                               
luke                                                                                                                                                      
vagrant$ stop a71                                                                                                                                          
stop: Unknown job: a71                                                                                                                                     
vagrant$ docker stop a71                                                                                                                                   
a71                                                                                                                                                        
vagrant$   
```

# `docker history`
quick sidetrek
```
vagrant$ docker history 875                                                                                                                                
IMAGE               CREATED             CREATED BY                                      SIZE                                                               
87549b9a0458        6 minutes ago       /bin/bash -c while true; do nc -l 9999 <<<hel   0 B                                                                
96864a7d2df3        5 days ago          /bin/sh -c #(nop) CMD [/bin/bash]               0 B                                                                
809ed259f845        5 days ago          /bin/sh -c apt-get update && apt-get dist-upg   12.39 MB                                                           
9387bcc9826e        5 days ago          /bin/sh -c sed -i 's/^#\s*\(deb.*universe\)$/   1.895 kB                                                           
897578f527ae        5 days ago          /bin/sh -c rm -rf /var/lib/apt/lists/*          0 B                                                                
c1f3bdbd8355        5 days ago          /bin/sh -c echo '#!/bin/sh' > /usr/sbin/polic   194.5 kB                                                           
bfb8b5a2ad34        5 days ago          /bin/sh -c #(nop) ADD file:a889e7d86acdbac15e   192.5 MB                                                           
511136ea3c5a        15 months ago                                                       0 B                                                                
vagrant$                                                                                                                                                   
```

# `docker tag`
back from sidetrek
so, we can run it, but how about what ugly name, want something like this 'docker run myapp'
lets tag it (note, we could have tagged it when we committed)


```
vagrant$ docker images                                                                                                                                     
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE                                                               
<none>              <none>              87549b9a0458        10 minutes ago      205.1 MB                                                                   
ubuntu              14.04               96864a7d2df3        5 days ago          205.1 MB                                                                   
java                8u40                c64588070549        7 days ago          607.2 MB                                                                   
centos              centos7             70214e5d0a90        2 weeks ago         224 MB                                                                     
mongo               2.7.5               5cecf32bbdbb        5 weeks ago         378.8 MB                                                                   
mysql               5.7.4               77ef40ef4fa6        5 weeks ago         252.2 MB                                                                   
node                0.10.30             32b8e915efd9        5 weeks ago         864.9 MB                                                                   
wordpress           3.9.2               30988b0c2902        6 weeks ago         203.7 MB                                                                   
vagrant$ docker tag 875 myapp                                                                                                                              
vagrant$ docker images                                                                                                                                     
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE                                                               
myapp               latest              87549b9a0458        10 minutes ago      205.1 MB                                                                   
ubuntu              14.04               96864a7d2df3        5 days ago          205.1 MB                                                                   
java                8u40                c64588070549        7 days ago          607.2 MB                                                                   
centos              centos7             70214e5d0a90        2 weeks ago         224 MB                                                                     
mongo               2.7.5               5cecf32bbdbb        5 weeks ago         378.8 MB                                                                   
mysql               5.7.4               77ef40ef4fa6        5 weeks ago         252.2 MB                                                                   
node                0.10.30             32b8e915efd9        5 weeks ago         864.9 MB                                                                   
wordpress           3.9.2               30988b0c2902        6 weeks ago         203.7 MB                                                                   
vagrant$ docker run --detach --publish 9999:9999 myapp                                                                                                     
e77f9ffbbbefee9665d01f4a244a63d1aa6b4270170627f1e6999757a90654d7                                                                                           
vagrant$ curl localhost:9999                                                                                                                               
luke                                                                                                                                                      
vagrant$ docker stop e77                                                                                                                                   
e77                                                                                                                                                        
vagrant$     

```

# `docker search`
# `docker push`
# `docker login`
sure, _we_ can run it, but how can we distribute it?

```
vagrant$ docker tag myapp lukewpatterson/myapp 
vagrant$ docker search lukewpatterson/myapp                                                                                                                
NAME                   DESCRIPTION   STARS     OFFICIAL   AUTOMATED                                                                                                                                                                                                                           
vagrant$ docker push lukewpatterson/myapp                                                                                                                  
The push refers to a repository [lukewpatterson/myapp] (len: 1)                                                                                            
Sending image list                                                                                                                                         
                                                                                                                                                           
Please login prior to push:                                                                                                                                
Username: lukewpatterson                                                                                                                                   
Password:                                                                                                                                                  
Email: lukewpatterson@gmail.com                                                                                                                            
Login Succeeded                                                                                                                                            
The push refers to a repository [lukewpatterson/myapp] (len: 1)                                                                                            
Sending image list                                                                                                                                         
Pushing repository lukewpatterson/myapp (1 tags)                                                                                                           
511136ea3c5a: Image already pushed, skipping                                                                                                               
bfb8b5a2ad34: Image already pushed, skipping                                                                                                               
c1f3bdbd8355: Image already pushed, skipping                                                                                                               
897578f527ae: Image already pushed, skipping                                                                                                               
9387bcc9826e: Image already pushed, skipping                                                                                                               
809ed259f845: Image already pushed, skipping                                                                                                               
96864a7d2df3: Image already pushed, skipping                                                                                                               
87549b9a0458: Image successfully pushed                                                                                                                    
Pushing tag for rev [87549b9a0458] on {https://cdn-registry-1.docker.io/v1/repositories/lukewpatterson/myapp/tags/latest}                                  
vagrant$ docker search lukewpatterson/myapp                                                                                                                
NAME                   DESCRIPTION   STARS     OFFICIAL   AUTOMATED                                                                                        
lukewpatterson/myapp                 0                                                                                                                     
vagrant$   
```

ok, so i pushed, where did it go?

https://hub.docker.com/u/lukewpatterson/




so, i 'push'ed, now you pull
# `docker pull`
you pull it, look at history, and run it

...


then i push another, and you directly run, see what happens


```
vagrant$ docker tag myapp lukewpatterson/apptopull                                                                                                         
vagrant$ docker push lukewpatterson/apptopull                                                                                                              
The push refers to a repository [lukewpatterson/apptopull] (len: 1)                                                                                        
Sending image list                                                                                                                                         
Pushing repository lukewpatterson/apptopull (1 tags)                                                                                                       
511136ea3c5a: Image already pushed, skipping                                                                                                               
bfb8b5a2ad34: Image already pushed, skipping                                                                                                               
c1f3bdbd8355: Image already pushed, skipping                                                                                                               
897578f527ae: Image already pushed, skipping                                                                                                               
9387bcc9826e: Image already pushed, skipping                                                                                                               
809ed259f845: Image already pushed, skipping                                                                                                               
96864a7d2df3: Image already pushed, skipping                                                                                                               
87549b9a0458: Image already pushed, skipping                                                                                                               
Pushing tag for rev [87549b9a0458] on {https://cdn-registry-1.docker.io/v1/repositories/lukewpatterson/apptopull/tags/latest}                              
vagrant$    
```

so, i published an app and shared with you





# env vars

how do we configure ready to go containers? a few ways, args to the command, files, and env vars
we'll cover files next, but first let's look at env vars

```
vagrant$ docker run ubuntu:14.04 /usr/bin/printenv                                                                                                                                                 
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin                                                                                                                                  
HOSTNAME=595d6e6972fc                                                                                                                                                                              
HOME=/root                                                                                                                                                                                         
vagrant$ docker run --env HOWDY=THERE ubuntu:14.04 /usr/bin/printenv                                                                                                                               
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin                                                                                                                                  
HOSTNAME=abaafcc95634                                                                                                                                                                              
HOWDY=THERE                                                                                                                                                                                        
HOME=/root                                                                                                                                                                                         
vagrant$     
```

so, if your app relied on the env var HOWDY, you can change behavior



# files

putting them into the container from the host, (so far we haven't seen any of environments' files show up in the container)
retrieving them from the container, and also see what files have changed since 'run'



about "changes"
# `docker diff`

what about deletion, well first what can we delete? how can we see what's available to 'rm'?


right 

```

vagrant$ docker run ubuntu:14.04 ls                                                                                                                              
bin                                                                                                                                                                                                
boot                                                                                                                                                                                               
dev                                                                                                                                                                                                
etc                                                                                                                                                                                                
home                                                                                                                                                                                               
lib                                                                                                                                                                                                
lib64                                                                                                                                                                                              
media                                                                                                                                                                                              
mnt                                                                                                                                                                                                
opt                                                                                                                                                                                                
proc                                                                                                                                                                                               
root                                                                                                                                                                                               
run                                                                                                                                                                                                
sbin                                                                                                                                                                                               
srv                                                                                                                                                                                                
sys                                                                                                                                                                                                
tmp                                                                                                                                                                                                
usr                                                                                                                                                                                                
var                                                                                                                                                                                                
   
vagrant$ docker run ubuntu:14.04 rm -rf /home                                                                                                                                                      
vagrant$ docker ps -l                                                                                                                                                                              
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES                                                               
55cdc71a84ad        ubuntu:14.04        "rm -rf /home"      2 seconds ago       Exited (0) 2 seconds ago                       determined_carson                                                   
vagrant$ docker diff 55c                                                                                                                                                                           
D /home                                                                                                                                                                                            
vagrant$    
```

that was delete, now what about add?

so, to demonstrate, let me create a file, what is cheesy way to do it from command line?  right, echo and redirect

```
vagrant$ echo wow > myfile.txt                                                                                                                                                                     
vagrant$ cat myfile.txt                                                                                                                                                                            
wow                                                                                                                                                                                                
vagrant$ docker run ubuntu:14.04 /bin/bash -c "echo wombat > animal.txt"                                                                                                                           
vagrant$ docker ps -l                                                                                                                                                                              
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS                     PORTS               NAMES                                                            
88e89bbc7f17        ubuntu:14.04        "/bin/bash -c 'echo    5 seconds ago       Exited (0) 4 seconds ago                       elegant_ptolemy                                                  
vagrant$ docker diff 88e                                                                                                                                                                           
A /animal.txt                                                                                                                                                                                      
vagrant$                                                                                                                                                                                           
```

ok, so docker knows a file was added

# `docker cp`

so how do we grab that file?


```
vagrant$ docker cp 88e:animal.txt .                                                                                                                                                                
vagrant$ ls                                                                                                                                                                                        
Dockerfile  README.md  Vagrantfile  aasdlfksadf.txt  animal.txt  exercises  myfile.txt  presenter-notes  somefileomine  thequestions.txt                                                           
vagrant$ cat animal.txt                                                                                                                                                                            
wombat                                                                                                                                                                                             
vagrant$                                                                                                                                                                        ```                   

and there's "C" of course, for changed, let's skip demoing that


```
root@44ecb7964ea5:/# apt-get install tree                                                                                                                                                          
Reading package lists... Done                                                                                                                                                                      
Building dependency tree                                                                                                                                                                           
Reading state information... Done                                                                                                                                                                  
The following NEW packages will be installed:                                                                                                                                                      
  tree                                                                                                                                                                                             
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.                                                                                                                                     
Need to get 37.8 kB of archives.                                                                                                                                                                   
After this operation, 109 kB of additional disk space will be used.                                                                                                                                
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/universe tree amd64 1.6.0-1 [37.8 kB]                                                                                                               
Fetched 37.8 kB in 0s (104 kB/s)                                                                                                                                                                   
Selecting previously unselected package tree.                                                                                                                                                      
(Reading database ... 11518 files and directories currently installed.)                                                                                                                            
Preparing to unpack .../tree_1.6.0-1_amd64.deb ...                                                                                                                                                 
Unpacking tree (1.6.0-1) ...                                                                                                                                                                       
Setting up tree (1.6.0-1) ...                                                                                                                                                                      
root@44ecb7964ea5:/#               
```

ok, so we saw how docker can diff containers, and grab files from containers

# volumes

we haven't put a file into a container yet, which is kinda important, cause how is a real app gonna run otherwise? think about it, our source code or compiled code needs to be running _inside_ the container

cause we can't do something like this:

```
vagrant$ echo haha > joke.txt                                                                                                                                                                      
vagrant$ cat joke.txt                                                                                                                                                                              
haha                                                                                                                                                                                               
vagrant$ docker run ubuntu:14.04 cat joke.txt                                                                                                                                                      
cat: joke.txt: No such file or directory                                                                                                                                                           
vagrant$              
```

why not?


```
vagrant$ docker run --volume /vagrant:/vagrant ubuntu:14.04 ls /vagrant                                                                                                                            
Dockerfile                                                                                                                                                                                         
README.md                                                                                                                                                                                          
Vagrantfile                                                                                                                                                                                        
aasdlfksadf.txt                                                                                                                                                                                    
animal.txt                                                                                                                                                                                         
exercises                                                                                                                                                                                          
joke.txt                                                                                                                                                                                           
myfile.txt                                                                                                                                                                                         
presenter-notes                                                                                                                                                                                    
somefileomine                                                                                                                                                                                      
thequestions.txt     

vagrant$ docker run --volume /vagrant:/vagrant ubuntu:14.04 cat /vagrant/joke.txt                                                                                                                  
haha    
vagrant$ echo appendsomestuff >> joke.txt                                                                                                                                                          
vagrant$ cat joke.txt                                                                                                                                                                              
haha                                                                                                                                                                                               
appendsomestuff                                                                                                                                                                                    
vagrant$ docker run --volume /vagrant:/vagrant ubuntu:14.04 cat /vagrant/joke.txt                                                                                                                  
haha                                                                                                                                                                                               
appendsomestuff                                                                                                                                                                                    
vagrant$   
```


let's take a break before diving into `docker build`, with something will be obscenely easy, so easy you might be upset

let's see how easy it is to run some real packaged app, e.g. wordpress

https://registry.hub.docker.com/

search for wordpress

https://registry.hub.docker.com/_/wordpress/

"If you'd like to be able to access the instance from the host without the container's IP, standard port mappings can be used:""

`docker run --name some-wordpress --link some-mysql:mysql -p 8080:80 -d wordpress:3.9.2` 
keeping in mind our version - 3.9.2

ok, but we need a database first, looks like mysql

k, go back and search for mysql

https://registry.hub.docker.com/_/mysql/

`docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mysql:5.7.4`
keeping in mind our version - 5.7.4

ok start the database up

then go to - http://192.168.169.170:8080/

log in, remembering password, create a post, do some stuff

then stop containsers















# `docker build`

ok, let's do some more easy stuff

want to try out spring boot?

ok navigate to http://spring.io/guides/gs/spring-boot/


a quick scan shows


`git clone https://github.com/spring-guides/gs-spring-boot.git`

cd into complete/



"
What you’ll need

About 15 minutes
A favorite text editor or IDE
JDK 1.6 or later
Gradle 1.11+ or Maven 3.0+ <--- don't know much about gradle, but i know it can bootstrap itself
You can also import the code from this guide as well as view the web page directly into Spring Tool Suite (STS) and work your way through it from there.
"

and it's a webapp, how do we start it and what port will it serve up on as default?

scrolled down to find - 

./gradlew build && java -jar build/libs/gs-spring-boot-0.1.0.jar

$ curl localhost:8080
Greetings from Spring Boot!


ok, let's start a Dockerfile --

---------
FROM ubuntu:14.04

EXPOSE 8080

ADD / /app

WORKDIR /app

CMD ./gradlew build && java -jar build/libs/gs-spring-boot-0.1.0.jar
---------


see if our good ol' trusty ubuntu:14.04 has what we need

```

complete$ docker run --interactive --tty --publish 8080:8080 --volume `pwd`:/app ubuntu:14.04 /bin/bash                               
root@ff110a8754f8:/# javac - version                                                                                                                                                       
bash: javac: command not found                                                                                                                                                                     
root@ff110a8754f8:/# exit                                                                                                                                                                          
exit                                                                                                                                                                            ```


```
complete$ docker run --interactive --tty --publish 8080:8080 java:8u40 /bin/bash                                                                                                                   
root@1c2bec5902e3:/# javac -version                                                                                                                                                               
javac 1.8.0_40-internal                                                                                                                                                                            
root@d4d558fd1752:/# cd /app/                                                                                                                                                                      
root@d4d558fd1752:/app# ./gradlew build && java -jar build/libs/gs-spring-boot-0.1.0.jar                                                                                                           
Downloading http://services.gradle.org/distributions/gradle-1.11-bin.zip                                                                                                                           
...................................................................................................................................................................................................
                                                                                                                                                                                                   
  .   ____          _            __ _ _                                                                                                                                                            
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \                                                                                                                                                           
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \                                                                                                                                                          
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )                                                                                                                                                         
  '  |____| .__|_| |_|_| |_\__, | / / / /                                                                                                                                                          
 =========|_|==============|___/=/_/_/_/                                                                                                                                                           
 :: Spring Boot ::        (v1.1.6.RELEASE)                                                                                                                                                         
                                            
...

tomcatEmbeddedServletContainerFactory                                                                                                                                                              
traceEndpoint                                                                                                                                                                                      
traceRepository                                                                                                                                                                                    
viewControllerHandlerMapping                                                                                                                                                                       
viewResolver                                                                                                                                                                                       
webRequestLoggingFilter       


```



ok, so let's just change our dockerfile

==========
FROM java:8u40

EXPOSE 8080

ADD / /app

WORKDIR /app

CMD ./gradlew build && java -jar build/libs/gs-spring-boot-0.1.0.jar
==========

docker run --interactive --tty --publish 8080:8080 --volume `pwd`:/app java:8u40 /bin/bash
compared to the Dockerfile
ok, so that ADD isn't quite the same as teh --volume, add is just a one time copy, but a lot of the concepts should feel similar



```
complete$ docker build .                                                                                                                                                                           
Sending build context to Docker daemon 11.54 MB                                                                                                                                                    
Sending build context to Docker daemon                                                                                                                                                             
Step 0 : FROM java:8u40                                                                                                                                                                            
 ---> c64588070549                                                                                                                                                                                 
Step 1 : EXPOSE 8080                                                                                                                                                                               
 ---> Using cache                                                                                                                                                                                  
 ---> 6d3405883c8c                                                                                                                                                                                 
Step 2 : ADD / /app                                                                                                                                                                                
 ---> 3d2db45300cd                                                                                                                                                                                 
Removing intermediate container fea5d0465f32                                                                                                                                                       
Step 3 : WORKDIR /app                                                                                                                                                                              
 ---> Running in 7c19a455c900                                                                                                                                                                      
 ---> d82a5dadd677                                                                                                                                                                                 
Removing intermediate container 7c19a455c900                                                                                                                                                       
Step 4 : CMD ./gradlew build && java -jar build/libs/gs-spring-boot-0.1.0.jar                                                                                                                      
 ---> Running in 025a9e8af6eb                                                                                                                                                                      
 ---> 8fb79a51ff3e                                                                                                                                                                                 
Removing intermediate container 025a9e8af6eb                                                                                                                                                       
Successfully built 8fb79a51ff3e                                                                                                                                                                    
complete$                       
```




let's build something else?  any suggestions?  what about grokola?
i suggest that only i run it on one machine for the demo, since it has lots of downloads

while that's building...


back to that spring boot example

wget https://services.gradle.org/distributions/gradle-2.1-all.zip
unzip gradle-2.1-all.zip



cover daemon cmds



* then build another active project





* then back to automated builds



---------------
FROM java:8u40

EXPOSE 8080

RUN wget https://services.gradle.org/distributions/gradle-2.1-all.zip
RUN unzip gradle-2.1-all.zip

ADD / /app

WORKDIR /app

CMD /gradle-2.1/bin/gradle build && java -jar build/libs/gs-spring-boot-0.1.0.jar
---------------

FROM java:8u40

EXPOSE 8080

RUN wget https://services.gradle.org/distributions/gradle-2.1-all.zip
RUN unzip gradle-2.1-all.zip

ADD / /app

WORKDIR /app
RUN /gradle-2.1/bin/gradle build

CMD java -jar build/libs/gs-spring-boot-0.1.0.jar

---------------


automated build
