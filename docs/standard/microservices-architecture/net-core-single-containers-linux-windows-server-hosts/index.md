---
title: Wdrażanie jeden kontener na podstawie aplikacji sieci Web .NET Core hosty z systemem Linux lub Windows Nano Server
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wdrażanie jeden kontener na podstawie aplikacji sieci Web .NET Core hosty z systemem Linux lub Windows Nano Server
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f429bc0c6e76c2be2e4f491768a15ab36ecb0d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591097"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Wdrażanie aplikacji sieci Web hosty z systemem Linux lub Windows Nano Server jeden kontener na podstawie .NET Core

*Kontenery Docker można użyć wdrożenia wbudowanymi prostsze aplikacji sieci web. Zwiększa to ciągłej integracji i ciągłe wdrażanie potoków i pomaga osiągnąć sukces wdrożenia do produkcji. Brak "działa w komputerze, dlaczego nie działa w środowisku produkcyjnym?"*

Architektura mikrousług ma wiele korzyści, ale pochodzą te korzyści kosztem zwiększenia złożoności. W niektórych przypadkach koszty przeważają korzyści i będzie można lepiej obsłużone z aplikacją wbudowanymi wdrożenia uruchomiona w kontenerze jednego lub kilku kontenerów. 

Wbudowanymi aplikacji nie może być łatwo decomposable w dobrze rozdzielonych mikrousług. Wiesz już, że powinno być partycjonowane przez funkcję: mikrousług powinny działać niezależnie od siebie, aby zapewnić bardziej elastyczne aplikacji. Nie można dostarczyć wycinków funkcji aplikacji, tylko on oddzielenie dodaje złożoności.

Aplikacja może jeszcze nie można skalować niezależnie funkcji. Załóżmy, że na początku życia aplikacji odwołanie eShopOnContainers ruch nie uzasadnia rozdzielić funkcje różnych mikrousług. Ruch jest duże, dodawanie zasobów do jednej usługi zazwyczaj przeznaczone Dodawanie zasobów do wszystkich usług. Dodatkowe czynności w celu rozdzielenia aplikacji do usług odrębny podać asysta minimalne.

Ponadto na początku tworzenia aplikacji możesz utracić dalsze skutkującej naturalne granice funkcjonalności. Podczas opracowywania minimalna produktu działało fizyczne rozdzielenie może nie jeszcze związane.

Niektóre z tych warunków mogą być tymczasowe. Może być Rozpocznij od utworzenia wbudowanymi aplikacji, a później rozdzielić niektóre funkcje, które mają być opracowane i wdrożony jako mikrousług. Inne warunki mogą być niezbędne do przestrzeni problem aplikacji, co oznacza, że aplikacja może nigdy nie można podzielić na wiele mikrousług.

Oddzielanie aplikacji do wielu procesów odrębny wprowadza również koszty. Jest bardziej złożona rozdzielić funkcje różnych procesów. Protokoły komunikacji staną się bardziej złożonych. Zamiast wywołania metody należy użyć komunikacji między usługami. W przypadku przejścia do architektury mikrousług, musisz dodać wiele bloków konstrukcyjnych w wersji mikrousług aplikacji eShopOnContainers: Obsługa magistrali zdarzeń, komunikatu odporności i ponownych prób i spójność ostateczna.

Uproszczone bardzo wersji eShopOnContainers (o nazwie [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) i zawarte w tym samym repozytorium GitHub) działają jako wbudowanymi aplikacji MVC i jak tylko opisane, istnieją korzyści wynikających z tego wyboru projektu. Można pobrać źródła dla tej aplikacji z usługi GitHub i uruchom lokalnie. Nawet wbudowanymi aplikacja korzysta z wdrożenia w środowisku kontenera.

Dla jednego wdrażania konteneryzowanych oznacza, że każde wystąpienie aplikacji jest uruchamiany w tym samym środowisku. Dotyczy to również środowiska deweloperskiego, w którym odbywa się wcześniej testowania i rozwoju. Zespół deweloperów można uruchomić aplikację w środowisku konteneryzowanych pasującą do środowiska produkcyjnego.

Ponadto konteneryzowanych aplikacji skalowania w poziomie na niższe koszty. Jak przedstawiono wcześniej, środowiska kontenera umożliwia udostępnianie niż tradycyjnych środowisk maszyny Wirtualnej większą zasobów.

