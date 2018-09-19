---
title: Technologie firmy Microsoft w aplikacjach zoptymalizowane pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Technologie firmy Microsoft w aplikacjach zoptymalizowane pod kątem chmury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 874eeffe77d7f5e459be4d1a93cc2c45e8f8711a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007519"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie firmy Microsoft w aplikacjach zoptymalizowane pod kątem chmury

Na poniższej liście opisano narzędzia, technologie i rozwiązania, które są rozpoznawane jako wymagania dotyczące aplikacji zoptymalizowane pod kątem chmury. Zoptymalizowane pod kątem chmury elementy można przyjąć selektywnie lub stopniowo, w zależności od priorytetów.

-   **Infrastruktura chmurowa**: infrastruktura, która udostępnia platformę obliczeniową, system operacyjny, sieci i magazynu. Microsoft Azure znajduje się na tym poziomie.

-   **Środowisko uruchomieniowe**: Ta warstwa zapewnia środowisko do uruchamiania aplikacji. Jeśli używasz kontenery tej warstwy zwykle opiera się na [aparat platformy Docker](https://docs.docker.com/engine/)uruchomiony na hostach z systemem Linux lub na hostach Windows. ([Kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane, począwszy od systemu Windows Server 2016. Kontenery Windows jest najlepszym wyborem dla istniejących aplikacji .NET Framework, które systemem Windows).

-   **Managed cloud**: po wybraniu opcji zarządzana usługa w chmurze, możesz uniknąć wydatków i złożoności zarządzania i obsługi poprawek do systemu operacyjnego podstawowej infrastruktury, w przypadku maszyn wirtualnych i konfigurację sieci. Jeśli chcesz przeprowadzić migrację za pomocą modelu IaaS, jesteś odpowiedzialny za wszystkie te zadania i powiązanych z nimi kosztów. Opcja zarządzana usługa w chmurze służy do zarządzania tylko aplikacji i usług, które tworzysz. Zazwyczaj dostawcy usług w chmurze zajmuje się całą resztą. Przykłady zarządzane usługi w chmurze na platformie Azure [usługi Azure SQL Database](https://azure.microsoft.com/services/sql-database), [usługi Azure Redis Cache](https://azure.microsoft.com/services/cache/), [usługi Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [usługi Azure Storage](https://azure.microsoft.com/services/storage/), [— Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [— Azure Database for postgresql w warstwie](https://azure.microsoft.com/services/postgresql/), [usługi Azure Active Directory](https://azure.microsoft.com/services/active-directory/)i zarządzanych usług obliczeniowych, takich jak [skalowania maszyn wirtualnych Ustawia](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [usługi Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [usługi Azure App Service](https://azure.microsoft.com/services/app-service/), i [usługi Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

-   **Tworzenie aplikacji**: możesz korzystać z wielu języków podczas kompilowania aplikacji działających w kontenerach. Ten przewodnik koncentruje się na [.NET](https://www.microsoft.com/net), jednak można tworzyć oparte na kontenerach aplikacje przy użyciu innych języków, takich jak Node.js, Python, Spring/Java, lub przejść.

-   **Monitorowanie telemetrii, rejestrowanie i przeprowadzanie inspekcji**: możliwość monitorowania i inspekcji aplikacji i kontenerów, które działają w chmurze jest krytyczny dla dowolnej aplikacji zoptymalizowane pod kątem chmury. [Usługa Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [pakietu Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) to głównego narzędzia firmy Microsoft, które zapewnia monitorowanie i przeprowadzanie inspekcji dla aplikacji zoptymalizowane pod kątem chmury.

-   **Inicjowanie obsługi administracyjnej**: automatyzacji narzędzia ułatwiają Inicjowanie obsługi infrastruktury oraz wdrażanie aplikacji dla wielu środowisk (produkcja, testowania, przemieszczania). Do zarządzania, konfiguracji i środowiska aplikacji, można użyć narzędzi, takich jak Chef i Puppet. Ta warstwa może również implementowany przy użyciu metod prostszy i bardziej bezpośredni. Na przykład, można wdrożyć bezpośrednio przy użyciu wiersza polecenia interfejsu CLI platformy Azure (Azure) narzędzia i Zastosuj ciągłe wdrażanie i zarządzanie potoki w wersji [usługom DevOps platformy Azure](https://visualstudio.microsoft.com/team-services/).

-   **Cykl życia aplikacji**: [usługom DevOps platformy Azure](https://visualstudio.microsoft.com/team-services/) i innych narzędzi, takich jak Jenkins, są serwery utworzonych automatyzacji, które ułatwiają wdrożenie potoków ciągłej integracji/ciągłego wdrażania, w tym rozwiązania release management.

Następne sekcje w tym rozdziale i pokrewne instruktaże, skupić się w dalszej części przedstawiono szczegółowe informacje o warstwie środowiska uruchomieniowego (systemu Windows Windows kontenery). Się ze wskazówkami w tym artykule opisano sposób, można wdrożyć maszyny wirtualne Windows kontenery w systemie Windows Server 2016 (lub nowszym) i Azure Container Instances. Obejmuje ona również bardziej zaawansowanych platform PaaS, takich jak usługa Azure App Service i programu orchestrator, takich jak Azure Service Fabric i usługi Azure Kubernetes Service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikacje monolityczne *można* być optymalizowane pod kątem chmury

Jest ważne podkreślić że monolitycznych aplikacji (aplikacje, które nie są oparte na mikrousługach) *można* być optymalizowane pod kątem chmury aplikacji. Możesz tworzyć i działanie aplikacji monolitycznej, które korzystać z zalet chmury obliczeniowej modelu, używając kombinacji kontenerów, ciągłego dostarczania i metodyki DevOps. W przypadku istniejącej aplikacji monolitycznych prawo do celów biznesowych, możesz go modernizować i nadać mu zoptymalizowane pod kątem chmury.

Podobnie jeśli monolitycznych aplikacji mogą być aplikacje zoptymalizowane pod kątem chmury, inne, bardziej złożone architektury, takie jak aplikacje N-warstwowe mogą również zmodernizowane jako aplikacje zoptymalizowane pod kątem chmury.

>[!div class="step-by-step"]
[Poprzednie](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[dalej](what-about-cloud-native-applications.md)
