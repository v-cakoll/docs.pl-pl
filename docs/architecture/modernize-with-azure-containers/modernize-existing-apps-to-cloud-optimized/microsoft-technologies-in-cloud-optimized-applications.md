---
title: Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676995"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury

Poniższa lista zawiera opis narzędzi, technologii i rozwiązań, które są rozpoznawane jako wymagania dotyczące aplikacji zoptymalizowanych pod kątem chmury. Można wdrażać elementy zoptymalizowane pod kątem chmury selektywnie lub stopniowo, w zależności od priorytetów.

- **Infrastruktura chmurowa**: Infrastruktura udostępniająca platformę obliczeniową, system operacyjny, Sieć i magazyn. Microsoft Azure jest umieszczony na tym poziomie.

- **Środowisko uruchomieniowe**: Ta warstwa zapewnia środowisko do uruchomienia aplikacji. Jeśli używasz kontenerów, ta warstwa zwykle opiera się na [aparacie platformy Docker](https://docs.docker.com/engine/), działającym na hostach z systemem Linux lub na hostach z systemem Windows. ([Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane począwszy od systemu windows Server 2016. Kontenery systemu Windows to najlepszy wybór dla istniejących aplikacji .NET Framework działających w systemie Windows.)

- **Chmura zarządzana**: Po wybraniu opcji zarządzanej chmury można uniknąć wydatków i złożoności zarządzania i obsługi podstawowej infrastruktury, maszyn wirtualnych, poprawek systemu operacyjnego i konfiguracji sieci. Jeśli zdecydujesz się na migrację za pomocą IaaS, odpowiadasz za wszystkie te zadania i powiązane z nimi koszty. W przypadku opcji zarządzanej chmury zarządzasz tylko aplikacjami i usługami, które opracowujesz. Dostawca usług w chmurze zwykle zarządza wszystkimi innymi. Przykłady zarządzanych usług Cloud Services na platformie Azure: [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Katalog](https://azure.microsoft.com/services/active-directory/)i zarządzane usługi obliczeniowe, takie jak [zestawy skalowania maszyn wirtualnych](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure App Service](https://azure.microsoft.com/services/app-service/)i [usługa Azure Kubernetes](https://azure.microsoft.com/services/container-service/).

- **Opracowywanie aplikacji**: Podczas kompilowania aplikacji uruchamianych w kontenerach można wybierać spośród wielu języków. Ten przewodnik koncentruje się na [platformie .NET](https://www.microsoft.com/net), ale można opracowywać aplikacje oparte na kontenerach za pomocą innych języków, takich jak Node. js, Python, sprężyny/Java lub go.

- **Monitorowanie, dane telemetryczne, rejestrowanie i inspekcja**: Możliwość monitorowania i inspekcji aplikacji i kontenerów działających w chmurze jest niezwykle ważna dla każdej aplikacji zoptymalizowanej pod kątem chmury. [Usługa Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) to główne narzędzia firmy Microsoft, które zapewniają monitorowanie i inspekcję aplikacji zoptymalizowanych pod kątem chmury.

- **Inicjowanie obsługi administracyjnej**: Narzędzia automatyzacji ułatwiają obsługę administracyjną infrastruktury i wdrażanie aplikacji w wielu środowiskach (w środowisku produkcyjnym, testowym, tymczasowym). Do zarządzania konfiguracją i środowiskiem aplikacji można używać narzędzi takich jak Chef i Puppet. Tę warstwę można również zaimplementować przy użyciu prostszego i bardziej bezpośredniego podejścia. Można na przykład wdrożyć bezpośrednio przy użyciu narzędzi interfejsu wiersza polecenia platformy Azure (CLI), a następnie użyć potoków ciągłego wdrażania i zarządzania zleceniami w [Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Cykl życia aplikacji**: [Azure DevOps Services](https://azure.microsoft.com/services/devops/) i inne narzędzia, takie jak Jenkins, są skompilowanymi serwerami automatyzacji, które pomagają wdrożyć potoki ciągłej integracji/ciągłego wdrażania, w tym Zarządzanie wersjami.

Kolejne sekcje tego rozdziału i powiązane z nimi instruktaże koncentrują się na szczegółach dotyczących warstwy środowiska uruchomieniowego (kontenery systemu Windows). Wskazówki opisują sposoby wdrażania kontenerów systemu Windows w systemie Windows Server 2016 (i nowszych wersjach) maszyn wirtualnych i Azure Container Instances. Obejmuje to również bardziej zaawansowane platformy PaaS, takie jak Azure App Service i Orchestrator, takie jak usługa Azure Kubernetes Service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikacje monolityczne *mogą* być zoptymalizowane pod kątem chmury

Należy zaznaczyć, że aplikacje monolityczne (aplikacje, które nie są oparte na mikrousługach) *mogą* być aplikacjami zoptymalizowanymi pod kątem chmury. Możesz tworzyć i obsługiwać aplikacje monolityczne, które wykorzystują model przetwarzania w chmurze, korzystając z kombinacji kontenerów, ciągłego dostarczania i DevOps. Jeśli istniejąca aplikacja monolityczna jest odpowiednia dla celów Twojej firmy, można ją modernizacjć i uczynić ją zoptymalizowaną pod kątem chmury.

Podobnie, jeśli aplikacje monolityczne mogą być aplikacjami zoptymalizowanymi pod kątem chmury, inne, bardziej złożone architektury, takie jak aplikacje N-warstwowe, mogą być również nowoczesne jako aplikacje zoptymalizowane pod kątem chmury.

>[!div class="step-by-step"]
>[Poprzedni](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)Następny
>[](what-about-cloud-native-applications.md)
