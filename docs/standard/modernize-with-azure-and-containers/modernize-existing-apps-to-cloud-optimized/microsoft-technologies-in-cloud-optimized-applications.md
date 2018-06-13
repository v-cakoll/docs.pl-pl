---
title: Technologii firmy Microsoft w chmurze są zoptymalizowane pod kątem aplikacji
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Technologii firmy Microsoft w chmurze są zoptymalizowane pod kątem aplikacji
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: ece366ee3918124bb60e367d3c7447c1d4555c72
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958222"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologii firmy Microsoft w chmurze są zoptymalizowane pod kątem aplikacji

Poniżej opisano narzędzia, technologiami i rozwiązaniami, które są rozpoznawane jako wymagania dotyczące aplikacji zoptymalizowanych pod kątem chmury. Elementy zoptymalizowanych pod kątem chmury można przyjąć selektywnie lub stopniowo, w zależności od priorytetów użytkownika.

-   **Infrastruktura chmurowa**: infrastrukturę, która zapewnia platforma obliczeniowa, systemu operacyjnego, sieci i magazynu. Microsoft Azure znajduje się na tym poziomie.

-   **Środowisko uruchomieniowe**: Ta warstwa udostępnia środowisko do uruchomienia aplikacji. Jeśli używasz kontenery tej warstwy zazwyczaj opiera się na [aparatem platformy Docker](https://docs.docker.com/engine/)uruchomiony na hostach z systemem Linux lub na hostach z systemem Windows. ([Kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane począwszy od systemu Windows Server 2016. Kontenery systemu Windows jest najlepszym wyborem istniejących aplikacji .NET Framework, uruchomionych w systemie Windows).

-   **Zarządzane chmury**: po wybraniu opcji zarządzanej chmury można uniknąć wydatków i złożoności, zarządzania i obsługi podstawowej infrastruktury, maszyn wirtualnych, poprawki systemu operacyjnego i konfigurację sieci. Jeśli wybierzesz opcję wykonania migracji za pomocą IaaS, jest odpowiedzialny dla wszystkich zadań i koszty. W przypadku opcji zarządzanej chmury zarządzanie tylko aplikacji i usług, które można rozwijać. Dostawcy usług w chmurze zarządza zwykle wszystkich innych urządzeń. Przykłady usługi w chmurze zarządzanych na platformie Azure [bazy danych SQL Azure](https://azure.microsoft.com/services/sql-database), [pamięć podręczna Redis Azure](https://azure.microsoft.com/services/cache/), [bazy danych Azure rozwiązania Cosmos](https://azure.microsoft.com/services/cosmos-db/), [usługi Azure Storage](https://azure.microsoft.com/services/storage/), [Bazy danych azure dla programu MySQL](https://azure.microsoft.com/services/mysql/), [bazą danych Azure dla PostgreSQL](https://azure.microsoft.com/services/postgresql/), [usługi Azure Active Directory](https://azure.microsoft.com/services/active-directory/)i zarządzanych usług obliczeniowych, takich jak [skalowania maszyny Wirtualnej Ustawia](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [sieć szkieletowa usług Azure](https://azure.microsoft.com/services/service-fabric/), [usłudze Azure App Service](https://azure.microsoft.com/services/app-service/), i [usługę Azure Kubernetes](https://azure.microsoft.com/services/container-service/).

-   **Projektowanie aplikacji**: wiele języków można wybrać podczas tworzenia aplikacji działających w kontenerach. Ten przewodnik koncentruje się na [.NET](https://www.microsoft.com/net), ale można tworzyć aplikacje na podstawie kontenera za pomocą innych języków, takich jak Node.js, Python, Spring/Java, lub przejść.

-   **Monitorowanie danych telemetrii, rejestrowanie i inspekcja**: możliwość monitorowania i inspekcji aplikacji i kontenerów, które działają w chmurze jest szczególnie ważne dla dowolnej aplikacji zoptymalizowanych pod kątem chmury. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [programu Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) są główne narzędzia firmy Microsoft, które zapewniają monitorowanie i przeprowadzanie inspekcji dla aplikacji zoptymalizowanych pod kątem chmury.

-   **Inicjowanie obsługi administracyjnej**: Automatyzacja narzędzia ułatwiają udostępniania infrastruktury i wdrożyć aplikację w wielu środowiskach (środowisko produkcyjne, testowanie, przemieszczania). Narzędzia, takie jak Chef i Puppet służy do zarządzania konfiguracji aplikacji i środowiska. Ta warstwa może również zaimplementowany przy użyciu podejścia prostszy i bardziej bezpośrednie. Na przykład można wdrożyć bezpośrednio za pomocą usługi Azure interfejsu wiersza polecenia (Azure CLI) narzędzi i użyj ciągłego wdrażania i zarządzania potoków w wersji [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Cykl życia aplikacji**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) i innych narzędzi, takich jak Wpięć, są serwery automatyzacji wbudowanych, które ułatwiają wdrażanie elementu konfiguracji/CD potoki, w tym zarządzania zleceniami.

Następne sekcje w tym rozdziale i powiązane wskazówki, w szczególności skoncentrować szczegółowe informacje o warstwie środowiska uruchomieniowego (kontenery systemu Windows). Wskazówki opisano sposoby można wdrożyć kontenery systemu Windows w systemie Windows Server 2016 (lub nowszym) maszyn wirtualnych i wystąpień kontenera platformy Azure. Obejmuje ona również bardziej zaawansowanych PaaS platformach, np. Azure App Service i orchestrator, takich jak sieć szkieletowa usług Azure i usługi Kubernetes platformy Azure.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikacje wbudowanymi *można* być zoptymalizowany pod kątem chmury

Ważne jest, aby wyróżnić przez wbudowanymi aplikacje (aplikacje, które nie są oparte na mikrousług) *można* być zoptymalizowany pod kątem chmury aplikacje. Możesz skompilować i działać wbudowanymi aplikacji, które zalet chmury obliczeniowej modelu przy użyciu kombinacji kontenerów, ciągłego dostarczania i opracowywania oprogramowania. W przypadku istniejącej aplikacji wbudowanymi prawo do celów biznesowych, możesz go modernizacji i nadać mu zoptymalizowanych pod kątem chmury.

Podobnie jeśli wbudowanymi aplikacje mogą być zoptymalizowany pod kątem chmury aplikacji, architektury innych, bardziej złożonych, takich jak aplikacje warstwowe można również modernizowana jako aplikacje zoptymalizowanych pod kątem chmury.

>[!div class="step-by-step"]
[Poprzednie](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[dalej](what-about-cloud-native-applications.md)
