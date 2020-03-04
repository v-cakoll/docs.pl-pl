---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157833"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Samouczek: Konteneryzowanie aplikacji .NET Core

W tym samouczku przedstawiono sposób tworzenia obrazu platformy Docker, który zawiera aplikację platformy .NET Core. Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.

Dowiesz się:

> [!div class="checklist"]
>
> - Tworzenie i publikowanie prostej aplikacji .NET Core
> - Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core
> - Kompilowanie obrazu platformy Docker
> - Tworzenie i uruchamianie kontenera platformy Docker

Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core. *Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*. Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.

> [!TIP]
> Jeśli pracujesz z istniejącą aplikacją ASP.NET Core, zapoznaj się z samouczkiem [uczenie się, jak konteneryzowanie aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj następujące wymagania wstępne:

- [Zestaw SDK platformy .NET Core 3,1](https://dotnet.microsoft.com/download)\
Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info`, aby określić, którego zestawu SDK używasz.

- [Platforma Docker Community Edition](https://www.docker.com/products/docker-desktop)

- Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core. W tym samouczku Nazwa programu *Docker Work* jest używana jako folder roboczy.

## <a name="create-net-core-app"></a>Tworzenie aplikacji .NET Core

Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker. Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go. W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:

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

`dotnet new` polecenie tworzy nowy folder o nazwie *App* i generuje aplikację "Hello World". Wprowadź folder *App* i uruchom polecenie `dotnet run`. Zobaczysz następujące dane wyjściowe:

```console
> dotnet run
Hello World!
```

Szablon domyślny tworzy aplikację, która drukuje do terminalu, a następnie kończy pracę. Na potrzeby tego samouczka będziesz używać aplikacji, która nieskończonie pętli. Otwórz plik *program.cs* w edytorze tekstu. Powinien wyglądać podobnie do następującego kodu:

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

Zastąp plik następującym kodem, który zlicza liczby w każdej sekundzie:

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

Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`. Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność. Użyj polecenia Cancel <kbd>CTRL</kbd>+<kbd>C</kbd> , aby go zatrzymać. Zobaczysz następujące dane wyjściowe:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Jeśli przekażesz liczbę w wierszu polecenia do aplikacji, będzie ona liczyć tylko do tej wartości, a następnie zostanie zakończona. Wypróbuj `dotnet run -- 5`, aby liczyć do pięciu.

> [!NOTE]
> Wszelkie parametry po `--` nie są przenoszone do polecenia `dotnet run` i zamiast tego są przesyłane do aplikacji.

## <a name="publish-net-core-app"></a>Publikowanie aplikacji platformy .NET Core

Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy opublikować ją. Upewnij się, że kontener uruchamia opublikowaną wersję aplikacji po jej uruchomieniu.

W folderze roboczym wprowadź folder *App* z przykładowym kodem źródłowym i uruchom następujące polecenie:

```dotnetcli
dotnet publish -c Release
```

To polecenie kompiluje aplikację do folderu *Publikowanie* . Ścieżka do folderu *publikowania* z folderu roboczego powinna być `.\app\bin\Release\netcoreapp3.1\publish\`

Aby sprawdzić, czy plik *MojaApl. dll* został utworzony, w folderze *App* należy uzyskać listę katalogów folderu publikacji.

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

Jeśli używasz systemu Linux lub macOS, użyj polecenia `ls`, aby uzyskać listę katalogów i sprawdzić, czy plik *MojaApl. dll* został utworzony.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Tworzenie pliku dockerfile

Plik *pliku dockerfile* jest używany przez polecenie `docker build`, aby utworzyć obraz kontenera. Ten plik jest plikiem tekstowym o nazwie *pliku dockerfile* , który nie ma rozszerzenia.

W terminalu przejdź do katalogu roboczego, który został utworzony na początku. Utwórz plik o nazwie *pliku dockerfile* w folderze roboczym i otwórz go w edytorze tekstu. W zależności od typu aplikacji, która ma zostać konteneryzowanie, należy wybrać środowisko uruchomieniowe ASP.NET Core lub środowisko uruchomieniowe platformy .NET Core. W razie wątpliwości Wybierz środowisko uruchomieniowe ASP.NET Core, które obejmuje środowisko uruchomieniowe platformy .NET Core. W tym samouczku zostanie użyty obraz środowiska uruchomieniowego ASP.NET Core, ale aplikacja utworzona w poprzednich sekcjach jest aplikacją platformy .NET Core.

- Środowisko uruchomieniowe ASP.NET Core

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- Środowisko uruchomieniowe programu .NET core

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

Polecenie `FROM` instruuje platformę Docker, aby ściągnąć obraz oznaczony **3,1** z określonego repozytorium. Upewnij się, że korzystasz z wersji środowiska uruchomieniowego, która pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK. Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 3,1 SDK i obrazu podstawowego, do którego odwołuje się w *pliku dockerfile* , jest oznaczona jako **3,1**.

Zapisz plik *pliku dockerfile* . Struktura katalogów folderu roboczego powinna wyglądać następująco. Niektóre pliki i foldery z bardziej szczegółowymi poziomami zostały wycięte w celu zaoszczędzenia miejsca w artykule:

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

W terminalu uruchom następujące polecenie:

```console
docker build -t myimage -f Dockerfile .
```

Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*. `.` w poleceniu `docker build` instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile*. To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **obraz** , który wskazuje na ten obraz. Po zakończeniu tego polecenia Uruchom `docker images`, aby wyświetlić listę zainstalowanych obrazów:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** . Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie. Dodajmy dwa polecenia do *pliku dockerfile*. Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym obraz wskazujący na wpis repozytorium **obrazu** .

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Polecenie `COPY` instruuje platformę Docker o skopiowanie określonego folderu na komputerze do folderu w kontenerze. W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.

Następne polecenie `ENTRYPOINT`, instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny. Po rozpoczęciu kontenera zostanie uruchomione polecenie `ENTRYPOINT`. Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.

W terminalu uruchom `docker build -t myimage -f Dockerfile .` i po zakończeniu tego polecenia Uruchom polecenie `docker images`.

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

Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**. Końcowy **Identyfikator obrazu** (będzie inny) to **ddcc6646461b** , a następnie utworzysz kontener oparty na tym obrazie.

## <a name="create-a-container"></a>Tworzenie kontenera

Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener. Kontener można utworzyć na dwa sposoby. Najpierw utwórz nowy kontener, który został zatrzymany.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

Polecenie `docker create` from powyżej utworzy kontener oparty na obrazie **obrazu** . Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera. Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Zarządzanie kontenerem

Do każdego kontenera jest przypisywana nazwa Losowa, której można użyć do odwoływania się do tego wystąpienia kontenera. Na przykład kontener, który został utworzony automatycznie wybiera nazwę **gallant_lehmann** (będzie się różnić), a ta nazwa może być używana do uruchamiania kontenera. Automatyczna nazwa zostanie zastąpiona określonym przez użycie parametru `docker create --name`.

Poniższy przykład używa polecenia `docker start`, aby uruchomić kontener, a następnie używa polecenia `docker ps` do wyświetlania tylko kontenerów z systemem:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Analogicznie, polecenie `docker stop` spowoduje zatrzymanie kontenera. Poniższy przykład używa polecenia `docker stop`, aby zatrzymać kontener, a następnie używa polecenia `docker ps`, aby pokazać, że żaden kontener nie jest uruchomiony:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Nawiązywanie połączenia z kontenerem

Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe. Użyj poleceń `docker start` i `docker attach`, aby uruchomić kontener i uzyskać wgląd w strumieniu danych wyjściowych. W tym przykładzie naciśnięcie klawiszy <kbd>Ctrl + C</kbd> jest używane do odłączenia od uruchomionego kontenera. To naciśnięcie klawisza może ostatecznie zakończyć proces w kontenerze, co spowoduje zatrzymanie kontenera. `--sig-proxy=false` parametr gwarantuje, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie zatrzyma procesu w kontenerze.

Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.

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

Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte. Usuń kontener, który został wcześniej utworzony. Jeśli kontener jest uruchomiony, Zatrzymaj go.

```console
> docker stop gallant_lehmann
```

Poniższy przykład wyświetla listę wszystkich kontenerów. Następnie używa polecenia `docker rm`, aby usunąć kontener, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Pojedynczy przebieg

Platforma Docker udostępnia polecenie `docker run`, aby utworzyć i uruchomić kontener jako pojedyncze polecenie. To polecenie eliminuje konieczność uruchamiania `docker create` a następnie `docker start`. Możesz również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera. Na przykład użyj `docker run -it --rm`, aby wykonać dwa czynności, w pierwszej kolejności automatycznie Użyj bieżącego terminalu do nawiązania połączenia z kontenerem, a następnie usuń go:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Za pomocą `docker run -it`polecenie <kbd>Ctrl + C</kbd> przestanie działać w kontenerze, który z kolei zatrzymuje kontener. Ponieważ podano parametr `--rm`, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany. Sprawdź, czy nie istnieje:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Zmień punkt wejścia

`docker run` polecenie umożliwia również modyfikowanie polecenia `ENTRYPOINT` z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera. Na przykład użyj następującego polecenia, aby uruchomić `bash` lub `cmd.exe`. W razie potrzeby zmodyfikuj polecenie.

#### <a name="windows"></a>System Windows

W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`. <kbd>Naciśnij klawisz CTRL</kbd>+<kbd>C</kbd> , aby zakończyć proces i zatrzymać kontener.

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

W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`. `quit` polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Najważniejsze polecenia

Platforma Docker ma wiele różnych poleceń, które obejmują, co chcesz zrobić z kontenerem i obrazami. Te polecenia platformy Docker mają kluczowe znaczenie dla zarządzania kontenerami:

- [Kompilacja platformy Docker](https://docs.docker.com/engine/reference/commandline/build/)
- [uruchomienie platformy Docker](https://docs.docker.com/engine/reference/commandline/run/)
- [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/)
- [zatrzymanie platformy Docker](https://docs.docker.com/engine/reference/commandline/stop/)
- [Platforma Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
- [Docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
- [obraz platformy Docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku utworzono kontenery i obrazy. Jeśli chcesz, usuń te zasoby. Użyj następujących poleceń, aby

01. Wyświetl listę wszystkich kontenerów

    ```console
    > docker ps -a
    ```

02. Zatrzymaj uruchomione kontenery. `CONTAINER_NAME` reprezentuje nazwę, która jest automatycznie przypisywana do kontenera.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Usuwanie kontenera

    ```console
    > docker rm CONTAINER_NAME
    ```

Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze. Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* . Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.

> [!NOTE]
> Pliki obrazów mogą być duże. Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji. Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak konteneryzowanie aplikację ASP.NET Coreową.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Wypróbuj ASP.NET Core samouczka mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Przejrzyj usługi platformy Azure, które obsługują kontenery.](https://azure.microsoft.com/overview/containers/)
- [Przeczytaj o poleceniach pliku dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Poznaj narzędzia kontenerów dla programu Visual Studio](/visualstudio/containers/overview)
