---
title: Aplikacje bazujące na proces programistyczny dla platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Aplikacje bazujące na proces programistyczny dla platformy Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 7736c1fe4cb1a2a4553ba36cecceab37e2fe90c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144471"
---
# <a name="development-process-for-docker-based-applications"></a>Proces programistyczny dotyczący aplikacji opartych na platformie Docker

*Opracowywanie konteneryzowanych aplikacji .NET lubisz, IDE skupia się za pomocą programu Visual Studio i Visual Studio tools for Docker lub interfejsu wiersza polecenia/Edytor skupia się przy użyciu interfejsu wiersza polecenia platformy Docker i Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Środowisko programistyczne dla aplikacji platformy Docker

### <a name="development-tool-choices-ide-or-editor"></a>Wybory dotyczące narzędzi rozwoju: Środowiskiem IDE lub edytorem

Czy wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, firma Microsoft ma narzędzia, które służą do tworzenia aplikacji platformy Docker.

**Program Visual Studio (for Windows)**. Tworzenie aplikacji opartych na platformie Docker, użyj programu Visual Studio 2017 lub nowsze wersje, które jest dostarczany za pomocą narzędzi dla platformy Docker wbudowane. Tools for Docker umożliwiają tworzenie, uruchamianie i Weryfikuj aplikacje bezpośrednio w docelowym środowisku platformy Docker. Naciśnij klawisz F5, aby uruchomić i zdebugować aplikację (jeden kontener lub wiele kontenerów) bezpośrednio do hosta platformy Docker lub naciśnij klawisze CTRL + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera. Jest to najbardziej wydajnymi procesorami wybór rozwój aplikacji opartych na platformie Docker.

**Visual Studio for Mac**. To środowisko IDE rozwoju programu Xamarin Studio, która działa w systemie macOS i obsługuje opracowywanie aplikacji opartych na platformie Docker. Powinna to być preferowanych przez dla deweloperów pracujących w komputerów Mac, również chcą korzystać z zaawansowanego środowiska IDE.

**Visual Studio Code i platformy Docker CLI**. Jeśli wolisz lekkie i Międzyplatformowe edytor, który obsługuje dowolny język programowania, można użyć programu Microsoft Visual Studio Code (VS Code) i interfejsu wiersza polecenia platformy Docker. Jest to podejście wieloplatformowego opracowywania aplikacji dla komputerów Mac, Linux i Windows.

Instalując [Docker Community Edition (CE)](https://www.docker.com/community-edition) narzędzi, można użyć pojedynczego interfejsu wiersza polecenia platformy Docker do tworzenia aplikacji dla systemów Windows i Linux. Ponadto Visual Studio Code obsługuje rozszerzenia dla platformy Docker, takie jak IntelliSense dla plików Dockerfile i skrót zadania to uruchamianie poleceń Docker z poziomu edytora.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Program Visual Studio Code** Oficjalna witryna.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Platformę docker Community Edition (CE) dla systemów Mac i Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET, języków i struktur dla kontenerów Docker

Jak wspomniano we wcześniejszych sekcjach tego przewodnika, można użyć środowiska .NET Framework, .NET Core lub projekt Mono typu open-source podczas opracowywania Docker kontenerowych nimi aplikacji .NET. Możesz tworzyć w języku C\#, F\#, lub Visual Basic podczas określania wartości docelowej systemu Linux lub Windows kontenery, w zależności od tego, które .NET framework jest w użyciu. Dla większej liczby języków about.NET szczegółowe informacje, zobacz wpis w blogu [strategia językowa platformy .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Poprzednie](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[dalej](docker-app-development-workflow.md)