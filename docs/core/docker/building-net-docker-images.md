---
title: Tworzenie obrazów platformy Docker programu .NET Core
description: Opis obrazów platformy Docker i platformy .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e48a263334ebb93a5d281032336aeb4073d8467c
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "34827342"
---
# <a name="building-docker-images-for-net-core-applications"></a>Tworzenie obrazów platformy Docker dla aplikacji .NET Core

 W tym samouczku skupimy się na używanie platformy .NET Core w Docker. Po pierwsze omówimy różnych obrazów platformy Docker, które są oferowane i konserwowane przez firmę Microsoft i przypadkami użycia. Firma Microsoft następnie Dowiedz się, jak tworzyć i przekształcać aplikacji ASP.NET Core.

W trakcie tego samouczka dowiesz się:
> [!div class="checklist"]
> * Więcej informacji na temat obrazów platformy Docker programu Microsoft .NET Core 
> * Pobierz przykładową aplikację w celu Dockerize platformy ASP.NET Core
> * Lokalne uruchamianie przykładowej aplikacji platformy ASP.NET
> * Kompilowanie i uruchamianie przykładu z platformy Docker dla kontenerów systemu Linux
> * Kompilowanie i uruchamianie przykładu z kontenerów platformy Docker for Windows

## <a name="docker-image-optimizations"></a>Optymalizacje obrazu platformy docker

Tworzenie obrazów platformy Docker dla deweloperów, skupiliśmy się na trzech głównych scenariuszy:

* Obrazy używane do tworzenia aplikacji platformy .NET Core
* Obrazy używane do tworzenia aplikacji platformy .NET Core
* Obrazy używane do uruchamiania aplikacji .NET Core

Dlaczego trzy obrazy?
Podczas tworzenia, kompilowania i uruchamiania konteneryzowanych aplikacji, mamy różnych priorytetach.

* **Programowanie:** skupiono się priorytetu na szybko iterować zmiany i możliwość debugowania zmiany. Rozmiar obrazu nie jest ważne, a nie można wprowadzić zmiany do kodu i szybkie wyświetlenie?

* **Kompilacja:** ten obraz zawiera wszystko, co jest potrzebne do kompilowania aplikacji, która obejmuje kompilator i inne zależności, aby zoptymalizować pliki binarne.  Możesz użyć obrazu kompilacji umożliwia tworzenie zasobów, które można umieścić w środowisku produkcyjnym obraz. Obraz kompilacji mogą być wykorzystane w celu zapewnienia ciągłej integracji, lub w środowisku kompilacji. Takie podejście umożliwia agenta kompilacji skompilować i utworzyć aplikację (wszystkie wymagane zależności) w przypadku obrazu kompilacji. Agenta kompilacji, wystarczy wiedzieć, jak uruchomić tego obrazu platformy Docker.

* **Produkcyjne:** jak szybko możesz wdrożyć i uruchomić obraz? Ten obraz jest mała, więc zoptymalizowane pod kątem wydajności sieci hostów platformy Docker z rejestru platformy Docker. Zawartość jest gotowa do uruchomienia, umożliwiając krótsze czasy docker, uruchom do przetwarzania wyników. Kompilacja kodu dynamicznej nie jest potrzebna w modelu platformy Docker. Zawartość, które można umieścić w ten obraz będzie ograniczona do plików binarnych i zawartość wymaganą do uruchomienia aplikacji.

    Na przykład `dotnet publish` dane wyjściowe zawierają:

    * skompilowane pliki binarne
    * pliki .js i CSS


Powód, aby uwzględnić `dotnet publish` danych wyjściowych polecenia w obrazie produkcji jest zapewnienie jego rozmiar do minimum.

Niektóre obrazy platformy .NET Core Udostępnij warstwy między różnych znaczników, więc pobieranie najnowszych tag jest stosunkowo lekkie procesu. Jeśli masz już starszą wersję na komputerze, ta architektura zmniejsza wymagana ilość miejsca na dysku.

Korzystając z wielu aplikacji obrazów wspólnych na tym samym komputerze, pamięci jest współużytkowana przez obrazów wspólnych. Obrazy musi być taka sama, do udostępnienia.

## <a name="docker-image-variations"></a>Różnice między obrazu platformy docker

