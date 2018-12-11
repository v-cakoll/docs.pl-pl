---
title: Visual Studio Tools for Docker na Windows
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: 79e9b5cc9bac317a368583013abbc5124ef2c9ac
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151216"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio Windows)

Visual Studio Tools dla przepływu pracy tworzenia oprogramowania platformy Docker jest podobny do przepływu pracy, podczas korzystania z programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker. W rzeczywistości opiera się na tym samym interfejsu wiersza polecenia platformy Docker, ale jest łatwiej rozpocząć pracę, upraszcza ten proces i zapewnia większą produktywność dla kompilacji, uruchom i redagowania zadań. Wykonywanie i Debuguj swoje kontenery za pomocą prostego akcji, takich jak **F5** i **Ctrl**+**F5**. Dzięki obsłudze aranżacji opcjonalny kontener, oprócz możliwości uruchamiać i debugować jeden kontener można uruchomić i debugować grupę kontenerów (całe rozwiązanie), w tym samym czasie.

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w Windows, a nie programu Visual Studio dla komputerów Mac.

## <a name="configure-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Najnowsze wersje platformy Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), proste Instalatora ułatwia tworzenie aplikacji platformy Docker.

Obsługę platformy docker znajduje się w programie Visual Studio 2017. Pobierz program Visual Studio 2017 w tym miejscu: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017

Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu. W projektach aplikacji sieci web platformy .NET Core, można po prostu dodać *pliku Dockerfile* pliku do projektu, należy włączyć obsługę platformy Docker. Następny poziom to obsługa aranżacji kontenerów, który dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i *docker-compose.yml* pliku na poziomie rozwiązania. W Visual Studio 2017 w wersji 15.7 lub wcześniejszej domyślnie zostanie dodana jego obsługa aranżacji kontenerów, za pomocą narzędzia Docker Compose. Obsługa aranżacji kontenerów to funkcja opcjonalna w wersjach programu Visual Studio 2017 15.8 lub później, w którym to przypadku narzędzia Docker Compose i Service Fabric są obsługiwane.

**Dodaj** > **obsługę platformy Docker** i **Dodaj** > **aranżacji kontenerów pomocy technicznej** polecenia są znajduje się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu aplikacji sieci web w **Eksploratora rozwiązań**, jak pokazano w rysunek 4-26:

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](media/add-docker-support-menu.png)

Rysunek 4-26: Dodawanie obsługi platformy Docker do projektu programu Visual Studio 2017

### <a name="add-docker-support"></a>Dodaj obsługę platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu aplikacji sieci web platformy .NET Core, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**. Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, które jest otwierane po kliknięciu **OK** w **nowy projekt** okno dialogowe, jak pokazano w rysunek 4-27.

![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

Ilustracja 4-27 Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017

Podczas dodawania lub Włącz obsługę platformy Docker, program Visual Studio dodaje *pliku Dockerfile* pliku do projektu.

> [!NOTE]
> Po włączeniu obsługi narzędzia Docker Compose podczas tworzenia projektu dla projektu aplikacji sieci web .NET Framework (nie platformy .NET Core projektu aplikacji sieci web), jak pokazano w rysunek 4-28, dodawany jest również obsługa aranżacji kontenerów.
>
> ![Włącz Docker compose obsługę projektu aplikacji sieci web w języku .NET Framework](media/enable-docker-compose-support.png)

> Ilustracja 4-28 Włączanie obsługi narzędzia Docker Compose w projekcie aplikacji sieci web .NET Framework w programie Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Dodanie obsługi aranżacji kontenerów

Do łączenia z wieloma kontenerami w celu rozwiązania, należy dodać Obsługa aranżacji kontenerów do swoich projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku.

Aby dodać obsługę aranżacji kontenerów, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj** > **kontener aranżacji obsługuje**. Następnie wybierz **narzędzia Docker Compose** lub **usługi Service Fabric** Zarządzanie kontenerów.

Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz plik Dockerfile dodane do projektu i **narzędzia docker compose** dodawany do rozwiązania w folderze **Eksploratora rozwiązań**, jak pokazano w rysunek 4-29:

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

Rysunek 4-29: Pliki docker w Eksploratorze rozwiązań w programie Visual Studio 2017

Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.

## <a name="configure-docker-tools"></a>Konfigurowanie narzędzi platformy Docker

W menu głównym wybierz **narzędzia** > **opcje**i rozwiń **narzędzia kontenerów** > **ustawienia**. Ustawienia narzędzia kontenerów są wyświetlane.

![](./media/visual-studio-docker-tools-options.png)

Ilustracja 4-30 Platformy docker narzędzia, opcje

Poniższa tabela może pomóc zdecydować, jak ustawić te opcje.

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | On | Narzędzia docker Compose | Aby zwiększyć wydajność, podczas ładowania projektów Visual Studio rozpocznie operacji ściągania aparatu Docker w tle, tak, aby gdy jesteś gotowy do uruchomienia kodu, obraz, który został już pobrany, lub w trakcie pobierania. Jeśli właśnie trwa ładowanie projektów i przeglądania kodu, możesz Wyłącz tę opcję, aby uniknąć pobierania obrazów kontenerów, które nie są potrzebne. |
| Automatycznie uruchom kontenery w tle | On | Narzędzia docker Compose | Ponownie do zwiększenia wydajności programu Visual Studio tworzy kontener z instaluje wolumin gotowy do podczas kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować, po utworzeniu kontenera, wyłącz tę opcję. |
| Automatycznie zabij kontenery rozwiązanie, zamknij | On | Narzędzia docker Compose | Wyłącz tę opcję, jeśli chcesz kontenerów do rozwiązania w celu będą nadal działać po zamknięcie rozwiązania lub zamknięcia programu Visual Studio. |
| Nie monituj o zaufanie certyfikatowi protokołu SSL | Off | Projekty ASP.NET Core 2.1 | Jeśli certyfikatowi protokołu SSL nie jest zaufany, Visual Studio wyświetli monit o za każdym razem, gdy uruchamiasz projekt, chyba że to pole wyboru jest zaznaczone. |

> [!WARNING]
> Jeśli certyfikatowi protokołu SSL nie jest zaufany, a następnie zaznacz odpowiednie pole, aby pominąć monit, żądań sieci web protokołu HTTPS może przestać działać w czasie wykonywania aplikacji lub usługi. W takim przypadku usuń zaznaczenie pola wyboru **nie Monituj** zaznacz pole wyboru Uruchom projekt i wskazać zaufania w wierszu.

**Więcej informacji:** więcej szczegółowych informacji dotyczących wdrażania usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:

Kompilowanie, debugowanie, aktualizacji i odświeżanie aplikacji w lokalnym kontenerze Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Wdrażanie kontenera platformy ASP.NET Core Docker do rejestru kontenerów: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
>[Poprzednie](docker-apps-inner-loop-workflow.md)
>[dalej](set-up-windows-containers-with-powershell.md)