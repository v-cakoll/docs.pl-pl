---
title: Konteneryzowanie aplikacji za pomocą samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzować aplikację .NET Core za pomocą platformy Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546578"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Samouczek: Konteneryzuj aplikację .NET Core

W tym samouczku dowiesz się, jak utworzyć obraz platformy Docker zawierający aplikację .NET Core. Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska programistycznego, chmury prywatnej lub chmury publicznej.

Nauczysz się:

> [!div class="checklist"]
>
> - Tworzenie i publikowanie prostej aplikacji .NET Core
> - Tworzenie i konfigurowanie pliku dockerfile dla programu .NET Core
> - Kompilowanie obrazu platformy Docker
> - Tworzenie i uruchamianie kontenera platformy Docker

Zrozumiesz kompilację kontenera platformy Docker i wdrożyć zadania dla aplikacji .NET Core. *Platforma Docker* używa *aparatu platformy Docker* do szybkiego tworzenia i pakowania aplikacji w *obrazach platformy Docker.* Te obrazy są zapisywane w formacie *Dockerfile* do wdrożenia i uruchomienia w kontenerze warstwowym.

> [!WARNING]
> **Ten samouczek nie jest przeznaczony dla aplikacji ASP.NET Core.** Jeśli używasz ASP.NET Core, przeczytaj [dowiedz się, jak konteneryzować samouczek aplikacji ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj następujące wymagania wstępne:

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)\
Jeśli masz zainstalowany program .NET `dotnet --info` Core, użyj polecenia, aby określić, którego sdk używasz.

