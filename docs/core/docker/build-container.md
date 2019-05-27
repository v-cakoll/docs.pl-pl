---
title: Konteneryzowanie aplikacji za pomocą samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikacji .NET Core za pomocą platformy Docker.
ms.date: 04/10/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 2ea9e9bc2614e62fe6ec0d59e39d42c2e32a80a1
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051812"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Samouczek: Konteneryzowanie aplikacji .NET Core

Tym samouczku pokazano, jak utworzyć obraz platformy Docker, który zawiera aplikację .NET Core. Obraz, który może służyć do utworzenia kontenerów dla lokalnego środowiska deweloperskiego, Chmura prywatna lub chmury publicznej.

Dowiesz się, jak:

> [!div class="checklist"]
> * Tworzenie i publikowanie prostą aplikację platformy .NET Core
> * Tworzenie i konfigurowanie pliku Dockerfile dla platformy .NET Core
> * Zbuduj obraz Docker
> * Tworzenie i uruchamianie kontenera platformy Docker

Będziesz zrozumieć Docker kontenera, twórz i wdrażaj zadania dla aplikacji .NET Core. *Platforma Docker* używa *aparat platformy Docker* umożliwiają szybkie tworzenie i pakowanie aplikacji jako *obrazów platformy Docker*. Te obrazy są zapisywane *pliku Dockerfile* format zostaną wdrożone i uruchomione w kontenerze warstwowej.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj następujące wymagania wstępne:

