---
title: Wdrażanie pojedynczego kontenera na podstawie aplikacji sieci Web programu .NET Core w systemie Linux lub Windows hostami Nano Server
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wdrażanie pojedynczego kontenera na podstawie aplikacji sieci Web programu .NET Core w systemie Linux lub Windows hostami Nano Server
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 56c41a51cddeca6c74b09710f9536195a6a88904
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404502"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Wdrażanie aplikacji sieci Web opartych na kontenerach pojedynczego .NET Core hosty z systemem Linux lub Windows Nano Server

_Korzystaj z kontenerów platformy Docker, monolitycznych wdrożenia aplikacji sieci web, prostsze. Zwiększa to ciągłej integracji i ciągłego wdrażania potoków i pomaga osiągnąć sukces wdrażania do produkcji. Nie ma więcej "działa w mojej maszynie, dlaczego nie działa w środowisku produkcyjnym?"_

Architektura mikrousług ma wiele zalet, ale te korzyści pochodzą kosztem wzrostu złożoności. W niektórych przypadkach koszty przeważają korzyści i aplikacji monolitycznych wdrożenia, działających w kontenerach jednego lub kilku jest lepszym rozwiązaniem.

Aplikacji monolitycznej może nie być w prosty sposób decomposable na mikrousługi dobrze rozdzielone. Wiesz, że takich mikrousług powinny być dzielone przez funkcję: powinno działają niezależnie od siebie, aby zapewnić lepszą odporność aplikacji. Jeśli nie można dostarczyć wycinki funkcji aplikacji, oddzielając tylko zwiększa złożoność.

Aplikacja nie może jeszcze wymagać niezależne przeskalowywanie się funkcje. Załóżmy, że we wczesnych etapach `eShopOnContainers` odwoływać się do aplikacji, ruch nie uzasadnienie, oddzielając funkcje na różne mikrousługi. Ruch był wystarczająco mała, zazwyczaj Dodawanie zasobów do jednej usługi przeznaczone dodawania zasobów do wszystkich usług. Dodatkowej pracy do rozdzielania aplikacji na osobne usługi udostępniane minimalny korzyści.

Ponadto na wczesnym etapie tworzenia aplikacji możesz nie mieć dalsze których naturalnych funkcjonalności. Podczas opracowywania minimalne produktu możliwego do użycia fizyczne rozdzielenie może nie jeszcze związane.

Niektóre z tych warunków, mogą być tymczasowe. Może rozpocząć od utworzenia aplikacji monolitycznej, a później oddzielić niektórymi funkcjami, które zostaną wdrożone i wdrażane jako mikrousług. Inne warunki mogą być niezbędne do przestrzeni problem aplikacji, co oznacza, że aplikacja może nigdy nie można podzielić na wiele mikrousług.

Oddzielenie aplikacji w wielu procesach dyskretnych wprowadza również obciążenie. Istnieje więcej złożoności w podziale funkcji w różnych procesach. Protokoły komunikacyjne są coraz bardziej złożone. Zamiast wywołania metody należy użyć komunikacji asynchronicznej między usługami. Po przeniesieniu do architektury mikrousług, musisz dodać wiele bloków konstrukcyjnych zaimplementowane w wersji mikrousług `eShopOnContainers` aplikacji: Obsługa magistrali zdarzeń, odporności komunikat i ponownych prób i spójności ostatecznej.

Nieco bardzo uproszczony w ramach aplikacji eShopOnContainers (o nazwie [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) i zawarte w tym samym repozytorium GitHub) jest uruchamiana jako monolityczny aplikacji MVC. Zgodnie z opisem, istnieją korzyści oferowane przez ten uzasadnienie wyboru tych elementów. Można pobrać źródła dla tej aplikacji z witryny GitHub i uruchomić go lokalnie. Nawet tej aplikacji monolitycznej korzysta z wdrażana w środowisku kontenera.

Do jednego wdrażania konteneryzowanych oznacza, że każde wystąpienie aplikacji działa w tym samym środowisku. Dotyczy to również Środowisko deweloperskie, gdzie odbywać się wcześnie środowisk testowych i programistycznych. Zespół opracowujący można uruchomić aplikację w środowisku konteneryzowanych, który odpowiada środowisku produkcyjnym.

Ponadto konteneryzowanych aplikacji skalowanie przy niskich kosztach. Jak wcześniej, środowisko kontenerów umożliwia udostępnianie niż tradycyjnych środowisk maszyny Wirtualnej większą zasobów.

