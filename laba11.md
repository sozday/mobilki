1.
```
docker swarm init
docker swarm join --token 
docker node ls
```

2.
```
docker node rm worker-1
docker swarm join --token
```
3. Создал простое приложение с использоанием C#
```
using System;
using System.Net;
using System.Net.Sockets;

class Program
{
    static void Main(string[] args)
    {
        string ipAddress = GetLocalIPAddress();
        Console.WriteLine("IP адрес текущего узла: " + ipAddress);
    }

    static string GetLocalIPAddress()
    {
        using (var socket = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, 0))
        {
            socket.Connect("8.8.8.8", 65530);
            var endPoint = socket.LocalEndPoint as IPEndPoint;
            return endPoint.Address.ToString();
        }
    }
}
```

Создал DockerFile

```
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build

WORKDIR /app

COPY *.csproj .
COPY Program.cs .

RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/runtime:5.0 AS runtime

WORKDIR /app

COPY --from=build /app/out .

EXPOSE 80

ENTRYPOINT ["dotnet", "fufufufu.dll"]

```

Запустил образ

```
docker build -t your-image-name

docker run -p 80:80 your-image-name
```

4.
```
docker service create --replicas 3 --name my-service -p 80:80 my-image
docker service ls
docker service scale my-service=5
```

5. Добавил в докерфайл
```
LABEL maintainer="SetKirito poor in programming <kaka.caca.kaka98@gmail.com>"

LABEL version="1.0"
```

Пересобрал и обновил
```
docker build -t my-image

docker service update --image my-image my-service
```
