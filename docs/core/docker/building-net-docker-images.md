---
title: "Tworzenie obrazy usługi Docker .NET Core"
description: "Opis obrazy usługi Docker i .NET Core"
keywords: .NET, .NET Core, Docker
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
ms.workload:
- dotnetcore
ms.openlocfilehash: d5631bdbc0334640b290c08df17cba0bfe99fe85
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="building-docker-images-for-net-core-applications"></a>Tworzenie aplikacji programu .NET Core obrazy usługi Docker

 W tym samouczku możemy skupić się na używanie .NET Core w Docker. Najpierw możemy Poznaj różne obrazy Docker oferowane i przechowywane przez firmę Microsoft i przypadki użycia. Firma Microsoft następnie Dowiedz się, jak utworzyć i dockerize aplikacji platformy ASP.NET Core.

W trakcie tego samouczka dowiesz się:
> [!div class="checklist"]
> * Więcej informacji o obrazach systemu Microsoft .NET Core Docker 
> * Pobierz przykładową aplikację Dockerize platformy ASP.NET Core
> * Uruchom przykładową aplikację ASP.NET lokalnie
> * Tworzenie i uruchamianie przykładu z rozwiązaniem Docker z kontenerów systemu Linux
> * Tworzenie i uruchamianie przykładu z kontenerami Docker dla systemu Windows

## <a name="docker-image-optimizations"></a>Optymalizacja obrazów docker

Tworząc obrazy usługi Docker dla deweloperów, firma Microsoft skupia się na trzech głównych scenariuszy:

* Obrazy używane do opracowywania aplikacji .NET Core
* Obrazy używane do tworzenia aplikacji platformy .NET Core
* Obrazy używane do uruchamiania aplikacji .NET Core

Dlaczego trzy obrazy?
Podczas tworzenia, tworzenie i uruchamianie aplikacji konteneryzowanych, mamy różnych priorytetów.

* **Programowanie:** skupiono się priorytet na szybko przejść zmiany i możliwość zmiany debugowania. Rozmiar obrazu nie jest równie ważne, a nie można wprowadzić zmiany w kodzie i szybkie wyświetlenie?

* **Kompilacja:** ten obraz zawiera wszystko, co jest potrzebne do skompilowania aplikacji, która obejmuje kompilator i innych zależności, aby zoptymalizować plików binarnych.  Obraz kompilacji umożliwia tworzenie zasobów, które zostanie umieszczony w obrazie produkcji. Obraz kompilacji będzie służyć do ciągłej integracji lub w środowisku kompilacji. Takie podejście umożliwia agenta kompilacji skompilować i utworzyć aplikację (z wymaganych zależności) w przypadku obrazu kompilacji. Agenta kompilacji musi znać tylko sposób uruchamiania tego obrazu Docker.

* **Produkcja:** tempa można wdrożyć i uruchomić obrazu? Ten obraz jest mały, więc jest zoptymalizowana wydajność sieci z rejestru Docker na hostach Docker. Zawartość jest gotowy do uruchomienia, włączanie o najszybszym czasie z Docker do przetwarzania wyników. Kompilacja kodu dynamicznej nie jest wymagana w modelu Docker. Zawartość, którą należy zaznaczyć ten obraz będzie ograniczony do plików binarnych i treści potrzebne do uruchomienia aplikacji.

    Na przykład `dotnet publish` dane wyjściowe zawierają:

    * skompilowane pliki binarne
    * pliki js i CSS


Powód, aby uwzględnić `dotnet publish` danych wyjściowych polecenia w obrazie produkcji jest zachowanie jego "rozmiar do minimum.

Niektóre obrazy .NET Core Udostępnianie warstw między tagami różnych tak pobieranie najnowszych tag jest stosunkowo lekkie procesu. Jeśli już masz starszą wersję na komputerze, to architektura zmniejsza ilość miejsca na dysku wymagana.

Korzystając z wielu aplikacji wspólnej obrazów na tym samym komputerze, pamięci jest udostępniana między wspólnej obrazów. Obrazy muszą być takie same, do udostępnienia.

## <a name="docker-image-variations"></a>Zmiany obrazu docker