Na koniec konteneryzowania aplikacji powoduje oddzielenie logiki biznesowej i storage server. Ponieważ aplikacja jest skalowana w poziomie, różnych kontenerów zostanie wszystkie polegają na średni jednego magazynu fizycznego. Ten magazyn zwykle są wysokiej dostępności serwera z systemem bazy danych programu SQL Server.

## <a name="application-tour"></a>Samouczek aplikacji

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) aplikacji reprezentuje część aplikacji ramach aplikacji eShopOnContainers, uruchomione jako aplikacji monolitycznej — oparte na programie ASP.NET Core MVC aplikacji uruchomionej na platformie .NET Core. Zapewnia przede wszystkim katalogu przeglądania zgodnie z opisem we wcześniejszych sekcjach.

Aplikacja korzysta z bazy danych programu SQL Server do przechowywania katalogu. W przypadku wdrożeń opartych na kontenerach ta aplikacja monolityczna dostęp tego samego magazynu danych jako aplikacji opartych na mikrousługach. Aplikacja jest skonfigurowana do uruchamiania programu SQL Server w kontenerze obok aplikacji monolitycznej. W środowisku produkcyjnym programu SQL Server może działać na komputerze o wysokiej dostępności, poza hosta platformy Docker. Dla wygody w środowisku deweloperskim lub testowym zalecane jest uruchomienie programu SQL Server we własnym kontenerze.

