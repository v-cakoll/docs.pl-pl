---
title: Konteneryzowanie aplikacji za pomocą platformy Docker
description: W tym samouczku pokazano, jak utworzyć podstawową aplikację platformy .NET Core i konteneryzowanie go za pomocą platformy Docker.
ms.date: 10/11/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: eed72553576f4154fe63b2e5cf035a781afe4b7c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169589"
---
# <a name="how-to-containerize-a-net-core-application"></a>Jak konteneryzowanie aplikacji .NET Core

W tym samouczku pokazano Docker kontenera, twórz i wdrażaj zadania dla aplikacji .NET Core. [Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparat platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) umożliwiają szybkie tworzenie i pakowanie aplikacji jako [obrazów platformy Docker](https://docs.docker.com/glossary/?term=image). Te obrazy są zapisywane [pliku Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format zostaną wdrożone i uruchomione [warstwie kontenerów](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

W trakcie tego samouczka dowiesz się:

> [!div class="checklist"]
> * Jak utworzyć plik Dockerfile
> * Jak utworzyć aplikację platformy .NET Core.
> * Jak wdrożyć aplikację w kontenerze platformy Docker.

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: Najprostszym sposobem na rozpoczęcie pracy

Przed utworzeniem obrazu platformy Docker, należy konteneryzowanie aplikacji. Można je utworzyć w systemie Linux, MacOS lub Windows. Najszybszym i najłatwiejszym sposobem wykonania tego zadania jest korzystanie z platformy .NET Core.

Jeśli jesteś zaznajomiony z zestawu narzędzi interfejsu wiersza polecenia platformy .NET Core, zapoznaj się z [Omówienie zestawu .NET Core SDK](../tools/index.md).

Możesz tworzyć kontenery systemów Windows i Linux za pomocą [wielu arch na podstawie tagów](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Twoja pierwsza aplikacja platformy .NET Core Docker

### <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

#### <a name="net-core-sdk"></a>Zestaw SDK dla platformy .NET core

* Zainstaluj [zestawu SDK programu .NET Core 2.1](https://www.microsoft.com/net/download) lub nowszej.

Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) dla platformy .NET Core 2.1 pełną listę obsługiwanych systemów operacyjnych, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

* Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio Code](https://code.visualstudio.com/download)!

#### <a name="installing-docker-client"></a>Instalowanie klienta platformy Docker

Zainstaluj [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta platformy Docker.

Klient platformy Docker można zainstalować w:

* Dystrybucje systemu Linux

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/).

### <a name="create-a-net-core-21-console-app-for-dockerization"></a>Tworzenie aplikacji konsolowej .NET Core 2.1 dla Dockerization

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenia:

```console
dotnet new console
dotnet run
```

Zróbmy szybkiego przewodnika:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) Tworzy aktualnej `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsolowej.  Tworzy również `Program.cs`, podstawowy plik zawierający punkt wejścia dla aplikacji.

   `Hello.csproj`:

   Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.

   * `OutputType` Tag Określa, czy tworzymy plik wykonywalny, innymi słowy aplikację konsolową w języku.
   * `TargetFramework` Tagów Określa, jakie firma Microsoft objęci implementacja programu .NET. W zaawansowanym scenariuszu można określić wielu platform docelowych i kompilacja — przejście do określonej struktury, w ramach jednej operacji. W tym samouczku, firma Microsoft tworzy dla platformy .NET Core 2.1.

   `Program.cs`:

   Program, który rozpoczyna się od `using System`. To zdanie oznacza, "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku." `System` Przestrzeń nazw zawiera podstawowymi konstrukcjami `string`, lub typów liczbowych.

   Następnie definiujemy przestrzeń nazwy wywołaną `Hello`. Można zmienić nazw, do żadnego elementu, który ma. Klasa o nazwie `Program` jest zdefiniowana w ramach tej przestrzeni nazw za pomocą `Main` metody, która przyjmuje tablicę ciągów, jako argumentem. Ta tablica zawiera listę argumentów przekazywanych do wywołanego skompilowanego programu. W tym przykładzie program zapisuje tylko "Hello World!" w konsoli.

   **nowe polecenia DotNet** uruchamia [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia. **DotNet restore** przywraca drzewo zależności za pomocą [NuGet](https://www.nuget.org/)wywołania (Menedżer pakietów dla platformy .NET).
   NuGet wykonuje następujące zadania:
   * analizuje *Hello.csproj* pliku.
   * pobiera plik zależności (lub chwyty z pamięci podręcznej komputera).
   * zapisuje *obj/project.assets.json* pliku.

   *Project.assets.json* plik jest kompletny zestaw wykres zależności NuGet, powiązania rozwiązania i innych metadanych dla aplikacji. To wymagane, plik jest używany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), aby poprawnie przetworzyć kodu źródłowego.

2. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) celu potwierdzenia pomyślnej kompilacji, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji.

    ```console
    $ dotnet run

    Hello World!
    ```

    W przypadku zaawansowanych scenariuszy, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md) Aby uzyskać szczegółowe informacje.

## <a name="dockerize-the-net-core-application"></a>Przekształcać aplikacji .NET Core

Aplikację konsoli Hello platformy .NET Core pomyślnie działa lokalnie. Teraz sklonujemy zabrać krok dalej i kompilowanie i uruchamianie aplikacji na platformie Docker.

### <a name="your-first-dockerfile"></a>Z pierwszego pliku Dockerfile

Otwórz Edytor tekstu i zaczynajmy! Wciąż pracujemy z katalogu Witaj, którą utworzyliśmy aplikację w.

Dodaj następujące instrukcje dotyczące platformy Docker dla dowolnego systemu Linux lub [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nowego pliku. Gdy skończysz, zapisz go w katalogu głównym katalogiem Hello jako **pliku Dockerfile**, bez rozszerzenia (może być konieczne ustawienie typu Twojego pliku `All types (*.*)` lub innego ogranicznika).

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Plik Dockerfile zawiera instrukcje dotyczące kompilacji platformy Docker, które uruchamiają się po kolei.

Pierwsza instrukcja musi być [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Ta instrukcja inicjuje nowy etap kompilacji i ustawiania obrazu podstawowego dla pozostałych instrukcji. Tagi wielu architektury ściągnięcia kontenery Windows lub Linux, w zależności od platformy Docker for Windows [tryb kontenera](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Obrazu podstawowego w przypadku naszej próbki jest styl obrazowy zestawu sdk 2.1 z repozytorium dotnet/firmy microsoft

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukcja Ustawia katalog roboczy dla wszelkie pozostałe przebiegu, CMD, ENTRYPOINT, KOPIOWANIA i Dodaj plik Dockerfile instrukcje. Jeśli katalog nie istnieje, zostanie utworzony. W tym przypadku WORKDIR ustawiono katalogu aplikacji.

```Dockerfile
WORKDIR /app
```

[ **KOPIOWANIA** ](https://docs.docker.com/engine/reference/builder/#copy) instrukcji kopiowania nowych plików lub katalogów ze ścieżki źródłowej i dodaje je do systemu plików kontenera docelowego. Za pomocą tej instrukcji Trwa kopiowanie pliku projektu C# do kontenera.

```Dockerfile
COPY *.csproj ./
```

[ **Uruchom** ](https://docs.docker.com/engine/reference/builder/#run) instrukcji wykonuje wszystkie polecenia w nowej warstwie na podstawie bieżącego obrazu i zatwierdź wyniki. Zatwierdzony obraz wynikowy jest używana do następnego kroku w pliku Dockerfile. Będziemy działają **dotnet restore** można pobrać wymagane zależności pliku projektu C#. 

```Dockerfile
RUN dotnet restore
```

To **KOPIOWANIA** instrukcji kopiuje pozostałą część plików do nasz kontener do nowego [warstwy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Obecnie publikujemy aplikację z tym **Uruchom** instrukcji. [ **Publikowania dotnet** ](../tools/dotnet-publish.md) polecenie kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu. Nasza aplikacja jest publikowana z **wersji** konfiguracji i dane wyjściowe do domyślnego katalogu.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **Punktu wejścia** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukcji umożliwia kontener, aby działał jako plik wykonywalny.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Teraz masz plik Dockerfile który:

* Kopiuje obraz aplikacji
* zależności aplikacji do obrazu
* Tworzy aplikację, aby działał jako plik wykonywalny

### <a name="build-and-run-the-hello-net-core-app"></a>Skompiluj i uruchom aplikację Hello platformy .NET Core

#### <a name="essential-docker-commands"></a>Podstawowe polecenia platformy Docker

Te polecenia Docker są istotne:

* [kompilacji platformy docker](https://docs.docker.com/engine/reference/commandline/build/)
* [Uruchamianie platformy docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [Zatrzymaj platformy docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [Menedżer zasobów platformy docker](https://docs.docker.com/engine/reference/commandline/rm/)
* [rmi platformy docker](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Obraz platformy docker](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Kompilowanie i uruchamianie

Zapisano plik dockerfile; teraz Docker tworzy aplikację, a następnie uruchamia kontener.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Dane wyjściowe z `docker build` polecenia powinny być podobne do następujących danych wyjściowych konsoli:

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
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
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

Jak widać z danych wyjściowych, aparat platformy Docker umożliwiających tworzenie nasz kontener pliku Dockerfile.

Dane wyjściowe z `docker run` polecenia powinny być podobne do następujących danych wyjściowych konsoli:

```console
Hello World!
```

Gratulacje! masz tylko:
> [!div class="checklist"]
> * Utworzone lokalnej aplikacji .NET Core
> * Utworzony plik Dockerfile, aby utworzyć swój pierwszy kontener
> * Wbudowane i uruchomiono aplikację Dockerized

## <a name="next-steps"></a>Następne kroki

Poniżej przedstawiono niektóre kolejne kroki, które należy wykonać:

* [Wprowadzenie do platformy Docker .NET obrazów, wideo](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, platformy Docker i Azure Container Instances razem lepiej!](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [Docker for pakiety Azure Quickstarts](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Wdrażanie aplikacji na platformy Docker na platformie Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się dzisiaj](https://azure.microsoft.com/free/?b=16.48) bezpłatne konto 30-dniowej i Odbierz 200 USD środków na korzystanie z platformy Azure możesz wypróbować dowolną kombinację usług platformy Azure.

## <a name="docker-images-used-in-this-sample"></a>Obrazy platformy docker, używane w tym przykładzie

Następujące obrazy platformy Docker są używane w tym przykładzie

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Powiązane zasoby

* [Przykłady Docker w programie .NET core](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [Plik Dockerfile kontenerów Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Przykłady Docker w programie .NET framework](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [Platforma ASP.NET Core w witrynie DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Przekształcać aplikacji .NET Core — samouczek platformy Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Praca z narzędzia Docker programu Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Wdrażanie obrazów platformy Docker z rejestru kontenerów platformy Azure w usłudze Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)