---
title: Aplikacje oparte na proces Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Aplikacje oparte na proces Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="development-process-for-docker-based-applications"></a>Proces tworzenia aplikacji opartych na Docker

*Opracowywanie konteneryzowanych aplikacji .NET lubisz, IDE fokus z programu Visual Studio i narzędzi Visual Studio tools for Docker lub interfejsu wiersza polecenia/Edytor fokus z interfejsu wiersza polecenia Docker i Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Środowisko projektowe dla aplikacji Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opcje narzędzia opracowywania: IDE lub edytora

Czy wolisz pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne, firma Microsoft udostępnia narzędzia, które służą do tworzenia aplikacji platformy Docker.

**Visual Studio (dla systemu Windows)**. Do tworzenia aplikacji opartych na Docker, użyj programu Visual Studio 2017 lub nowsze wersje, które jest dostarczany z tools for Docker już wbudowanych. Tools for Docker umożliwiają tworzenie, uruchamianie i sprawdzanie poprawności aplikacji bezpośrednio w środowisku docelowym Docker. Naciśnij klawisz F5, aby uruchomić i debugowania aplikacji (jeden kontener lub wielu kontenerów) bezpośrednio do hostów Docker lub naciśnij klawisze CTRL + F5, edytowanie i odświeżanie aplikacji bez konieczności odbudować kontenera. Jest to najbardziej zaawansowanych wybór programowanie dla aplikacji opartych na Docker.

**Visual Studio for Mac**. Jest IDE ewolucja platformy Xamarin Studio uruchomionym w macOS i obsługuje tworzenie aplikacji opartej na Docker. Powinno to być preferowany wybór dla deweloperów pracujących w komputerach Mac, również chcą korzystać z zaawansowanych IDE.

**Visual Studio Code i Docker CLI**. Jeśli wolisz nieskomplikowane i Międzyplatformowe edytorze, który obsługuje dowolnego języka programowania, można użyć programu Microsoft Visual Studio (kod VS) i interfejsu wiersza polecenia Docker. To podejście wiele platform dla komputerów Mac, Linux i Windows.

Instalując [Docker Community Edition (CE)](https://www.docker.com/community-edition) narzędzi, można użyć jednego interfejsu wiersza polecenia Docker umożliwia tworzenie aplikacji dla systemu Windows i Linux. Ponadto program Visual Studio Code obsługuje rozszerzenia Docker, takie jak IntelliSense dla zadań Dockerfiles i skrót do uruchamiania polecenia Docker w edytorze.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Visual Studio Code**. Oficjalna witryna.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Docker Community Edition (CE) dla systemów Mac i systemu Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET języków i struktur dla kontenerów Docker

Jak wspomniano we wcześniejszych sekcjach tego przewodnika, można użyć .NET Framework .NET Core i Mono projekt open source podczas opracowywania Docker konteneryzowanych aplikacji .NET. Można tworzyć w języku C\#, F\#, lub Visual Basic, jeśli Linux lub kontenery systemu Windows, w zależności od tego, które .NET framework jest używana. W przypadku języków about.NET więcej szczegółów, zobacz wpis w blogu [strategii języka .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).


>[!div class="step-by-step"]
[Poprzednie] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [dalej] (docker-app-development-workflow.md)