Na koniec containerizing aplikacja wymusza oddzielenie logiki biznesowej i storage server. Jak aplikacja skaluje się, wiele kontenerów będzie wszystkie używana na nośniku jednego magazynu fizycznego. Zazwyczaj powinien to być serwerem wysokiej dostępności bazy danych programu SQL Server.

## <a name="application-tour"></a>Samouczek aplikacji

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) aplikacji reprezentuje część aplikacji eShopOnContainers uruchomiona jako aplikacja wbudowanymi — aplikacji ASP.NET MVC rdzeni na podstawie uruchomionej na .NET Core. Zapewnia on głównie katalogu Przeglądanie możliwości, które firma Microsoft opisano we wcześniejszych sekcjach.

Aplikacja używa bazy danych programu SQL Server do przechowywania katalogu. W przypadku wdrożeń na podstawie kontenera ta wbudowanymi dostęp aplikacji tego samego magazynu danych jako aplikacji opartej na mikrousług. Aplikacja jest skonfigurowana do uruchamiania programu SQL Server w kontenerze równolegle z wbudowanymi aplikacji. W środowisku produkcyjnym programu SQL Server może działać na maszynie wysokiej dostępności, poza hostów Docker. Dla wygody w środowisku deweloperów lub testowym zaleca się programem SQL Server w jego własnej kontenera.