- [.NET core SDK 2,2](https://dotnet.microsoft.com/download)\
Jeśli masz platformy .NET Core zainstalowany, użyj `dotnet --info` polecenie, aby określić zestaw SDK, których używasz.

- [Docker Community Edition](https://www.docker.com/products/docker-desktop)

- Tymczasowe katalog roboczy dla *pliku Dockerfile* i .NET Core przykładowej aplikacji.

### <a name="use-sdk-version-22"></a>Korzystanie z zestawu SDK w wersji 2.2

Jeśli używasz zestawu SDK, która jest nowsza, takich jak 3.0, upewnij się, czy aplikacja jest zmuszony do używania 2,2 zestawu SDK. Utwórz plik o nazwie `global.json` w katalogu roboczym i wklej następujący kod json:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Zapisz ten plik. Obecność pliku spowoduje to wymuszenie platformy .NET Core, aby użyć wersji 2.2 dla każdego `dotnet` polecenie wywołane z tego katalogu i poniżej.

## <a name="create-net-core-app"></a>Tworzenie, .NET Core aplikacji

Potrzebujesz aplikacji .NET Core, która uruchomi kontener platformy Docker. Otwórz terminal, Utwórz katalog roboczy, a następnie wprowadź go. W katalogu roboczym uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie aplikacji:

```console
dotnet new console -o app -n myapp
```

Czy polecenie tworzy nowy katalog o nazwie *aplikacji* i wygeneruje aplikację "Hello World". Można przetestować tę aplikację, aby zobaczyć, jak działa. Wprowadź *aplikacji* katalogu i wykonaj polecenie `dotnet run`. Zostanie wyświetlone następujące dane wyjściowe:

```console
> dotnet run
Hello World!
```

Domyślny szablon tworzy aplikację, która drukuje do terminala, a następnie kończy działanie. W tym samouczku użyjesz aplikacji, która działa w pętli nieskończoność. Otwórz **Program.cs** plik w edytorze tekstów. On obecnie powinien wyglądać podobnie do poniższego kodu:

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

Zastąp go następującym kodem, który zlicza liczby co sekundę:

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Zapisz plik i przetestować program ponownie, używając `dotnet run`. Należy pamiętać, że ta aplikacja działa przez czas nieokreślony. Za pomocą polecenia Anuluj <kbd>klawisze CTRL + C</kbd> go zatrzymać. Zostanie wyświetlone następujące dane wyjściowe:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Jeśli przekażesz liczbą w wierszu polecenia do aplikacji, zostanie tylko policzone maksymalnie, kwota, a następnie zamknij. Wypróbuj ją za pomocą `dotnet run -- 5` zliczania do pięciu.

> [!NOTE]
> Wszelkie parametry po `--` są przekazywane do aplikacji.

## <a name="publish-net-core-app"></a>Publikowanie .NET Core aplikacji

Przed dodaniem aplikacji .NET Core do obrazu platformy Docker, należy go opublikować. Kontener wykona opublikowanej wersji aplikacji, gdy jest ona uruchamiana.

Z katalogu roboczego wprowadź **aplikacji** katalogu, w przykładzie kodu źródłowego i uruchom następujące polecenie:

```console
dotnet publish -c Release
```

To polecenie kompiluje aplikację, aby **publikowania** folderu w folderze danych wyjściowych aplikacji. Ścieżka do **publikowania** folder z katalogu roboczego powinien być `.\app\bin\Release\netcoreapp2.2\publish\`

Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy **myapp.dll** został utworzony. Z **aplikacji** katalogu, uruchom jedno z następujących poleceń:

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\path-to-working-dir\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/path-to-working-dir/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

W terminalu Przejdź katalog do katalogu roboczego.

## <a name="create-the-dockerfile"></a>Utwórz plik Dockerfile

*Pliku Dockerfile* plik jest używany przez `docker build` polecenie, aby utworzyć obraz kontenera. Ten plik jest plikiem zwykłego tekstu, o nazwie *pliku Dockerfile* nie ma rozszerzenia. Utwórz plik o nazwie *pliku Dockerfile* w katalogu roboczym, a następnie otwórz go w edytorze tekstów. W pierwszym wierszu pliku, należy dodać następujące polecenie:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

`FROM` Polecenie informuje, Docker, aby ściągnąć obraz oznaczony **2.2** z **mcr.microsoft.com/dotnet/core/runtime** repozytorium. Upewnij się, ściągania środowiska uruchomieniowego .NET Core, które odpowiada celem zestawu SDK środowiska uruchomieniowego. Na przykład aplikację utworzoną w poprzedniej sekcji używane .NET Core 2.2 SDK i utworzyć aplikację, która docelowej platformy .NET Core 2.2. Dlatego obraz podstawowy, o których mowa w *pliku Dockerfile* oznakowano **2.2**.

Zapisz plik. W terminalu Uruchom `docker build -t myimage .` i Docker będzie przetwarzać każdy wiersz w *pliku Dockerfile*. `.` w `docker build` polecenie informuje platformy docker do korzystania z bieżącego katalogu można znaleźć *pliku Dockerfile*. To polecenie tworzy obraz i tworzy lokalne repozytorium o nazwie **myimage** wskazującego na tym obrazie. Po zakończeniu działania tego polecenia, uruchom `docker images` umożliwia wyświetlenie listy obrazów zainstalowane:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

Zwróć uwagę, że dwa obrazy współużytkować ten sam **identyfikator obrazu** wartość. Wartość jest taka sama oba obrazy, ponieważ tylko polecenia w *pliku Dockerfile* został podstawą nowy obraz istniejącego obrazu. Dodajmy dwa polecenia, aby *pliku Dockerfile*. Każde polecenie tworzy nową warstwę obrazu za pomocą polecenia końcowego reprezentujący obraz **myimage** wskaż repozytorium.

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` Polecenie informuje, Docker, aby skopiować określonego folderu na komputerze do folderu w kontenerze. W tym przykładzie **publikowania** folder jest kopiowany do folderu o nazwie **aplikacji** w kontenerze.

Następne polecenie `ENTRYPOINT`, platformy docker, aby skonfigurować kontener, aby działał jako plik wykonywalny. Po uruchomieniu kontenera, `ENTRYPOINT` polecenia. Po zakończeniu tego polecenia, kontenera zostanie automatycznie zatrzymany.

Zapisz plik. W terminalu Uruchom `docker build -t myimage .` i gdy które polecenie zostanie zakończone, uruchom `docker images`.

```console
> docker build -t myimage .
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

Każde polecenie w *pliku Dockerfile* wygenerowany warstwy i utworzyć **identyfikator obrazu**. Końcowe **identyfikator obrazu** (Twój będzie inny) jest **ddcc6646461b** i następnie utworzysz kontener na podstawie tego obrazu.

## <a name="create-a-container"></a>Tworzenie kontenera

Teraz, gdy masz obrazu, który zawiera aplikację, można utworzyć kontenera. Kontener można utworzyć na dwa sposoby. Najpierw utwórz nowy kontener, który został zatrzymany.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

`docker create` Polecenia z powyższych utworzy kontener na podstawie **myimage** obrazu. Wyświetlone dane wyjściowe tego polecenia **identyfikator kontenera** (Twój będzie inny) utworzonego kontenera. Aby wyświetlić listę *wszystkich* kontenery, używają `docker ps -a` polecenia:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Zarządzaj kontenera

Każdy kontener jest przypisany losową nazwę, która służy do odwoływania się do wystąpienia kontenera. Na przykład kontener, który został utworzony automatycznie wybrana nazwa **boring_matsumoto** (Twój będzie inny), tę nazwę można umożliwia uruchamianie kontenera. Zastąp automatyczne nazwą jeden z nich przy użyciu `docker create --name` parametru.

W poniższym przykładzie użyto `docker start` polecenie, aby uruchomić kontener, a następnie używa `docker ps` polecenie, aby wyświetlić tylko kontenerów, które są uruchomione:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

Podobnie `docker stop` polecenie spowoduje zatrzymanie kontenera. W poniższym przykładzie użyto `docker stop` polecenie, aby zatrzymać kontener, a następnie używa `docker ps` polecenie, aby pokazać, że kontenery nie są uruchomione.

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Łączenie do kontenera

Po uruchomieniu kontenera możesz połączyć się do niej, aby wyświetlić dane wyjściowe. Użyj `docker start` i `docker attach` poleceń, aby rozpocząć, kontener i wgląd w dane ze strumienia wyjściowego. W tym przykładzie <kbd>klawisze CTRL + C</kbd> polecenie jest używane do odłączenia uruchomionego kontenera. To, że faktycznie zakończenie procesu w kontenerze, w której zostanie zatrzymane kontenera. `--sig-proxy=false` Parametru gwarantuje, że <kbd>klawisze CTRL + C</kbd> lokacji nie zatrzyma proces w kontenerze.

Po odłączeniu z kontenera, ponownie dołączyć, aby sprawdzić, czy jest nadal uruchomiona i zliczania.

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

### <a name="delete-a-container"></a>Usuń kontener

Na potrzeby tego artykułu nie chcesz po prostu zawiesza się wokół czynności kontenerów. Usuń kontener, który został wcześniej utworzony. Jeśli kontener jest uruchomiona, zatrzymaj ją.

```console
> docker stop boring_matsumoto
```

Poniższy przykład wyświetla listę wszystkich kontenerów. Następnie używa `docker rm` polecenia można usunąć kontenera, a następnie sprawdza po raz drugi dla dowolnego uruchomione kontenery.

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

Środowisko docker zawiera `docker run` polecenia do tworzenia i uruchamiania kontenera jako pojedyncze polecenie. To polecenie eliminuje konieczność uruchamiania `docker create` i następnie `docker start`. Można również ustawić to polecenie, aby automatycznie usunąć kontener po zatrzymaniu kontenera. Na przykład użyć `docker run -it --rm` zrobić dwie rzeczy, najpierw automatycznie za pomocą bieżącego terminalu połączyć z kontenera i następnie po zakończeniu kontenera, usuń go:

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Za pomocą `docker run -it`, <kbd>klawisze CTRL + C</kbd> polecenie spowoduje zatrzymanie procesu, który jest uruchomiony w kontenerze, który z kolei zatrzymuje kontener. Ponieważ `--rm` podano parametr, kontenera są automatycznie usuwane, gdy proces zostanie zatrzymany. Sprawdź, czy nie istnieją:

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Zmiana punktu wejścia

`docker run` Polecenie umożliwia również modyfikowanie `ENTRYPOINT` polecenia *pliku Dockerfile* i uruchom coś innego, ale tylko dla tego kontenera. Na przykład następujące polecenie do uruchomienia `bash` lub `cmd.exe`. Edytuj polecenia zgodnie z potrzebami.

#### <a name="windows"></a>Windows
W tym przykładzie `ENTRYPOINT` jest zmieniana na `cmd.exe`. <kbd>CTRL + C,</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać kontenera.

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

W tym przykładzie `ENTRYPOINT` jest zmieniana na `bash`. `quit` Polecenie jest wykonywane, która kończy proces i przestanie kontenera.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Podstawowe polecenia

Docker ma wiele różnych poleceń, które obejmują co chcesz zrobić za pomocą kontenera i obrazy. Te polecenia Docker mają zasadnicze znaczenie dla zarządzania kontenerów:

* [kompilacji platformy docker](https://docs.docker.com/engine/reference/commandline/build/)
* [Uruchamianie platformy docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [Zatrzymaj platformy docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [Menedżer zasobów platformy docker](https://docs.docker.com/engine/reference/commandline/rm/)
* [rmi platformy docker](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Obraz platformy docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku utworzono kontenerów i obrazy. Jeśli chcesz, należy usunąć te zasoby. Użyj następujących poleceń do

01. Listę wszystkich kontenerów

    ```console
    > docker ps -a
    ```

02. Zatrzymaj kontenerów, które są uruchomione. `CONTAINER_NAME` Reprezentuje nazwę automatycznie przypisywane do kontenera.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Usuwanie kontenera

    ```console
    > docker rm CONTAINER_NAME
    ```

Następnie usuń wszelkie obrazy, które nie mają już na komputerze. Usuń obraz utworzone przez użytkownika *pliku Dockerfile* , a następnie usuń obraz platformy .NET Core *pliku Dockerfile* zależała od. Możesz użyć **identyfikator obrazu** lub **REPOZYTORIUM: TAG** ciąg w formacie.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

Użyj `docker images` polecenie, aby wyświetlić listę obrazów, zainstalowane.

> [!NOTE]
> Pliki obrazów mogą być duże. Zazwyczaj należy usunąć kontenery tymczasowe, utworzone podczas testowania i opracowywania aplikacji. Zazwyczaj można przechowywać obrazy podstawowe za pomocą środowiska uruchomieniowego zainstalowanego, jeśli planujesz tworzenie innych obrazów oparte na tego środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

* [Wypróbuj samouczek platformy ASP.NET Core Mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Przegląd usług platformy Azure, które obsługują kontenery.](https://azure.microsoft.com/overview/containers/)
* [Informacje na temat poleceń pliku Dockerfile.](https://docs.docker.com/engine/reference/builder/)
* [Poznaj narzędzia kontenerów programu Visual Studio](/visualstudio/containers/overview)
