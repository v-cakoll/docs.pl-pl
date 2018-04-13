---
title: Technologii firmy Microsoft w aplikacji w chmurze gotowe do opracowywania oprogramowania
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Technologii firmy Microsoft w aplikacjach DevOps gotowe do chmury"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66579905ad2694cf08950d0c0a69e2405ab2c1ee
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>Technologii firmy Microsoft w aplikacji w chmurze gotowe do opracowywania oprogramowania

Poniżej opisano narzędzia, technologii i rozwiązań, które są rozpoznawane jako wymagania dotyczące aplikacji DevOps gotowe do chmury. Aplikacje gotowe DevOps chmury można przyjąć selektywnie lub stopniowo, w zależności od priorytetów użytkownika.

-   **Infrastruktura chmurowa**: infrastrukturę, która zapewnia platforma obliczeniowa, systemu operacyjnego, sieci i magazynu. Microsoft Azure znajduje się na tym poziomie.

-   **Środowisko uruchomieniowe**: Ta warstwa udostępnia środowisko do uruchomienia aplikacji. Jeśli używasz kontenery tej warstwy zazwyczaj opiera się na [aparatem platformy Docker](https://docs.docker.com/engine/)uruchomiony na hostach z systemem Linux lub na hostach z systemem Windows. ([Kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane począwszy od systemu Windows Server 2016. Kontenery systemu Windows jest najlepszym wyborem istniejących aplikacji .NET Framework, uruchomionych w systemie Windows).

-   **Zarządzane chmury**: po wybraniu opcji zarządzanej chmury można uniknąć wydatków i złożoności, zarządzania i obsługi podstawowej infrastruktury, maszyn wirtualnych, poprawki systemu operacyjnego i konfigurację sieci. Jeśli wybierzesz opcję wykonania migracji za pomocą IaaS, jest odpowiedzialny dla wszystkich zadań i koszty. W przypadku opcji zarządzanej chmury zarządzanie tylko aplikacji i usług, które można rozwijać. Dostawcy usług w chmurze zarządza zwykle wszystkich innych urządzeń. Przykłady usługi w chmurze zarządzanych na platformie Azure [bazy danych SQL Azure](https://azure.microsoft.com/services/sql-database), [pamięć podręczna Redis Azure](https://azure.microsoft.com/services/cache/), [bazy danych Azure rozwiązania Cosmos](https://azure.microsoft.com/services/cosmos-db/), [usługi Azure Storage](https://azure.microsoft.com/services/storage/), [Bazy danych azure dla programu MySQL](https://azure.microsoft.com/services/mysql/), [bazą danych Azure dla PostgreSQL](https://azure.microsoft.com/services/postgresql/), [usługi Azure Active Directory](https://azure.microsoft.com/services/active-directory/)i zarządzanych usług obliczeniowych, takich jak [skalowania maszyny Wirtualnej Ustawia](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [sieć szkieletowa usług Azure](https://azure.microsoft.com/services/service-fabric/), [usłudze Azure App Service](https://azure.microsoft.com/services/app-service/), i [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/).

-   **Projektowanie aplikacji**: wiele języków można wybrać podczas tworzenia aplikacji działających w kontenerach. W tym przewodniku, możemy skupić się na [.NET](https://www.microsoft.com/net), ale można utworzyć na podstawie kontenera aplikacji przy użyciu innych języków, takich jak Node.js, Python, Spring/Java lub GoLang.

-   **Monitorowanie danych telemetrii, rejestrowanie i inspekcja**: możliwość monitorowania i inspekcji aplikacji i kontenerów, które działają w chmurze jest szczególnie ważne dla dowolnej aplikacji DevOps gotowe do chmury. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [programu Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) to główny narzędzia firmy Microsoft, które zapewnia monitorowanie i przeprowadzanie inspekcji dla aplikacji DevOps gotowe do chmury.

-   **Inicjowanie obsługi administracyjnej**: Automatyzacja narzędzia ułatwiają udostępniania infrastruktury i wdrożyć aplikację w wielu środowiskach (środowisko produkcyjne, testowanie, przemieszczania). Narzędzia, takie jak Chef i Puppet służy do zarządzania konfiguracji aplikacji i środowiska. Ta warstwa może również zaimplementowany przy użyciu podejścia prostszy i bardziej bezpośrednie. Na przykład można wdrożyć bezpośrednio za pomocą usługi Azure interfejsu wiersza polecenia (Azure CLI) narzędzi i użyj ciągłego wdrażania i zarządzania potoków w wersji [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Cykl życia aplikacji**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) i innych narzędzi, takich jak Wpięć, są serwery automatyzacji kompilacji, które ułatwiają wdrożenia elementu konfiguracji/CD potoki, w tym zarządzania zleceniami.

Następne sekcje w tym rozdziale i powiązane wskazówki, w szczególności skoncentrować szczegółowe informacje o warstwie środowiska uruchomieniowego (kontenery systemu Windows). Wskazówki opisano sposoby można wdrożyć maszyn wirtualnych kontenery systemu Windows w systemie Windows Server 2016 (lub nowszym). Obejmuje ona również bardziej zaawansowanych warstwy programu orchestrator, takich jak sieć szkieletowa usług Azure, Kubernetes i usługi kontenera platformy Azure. Ustawienie warstwy programu orchestrator jest podstawowe wymagania dotyczące modernizacji istniejących aplikacji .NET Framework (z systemem Windows) jako aplikacje gotowe DevOps chmury.

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>Aplikacje wbudowanymi *można* być gotowe DevOps chmury

Ważne jest, aby wyróżnić przez wbudowanymi aplikacje (aplikacje, które nie są oparte na mikrousług) *można* być aplikacje gotowe DevOps chmury. Możesz skompilować i działać wbudowanymi aplikacji, które zalet chmury obliczeniowej modelu przy użyciu kombinacji kontenerów, ciągłego dostarczania i opracowywania oprogramowania. W przypadku istniejącej aplikacji wbudowanymi prawo do celów biznesowych, można go modernizacji i była DevOps gotowe do chmury.

Podobnie jeśli wbudowanymi aplikacje mogą być aplikacje gotowe do chmury DevOps, architektury innych, bardziej złożonych, takich jak aplikacje warstwowe również może być modernizowana jako aplikacje gotowe do chmury DevOps.

>[!div class="step-by-step"]
[Poprzednie](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[dalej](what-about-cloud-optimized-applications.md)
