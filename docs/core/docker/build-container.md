---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200031"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Samouczek: Konteneryzowanie aplikacji .NET Core

W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker. Kontenery mają wiele funkcji i korzyści, takie jak niezmienne infrastruktury, zapewniające przenośną architekturę i umożliwiające skalowalność. Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.

W tym samouczku zostały wykonane następujące czynności:

> [!div class="checklist"]
>
> - Tworzenie i publikowanie prostej aplikacji .NET Core
> - Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core
> - Kompilowanie obrazu platformy Docker
> - Tworzenie i uruchamianie kontenera platformy Docker

Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core. *Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*. Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.

> [!NOTE]
> Ten samouczek **nie dotyczy** aplikacji ASP.NET Core. Jeśli używasz ASP.NET Core, zapoznaj się z samouczkiem [uczenie się, jak konteneryzowanie aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj następujące wymagania wstępne:

- [Zestaw SDK platformy .NET Core 3,1](https://dotnet.microsoft.com/download)\
Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info` , aby określić, którego zestawu SDK używasz.
- [Platforma Docker Community Edition](https://www.docker.com/products/docker-desktop)
- Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core. W tym samouczku Nazwa programu *Docker Work* jest używana jako folder roboczy.

## <a name="create-net-core-app"></a>Tworzenie aplikacji .NET Core

Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker. Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go. W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

Drzewo folderów będzie wyglądać następująco:

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

`dotnet new` Polecenie tworzy nowy folder o nazwie *App* i generuje aplikację konsolową "Hello World". Zmień katalogi i przejdź do folderu *aplikacji* z sesji terminala. Użyj `dotnet run` polecenia, aby uruchomić aplikację. Aplikacja zostanie uruchomiona i wydrukowana `Hello World!` poniżej polecenia:

```dotnetcli
dotnet run
Hello World!
```

Szablon domyślny tworzy aplikację, która drukuje do terminalu, a następnie natychmiast kończy pracę. Na potrzeby tego samouczka będziesz używać aplikacji, która nieskończonie pętli. Otwórz plik *program.cs* w edytorze tekstu.

> [!TIP]
> Jeśli używasz Visual Studio Code, w poprzedniej sesji terminala wpisz następujące polecenie:
>
> ```
> code .
> ```
>
> Spowoduje to otwarcie folderu *aplikacji* zawierającego projekt w Visual Studio Code.

*Program.cs* powinien wyglądać podobnie do następującego kodu w języku C#:

```csharp
using System;

namespace NetCore.Docker
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

Zastąp plik następującym kodem, który zlicza liczby w każdej sekundzie:

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`programu. Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność. Aby zatrzymać, użyj polecenia Cancel <kbd>Ctrl + C</kbd> . Oto przykładowe dane wyjściowe:

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Jeśli przekażesz liczbę w wierszu polecenia do aplikacji, będzie ona liczyć tylko do tej wartości, a następnie zostanie zakończona. Wypróbuj go, `dotnet run -- 5` aby liczyć do pięciu.

> [!IMPORTANT]
> Wszystkie parametry po `--` nie są przenoszone do `dotnet run` polecenia i zamiast tego są przesyłane do aplikacji.

## <a name="publish-net-core-app"></a>Publikowanie aplikacji platformy .NET Core

Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy najpierw ją opublikować. Najlepszym rozwiązaniem jest uruchomienie przez kontener opublikowanej wersji aplikacji. Aby opublikować aplikację, uruchom następujące polecenie:

```dotnetcli
dotnet publish -c Release
```

To polecenie kompiluje aplikację do folderu *Publikowanie* . Ścieżka do folderu *publikowania* z folderu roboczego powinna być`.\App\bin\Release\netcoreapp3.1\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

W folderze *App (aplikacja* ) Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy został utworzony plik z systemem. *Docker. dll* .

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

Użyj `ls` polecenia, aby uzyskać listę katalogów i sprawdzić, czy plik. *Docker. dll* został utworzony.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>Tworzenie pliku dockerfile

Plik *pliku dockerfile* jest używany przez `docker build` polecenie do tworzenia obrazu kontenera. Ten plik jest plikiem tekstowym o nazwie *pliku dockerfile* , który nie ma rozszerzenia.

Utwórz plik o nazwie *pliku dockerfile* w katalogu zawierającym element *. csproj* i otwórz go w edytorze tekstu. W tym samouczku zostanie użyty obraz środowiska uruchomieniowego ASP.NET Core (zawierający obraz środowiska uruchomieniowego programu .NET Core), który odpowiada aplikacji konsolowej programu .NET Core.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> Obraz środowiska uruchomieniowego ASP.NET Core jest używany w sposób celowy, `mcr.microsoft.com/dotnet/core/runtime:3.1` chociaż można było użyć obrazu.

`FROM` Słowo kluczowe wymaga w pełni kwalifikowanej nazwy obrazu kontenera Docker. Microsoft Container Registry (MCR, mcr.microsoft.com) to zespolone centrum Docker, które hostuje dostępne publicznie kontenery. `dotnet/core` Segment jest repozytorium kontenera, gdzie jako `aspnet` segment jest nazwą obrazu kontenera. Obraz jest otagowany przy `3.1`użyciu, który jest używany do przechowywania wersji. `mcr.microsoft.com/dotnet/core/aspnet:3.1` W tym przypadku środowisko uruchomieniowe programu .net Core 3,1. Upewnij się, że korzystasz z wersji środowiska uruchomieniowego, która pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK. Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 3,1 SDK i obrazu podstawowego, do którego odwołuje się w *pliku dockerfile* , jest oznaczona jako **3,1**.

Zapisz plik *pliku dockerfile* . Struktura katalogów folderu roboczego powinna wyglądać następująco. Niektóre pliki i foldery bardziej szczegółowe zostały pominięte w celu zaoszczędzenia miejsca w artykule:

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

W terminalu uruchom następujące polecenie:

```Docker
docker build -t counter-image -f Dockerfile .
```

Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*. W poleceniu polecenie instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile.* `.` `docker build` To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **Counter-Image** , które wskazuje na ten obraz. Po zakończeniu tego polecenia Uruchom `docker images` polecenie, aby wyświetlić listę zainstalowanych obrazów:

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** . Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie. Dodajmy trzy polecenia do *pliku dockerfile*. Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym punkty wejścia repozytorium **obrazu licznika** do.

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

`COPY` Polecenie instruuje platformę Docker, aby skopiował określony folder na komputerze do folderu w kontenerze. W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.

`WORKDIR` Polecenie zmienia **bieżący katalog** wewnątrz kontenera na *aplikację*.

Następne polecenie,, `ENTRYPOINT`instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny. Po uruchomieniu kontenera `ENTRYPOINT` polecenie zostanie uruchomione. Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.

W terminalu uruchom `docker build -t counter-image -f Dockerfile .` polecenie i po zakończeniu wykonywania `docker images`polecenia.

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**. Końcowy **Identyfikator obrazu** (będzie inny) to **cd11c3df9b19** , a następnie utworzysz kontener oparty na tym obrazie.

## <a name="create-a-container"></a>Tworzenie kontenera

Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener. Kontener można utworzyć na dwa sposoby. Najpierw utwórz nowy kontener, który został zatrzymany.

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

Powyższe `docker create` polecenie spowoduje utworzenie kontenera na podstawie obrazu **licznika** . Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera. Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>Zarządzanie kontenerem

Kontener został utworzony z określoną nazwą `core-counter`. Ta nazwa jest używana do zarządzania kontenerem. Poniższy przykład używa `docker start` polecenia do uruchomienia kontenera, a następnie używa `docker ps` polecenia do wyświetlania tylko kontenerów, które są uruchomione:

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

Podobnie `docker stop` polecenie spowoduje zatrzymanie kontenera. Poniższy przykład używa `docker stop` polecenia do zatrzymania kontenera, a następnie używa `docker ps` polecenia, aby pokazać, że żaden kontener nie jest uruchomiony:

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>Nawiązywanie połączenia z kontenerem

Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe. Użyj poleceń `docker start` i `docker attach` , aby uruchomić kontener i wgląd do strumienia wyjściowego. W tym przykładzie naciśnięcie klawiszy <kbd>Ctrl + C</kbd> jest używane do odłączenia od uruchomionego kontenera. Naciśnięcie klawisza spowoduje zakończenie procesu w kontenerze, o ile nie określono inaczej, co spowodowałoby zatrzymanie kontenera. `--sig-proxy=false` Parametr zapewnia, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie spowoduje zatrzymania procesu w kontenerze.

Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Usuwanie kontenera

Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte. Usuń kontener, który został wcześniej utworzony. Jeśli kontener jest uruchomiony, Zatrzymaj go.

```Docker
docker stop core-counter
```

Poniższy przykład wyświetla listę wszystkich kontenerów. Następnie używa `docker rm` polecenia do usuwania kontenera, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>Pojedynczy przebieg

Docker udostępnia `docker run` polecenie do tworzenia i uruchamiania kontenera jako pojedyncze polecenie. To polecenie eliminuje konieczność uruchomienia `docker create` , a następnie `docker start`. Możesz również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera. Na przykład użyj `docker run -it --rm` do dwóch rzeczy, najpierw automatycznie Użyj bieżącego terminalu do łączenia się z kontenerem, a następnie usuń go:

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Kontener przekazuje również parametry do wykonywania aplikacji .NET Core. Aby nakazać aplikacji .NET Core zliczanie tylko do 3 przebiegów 3.

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

W `docker run -it`programie <kbd>naciśnięcie polecenia CTRL + C</kbd> spowoduje zatrzymanie procesu, który jest uruchomiony w kontenerze, co z kolei powoduje zatrzymanie kontenera. Ponieważ `--rm` parametr został dostarczony, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany. Sprawdź, czy nie istnieje:

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>Zmień punkt wejścia

`docker run` Polecenie umożliwia również modyfikowanie `ENTRYPOINT` polecenia z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera. Na przykład użyj poniższego polecenia, aby uruchomić `bash` polecenie `cmd.exe`lub. W razie potrzeby zmodyfikuj polecenie.

#### <a name="windows"></a>[Windows](#tab/windows)

W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`. <kbd>Ctrl + C</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać kontener.

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

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

#### <a name="linux"></a>[Linux](#tab/linux)

W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`. `exit` Polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>Najważniejsze polecenia

Platforma Docker ma wiele różnych poleceń, które tworzą i obsługują kontenery i obrazy oraz zarządzają nimi. Te polecenia platformy Docker mają kluczowe znaczenie dla zarządzania kontenerami:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [uruchomienie platformy Docker](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [zatrzymanie platformy Docker](https://docs.docker.com/engine/reference/commandline/stop/)
- [Platforma Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
- [Docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
- [obraz platformy Docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku utworzono kontenery i obrazy. Jeśli chcesz, usuń te zasoby. Użyj następujących poleceń, aby

01. Wyświetl listę wszystkich kontenerów

    ```Docker
    docker ps -a
    ```

02. Zatrzymaj kontenery uruchomione przez ich nazwę.

    ```Docker
    docker stop counter-image
    ```

03. Usuwanie kontenera

    ```Docker
    docker rm counter-image
    ```

Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze. Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* . Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Użyj polecenia `docker images` , aby wyświetlić listę zainstalowanych obrazów.

> [!TIP]
> Pliki obrazów mogą być duże. Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji. Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak konteneryzowanie aplikację ASP.NET Coreową.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Wypróbuj ASP.NET Core samouczka mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Przejrzyj usługi platformy Azure, które obsługują kontenery.](https://azure.microsoft.com/overview/containers/)
- [Przeczytaj o poleceniach pliku dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Poznaj narzędzia kontenerów dla programu Visual Studio](/visualstudio/containers/overview)