Funkcja początkowej ustawiona tylko umożliwia przeglądanie katalogu. Aktualizacje umożliwiłyby pełny zestaw funkcji konteneryzowanych aplikacji. A bardziej zaawansowane Architektura aplikacji sieci web wbudowanymi jest opisany w [aplikacji sieci Web ASP.NET architektura rozwiązań](https://aka.ms/webappebook) Książka elektroniczna i pokrewnych [eShopOnWeb przykładowej aplikacji](http://aka.ms/WebAppArchitecture), mimo że w takim przypadku nie działa na kontenery Docker ponieważ w tym scenariuszu skupiono się na projektowanie zwykłych witryn sieci web z platformy ASP.NET Core.

Jednak uproszczonej wersji dostępnej w eShopOnContainers (eShopWeb) uruchamia się w kontenerze Docker.

## <a name="docker-support"></a>Obsługa docker

Projekt eShopOnWeb działa na .NET Core. W związku z tym można go uruchomić w kontenerach opartych na systemie Linux albo systemem Windows. Uwaga dla wdrożenia Docker chcesz używać tego samego typu hosta dla programu SQL Server. Kontenery opartych na systemie Linux Zezwalaj na mniejsze zużycie i są preferowane.

Program Visual Studio udostępnia szablon projektu, który dodaje obsługę Docker do rozwiązania. Kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj** następuje **Obsługa Docker**. Szablon dodaje plik Dockerfile do projektu, a nowy **rozwiązania docker compose** projektu, który zawiera plik docker-compose.yml początkowego. W tym kroku została już wykonana w projekcie eShopOnWeb pobrać z witryny GitHub. Zobaczysz, że rozwiązanie zawiera **eShopOnWeb** projektu i **rozwiązania docker compose** projektu, jak pokazano w rysunek 6-1.

![](./media/image1.png)

**Rysunek 6-1**. **Rozwiązania docker compose** projektu w aplikacji sieci web jednym kontenera

Te pliki są standard docker — pliki zgodne z żadnym projekcie rozwiązania Docker compose. Można używać ich z programem Visual Studio lub z wiersza polecenia. Ta aplikacja .NET Core, korzysta kontenery systemu Linux, również kodu, tworzenia i uruchamiania na komputerze Mac lub na komputerze z systemem Linux.

Plik docker-compose.yml zawiera informacje o jakie obrazy do tworzenia i jakie kontenerów do uruchomienia. Szablony określ w jaki sposób utworzyć obraz eshopweb i uruchamianie kontenerów aplikacji. Konieczne jest dodanie zależności w programie SQL Server w tym obrazie (na przykład mssql serwera linux), a usługą obrazu sql.data Docker skompilować i uruchomić tego kontenera. W poniższym przykładzie przedstawiono te ustawienia:

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

Zależy od\_w dyrektywie informuje Docker że obrazu eShopWeb zależy od sql.data obrazu. Poniższe wiersze, które są z instrukcjami, aby utworzyć obraz oznakowane sql.data przy użyciu obrazu microsoft/mssql-server-linux.

**Rozwiązania docker compose** projektu zawiera inne pliki docker-compose w węźle głównym docker-compose.yml do wskazywania stanu dotyczące tych plików. Plik docker tworzą override.yml zawiera ustawienia dla obu usług, takich jak parametry połączenia i inne ustawienia aplikacji.

W poniższym przykładzie przedstawiono plik docker-compose.vs.debug.yml, który zawiera ustawienia używane na potrzeby debugowania w programie Visual Studio. W tym pliku obrazu eshopweb ma tag deweloperów, dołączone do niego. Czy pomaga oddzielić debugowania z wersji obrazów, aby nie przypadkowo wdrażać informacje debugowania w środowisku produkcyjnym:

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

Ostatni plik dodany jest docker compose.ci.build.yml. Czy można użyć w wierszu polecenia do tworzenia projektów z serwera konfiguracji. Ten plik Redaguj uruchamia kontener Docker, który tworzy obrazy wymagane dla aplikacji. W poniższym przykładzie przedstawiono zawartość pliku docker compose.ci.build.yml.

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

**Uwaga**: począwszy od programu .NET Core 2.0 polecenia restore dotnet wykonywane automatycznie, gdy publikowanie dotnet jest wykonywana.

Należy zauważyć, że obraz jest obrazem kompilacji platformy ASP.NET Core. Ten obraz zawiera zestawu SDK i kompilacji narzędzia do tworzenia aplikacji i utworzyć wymagane obrazy. Uruchomiona **rozwiązania docker compose** projektu przy użyciu tego pliku kontenera kompilacji jest uruchamiany z obrazu, a następnie tworzy obraz aplikacji, w tym kontenerze. Określ ten docker-utworzenie pliku jako część wiersza polecenia, aby skompilować aplikację w kontenerze Docker, a następnie uruchomić go.

W programie Visual Studio, wybierając można uruchomić aplikacji w kontenerach Docker **docker-tworzą** projekt jako projekt startowy, a następnie nacisnąć klawisze Ctrl + F5 (F5, aby debugować), jak w przypadku innych aplikacji. Po rozpoczęciu **rozwiązania docker compose** projektu, działanie programu Visual Studio **rozwiązania docker compose** przy użyciu plik docker-compose.yml, plik docker-compose.override.yml i jedną docker compose.vs.\* pliki. Po uruchomieniu aplikacji, Visual Studio spowoduje uruchomienie przeglądarki dla Ciebie.

Jeśli uruchamianie aplikacji w debugerze programu Visual Studio będzie Dołącz do uruchomionej aplikacji w Docker.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

W tej sekcji opisano kilka problemów, które mogą wystąpić podczas wykonywania kontenery lokalnie, a także sugeruje niektóre poprawki.

### <a name="stopping-docker-containers"></a>Zatrzymywanie kontenery Docker 

Po uruchomieniu aplikacji konteneryzowanych kontenery w dalszym ciągu działać po zatrzymaniu debugowania. Polecenie ps docker można uruchomić z wiersza polecenia, aby wyświetlić kontenery, które są uruchomione. Polecenie zatrzymania docker Zatrzymuje uruchomione kontenera, jak pokazano na rysunku 6-2.

![](./media/image2.png)

**Rysunek 6-2**. Wyświetlanie i zatrzymywanie kontenery docker ps i docker zatrzymać polecenia interfejsu wiersza polecenia

Konieczne może być Zatrzymaj uruchomione procesy, podczas przełączania się między różne konfiguracje. W przeciwnym razie kontenera, w którym działa aplikacja sieci web używającej portu dla aplikacji (5106 w tym przykładzie).

### <a name="adding-docker-to-your-projects"></a>Dodawanie do projektów platformy Docker

Kreator dodaje obsługę Docker komunikuje się z uruchomionym procesem Docker. Kreator nie będzie działać poprawnie Docker nie jest uruchomiony podczas uruchamiania kreatora. Ponadto Kreator sprawdza, czy bieżący wybór kontenera dodać poprawną obsługę Docker. Aby dodać obsługę kontenery systemu Windows, należy uruchomić kreatora, gdy masz Docker z kontenerów systemu Windows skonfigurowane. Jeśli chcesz dodać obsługę systemu Linux kontenerów, uruchom kreatora podczas Docker z kontenerów Linux skonfigurowany.

>[!div class="step-by-step"]
[Poprzednie] (.. / docker-application-development-process/docker-app-development-workflow.md) [dalej] (.. /containerize-NET-Framework-Applications/index.MD)
