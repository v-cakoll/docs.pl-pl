---
title: Przepływ pracy devops aplikacji platformy docker przy użyciu narzędzi firmy Microsoft
description: Konteneryzowane cyklem życia aplikacji platformy Docker za pomocą platformy firmy Microsoft i Toolsdevops przepływu pracy z narzędziami firmy Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d313cb8ff6762eba6534ca20b214063315a456f0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561672"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Przepływ pracy DevOps aplikacji platformy docker przy użyciu narzędzi firmy Microsoft

Microsoft Visual Studio, usługom DevOps platformy Azure, Team Foundation Server i usługi Application Insights zapewnienia kompleksowej ekosystemu opracowywania i operacjami IT, które wyposaż swój zespół w narzędzia do zarządzania projektami i szybkiego tworzenia, testowania i wdrażania konteneryzowanych aplikacji.

Za pomocą programu Visual Studio i usługom DevOps platformy Azure w chmurze, wraz z Team Foundation Server w środowisku lokalnym zespoły deweloperów mogą wydajnie tworzenia, testowania i wersji konteneryzowanych aplikacji skierowaną do dowolnej platformy (Windows lub Linux).

Narzędzia Microsoft można zautomatyzować potoku dla określonej implementacji konteneryzowanych aplikacji — Docker, platformy .NET Core lub dowolnej kombinacji z innymi platformami — od globalnej kompilacje i ciągłej integracji (CI) i testy usługom DevOps platformy Azure lub zespołowi Foundation Server, do ciągłego wdrażania (polecenie CD) do platformy Docker, środowisk (tworzenia, wdrażania przejściowego, produkcji), a do przesyłania informacji analitycznych dotyczących usług do zespołu programistycznego za pomocą usługi Application Insights. Każde zatwierdzenie kodu można zainicjować kompilacji (CI) i automatycznie wdrażać usługi dla określonych środowisk konteneryzowanych (polecenie CD).

Deweloperzy i testerzy mogą łatwo i szybko aprowizować środowiska deweloperskie i testowe środowiska przypominającej środowisko produkcyjne na podstawie platformy Docker przy użyciu szablonów w systemie Microsoft Azure.

Złożoność tworzenia konteneryzowanych aplikacji stale zwiększa się w zależności od potrzeb biznesowych złożoności i skalowalności. Dobrym przykładem są aplikacje oparte na architekturze mikrousług. Została wykonana pomyślnie, w takim środowisku, projekt musi Automatyzacja całego cyklu życia — nie tylko kompilacji i wdrażania, ale również musi zarządzać wersjami oraz zbieranie danych telemetrycznych. Azure usługom DevOps i platformy Azure oferuje następujące możliwości:

-   Zarządzanie kodem źródłowym DevOps usług/Team Foundation Server w usłudze Azure (na podstawie usługi Git lub Team Foundation Version Control), elastycznego planowania (Agile, Scrum i CMMI są obsługiwane), ciągła Integracja, release management i inne narzędzia dla zespołów Agile.

-   Usługa Azure DevOps usług/Team Foundation Server obejmują zaawansowane i rosnący ekosystem rozszerzeń pierwszy i innych firm za pomocą których łatwo można skonstruować ciągłej integracji, kompilacji, testowania, dostarczania i release management potoku dla mikrousług.

-   Uruchom testy automatyczne jako część potoku kompilacji w usługom DevOps platformy Azure.

-   Usługi Azure DevOps zwiększania DevOps cyklu życia z dostarczania w wielu środowiskach, nie tylko w środowiskach produkcyjnych, ale także do testowania, takie jak A / B eksperymentowania, [kanarkowe](https://martinfowler.com/bliki/CanaryRelease.html)i tak dalej.

-   Organizacje mogą zainicjować obsługę kontenerów platformy Docker z prywatnych obrazów przechowywanych w usłudze Azure Container Registry, wraz z jej zależności od składników platformy Azure (danych, PaaS, itp.) przy użyciu szablonów usługi Azure Resource Manager za pomocą narzędzi, z którymi są one już Praca komfortowo, jednocześnie.


>[!div class="step-by-step"]
[Poprzednie](../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md)
[dalej](docker-application-outer-loop-devops-workflow.md)
