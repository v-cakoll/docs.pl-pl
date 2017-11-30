---
title: "Dowiedz się podstawy Docker z platformą .NET Core"
description: Docker i .NET Core podstawowy samouczek
keywords: .NET, .NET core, Docker, samouczek
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>Dowiedz się podstawy Docker z platformą .NET Core

Ten samouczek zawiera Docker kontenera tworzenia i wdrażania zadania dla aplikacji .NET Core. W trakcie tego samouczka dowiesz się:

> [!div class="checklist"]
> * Jak utworzyć plik Dockerfile
> * Jak utworzyć aplikację .NET Core.
> * Jak wdrożyć aplikację w kontenerze Docker.

[Platformy Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparatem platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) szybkie tworzenie i pakietu aplikacji jako [obrazy usługi Docker](https://docs.docker.com/glossary/?term=image). Te obrazy są zapisywane [plik Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format, aby wdrożyć i uruchomić w [warstwie kontenera](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>Oprogramowanie .NET core: Najłatwiejszym sposobem na rozpoczęcie pracy

Przed utworzeniem obrazu Docker, należy containerize aplikacji. Można go utworzyć w systemie Linux, MacOS lub systemu Windows. Jest najszybszym i Najprostszym sposobem wykonania tego używać .NET Core.

Jeśli znasz zestaw narzędzi interfejsu wiersza polecenia platformy .NET Core odczytu [Omówienie zestawu SDK programu .NET Core](../tools/index.md).

Można tworzyć kontenery w systemach Windows i Linux z [tagi na podstawie wielu arch](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Pierwszej aplikacji platformy .NET Core Docker

### <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

#### <a name="net-core-20-sdk"></a>.NET core 2.0 SDK

* Zainstaluj [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

* Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalowanie klienta Docker

Zainstaluj [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta Docker.

Klient Docker można zainstalować w:

* Dystrybucje systemu Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [System macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Tworzenie aplikacji konsoli .NET Core 2.0 dla Dockerization

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do folderu, który został utworzony i wpisz następujące polecenia:

```console
dotnet new console
dotnet run
```

Poznajmy Szybkie wskazówki:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md)Tworzy aktualne `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsoli.  Tworzy również `Program.cs`, podstawowe plik zawierający punkt wejścia dla aplikacji.
   
   `Hello.csproj`:

   Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.

   * `OutputType` Określa tag tworzymy plik wykonywalny, innymi słowy aplikacji konsoli.
   * `TargetFramework` Tag Określa, jakie implementacji .NET możemy docelowych. Realizując bardziej zaawansowany scenariusz można określić wiele platform docelowych i kompilacja — przejście do określonej struktury w ramach jednej operacji. W tym samouczku będziemy kompilacji dla programu .NET Core 2.0.

   `Program.cs`:

   Program, który rozpoczyna się od `using System`. To zdanie oznacza, "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku." `System` Przestrzeń nazw zawiera podstawowe konstrukcji `string`, lub typy liczbowe.

   Następnie definicję przestrzeni nazw o nazwie `Hello`. Przestrzeń nazw, można zmienić na dowolnych znaków. Klasa o nazwie `Program` jest zdefiniowany w tej przestrzeni nazw z `Main` metody pobierającej tablicy ciągów jako jej argument. Ta tablica zawiera listę argumentów przekazana wywołanego skompilowany program. W naszym przykładzie program zapisuje tylko "Witaj świecie!" w konsoli.

2. `$ dotnet restore`

   W .NET Core 2.x, **dotnet nowe** uruchamia [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia. **Przywracanie DotNet** przywraca drzewie zależności z [NuGet](https://www.nuget.org/)wywołania (.NET Menedżera pakietów).
   NuGet wykonuje następujące zadania:
   * analizuje *Hello.csproj* pliku 
   * pobiera plik zależności (lub chwyty z pamięci podręcznej komputera)
   * zapisuje *obj/project.assets.json* pliku

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json* plików jest pełny zestaw wykres zależności NuGet rozwiązania powiązania i innych metadanych aplikacji. To wymagane, plik jest używany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), aby poprawnie przetworzyć kodu źródłowego.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) o potwierdzenie pomyślnego utworzenia kompilacji, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Dla zaawansowanych scenariuszy, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) szczegółowe informacje.

## <a name="dockerize-the-net-core-application"></a>Dockerize aplikacji .NET Core

Aplikacja konsoli Hello .NET Core pomyślnie działa lokalnie. Teraz załóżmy zabrać krok dalsze i skompilować i uruchomić aplikację w Docker.

### <a name="your-first-dockerfile"></a>Twoje pierwszy plik Dockerfile

Otwórz w edytorze tekstów i do dzieła! Nadal trwają prace z katalogu Hello możemy tworzone w aplikacji.

Dodaj następujące instrukcje Docker albo Linux lub [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nowego pliku. Po zakończeniu zapisz go w folderze głównym katalogiem Hello jako **plik Dockerfile**, bez rozszerzenia (konieczne może być równa danego typu pliku `All types (*.*)` lub coś podobnego).

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Plik Dockerfile zawiera instrukcje kompilacji Docker, które są wykonywane sekwencyjnie.

Pierwsza instrukcja musi być [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Ta instrukcja inicjuje nowy etap kompilacji i ustawia obraz podstawowy dla pozostałych instrukcji. Tagi wielu architektury ściągnięcia kontenery systemu Windows lub Linux, w zależności od platformy Docker dla systemu Windows [tryb kontenera](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Obraz podstawowy dla naszej próbki jest obrazem zestawu sdk 2.0 z repozytorium microsoft/dotnet

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukcji Ustawia katalog roboczy dla wszelkie pozostałe wykonywania, CMD, punktu wejścia, KOPIOWANIA i Dodaj plik Dockerfile instrukcje. Jeśli katalog nie istnieje, zostanie on utworzony. W takim przypadku WORKDIR ustawiono do katalogu aplikacji.

```Dockerfile
WORKDIR /app
```

[ **KOPIOWANIA** ](https://docs.docker.com/engine/reference/builder/#copy) instrukcji kopiuje nowe pliki lub katalogi ze ścieżki źródłowej i dodaje je do plików kontenera docelowego. Z tej instrukcji Trwa kopiowanie plików projektu C# do kontenera.

```Dockerfile
COPY *.csproj ./
```

[ **Uruchom** ](https://docs.docker.com/engine/reference/builder/#run) instrukcji wykonuje żadnych poleceń w nową warstwę ponad bieżący obraz i zatwierdź wyniki. Obraz wynikowy zatwierdzone służy do następnego kroku w plik Dockerfile. Uruchamiamy **przywracania dotnet** uzyskać wymagane zależności pliku projektu C#. 

```Dockerfile
RUN dotnet restore
```

To **KOPIOWANIA** instrukcji kopiuje pozostałych plików do naszej kontenera do nowych [warstwy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Firma Microsoft publikowania aplikacji z tym **Uruchom** instrukcji. [ **Publikowania dotnet** ](../tools/dotnet-publish.md) polecenie kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu. Naszej aplikacji jest publikowany razem **wersji** konfiguracji i dane wyjściowe do domyślnego katalogu.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **Punktu wejścia** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukcji umożliwia kontener uruchamianie jako plik wykonywalny.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Teraz masz plik Dockerfile który:

* Kopiuje obraz aplikacji
* zależności aplikacji do obrazu
* Tworzy aplikację do uruchamiania jako plik wykonywalny

### <a name="build-and-run-the-hello-net-core-20-app"></a>Tworzenie i uruchamianie aplikacji Hello .NET Core 2.0

#### <a name="essential-docker-commands"></a>Niezbędne polecenia Docker

Te polecenia Docker są niezbędne:

* [docker kompilacji](https://docs.docker.com/engine/reference/commandline/build/)
* [Uruchom docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [Zatrzymaj docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Obraz docker](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Tworzenie i uruchamianie

Zapisano plik dockerfile; teraz Docker tworzy aplikację, a następnie uruchomi kontener.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Dane wyjściowe z `docker build` polecenia powinny być podobne do następujących danych wyjściowych konsoli:

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

Jak widać z danych wyjściowych, aparatem platformy Docker używane plik Dockerfile do budowania naszych kontenera.

Dane wyjściowe z `docker run` polecenia powinny być podobne do następujących danych wyjściowych konsoli:

```console
Hello World!
```

Gratulacje! masz tylko:
> [!div class="checklist"]
> * Utworzyć lokalnej aplikacji .NET Core
> * Utworzony plik Dockerfile do kompilacji z pierwszego kontenera
> * Wbudowane i uruchomiono aplikację Dockerized



## <a name="next-steps"></a>Następne kroki

Poniżej przedstawiono niektóre czynności, które można wykonać:

* [Wprowadzenie do platformy .NET Docker obrazów wideo](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker i wystąpień kontenera Azure lepsze razem!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker dla skrócone podręczniki platformy Azure](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Wdrażanie aplikacji na Docker na platformie Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.

## <a name="docker-images-used-in-this-sample"></a>Używane w tym przykładzie obrazy usługi docker

Na poniższych ilustracjach Docker są używane w tym przykładzie

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Powiązane zasoby

* [Przykłady .NET core Docker](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Plik Dockerfile kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Przykłady programu .NET framework Docker](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [Platformy ASP.NET Core na DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerize aplikację .NET Core — samouczek Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Praca z narzędzia Docker programu Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)