Funkcja początkowej tylko zestaw umożliwia przeglądanie katalogu. Aktualizacje umożliwiłby pełny zestaw funkcji konteneryzowanych aplikacji. A bardziej zaawansowane Architektura aplikacji monolitycznych w sieci web jest opisana w [rozwiązania architektury aplikacji sieci Web ASP.NET](https://aka.ms/webappebook) e booka i powiązane [eShopOnWeb przykładowej aplikacji](http://aka.ms/WebAppArchitecture).

## <a name="docker-support"></a>Obsługę platformy docker

Projekt eShopOnWeb działa na platformie .NET Core. Oznacza to, że może działać w kontenerach opartych na systemie Linux albo systemem Windows. Należy pamiętać, wdrożenie platformy Docker, chcesz używać tego samego typu hosta dla programu SQL Server. Kontenery opartych na systemie Linux Zezwalaj na mniejszych rozmiarów i są preferowane.

Visual Studio zawiera szablon projektu, który dodaje obsługę platformy Docker do rozwiązania. Kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj** następuje **obsługę platformy Docker**. Szablon dodaje plik Dockerfile do swojego projektu i nową **narzędzia docker compose** projektu, który zawiera moduł uruchamiający *docker-compose.yml* pliku. Ten krok ma jeszcze nie zostały otwarte w projekcie eShopOnWeb pobierane z usługi GitHub. Widać, że rozwiązanie zawiera **eShopOnWeb** projektu i **narzędzia docker compose** projektu, jak pokazano w rysunek 6-1.

![](./media/image1.png)

**Rysunek 6-1**. **Narzędzia docker compose** projektu w aplikacji sieci web jednym kontenerze

Te pliki są standardowe docker-compose pliki zgodne z jakimkolwiek projektem platformy Docker. Można je za pomocą programu Visual Studio lub z wiersza polecenia. Ta aplikacja działa na platformie .NET Core i używa kontenerów systemu Linux. Tak użytkownik może również kodu, kompilacji i ją uruchomić na komputerze Mac lub na maszynie z systemem Linux.

*Docker-compose.yml* plik zawiera informacje o jakie obrazy do tworzenia i jakie kontenery do uruchomienia. Szablony określają sposób tworzenia `eshopweb` obrazów i uruchamiaj kontenery aplikacji. Należy dodać zależności w programie SQL Server przy tym obrazu (na przykład `mssql-server-linux`), a usługą sql.data obrazu platformy Docker skompilować i uruchomić tego kontenera. Te ustawienia zostały pokazane w poniższym przykładzie:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

`depends_on` Dyrektywy informuje platformy Docker, że obraz eShopWeb zależy od obrazu sql.data. Poniższe wiersze `depends_on` znajdują się instrukcje, aby skompilować obraz oznaczony `sql.data` przy użyciu `microsoft/mssql-server-linux` obrazu.

**Narzędzia docker compose** projektu zawiera inne pliki docker-compose pod głównym *docker-compose.yml* węzeł, aby zapewnić wizualne wskazanie, że te pliki są ze sobą powiązane. *Docker-compose-override.yml* plik zawiera ustawienia dla obu usług, takich jak parametry połączenia i inne ustawienia aplikacji.

W poniższym przykładzie przedstawiono *docker compose.vs.debug.yml* pliku, który zawiera ustawienia używane do debugowania w programie Visual Studio. W tym pliku obrazu eshopweb ma tag dev dołączone do niego. Czy pomaga oddzielić debugowania z obrazów w wersji, tak, aby informacje o debugowaniu nie przypadkowo wdrożono w środowisku produkcyjnym:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

Ostatni plik, dodawane jest *docker-compose.ci.build.yml*. Ten plik, będzie używany z wiersza polecenia do tworzenia projektów z serwera ciągłej integracji. Ten plik compose uruchamia kontener platformy Docker, która tworzy obrazy potrzebne dla aplikacji. W poniższym przykładzie pokazano zawartość *docker-compose.ci.build.yml* pliku:

```yml
version: '2'

services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

> [!NOTE]
> Począwszy od programu .NET Core SDK 2.0, [dotnet restore](../../../core/tools/dotnet-restore.md) polecenie jest wykonywane automatycznie po [publikowania dotnet](../../../core/tools/dotnet-publish.md) jest wykonywany.

Należy zauważyć, że obraz jest obrazem kompilacji platformy ASP.NET Core. Ten obraz zawiera narzędzia zestawu SDK i kompilacji, aby skompilować aplikację i utworzyć wymagane obrazy. Uruchamianie **narzędzia docker compose** projektu przy użyciu tego pliku uruchamia kontener kompilacji z obrazu, a następnie tworzy obraz swojej aplikacji, w tym kontenerze. Możesz określić, że *docker-compose* pliku jako część wiersza polecenia, aby skompilować aplikację w kontenerze platformy Docker, a następnie uruchom go.

W programie Visual Studio, można uruchomić aplikację w kontenerach platformy Docker, wybierając **docker-compose** projekt jako projekt startowy, a następnie naciskając klawisze Ctrl + F5 (F5, aby debugować), jak w przypadku innych aplikacji. Po uruchomieniu **narzędzia docker compose** projektu Visual Studio będzie działać **narzędzia docker compose** przy użyciu *docker-compose.yml* pliku  *docker-compose.override.yml* plików i z platformy docker — compose.vs.\* plików. Po rozpoczęciu aplikacji Visual Studio otworzy w przeglądarce dla Ciebie.

Jeśli uruchamianie aplikacji w debugerze programu Visual Studio dołącza do uruchomionej aplikacji na platformie Docker.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

W tej sekcji opisano kilka kwestii, które mogą wystąpić podczas uruchamiania kontenerów lokalnie, a także sugeruje kilka poprawek.

### <a name="stop-docker-containers"></a>Zatrzymaj kontenerów platformy Docker

Po uruchomieniu konteneryzowanych aplikacji, kontenerów w dalszym ciągu działać po zatrzymaniu debugowania. Możesz uruchomić `docker ps` polecenie w wierszu polecenia, aby zobaczyć, kontenery, które są uruchomione. `docker stop` Polecenie zatrzymuje działający kontener, jak pokazano w rysunek 6-2.

![](./media/image2.png)

**Rysunek 6-2**. Wyświetlanie listy i zatrzymywanie kontenerów przy użyciu platformy docker ps i interfejsu wiersza polecenia platformy docker stop

Może być konieczne zatrzymanie procesów podczas przełączania między różne konfiguracje. W przeciwnym razie kontenera, w którym działa aplikacja sieci web jest używany port dla swojej aplikacji (5106 w tym przykładzie).

### <a name="add-docker-to-your-projects"></a>Dodaj platformy Docker do swoich projektów

Kreator, który dodaje obsługę platformy Docker komunikuje się z uruchomionego procesu platformy Docker. Jeśli platformy Docker nie jest uruchomiona, po uruchomieniu kreatora, Kreator nie będzie działać poprawnie. Kreator sprawdza, czy bieżący wybór kontenera można dodać poprawną obsługę platformy Docker. Aby dodać obsługę kontenerów Windows, należy uruchomić kreatora, masz uruchomiony za pomocą kontenerów Windows skonfigurowane platformy Docker. Aby dodać obsługę kontenerów systemu Linux, uruchom kreatora, kiedy masz platformy Docker z kontenerów systemu Linux skonfigurowany.

>[!div class="step-by-step"]
[Poprzednie](../docker-application-development-process/docker-app-development-workflow.md)
[dalej](../containerize-net-framework-applications/index.md)