- [Wersja społeczności platformy Docker](https://www.docker.com/products/docker-desktop)

- Tymczasowy folder roboczy dla przykładowej aplikacji *Dockerfile* i .NET Core. W tym samouczku nazwa *docker-working* jest używana jako folder roboczy.

## <a name="create-net-core-app"></a>Tworzenie aplikacji .NET Core

Potrzebujesz aplikacji .NET Core, która będzie uruchamiana przez kontener platformy Docker. Otwórz terminal, utwórz folder roboczy, jeśli jeszcze tego nie zrobiłeś, i wprowadź go. W folderze roboczym uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *aplikacji:*

```dotnetcli
dotnet new console -o app -n myapp
```

Drzewo folderów będzie wyglądać następująco:

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

Polecenie `dotnet new` tworzy nowy folder o nazwie *aplikacji* i generuje "Hello World" aplikacji. Wprowadź folder *aplikacji* i `dotnet run`uruchom polecenie . Zobaczysz następujące dane wyjściowe:

```console
> dotnet run
Hello World!
```

Szablon domyślny tworzy aplikację, która drukuje do terminala, a następnie kończy pracę. W tym samouczku użyjesz aplikacji, która zapętla się przez czas nieokreślony. Otwórz plik *Program.cs* w edytorze tekstu. Obecnie powinien wyglądać jak następujący kod:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Zastąp plik następującym kodem, który zlicza liczby co sekundę:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Zapisz plik i ponownie przetestuj program za pomocą pliku `dotnet run`. Pamiętaj, że ta aplikacja działa przez czas nieokreślony. Użyj polecenia anuluj <kbd>CTRL</kbd>+<kbd>C,</kbd> aby go zatrzymać. Zobaczysz następujące dane wyjściowe:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Jeśli przekażesz numer w wierszu polecenia do aplikacji, będzie on liczony tylko do tej kwoty, a następnie zakończyć. Spróbuj z `dotnet run -- 5` liczyć do pięciu.

> [!NOTE]
> Wszelkie parametry `--` po nie `dotnet run` są przekazywane do polecenia i zamiast tego są przekazywane do aplikacji.

## <a name="publish-net-core-app"></a>Publikowanie aplikacji .NET Core

Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy ją opublikować. Chcesz upewnić się, że kontener uruchamia opublikowaną wersję aplikacji po jej uruchomieniu.

W folderze roboczym wprowadź folder *aplikacji* z przykładowym kodem źródłowym i uruchom następujące polecenie:

```dotnetcli
dotnet publish -c Release
```

To polecenie kompiluje aplikację do folderu *publikowania.* Ścieżka do folderu *publikowania* z folderu roboczego powinna być`.\app\bin\Release\netcoreapp3.1\publish\`

Z folderu *aplikacji* pobierz listę katalogów folderu publikowania, aby sprawdzić, czy plik *myapp.dll* został utworzony.

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

Jeśli używasz systemu Linux lub macOS, użyj `ls` tego polecenia, aby uzyskać listę katalogów i sprawdzić, czy plik *myapp.dll* został utworzony.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Tworzenie pliku dockerfile

Plik *Dockerfile* jest używany `docker build` przez polecenie do tworzenia obrazu kontenera. Ten plik jest plikiem tekstowym o nazwie *Dockerfile,* który nie ma rozszerzenia.

W terminalu przejdź w górę katalogu do folderu roboczego utworzonego na początku. Utwórz plik o nazwie *Dockerfile* w folderze roboczym i otwórz go w edytorze tekstu. W zależności od typu aplikacji, który zamierzasz konteneryzować, wybierzesz ASP.NET core runtime lub .NET Core runtime. W razie wątpliwości wybierz ASP.NET core runtime, który obejmuje środowisko uruchomieniowe .NET Core. W tym samouczku użyje się ASP.NET core obrazu środowiska uruchomieniowego, ale aplikacja utworzona w poprzednich sekcjach jest aplikacją .NET Core.

- ASP.NET Podstawowy czas pracy

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- Core .NET środowisko uruchomieniowe

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

Polecenie `FROM` nakazuje docker, aby ściągnąć w dół obraz oznaczony **3.1** z określonego repozytorium. Upewnij się, że ściągasz wersję środowiska wykonawczego, która odpowiada środowiska uruchomieniowego docelowego przez sdk. Na przykład aplikacja utworzona w poprzedniej sekcji używała SDK .NET Core 3.1, a obraz podstawowy, o którym mowa w *pliku Dockerfile,* jest oznaczony tagiem **3.1**.

Zapisz plik *Dockerfile.* Struktura katalogów folderu roboczego powinna wyglądać następująco. Niektóre pliki i foldery na głębszym poziomie zostały wycięte, aby zaoszczędzić miejsce w artykule:

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

Z terminala uruchom następujące polecenie:

```console
docker build -t myimage -f Dockerfile .
```

Docker będzie przetwarzać każdy wiersz w *pliku Dockerfile*. W `.` poleceniu nakazuje programowi `docker build` Docker użycie bieżącego folderu w celu znalezienia pliku *Dockerfile*. To polecenie tworzy obraz i tworzy lokalne repozytorium o nazwie **myimage,** który wskazuje na ten obraz. Po zakończeniu tego polecenia `docker images` uruchom, aby wyświetlić listę zainstalowanych obrazów:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Należy zauważyć, że dwa obrazy mają tę samą wartość **identyfikatora OBRAZU.** Wartość jest taka sama między obu obrazów, ponieważ jedynym poleceniem w *Dockerfile* było oprzeć nowy obraz na istniejącym obrazie. Dodajmy dwa polecenia do pliku *dockerfile*. Każde polecenie tworzy nową warstwę obrazu z poleceniem końcowym reprezentującym obraz, do których wskazuje wejście repozytorium **myimage.**

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Polecenie `COPY` nakazuje programowi Docker skopiowanie określonego folderu na komputerze do folderu w kontenerze. W tym przykładzie folder *publikowania* jest kopiowany do folderu o nazwie *aplikacji* w kontenerze.

Następne polecenie `ENTRYPOINT`, mówi docker skonfigurować kontener do uruchomienia jako plik wykonywalny. Po uruchomieniu kontenera `ENTRYPOINT` jest uruchamiane. Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.

Z terminala `docker build -t myimage -f Dockerfile .` uruchom i po zakończeniu `docker images`tego polecenia uruchom polecenie .

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Każde polecenie w pliku *Dockerfile wygenerowało* warstwę i utworzyło **identyfikator OBRAZU**. Ostateczny **identyfikator OBRAZU** (twój będzie inny) to **ddcc6646461b,** a następnie utworzysz kontener na podstawie tego obrazu.

## <a name="create-a-container"></a>Tworzenie kontenera

Teraz, gdy masz obraz, który zawiera aplikację, można utworzyć kontener. Kontener można utworzyć na dwa sposoby. Najpierw utwórz nowy kontener, który jest zatrzymany.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

Polecenie `docker create` z góry utworzy kontener na podstawie obrazu **myimage.** Dane wyjściowe tego polecenia pokazuje **identyfikator kontenera** (twój będzie inny) utworzonego kontenera. Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Zarządzanie kontenerem

Każdemu kontenerowi jest przypisywana losowa nazwa, której można użyć do odwoływania się do tego wystąpienia kontenera. Na przykład kontener, który został utworzony automatycznie wybrał nazwę **gallant_lehmann** (twoja będzie inna) i tej nazwy może służyć do uruchamiania kontenera. Zastąpisz nazwę automatyczną określoną przy użyciu `docker create --name` parametru.

Poniższy przykład używa `docker start` polecenia do uruchomienia kontenera, `docker ps` a następnie używa polecenia, aby wyświetlić tylko kontenery, które są uruchomione:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Podobnie `docker stop` polecenie zatrzyma kontener. Poniższy przykład używa `docker stop` polecenia, aby zatrzymać kontener, `docker ps` a następnie używa polecenia, aby pokazać, że żadne kontenery nie są uruchomione:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Łączenie się z kontenerem

Po uruchomieniu kontenera można połączyć się z nim, aby wyświetlić dane wyjściowe. Użyj `docker start` i `docker attach` polecenia, aby uruchomić kontener i zajrzeć do strumienia wyjściowego. W tym przykładzie naciśnięcie klawisza <kbd>CTRL + C</kbd> jest używane do odłączyć od uruchomionego kontenera. To naciśnięcie klawisza może faktycznie zakończyć proces w kontenerze, który zatrzyma kontenera. Parametr `--sig-proxy=false` zapewnia, że <kbd>CTRL + C</kbd> nie zatrzyma proces w kontenerze.

Po odłączeniu od kontenera, ponownie dołączyć, aby sprawdzić, czy jest nadal uruchomiony i zliczanie.

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Usuwanie kontenera

Na potrzeby tego artykułu nie chcesz, aby kontenery po prostu nie robiły nic. Usuń poprzednio utworzony kontener. Jeśli kontener jest uruchomiony, zatrzymaj go.

```console
> docker stop gallant_lehmann
```

Poniższy przykład zawiera listę wszystkich kontenerów. Następnie używa `docker rm` polecenia, aby usunąć kontener, a następnie sprawdza po raz drugi dla wszystkich uruchomionych kontenerów.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Pojedynczy bieg

Docker udostępnia `docker run` polecenie tworzenia i uruchamiania kontenera jako pojedynczego polecenia. To polecenie eliminuje konieczność `docker create` uruchamiania, a następnie `docker start`. Można również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera. Na przykład `docker run -it --rm` użyj do wykonania dwóch czynności, najpierw automatycznie użyj bieżącego terminala do połączenia z kontenerem, a następnie po zakończeniu kontenera usuń go:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Za `docker run -it`pomocą polecenia <kbd>CTRL + C</kbd> zatrzyma proces uruchomiony w kontenerze, który z kolei zatrzymuje kontener. Ponieważ `--rm` parametr został dostarczony, kontener jest automatycznie usuwany po zatrzymaniu procesu. Sprawdź, czy nie istnieje:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Zmienianie PUNKTU WEJŚCIA

Polecenie `docker run` umożliwia również modyfikowanie `ENTRYPOINT` polecenia z pliku *Dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera. Na przykład użyj następującego `bash` polecenia, aby uruchomić lub `cmd.exe`. W razie potrzeby edytuj polecenie.

#### <a name="windows"></a>Windows

W tym `ENTRYPOINT` przykładzie `cmd.exe`zostanie zmieniona na . <kbd>Ctrl</kbd>+<kbd>C</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać pojemnik.

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>Linux

W tym `ENTRYPOINT` przykładzie `bash`zostanie zmieniona na . Polecenie `quit` jest uruchamiane, co kończy proces i zatrzymuje kontener.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Niezbędne polecenia

Docker ma wiele różnych poleceń, które obejmują, co chcesz zrobić z kontenera i obrazów. Te polecenia platformy Docker są niezbędne do zarządzania kontenerami:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [uruchamianie platformy docker](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [zatrzymanie platformy docker](https://docs.docker.com/engine/reference/commandline/stop/)
- [rm docker](https://docs.docker.com/engine/reference/commandline/rm/)
- [rmi platformy docker](https://docs.docker.com/engine/reference/commandline/rmi/)
- [obraz platformy docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Podczas tego samouczka utworzono kontenery i obrazy. Jeśli chcesz, usuń te zasoby. Użyj następujących poleceń, aby

01. Lista wszystkich kontenerów

    ```console
    > docker ps -a
    ```

02. Zatrzymaj uruchomione kontenery. Reprezentuje `CONTAINER_NAME` nazwę automatycznie przypisane do kontenera.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Usuwanie kontenera

    ```console
    > docker rm CONTAINER_NAME
    ```

Następnie usuń wszystkie obrazy, których nie chcesz już na komputerze. Usuń obraz utworzony przez plik *Dockerfile,* a następnie usuń obraz .NET Core, na podstawie na podstawie pliku *Dockerfile.* Można użyć **identyfikatora OBRAZU** lub **ciągu sformatowanego w formacie REPOZYTORIUM:TAG.**

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.

> [!NOTE]
> Pliki obrazów mogą być duże. Zazwyczaj należy usunąć tymczasowe kontenery utworzone podczas testowania i tworzenia aplikacji. Zazwyczaj zachować obrazy podstawowe z zainstalowanym czasem wykonywania, jeśli planujesz na tworzenie innych obrazów na podstawie tego środowiska wykonawczego.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak konteneryzować aplikację ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Wypróbuj ASP.NET Core Microservice Tutorial.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Przejrzyj usługi platformy Azure, które obsługują kontenery.](https://azure.microsoft.com/overview/containers/)
- [Przeczytaj o poleceniach dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Zapoznaj się z narzędziami kontenerów dla programu Visual Studio](/visualstudio/containers/overview)
