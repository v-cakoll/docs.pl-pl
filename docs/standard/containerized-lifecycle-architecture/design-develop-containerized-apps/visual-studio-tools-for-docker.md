---
title: Visual Studio Tools for Docker na Windows
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170798"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio Windows)

Visual Studio Tools dla przepływu pracy dla deweloperów platformy Docker jest podobny do przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia Docker (opiera się na tym samym interfejsu wiersza polecenia platformy Docker). Program Visual Studio Tools dla platformy Docker sprawia, że jeszcze łatwiej rozpocząć pracę, upraszcza i zapewnia większą produktywność dla kompilacji, uruchamianie i redagowania zadań. Wykonywanie i Debuguj swoje kontenery za pomocą prostego akcji, takich jak **F5** i **Ctrl**+**F5**.

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w Windows, a nie programu Visual Studio dla komputerów Mac.

## <a name="configure-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Najnowsze wersje platformy Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), proste Instalatora ułatwia tworzenie aplikacji platformy Docker.

Obsługę platformy docker znajduje się w programie Visual Studio 2017. Pobierz program Visual Studio 2017 w tym miejscu: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017

Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu. W projektach aplikacji sieci web platformy .NET Core, można po prostu dodać *pliku Dockerfile* pliku do projektu, należy włączyć obsługę platformy Docker. Następny poziom to obsługi orkiestratora kontenerów, który dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i *docker-compose.yml* pliku na poziomie rozwiązania.

**Dodaj** > **obsługę platformy Docker** i **Dodaj** > **obsługi Orkiestratora kontenerów** polecenia są znajduje się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu aplikacji sieci web w **Eksploratora rozwiązań**, jak pokazano w rysunek 4-26:

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](media/add-docker-support-menu.png)

Rysunek 4-26: Dodawanie obsługi programu Docker do projektu programu Visual Studio 2017

### <a name="add-docker-support"></a>Dodaj obsługę platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu aplikacji sieci web platformy .NET Core, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**. Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, które jest otwierane po kliknięciu **OK** w **nowy projekt** okno dialogowe, jak pokazano w rysunek 4-27.

![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

Rysunek 4-27: Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017

Podczas dodawania lub Włącz obsługę platformy Docker, program Visual Studio dodaje *pliku Dockerfile* pliku do projektu.

> [!NOTE]
> Po włączeniu obsługi narzędzia Docker Compose podczas tworzenia projektu dla projektu aplikacji sieci web .NET Framework (nie platformy .NET Core projektu aplikacji sieci web), jak pokazano w rysunek 4-28, dodawany jest również obsługa orkiestratora kontenerów.
>
> ![Włącz Docker compose obsługę projektu aplikacji sieci web w języku .NET Framework](media/enable-docker-compose-support.png)

> Rysunek 4-28: Włączanie narzędzia Docker Compose pomocy technicznej w projekcie aplikacji sieci web .NET Framework w programie Visual Studio 2017

### <a name="add-container-orchestrator-support"></a>Dodawanie obsługi orkiestratora kontenerów

W przypadku tworzenia z wieloma kontenerami w celu rozwiązania Dodawanie obsługi orkiestratora kontenerów do swoich projektów. Podczas dodawania obsługi orkiestratora kontenerów programu Visual Studio dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i globalną *docker-compose.yml* pliku na poziomie rozwiązania. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku. Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.

Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz plik Dockerfile dodane do projektu i **narzędzia docker compose** dodawany do rozwiązania w folderze **Eksploratora rozwiązań**, jak pokazano w rysunek 4-29:

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

Ilustracja 4-29 plików Docker w Eksploratorze rozwiązań w programie Visual Studio 2017

**Więcej informacji:** więcej szczegółowych informacji dotyczących wdrażania usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:

Kompilowanie, debugowanie, aktualizacji i odświeżanie aplikacji w lokalnym kontenerze Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Wdrażanie kontenera platformy ASP.NET Core Docker do rejestru kontenerów: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Poprzednie](docker-apps-inner-loop-workflow.md)
[dalej](set-up-windows-containers-with-powershell.md)