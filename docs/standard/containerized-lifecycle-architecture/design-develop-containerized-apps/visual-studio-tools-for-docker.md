---
title: Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio Windows)
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488954"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio Windows)

Przepływ pracy tworzenia oprogramowania przy użyciu Visual Studio Tools for Docker jest podobny do przepływu pracy, podczas korzystania z programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker. W rzeczywistości opiera się na tym samym interfejsu wiersza polecenia platformy Docker, ale jest łatwiej rozpocząć pracę, upraszcza ten proces i zapewnia większą produktywność dla kompilacji, uruchom i redagowania zadań. Istnieje również możliwość wykonywania i Debuguj swoje kontenery za pomocą prostego akcji, takich jak klawisza F5 i Ctrl + F5 w programie Visual Studio. Dzięki obsłudze aranżacji opcjonalny kontener, oprócz możliwości uruchamiać i debugować jeden kontener można uruchomić i debugować grupę kontenerów (całe rozwiązanie), w tym samym czasie. Tylko definiuje kontenery, w tym samym *docker-compose.yml* pliku na poziomie rozwiązania.

## <a name="configuring-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Obsługę platformy docker znajduje się w programie Visual Studio 2017 z żadnego z zainstalowanych obciążeń .NET i .NET Core. Oddzielna instalacja platformy Docker for Windows.

Za pomocą najnowszych wersji platformy Docker for Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker ponieważ Instalator jest proste, jak wyjaśniono w następujących odwołań.

**Więcej informacji:** Aby dowiedzieć się więcej o instalowaniu platformy Docker for Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.

**Więcej informacji:** instrukcje dotyczące instalowania programu Visual Studio, przejdź do [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).

Aby wyświetlić więcej informacji o instalowaniu programu Visual Studio Tools for Docker, przejdź do <http://aka.ms/vstoolsfordocker> i <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

## <a name="using-docker-tools-in-visual-studio-2017"></a>Za pomocą narzędzi Docker w programie Visual Studio 2017

Podczas dodawania obsługi programu Docker do projektu (zobacz rysunek 4-26), program Visual Studio dodaje *pliku Dockerfile* w katalogu głównym projektu.

![Włączanie obsługi rozwiązania Docker w projekcie programu Visual Studio 2017](./media/image32.png)

Rysunek 4-26: Włączanie obsługi rozwiązania Docker w projekcie programu Visual Studio 2017

 W Visual Studio 2017 w wersji 15.7 lub wcześniejszej domyślnie zostanie dodana jego obsługa aranżacji kontenerów, za pomocą narzędzia Docker Compose. Obsługa aranżacji kontenerów to funkcja opcjonalna w wersjach programu Visual Studio 2017 15.8 lub później, w którym to przypadku narzędzia Docker Compose i Service Fabric są obsługiwane.

Dzięki programowi Visual Studio w wersji należy zachować 15,8 i nowszych można dodać obsługę wielu projektów w rozwiązaniu, w których każdy może mieć skojarzony kontener. Kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj** > **Obsługa aranżacji kontenerów**.  Następnie wybierz **narzędzia Docker Compose** lub **usługi Service Fabric** Zarządzanie kontenerów.

Po wybraniu **narzędzia Docker Compose**, program Visual Studio dodaje sekcji usługi w swoim rozwiązaniu *docker-compose.yml* plików (lub tworzy pliki, jeśli nie istnieją). Jest to prosty sposób rozpocząć tworzenie rozwiązania wielokontenerowych; następnie można otworzyć *docker-compose.yml* pliki i aktualizować je, oraz dodatkowe funkcje.

Ta akcja spowoduje dodanie wymaganej konfiguracji linii kodu w celu *docker-compose.yml* ustawienie poziomie rozwiązania.

Możesz również włączyć obsługę platformy Docker podczas tworzenia projektu ASP.NET Core w programie Visual Studio 2017, jak pokazano w rysunek 4-27.

![Włączanie obsługi platformy Docker, podczas tworzenia projektu](./media/image33.png)

Rysunek 4-27: Włączanie obsługi platformy Docker, podczas tworzenia projektu

Po dodaniu obsługi programu Docker do rozwiązania w programie Visual Studio również zobaczysz nowego węzła drzewa w **Eksploratora rozwiązań** z dodany *docker-compose.yml* plików, jak pokazano w rysunek 4-28.

![pliki docker-compose.yml są teraz wyświetlane w Eksploratorze rozwiązań](./media/image34.PNG)

Rysunek 4-28: pliki docker-compose.yml są teraz wyświetlane w **Eksploratora rozwiązań**

Można wdrożyć aplikację obsługującą wiele kontenerów przy użyciu pojedynczej *docker-compose.yml* plików po uruchomieniu `docker-compose up`; jednak program Visual Studio dodaje grupę z tych funkcji, dzięki czemu można zastąpić wartości w zależności od środowiska (Programowanie w porównaniu z środowisko produkcyjne) i wykonywanie, wpisz (wersja w stosunku do debugowania). Ta funkcja lepiej zostało wyjaśnione w rozdziałach nowsze.

Umożliwia także usługi Service Fabric zamiast narzędzia Docker Compose Zarządzanie wiele kontenerów. Zobacz [samouczek: Wdrażanie aplikacji .NET w kontenerze Windows w usłudze Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).

**Więcej informacji:** więcej szczegółowych informacji dotyczących wdrażania usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:

Kompilowanie, debugowanie, aktualizacji i odświeżanie aplikacji w lokalnym kontenerze Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Wdrażanie kontenera platformy ASP.NET Core Docker do rejestru kontenerów: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Poprzednie](docker-apps-inner-loop-workflow.md)
[dalej](set-up-windows-containers-with-powershell.md)
