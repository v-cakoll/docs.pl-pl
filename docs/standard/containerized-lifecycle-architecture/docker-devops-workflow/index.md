---
title: Przepływ pracy devops aplikacji docker z narzędzi firmy Microsoft
description: Konteneryzowanych cyklem życia aplikacji Docker z platformy Microsoft a Toolsdevops przepływu pracy przy użyciu narzędzi firmy Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b915c53b70192139c64c63d8b47110263e1621d0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104468"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Przepływ pracy DevOps aplikacji docker z narzędzi firmy Microsoft

Microsoft Visual Studio, Visual Studio Team Services Team Foundation Server i usługi Application Insights Podaj kompleksowe ekosystemu dla rozwoju i operacji IT, które zapewniają narzędzia do zarządzania projektami i szybkiego tworzenia, testowania i wdrażania zespołu konteneryzowanych aplikacji.

Z programu Visual Studio i Visual Studio Team Services w chmurze, wraz z Team Foundation Server w infrastrukturze lokalnej zespoły rozwoju aplikacji mogą efektywnie tworzenia, testowania i wersji aplikacji konteneryzowanych skierowaną do dowolnej platformy (Windows lub Linux).

Narzędzia Microsoft można zautomatyzować potoku określonej implementacji aplikacji konteneryzowanych — Docker, .NET Core lub dowolną kombinację z innych platform — z globalnego kompilacje i ciągłej integracji (CI) i testy za pomocą programu Visual Studio Team Services lub Team Foundation Server, do ciągłego wdrażania (CD) do środowiska Docker (Programowanie, przemieszczania, produkcji) i do przesyłania analizy informacji o usługach zespół deweloperów za pomocą usługi Application Insights. Każdym zatwierdzeniem kodu można zainicjować kompilacji (CI) i automatycznie wdrażać usługi do określonego środowiska konteneryzowanych (CD).

Deweloperzy i testerzy mogą łatwo i szybko udostępnić środowisk projektowania i testowania przypominającej środowisko produkcyjne oparte na Docker przy użyciu szablonów w Microsoft Azure.

Złożoność projektowanie aplikacji konteneryzowanych stopniowo zwiększa się w zależności od potrzeb biznesowych złożoność i skalowalność. Dobrym przykładem są aplikacje oparte na architekturze mikrousług. Aby pomyślnie w środowisku z projektu musi zautomatyzować przez cały cykl życia — nie tylko kompilacji i wdrożenia, ale również należy zarządzać wersjach, oraz zbierania danych telemetrycznych. Visual Studio Team Services i platformy Azure oferuje następujące możliwości:

-   Zarządzania z kodem źródłowym programu Visual Studio Team Services i Team Foundation Server z (na podstawie Git lub Team Foundation Version Control), planowania Zwinnego (Agile, Scrum i CMMI są obsługiwane), elementu konfiguracji, zarządzania zleceniami i inne narzędzia umożliwiające Agile zespołów.

-   Visual Studio Team Services i Team Foundation Server obejmują wydajny i rosnącym ekosystemu rozszerzenia pierwszy i innych firm, z którymi możesz łatwo tworzenia elementu konfiguracji, kompilacji, testu, dostarczania i release management potoku dla mikrousług.

-   Uruchamianie testów automatycznych jako część planowaną kompilacji w programie Visual Studio Team Services.

-   Visual Studio Team Services można zwiększyć DevOps cyklu życia z dostarczaniem w wielu środowiskach, nie tylko dla środowisk produkcyjnych, ale także do testowania, takie jak A / B eksperymenty, [mozgi wersjach](https://martinfowler.com/bliki/CanaryRelease.html)i tak dalej.

-   Organizacje łatwo można udostępnić kontenery Docker z prywatnej obrazy przechowywane w rejestrze kontenera Azure oraz wszelkie zależności na składnikach platformy Azure (danych, PaaS itp.) z narzędziami, które już znajdują się przy użyciu szablonów usługi Azure Resource Manager doświadczenia pracy.


>[!div class="step-by-step"]
[Poprzednie](../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md)
[dalej](docker-application-outer-loop-devops-workflow.md)
