# RedisTest
this repository has a proof of concept about net core console application connect to a redis server, where this redis server is pull from docker hub

Get a docker image of redis.

`docker pull redis`

Run redis docker images.

`docker run -p 6379:6379 --name redis-test -d redis` 

Create a new net core console app.

`dotnet new console -o Redistest`

Add Microsoft.Extensions.Configuration package to solution.

`dotnet add package Microsoft.Extensions.Configuration.UserSecrets`

Add Redis package to solution.

`dotnet add package StackExchange.Redis`

Build the solution.

`dotnet build`

Run the solution.

`dotnet run`

The console will show something like this.

```
Cache command  : PING
Cache response : PONG

Cache command  : GET Message or StringGet()
Cache response : 

Cache command  : SET Message "Hello! The cache is working from a .NET Core console app!" or StringSet()
Cache response : True

Cache command  : GET Message or StringGet()
Cache response : Hello! The cache is working from a .NET Core console app!

Cache command  : CLIENT LIST
Cache response :
id=9 addr=172.17.0.1:33558 laddr=172.17.0.2:6379 fd=8 name=dev03 age=0 idle=0 flags=N db=0 sub=0 psub=0 multi=-1 qbuf=26 qbuf-free=40928 argv-mem=10 obl=0 oll=0 omem=0 tot-mem=61466 events=r cmd=client user=default redir=-1
id=10 addr=172.17.0.1:33560 laddr=172.17.0.2:6379 fd=9 name=dev03 age=0 idle=0 flags=P db=0 sub=1 psub=0 multi=-1 qbuf=0 qbuf-free=0 argv-mem=0 obl=0 oll=0 omem=0 tot-mem=20504 events=r cmd=subscribe user=default redir=-1
```

**Base on [this](https://docs.microsoft.com/en-us/azure/azure-cache-for-redis/cache-dotnet-core-quickstart) tutorial.**