Aby osiągnąć powyższe cele, firma Microsoft zapewnia wariantów obraz w ramach [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Ten obraz zawiera zestaw .NET Core SDK, co obejmuje .NET Core i narzędzia wiersza polecenia (CLI). Ten obraz mapuje **scenariusz tworzenia**. Możesz użyć tego obrazu lokalny rozwój, debugowanie i testy jednostkowe. Ten obraz może również służyć do Twojej **kompilacji** scenariuszy. Za pomocą `microsoft/dotnet:sdk` zawsze zawiera najnowszą wersję.

> [!TIP]
> Jeśli nie wiesz o Twoje potrzeby, chcesz użyć `microsoft/dotnet:<version>-sdk` obrazu. Jako obraz "de facto", został zaprojektowany tak, ma być używany jako throw away kontenera instalacji kodu źródłowego i uruchamianie kontenera, aby uruchomić aplikację, a jako obraz podstawowy, tworzyć innych obrazów z.

* `microsoft/dotnet:<version>-runtime`: Ten obraz zawiera .NET Core (środowisko uruchomieniowe i biblioteki) i jest zoptymalizowany pod kątem uruchamiania aplikacji .NET Core **produkcji**.

## <a name="alternative-images"></a>Alternatywne obrazów

Oprócz zoptymalizowane scenariusze programowania, kompilacji i produkcji oferujemy dodatkowe obrazy:

* `microsoft/dotnet:<version>-runtime-deps`**Deps środowiska uruchomieniowego** obraz zawiera system operacyjny, ze wszystkimi natywnych zależności wymagane przez platformy .NET Core. Ten obraz dotyczy [aplikacje samodzielne](../deploying/index.md).

Najnowsze wersje każdego wariantu:

* `microsoft/dotnet` lub `microsoft/dotnet:latest` (alias obrazu zestawu SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Przykłady, aby zapoznać się z

* [W tym przykładzie platformy Docker programu ASP.NET Core](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla platformy ASP.NET Core z aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów systemów Linux i Windows.

* Docker w programie .NET Core w przykładzie pokazano wzorzec najlepsze praktyki dla [tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)

## <a name="forward-the-request-scheme-and-original-ip-address"></a>Przesyła schemat żądania i oryginalnego adresu IP

Serwery proxy, moduły równoważenia obciążenia i innych urządzeniach sieciowych często zasłaniać informacje o żądaniu przed osiągnięciem przez nią konteneryzowaną aplikację:

* Gdy żądania HTTPS są przekazywane za pośrednictwem protokołu HTTP, oryginalnym schematem (HTTPS) zostaną utracone i muszą być przekazywane w nagłówku.
* Ponieważ aplikacja odbiera żądanie z serwera proxy i jej wartość true, źródła w Internecie lub w sieci firmowej, oryginalnego adresu IP klienta, również muszą być przekazywane w nagłówku.

Te informacje mogą być ważne przetwarzanie żądań, na przykład w przekierowania, uwierzytelnianie, generowanie konsolidacji, ocena zasad i geolokalizacja klienta.

Do przekazywania schemat i oryginalnego adresu IP do konteneryzowanych aplikacji platformy ASP.NET Core, użyj przekazywane oprogramowania pośredniczącego nagłówków. Aby uzyskać więcej informacji, zobacz [Konfigurowanie platformy ASP.NET Core pracować z serwerów proxy i moduły równoważenia obciążenia](/aspnet/core/host-and-deploy/proxy-load-balancer).

## <a name="your-first-aspnet-core-docker-app"></a>Twoja pierwsza aplikacja platformy ASP.NET Core Docker

W tym samouczku umożliwia korzystanie z aplikacji przykładowej platformy ASP.NET Core Docker dla aplikacji, którą chcemy, aby przekształcać. Ta przykładowa aplikacja platformy ASP.NET Core Docker przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla platformy ASP.NET Core z aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów systemów Linux i Windows.

Przykładowy plik Dockerfile tworzy obraz platformy Docker aplikacji dla platformy ASP.NET Core na podstawie obrazu podstawowego platformy Docker programu ASP.NET Core środowiska uruchomieniowego.

Używa ona [wieloetapowych platformy Docker, tworzenie funkcji](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) do:

* stworzyć próbkę w kontenerze, w oparciu o **większych** obraz podstawowy platformy Docker programu ASP.NET Core kompilacji 
* kopiuje wynik końcowy kompilacji do obrazu platformy Docker, na podstawie **mniejszych** obrazu podstawowego środowiska uruchomieniowego programu ASP.NET Core platformy Docker

> [!NOTE]
> Obraz kompilacji zawiera wymagane narzędzia do kompilowania aplikacji, a nie obraz środowiska uruchomieniowego.

### <a name="prerequisites"></a>Wymagania wstępne

Aby skompilować i uruchomić, należy zainstalować następujące elementy:

#### <a name="net-core-21-sdk"></a>.NET core 2.1 SDK

* Zainstaluj [platformy .NET Core SDK 2.1](https://www.microsoft.com/net/core).

* Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalowanie klienta platformy Docker

Zainstaluj [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta platformy Docker.

Klient platformy Docker można zainstalować w:

* Dystrybucje systemu Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>Instalowanie usługi Git do repozytorium przykładów

* Zainstaluj [git](https://git-scm.com/download) Jeśli chcesz sklonować repozytorium.

### <a name="getting-the-sample-application"></a>Wprowadzenie do przykładowej aplikacji

Najprostszym sposobem uzyskania próbki jest przez Sklonowanie [repozytorium Docker w programie .NET Core](https://github.com/dotnet/dotnet-docker) przy użyciu narzędzia git, przy użyciu następujących instrukcji: 

```console
git clone https://github.com/dotnet/dotnet-docker
```

Można również pobrać repozytorium (jest to mała) w formie pliku zip z repozytorium Docker w programie .NET Core.

### <a name="run-the-aspnet-app-locally"></a>Lokalne uruchamianie aplikacji platformy ASP.NET

Dla punktu odniesienia zanim będziemy konteneryzowanie aplikacji, najpierw uruchom aplikację lokalnie.

Można tworzyć i uruchom aplikację lokalnie, za pomocą zestawu .NET Core 2.1 SDK przy użyciu następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Kompilowanie i uruchamianie przykładu z platformy Docker dla kontenerów systemu Linux

Można tworzyć i uruchom aplikację przykładową na platformie Docker przy użyciu kontenerów systemu Linux przy użyciu następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` "-P" argument mapowania portu 5000 na komputerze lokalnym do portu 80 w kontenerze (formularz mapowania portów jest `host:container`). Aby uzyskać więcej informacji, zobacz [platformy docker, uruchom](https://docs.docker.com/engine/reference/commandline/exec/) odwołania dotyczące parametrów wiersza polecenia.

Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Kompilowanie i uruchamianie przykładu z kontenerów platformy Docker for Windows

Można tworzyć i uruchom aplikację przykładową na platformie Docker przy użyciu kontenerów Windows za pomocą następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Musisz przejść do **adres IP kontenera** (w przeciwieństwie do http://localhost) w przeglądarce bezpośrednio podczas korzystania z kontenerów Windows. Można uzyskać adresu IP kontenera wykonując następujące kroki:

* Otwórz innego wiersza polecenia.
* Uruchom `docker ps` Aby wyświetlić uruchomione kontenery. Kontener "aspnetcore_sample" powinny być dostępne.
* Uruchom `docker exec aspnetcore_sample ipconfig`.
* Skopiuj adres IP kontenera, a następnie wklej w przeglądarce (na przykład 172.29.245.43).

> [!NOTE]
> Docker exec obsługuje identyfikujące kontenery przy użyciu nazwy lub wyznaczania wartości skrótu. Nazwa (aspnetcore_sample) jest używana w tym przykładzie.

Zobacz poniższy przykład sposobu uzyskania adresu IP działający kontener Windows.

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
> Docker exec działa nowego polecenia w uruchomionego kontenera. Aby uzyskać więcej informacji, zobacz [odwołania exec docker](https://docs.docker.com/engine/reference/commandline/exec/) dotyczące parametrów wiersza polecenia.

Służy do tworzenia aplikacji, która jest gotowa do wdrożenia w środowisku produkcyjnym lokalnie przy użyciu [publikowania dotnet](../tools/dotnet-publish.md) polecenia.

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> - C argument wersji kompilacji aplikacji w trybie wydania (wartość domyślna to tryb debugowania). Aby uzyskać więcej informacji, zobacz [dotnet Uruchom odwołanie](../tools/dotnet-run.md) dotyczące parametrów wiersza polecenia.

Aplikację można uruchomić na **Windows** przy użyciu następującego polecenia.

```console
dotnet published\aspnetapp.dll
```

Aplikację można uruchomić na **Linux** lub **macOS** przy użyciu następującego polecenia.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Obrazy platformy docker, używane w tym przykładzie

Następujące obrazy platformy Docker są używane w tym przykładowego pliku dockerfile.

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

Gratulacje! masz tylko:
> [!div class="checklist"]
> * Przedstawia informacje na temat obrazów platformy Docker programu Microsoft .NET Core
> * Otrzymano przykładową aplikację w celu Dockerize platformy ASP.NET Core
> * Lokalnie uruchomiono przykładową aplikację platformy ASP.NET
> * Wbudowane i uruchomiono przykład za pomocą platformy Docker dla kontenerów systemu Linux
> * Wbudowane i uruchomiono przykład za pomocą kontenerów platformy Docker for Windows

**Następne kroki**

Poniżej przedstawiono niektóre kolejne kroki, które należy wykonać:

* [Praca z narzędzia Docker programu Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Wdrażanie obrazów platformy Docker z rejestru kontenerów platformy Azure w usłudze Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Debugowanie za pomocą programu Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Praktycznym doświadczeniu z programem Visual Studio dla komputerów Mac, kontenerów i kod bez użycia serwera w chmurze](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Wprowadzenie do platformy Docker i programu Visual Studio dla komputerów Mac laboratorium](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się dzisiaj](https://azure.microsoft.com/free/?b=16.48) bezpłatne konto 30-dniowej i Odbierz 200 USD środków na korzystanie z platformy Azure możesz wypróbować dowolną kombinację usług platformy Azure.