Aby osiągnąć powyższe cele, firma Microsoft udostępnia wariantów obrazu w obszarze [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Ten obraz zawiera .NET Core SDK, w tym oprogramowanie .NET Core i narzędzia wiersza polecenia (CLI). Ten obraz mapy do **rozwojowych**. Skorzystaj z tego obrazu dla rozwoju lokalnych, debugowania i testowania jednostek. Ten obraz może także służyć do Twojej **kompilacji** scenariuszy. Przy użyciu `microsoft/dotnet:sdk` zawsze zawiera najnowszą wersję.

> [!TIP]
> Jeśli nie wiesz o Twoje potrzeby, chcesz użyć `microsoft/dotnet:<version>-sdk` obrazu. Jako "faktyczne" obrazu zostało zaprojektowane do użycia jako throw nieobecności kontenera (kodu źródłowego instalacji i rozpocząć kontener, aby uruchomić aplikację), a jako obrazu podstawowego, aby utworzyć inne obrazy z.

* `microsoft/dotnet:<version>-runtime`: Ten obraz zawiera .NET Core (środowisko uruchomieniowe i biblioteki) i jest zoptymalizowana pod kątem uruchamiania aplikacji .NET Core **produkcji**.

## <a name="alternative-images"></a>Alternatywne obrazów

Oprócz zoptymalizowane scenariusze programowania, kompilacji i produkcji firma Microsoft udostępnia dodatkowe obrazy:

* `microsoft/dotnet:<version>-runtime-deps`: **Deps środowiska uruchomieniowego** obraz zawiera system operacyjny ze wszystkimi zależnościami macierzystego, wymagane przez oprogramowanie .NET Core. Ten obraz dotyczy [niezależne aplikacji](../deploying/index.md).

Najnowsze wersje każdego wariantu:

* `microsoft/dotnet` lub `microsoft/dotnet:latest` (alias obrazu zestawu SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Przykłady do eksplorowania

* [W tym przykładzie platformy ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) pokazuje wzorzec najlepszych rozwiązań tworzenia obrazy usługi Docker dla platformy ASP.NET Core aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów zarówno systemu Linux i Windows.

* W tym przykładzie .NET Core Docker pokazuje wzorzec najlepsze praktyki dla [tworzenia obrazów Docker dla aplikacji .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>Pierwszej aplikacji platformy ASP.NET Core Docker

W tym samouczku umożliwia korzystanie z platformy ASP.NET Core Docker przykładowych aplikacji dla aplikacji, którą chcemy udostępnić dockerize. Ta przykładowa aplikacja platformy ASP.NET Core Docker pokazuje wzorzec najlepszych rozwiązań tworzenia obrazy usługi Docker dla platformy ASP.NET Core aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów zarówno systemu Linux i Windows.

Przykładowy plik Dockerfile tworzy obraz Docker aplikacji platformy ASP.NET Core, na podstawie obrazu platformy ASP.NET Core środowiska uruchomieniowego Docker.

Używa [Docker wieloetapowym kompilacji funkcji](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) do:

* utworzyć przykład w kontenerze oparciu **większych** obrazu podstawowego platformy ASP.NET Core kompilacji Docker 
* kopiuje wynik końcowy kompilacji do obrazu platformy Docker na podstawie **mniejszych** obrazu podstawowego środowiska wykonawczego programu ASP.NET Core Docker

> [!NOTE]
> Obraz kompilacji zawiera wymagane narzędzia do tworzenia aplikacji, a nie w obrazie środowiska wykonawczego.

### <a name="prerequisites"></a>Wymagania wstępne

Aby skompilować i uruchomić, należy zainstalować następujące elementy:

#### <a name="net-core-20-sdk"></a>.NET core 2.0 SDK

* Zainstaluj [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

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

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>Instalowanie narzędzia Git do repozytorium przykładowej

* Zainstaluj [git](https://git-scm.com/download) Jeśli chcesz sklonować repozytorium.

### <a name="getting-the-sample-application"></a>Pobieranie przykładowej aplikacji

Najprostszym sposobem uzyskania próbki jest w klonowania [przykłady repozytorium](https://github.com/dotnet/dotnet-docker-samples) za pomocą narzędzia git, korzystając z następujących instrukcji: 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

Możesz również pobrać repozytorium (jest mała) jako zip z repozytorium przykłady .NET Core Docker.

### <a name="run-the-aspnet-app-locally"></a>Lokalne uruchamianie aplikacji platformy ASP.NET

Jako punkt odniesienia przed możemy containerize aplikacji, najpierw uruchom aplikację lokalnie.

Możesz skompilować i uruchomić aplikację lokalnie .NET SDK 2.0 Core za pomocą następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):

```console
cd aspnetapp
dotnet run
```

Po uruchomieniu aplikacji, odwiedź stronę **http://localhost: 5000** w przeglądarce sieci web.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Tworzenie i uruchamianie przykładu z rozwiązaniem Docker z kontenerów systemu Linux

Możesz skompilować i uruchomić przykładowy w Docker przy użyciu kontenerów systemu Linux przy użyciu następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` "-P" argument mapy port 5000 na komputerze lokalnym do portu 80 w kontenerze (formularz mapowania portów jest `host:container`). Aby uzyskać więcej informacji, zobacz [docker Uruchom](https://docs.docker.com/engine/reference/commandline/exec/) odwołania dotyczące parametrów wiersza polecenia.

Po uruchomieniu aplikacji, odwiedź stronę **http://localhost: 5000** w przeglądarce sieci web.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Tworzenie i uruchamianie przykładu z kontenerami Docker dla systemu Windows

Możesz skompilować i uruchomić przykładowy w Docker przy użyciu kontenery systemu Windows za pomocą następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Musisz przejść do **adres IP kontenera** (w przeciwieństwie do http://localhost) w przeglądarce bezpośrednio po użyciu kontenery systemu Windows. Możesz uzyskać adres IP z kontenera następujące czynności:

* Otwórz innego wiersza polecenia.
* Uruchom `docker ps` wyświetlić uruchomionych kontenerów. Kontener "aspnetcore_sample" powinny być dostępne.
* Run `docker exec aspnetcore_sample ipconfig`.
* Skopiuj adres IP kontenera i Wklej w przeglądarce (na przykład 172.29.245.43).

> [!NOTE]
> Docker exec obsługuje identyfikację kontenery o nazwie lub wyznaczania wartości skrótu. Nazwa (aspnetcore_sample) jest używana w naszym przykładzie.

Zobacz poniższy przykład sposobu uzyskania adresu IP uruchomionych kontenera systemu Windows.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> Docker exec uruchamia nowe polecenie w kontenerze uruchomione. Aby uzyskać więcej informacji, zobacz [odwołania exec docker](https://docs.docker.com/engine/reference/commandline/exec/) na parametry wiersza polecenia.

Służy do tworzenia aplikacji, która jest gotowe do wdrożenia w środowisku produkcyjnym lokalnie za pomocą [publikowania dotnet](../tools/dotnet-publish.md) polecenia.

```console
dotnet publish -c release -o published
```

> [!NOTE]
> -C argument wersji kompilacji aplikacji w trybie przygotowania do wydania (wartość domyślna to tryb debugowania). Aby uzyskać więcej informacji, zobacz [dotnet Uruchom odwołanie](../tools/dotnet-run.md) na parametry wiersza polecenia.

Aplikację można uruchomić na **Windows** przy użyciu następującego polecenia.

```console
dotnet published\aspnetapp.dll
```

Aplikację można uruchomić na **Linux** lub **macOS** przy użyciu następującego polecenia.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Używane w tym przykładzie obrazy usługi docker

Na poniższych ilustracjach Docker są używane w tym przykładzie

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

Gratulacje! masz tylko:
> [!div class="checklist"]
> * Podstawowe informacje o obrazach systemu Microsoft .NET Core Docker
> * Otrzymano Dockerize przykładowej aplikacji platformy ASP.NET Core
> * Uruchomiono lokalnie przykładową aplikację ASP.NET
> * Wbudowane i uruchomiono próbki z rozwiązaniem Docker z kontenerów systemu Linux
> * Wbudowane i uruchomiono próbki z kontenerów Docker dla systemu Windows


**Następne kroki**

Poniżej przedstawiono niektóre czynności, które można wykonać:

* [Praca z narzędzia Docker programu Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Profilowanie kodu Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Wprowadzenie ręce na z programem Visual Studio for Mac, kontenery i niekorzystającą kodu w chmurze](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Pierwsze kroki z Docker i Visual Studio for Mac laboratorium](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.
