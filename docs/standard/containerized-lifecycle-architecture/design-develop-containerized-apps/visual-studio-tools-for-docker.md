---
title: Visual Studio Tools for Docker on Windows
description: Ustal, jakimi narzędzi platformy Docker, dostępnych w programie Visual Studio 2017 w wersji 15.7 lub nowszej.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 78ea3e553e4e449b307bc3585ed66fa48d2c0d8e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680363"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017 na Windows

Przepływu pracy dewelopera, podczas korzystania z narzędzi platformy Docker, zawarte w programie Visual Studio 2017 wersji 15.7 lub nowszej, jest podobny do przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia Docker (w rzeczywistości opiera się na tym samym interfejsu wiersza polecenia platformy Docker), ale je łatwiej rozpocząć pracę, upraszcza ten proces i zapewnia większą produktywność dla kompilacji, uruchom i redagowania zadań. Można również uruchamiać i debugować swoje kontenery za pomocą zwykłego `F5` i `Ctrl+F5` kluczy z poziomu programu Visual Studio. Można nawet debugowanie całego rozwiązania, jeśli jego kontenerów są zdefiniowane w tym samym `docker-compose.yml` pliku na poziomie rozwiązania.

## <a name="configure-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Za pomocą najnowszych wersji platformy Docker for Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker ponieważ Instalator jest proste, jak wyjaśniono w następujących odwołań.

> [! Informacje o] Dowiedz się więcej o instalowaniu platformy Docker for Windows, przejdź do (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Obsługę platformy docker w programie Visual Studio 2017

Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu. W projektach ASP.NET Core, można po prostu dodać `Dockerfile` pliku do projektu, należy włączyć obsługę platformy Docker. Następny poziom to obsługa aranżacji kontenerów, który dodaje `Dockerfile` do projektu (jeśli jeszcze nie istnieje) i `docker-compose.yml` pliku na poziomie rozwiązania. Obsługa aranżacji kontenerów przy użyciu narzędzia Docker Compose jest dodawany domyślnie Visual Studio 2017 w wersji 15.0 wersji 15.7. Obsługa aranżacji kontenerów to funkcja opcjonalna w wersjach programu Visual Studio 2017, należy zachować 15,8 lub nowszej. Wersja 15.8 wiadomość później obsługuje narzędzia Docker Compose i Service Fabric.

**Dodaj > obsługę platformy Docker** i **Dodaj > Obsługa Orkiestratora kontenerów** polecenia znajdują się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu platformy ASP.NET Core w  **Eksplorator rozwiązań**, jak pokazano w rysunek 4-31:

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](./media/add-docker-support-menu.png)

**Rysunek 4-31**. Dodawanie obsługi platformy Docker do projektu programu Visual Studio 2017

### <a name="add-docker-support"></a>Dodaj obsługę platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu platformy ASP.NET Core, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**. Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, które jest otwierane po kliknięciu **OK** w **nowy projekt** okno dialogowe, jak pokazano w rysunek 4-32.

![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

**Rysunek 4-32**. Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017

Podczas dodawania lub Włącz obsługę platformy Docker, program Visual Studio dodaje *pliku Dockerfile* pliku do projektu.

> [!NOTE]
> Po włączeniu obsługi narzędzia Docker Compose podczas tworzenia projektu dla projektu platformy ASP.NET (.NET Framework, nie w projekcie platformy .NET Core), jak pokazano w rysunek 4-33, dodawany jest również obsługa aranżacji kontenerów.

![Włącz Docker compose obsługę projektu programu ASP.NET](media/enable-docker-compose-support.png)

**Rysunek 4-33**. Włączanie obsługi narzędzia Docker Compose projektu programu ASP.NET w programie Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Dodanie obsługi aranżacji kontenerów

Do tworzenia rozwiązania wielu kontenerów, należy dodać Obsługa aranżacji kontenerów do swoich projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku.

Aby dodać obsługę aranżacji kontenerów, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj > kontener obsługuje aranżacji**. Następnie wybierz **narzędzia Docker Compose** lub **usługi Service Fabric** Zarządzanie kontenerów.

Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz plik Dockerfile dodane do projektu i **narzędzia docker compose** dodawany do rozwiązania w folderze **Eksploratora rozwiązań**, jak pokazano w rysunek 4-34:

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

**Rysunek 4-34**. Pliki docker w Eksploratorze rozwiązań w programie Visual Studio 2017

Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.

## <a name="configure-docker-tools"></a>Konfigurowanie narzędzi platformy Docker

W menu głównym wybierz **Narzędzia > Opcje**i rozwiń **narzędzia kontenerów > Ustawienia**. Ustawienia narzędzia kontenerów są wyświetlane.

![Visual Studio platformy Docker narzędzia Opcje przedstawiający: Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu, automatycznie uruchom kontenery w tle, automatycznie kill kontenerów na Zamknij rozwiązanie i nie Monituj o ufanie certyfikatu SSL.](./media/visual-studio-docker-tools-options.png)

**Rysunek 4 – 35**. Docker Tools Options

Poniższa tabela może pomóc zdecydować, jak ustawić te opcje.

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | On | Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów programu Visual Studio rozpocznie operacji ściągania aparatu Docker w tle, tak, aby gdy wszystko będzie gotowe uruchomić kod, obraz, który został już pobrany, lub w trakcie pobierania. Jeśli właśnie trwa ładowanie projektów i przeglądania kodu, możesz Wyłącz tę opcję, aby uniknąć pobierania obrazów kontenerów, które nie są potrzebne. |
| Automatycznie uruchom kontenery w tle | On | Docker Compose | Ponownie do zwiększenia wydajności programu Visual Studio tworzy kontener z instaluje wolumin gotowy do podczas kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować, po utworzeniu kontenera, wyłącz tę opcję. |
| Automatycznie zabij kontenery rozwiązanie, zamknij | On | Docker Compose | Wyłącz tę opcję, jeśli chcesz kontenerów do rozwiązania w celu będą nadal działać po zamknięcie rozwiązania lub zamknięcia programu Visual Studio. |
| Nie monituj o zaufanie certyfikatowi protokołu SSL | Off | Projekty ASP.NET Core 2.1 | Jeśli certyfikatowi protokołu SSL nie jest zaufany, Visual Studio wyświetli monit o za każdym razem, gdy uruchamiasz projekt, chyba że to pole wyboru jest zaznaczone. |

> [!WARNING]
> Jeśli certyfikatowi protokołu SSL nie jest zaufany, a następnie zaznacz odpowiednie pole, aby pominąć monit, żądań sieci web protokołu HTTPS może przestać działać w czasie wykonywania aplikacji lub usługi. W takim przypadku usuń zaznaczenie pola wyboru **nie Monituj** zaznacz pole wyboru Uruchom projekt i wskazać zaufania w wierszu.

> [! Informacje o] Aby uzyskać więcej informacji o implementacji usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:
>
>Debugowanie aplikacji w lokalnym kontenerze Docker: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Wdrażanie kontenera platformy ASP.NET do rejestru kontenerów przy użyciu programu Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Poprzednie](docker-apps-inner-loop-workflow.md)
>[dalej](set-up-windows-containers-with-powershell.md)
