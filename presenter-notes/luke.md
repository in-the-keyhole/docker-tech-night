`export PS1="\W$ "`

zoom - 125%
theme - white
terminal: theme - man_page, font size - 20


`while true ; do nc -l 9999 < index.html ; done`

`while true ; do nc -l 9999 <<<luke ; done`


is docker installed?  what version are we using?
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
sure, _we_ can run it, but how can we distrubute it?

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




# `docker build`
# `docker cp`
# `docker diff`
# `docker inspect`

