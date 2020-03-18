---
title: Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676995"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury

Na poniższej liście opisano narzędzia, technologie i rozwiązania, które są rozpoznawane jako wymagania dla aplikacji zoptymalizowanych pod kątem chmury. Elementy zoptymalizowane pod kątem chmury można przyjmować selektywnie lub stopniowo, w zależności od priorytetów.

- **Infrastruktura w chmurze**: infrastruktura zapewniająca platformę obliczeniową, system operacyjny, sieć i magazyn. Platforma Microsoft Azure jest pozycjonowana na tym poziomie.

- **Środowisko uruchomieniowe**: Ta warstwa zapewnia środowisko do uruchomienia aplikacji. Jeśli używasz kontenerów, ta warstwa jest zwykle oparta na [docker engine](https://docs.docker.com/engine/), uruchomiony na hostach systemu Linux lub na hostach systemu Windows. ([Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane począwszy od systemu Windows Server 2016. Kontenery systemu Windows to najlepszy wybór dla istniejących aplikacji .NET Framework uruchamianych w systemie Windows).

- **Chmura zarządzana:** Po wybraniu opcji chmury zarządzanej można uniknąć kosztów i złożoności zarządzania i obsługi podstawowej infrastruktury, maszyn wirtualnych, poprawek systemu operacyjnego i konfiguracji sieci. Jeśli zdecydujesz się na migrację przy użyciu usługi IaaS, jesteś odpowiedzialny za wszystkie te zadania i związane z nimi koszty. W opcji chmury zarządzanej zarządzasz tylko aplikacjami i usługami, które tworzysz. Dostawca usług w chmurze zazwyczaj zarządza wszystkim innym. Przykłady zarządzanych usług w chmurze na platformie Azure obejmują [bazę danych SQL Azure,](https://azure.microsoft.com/services/sql-database) [usługę Azure Redis Cache,](https://azure.microsoft.com/services/cache/) [usługę Azure Cosmos DB,](https://azure.microsoft.com/services/cosmos-db/) [usługę Azure Storage,](https://azure.microsoft.com/services/storage/) [usługę Azure Database for MySQL,](https://azure.microsoft.com/services/mysql/) [bazę danych Azure dla postgreSQL,](https://azure.microsoft.com/services/postgresql/) [usługę Azure Active Directory](https://azure.microsoft.com/services/active-directory/)oraz zarządzane usługi obliczeniowe, takie jak [zestawy skalowania maszyn wirtualnych,](https://azure.microsoft.com/services/virtual-machine-scale-sets/) [usługę Azure App Service](https://azure.microsoft.com/services/app-service/)i usługę Azure [Kubernetes .](https://azure.microsoft.com/services/container-service/)

- **Tworzenie aplikacji**: Można wybierać spośród wielu języków podczas tworzenia aplikacji uruchamianych w kontenerach. Ten przewodnik koncentruje się na [.NET](https://www.microsoft.com/net), ale można tworzyć aplikacje oparte na kontenerach przy użyciu innych języków, takich jak Node.js, Python, Spring / Java lub Go.

- **Monitorowanie, telemetria, rejestrowanie i inspekcja:** Możliwość monitorowania i inspekcji aplikacji i kontenerów działających w chmurze ma kluczowe znaczenie dla dowolnej aplikacji zoptymalizowanej pod kątem chmury. [Usługi Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) to główne narzędzia firmy Microsoft, które zapewniają monitorowanie i inspekcję aplikacji zoptymalizowanych pod kątem chmury.

- **Inicjowanie obsługi administracyjnej**: Narzędzia automatyzacji ułatwiają aprowizacje infrastruktury i wdrażanie aplikacji w wielu środowiskach (produkcyjnych, testujących, przejściowych). Za pomocą narzędzi, takich jak Chef i Puppet, można zarządzać konfiguracją i środowiskiem aplikacji. Tę warstwę można również zaimplementować przy użyciu prostszych i bardziej bezpośrednich podejść. Na przykład można wdrożyć bezpośrednio przy użyciu narzędzi interfejsu wiersza polecenia platformy Azure (Azure CLI), a następnie użyć potoków ciągłego wdrażania i zarządzania wersjami w [usłudze Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Cykl życia aplikacji:** [Usługi Azure DevOps](https://azure.microsoft.com/services/devops/) i inne narzędzia, takie jak Jenkins, to wbudowane serwery automatyzacji, które ułatwiają wdrażanie potoków ciągłej integracji/ciągłego wdrażania, w tym zarządzania wersjami.

Następne sekcje tego rozdziału i powiązane instruktaże koncentrują się w szczególności na szczegółach dotyczących warstwy środowiska uruchomieniowego (Kontenery systemu Windows). Wskazówki opisano sposoby wdrażania kontenerów systemu Windows na windows server 2016 (i nowszych wersjach) maszyn wirtualnych i wystąpień kontenera platformy Azure. Obejmuje również bardziej zaawansowane platformy PaaS, takie jak usługa Azure App Service i koordynator, takie jak usługa Azure Kubernetes.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikacje monolityczne *mogą* być zoptymalizowane pod kątem chmury

Należy podkreślić, że monolityczne aplikacje (aplikacje, które nie są oparte na mikrousługach) *mogą* być aplikacjami zoptymalizowanymi pod kątem chmury. Można tworzyć i obsługiwać monolityczne aplikacje, które korzystają z modelu przetwarzania w chmurze przy użyciu kombinacji kontenerów, ciągłego dostarczania i DevOps. Jeśli istniejąca aplikacja monolityczna jest odpowiednia dla Twoich celów biznesowych, można ją zmodernizować i uczynić z niej zoptymalizowaną pod kątem chmury.

Podobnie jeśli aplikacje monolityczne mogą być aplikacjami zoptymalizowanymi pod kątem chmury, inne, bardziej złożone architektury, takie jak aplikacje N-Warstwowe, mogą być również modernizowane jako aplikacje zoptymalizowane pod kątem chmury.

>[!div class="step-by-step"]
>[Poprzedni](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[następny](what-about-cloud-native-applications.md)
