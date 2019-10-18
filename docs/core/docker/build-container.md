---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b344731c7d356f3705d9909b6901234f91ec7d6d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521887"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Samouczek: Konteneryzowanie aplikacji .NET Core

W tym samouczku przedstawiono sposób tworzenia obrazu platformy Docker, który zawiera aplikację platformy .NET Core. Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.

Dowiesz się:

> [!div class="checklist"]
>
> - Tworzenie i publikowanie prostej aplikacji .NET Core
> - Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core
> - Tworzenie obrazu platformy Docker
> - Tworzenie i uruchamianie kontenera platformy Docker

Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core. *Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*. Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj następujące wymagania wstępne:

- [Zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download) \
Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info`, aby określić, którego zestawu SDK używasz.

- [Platforma Docker Community Edition](https://www.docker.com/products/docker-desktop)

- Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core. W tym samouczku nazwa `docker-working` jest używana jako folder roboczy.

### <a name="use-sdk-version-22"></a>Użyj zestawu SDK 2,2

Jeśli używasz zestawu SDK, który jest nowszy, na przykład 3,0, upewnij się, że aplikacja ma wymuszone użycie zestawu 2,2 SDK. Utwórz plik o nazwie *Global. JSON* w folderze roboczym i wklej go w następującym kodzie JSON:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Zapisz ten plik. Obecność pliku spowoduje wymuszenie użycia przez program .NET Core wersji 2,2 dla każdego polecenia `dotnet` wywołana z tego folderu i poniżej.

## <a name="create-net-core-app"></a>Tworzenie aplikacji platformy .NET Core

Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker. Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go. W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:

```dotnetcli
dotnet new console -o app -n myapp
```

Drzewo folderów będzie wyglądać następująco:

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

@No__t_0 polecenie tworzy nowy folder o nazwie *App* i generuje aplikację "Hello World". Wprowadź folder *App* i uruchom polecenie `dotnet run`. Zobaczysz następujące dane wyjściowe:

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

Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`. Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność. Użyj polecenia Cancel <kbd>CTRL</kbd> +<kbd>C</kbd> , aby go zatrzymać. Zobaczysz następujące dane wyjściowe:

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

To polecenie kompiluje aplikację do folderu *Publikowanie* . Ścieżka do folderu *publikowania* z folderu roboczego powinna być `.\app\bin\Release\netcoreapp2.2\publish\`

Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy *plik MojaApl. dll* został utworzony. W folderze *aplikacja* Uruchom jedno z następujących poleceń:

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Tworzenie pliku dockerfile

Plik *pliku dockerfile* jest używany przez polecenie `docker build`, aby utworzyć obraz kontenera. Ten plik jest plikiem w postaci zwykłego tekstu o nazwie *pliku dockerfile* , który nie ma rozszerzenia.

W terminalu przejdź do katalogu roboczego, który został utworzony na początku. Utwórz plik o nazwie *pliku dockerfile* w folderze roboczym i otwórz go w edytorze tekstu. Dodaj następujące polecenie jako pierwszy wiersz pliku:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

Polecenie `FROM` informuje platformę Docker o konieczności ściągnięcia obrazu oznaczonego jako **2,2** z repozytorium **MCR.Microsoft.com/dotnet/Core/Runtime** . Upewnij się, że używasz środowiska uruchomieniowego programu .NET Core, które pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK. Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 2,2 SDK i utworzyła aplikację, która jest przeznaczona dla platformy .NET Core 2,2. Dlatego obraz podstawowy, do którego odwołuje się *pliku dockerfile* , jest oznaczony **2,2**.

Zapisz plik *pliku dockerfile* . Struktura katalogów folderu roboczego powinna wyglądać następująco. Niektóre pliki i foldery z bardziej szczegółowymi poziomami zostały wycięte w celu zaoszczędzenia miejsca w artykule:

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
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

Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*. @No__t_0 w poleceniu `docker build` instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile*. To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **obraz** , który wskazuje na ten obraz. Po zakończeniu tego polecenia Uruchom `docker images`, aby wyświetlić listę zainstalowanych obrazów:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** . Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie. Dodajmy dwa polecenia do *pliku dockerfile*. Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym obraz, do którego będzie **wskazywał repozytorium.**

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Polecenie `COPY` instruuje platformę Docker o skopiowanie określonego folderu na komputerze do folderu w kontenerze. W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.

Następne polecenie `ENTRYPOINT`, instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny. Po rozpoczęciu kontenera zostanie uruchomione polecenie `ENTRYPOINT`. Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.

W terminalu uruchom `docker build -t myimage -f Dockerfile .` i po zakończeniu tego polecenia Uruchom polecenie `docker images`.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**. Końcowy **Identyfikator obrazu** (będzie inny) to **ddcc6646461b** , a następnie utworzysz kontener oparty na tym obrazie.

## <a name="create-a-container"></a>Tworzenie kontenera

Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener. Kontener można utworzyć na dwa sposoby. Najpierw utwórz nowy kontener, który został zatrzymany.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

Polecenie `docker create` from powyżej utworzy kontener oparty na obrazie **obrazu** . Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera. Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Zarządzanie kontenerem

Do każdego kontenera jest przypisywana nazwa Losowa, której można użyć do odwoływania się do tego wystąpienia kontenera. Na przykład kontener, który został utworzony automatycznie wybiera nazwę **boring_matsumoto** (będzie się różnić) i tej nazwy można użyć do uruchomienia kontenera. Automatyczna nazwa zostanie zastąpiona określonym przez użycie parametru `docker create --name`.

Poniższy przykład używa polecenia `docker start`, aby uruchomić kontener, a następnie używa polecenia `docker ps` do wyświetlania tylko kontenerów z systemem:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

Analogicznie, polecenie `docker stop` spowoduje zatrzymanie kontenera. Poniższy przykład używa polecenia `docker stop`, aby zatrzymać kontener, a następnie używa polecenia `docker ps`, aby pokazać, że żaden kontener nie jest uruchomiony:

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Nawiązywanie połączenia z kontenerem

Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe. Użyj poleceń `docker start` i `docker attach`, aby uruchomić kontener i uzyskać wgląd w strumieniu danych wyjściowych. W tym przykładzie polecenie <kbd>Ctrl + C</kbd> służy do odłączenia od uruchomionego kontenera. Może to ostatecznie zakończyć proces w kontenerze, co spowoduje zatrzymanie kontenera. @No__t_0 parametr gwarantuje, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie zatrzyma procesu w kontenerze.

Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Usuwanie kontenera

Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte. Usuń kontener, który został wcześniej utworzony. Jeśli kontener jest uruchomiony, Zatrzymaj go.

```console
> docker stop boring_matsumoto
```

Poniższy przykład wyświetla listę wszystkich kontenerów. Następnie używa polecenia `docker rm`, aby usunąć kontener, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

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

Za pomocą `docker run -it` polecenie <kbd>Ctrl + C</kbd> przestanie działać w kontenerze, który z kolei zatrzymuje kontener. Ponieważ podano parametr `--rm`, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany. Sprawdź, czy nie istnieje:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Zmień punkt wejścia

@No__t_0 polecenie umożliwia również modyfikowanie polecenia `ENTRYPOINT` z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera. Na przykład użyj następującego polecenia, aby uruchomić `bash` lub `cmd.exe`. W razie potrzeby zmodyfikuj polecenie.

#### <a name="windows"></a>Windows

W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`. <kbd>Naciśnij klawisz CTRL</kbd> +<kbd>C</kbd> , aby zakończyć proces i zatrzymać kontener.

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

W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`. @No__t_0 polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.

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

## <a name="clean-up-resources"></a>Czyszczenie zasobów

W tym samouczku utworzono kontenery i obrazy. Jeśli chcesz, usuń te zasoby. Użyj następujących poleceń, aby

01. Wyświetl listę wszystkich kontenerów

    ```console
    > docker ps -a
    ```

02. Zatrzymaj uruchomione kontenery. @No__t_0 reprezentuje nazwę, która jest automatycznie przypisywana do kontenera.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Usuń kontener

    ```console
    > docker rm CONTAINER_NAME
    ```

Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze. Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* . Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.

> [!NOTE]
> Pliki obrazów mogą być duże. Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji. Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

- [Wypróbuj ASP.NET Core samouczka mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Przejrzyj usługi platformy Azure, które obsługują kontenery.](https://azure.microsoft.com/overview/containers/)
- [Przeczytaj o poleceniach pliku dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Poznaj narzędzia kontenerów dla programu Visual Studio](/visualstudio/containers/overview)
