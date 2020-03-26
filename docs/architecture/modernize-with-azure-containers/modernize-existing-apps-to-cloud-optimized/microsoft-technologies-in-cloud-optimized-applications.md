---
title: Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury
ms.date: 04/28/2018
ms.openlocfilehash: c5222ba13258f9c8a40ca3b9ce240aeb9f41da63
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546513"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie firmy Microsoft w aplikacjach zoptymalizowanych pod kątem chmury

Na poniższej liście opisano narzędzia, technologie i rozwiązania, które są rozpoznawane jako wymagania dotyczące aplikacji zoptymalizowanych pod kątem chmury. Elementy zoptymalizowane pod kątem chmury można przyjmować wybiórczo lub stopniowo, w zależności od priorytetów.

- **Infrastruktura chmury:** infrastruktura zapewniająca platformę obliczeniową, system operacyjny, sieć i pamięć masową. Platforma Microsoft Azure jest pozycjonowana na tym poziomie.

- **Środowisko uruchomieniowe:** Ta warstwa zapewnia środowisko do uruchomienia aplikacji. Jeśli używasz kontenerów, ta warstwa jest zwykle oparta na [programie Docker Engine](https://docs.docker.com/engine/), działającym na hostach systemu Linux lub na hostach systemu Windows. ([Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) są obsługiwane począwszy od systemu Windows Server 2016. Kontenery systemu Windows to najlepszy wybór dla istniejących aplikacji .NET Framework, które działają w systemie Windows.)

- **Chmura zarządzana:** Wybierając opcję zarządzanej chmury, można uniknąć wydatków i złożoności zarządzania i obsługi podstawowej infrastruktury, maszyn wirtualnych, poprawek systemu operacyjnego i konfiguracji sieci. Jeśli zdecydujesz się przeprowadzić migrację przy użyciu usługi IaaS, użytkownik jest odpowiedzialny za wszystkie te zadania i za związane z nimi koszty. W opcji zarządzanej chmury można zarządzać tylko aplikacjami i usługami, które opracowywać. Dostawca usług w chmurze zazwyczaj zarządza wszystkim innym. Przykłady zarządzanych usług w chmurze na platformie Azure obejmują [usługę Azure SQL Database](https://azure.microsoft.com/services/sql-database), pamięć [podręczną Usługi Azure Redis](https://azure.microsoft.com/services/cache/)Cache, [usługę Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [usługę Azure Storage](https://azure.microsoft.com/services/storage/), usługę Azure Database [for MySQL,](https://azure.microsoft.com/services/mysql/) [usługę Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [usługę Azure Active Directory](https://azure.microsoft.com/services/active-directory/)oraz zarządzane usługi obliczeniowe, takie jak [zestawy skalowania maszyn wirtualnych,](https://azure.microsoft.com/services/virtual-machine-scale-sets/) [usługę Azure App Service](https://azure.microsoft.com/services/app-service/)i usługę Azure [Kubernetes](https://azure.microsoft.com/services/container-service/).

- **Tworzenie aplikacji:** Można wybrać z wielu języków podczas tworzenia aplikacji, które są uruchamiane w kontenerach. Ten przewodnik koncentruje się na [.NET](https://dotnet.microsoft.com), ale można tworzyć aplikacje oparte na kontenerach przy użyciu innych języków, takich jak Node.js, Python, Spring/Java lub Go.

- **Monitorowanie, telemetria, rejestrowanie i inspekcja:** możliwość monitorowania i inspekcji aplikacji i kontenerów, które są uruchomione w chmurze ma kluczowe znaczenie dla każdej aplikacji zoptymalizowanej pod kątem chmury. [Usługa Azure Application Insights](https://azure.microsoft.com/services/application-insights/) i [pakiet Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) to główne narzędzia firmy Microsoft, które zapewniają monitorowanie i inspekcję aplikacji zoptymalizowanych pod kątem chmury.

- **Inicjowanie obsługi administracyjnej:** Narzędzia automatyzacji pomagają aprowizować infrastrukturę i wdrażać aplikację w wielu środowiskach (produkcja, testowanie, przemieszczanie). Za pomocą narzędzi, takich jak Chef i Puppet, można zarządzać konfiguracją i środowiskiem aplikacji. Warstwa ta może być również zaimplementowana przy użyciu prostszych i bardziej bezpośrednich metod. Na przykład można wdrożyć bezpośrednio przy użyciu narzędzi interfejsu wiersza polecenia platformy Azure (Azure CLI), a następnie użyć potoków zarządzania ciągłym wdrażaniem i wydaniem w [usługach Azure DevOps.](https://azure.microsoft.com/services/devops/)

- **Cykl życia aplikacji:** [Usługi Azure DevOps](https://azure.microsoft.com/services/devops/) i inne narzędzia, takie jak Jenkins, są wbudowanymi serwerami automatyzacji, które ułatwiają implementowanie potoków ciągłej integracji/ciągłego wdrażania, w tym zarządzanie wersjami.

Następne sekcje tego rozdziału i związane z nimi wskazówki koncentrują się w szczególności na szczegółach dotyczących warstwy środowiska wykonawczego (Kontenery systemu Windows). W wskazówki opisano sposoby wdrażania kontenerów systemu Windows na maszynach wirtualnych systemu Windows Server 2016 (i nowszych wersjach) i wystąpieniach kontenerów platformy Azure. Obejmuje również bardziej zaawansowane platformy PaaS, takie jak usługa Azure App Service i orchestrator, takie jak usługa Azure Kubernetes.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikacje monolityczne *mogą* być zoptymalizowane pod kątem chmury

Należy podkreślić, że aplikacje monolityczne (aplikacje, które nie są oparte na mikrousługach) *mogą* być aplikacjami zoptymalizowanymi pod kątem chmury. Można tworzyć i obsługiwać aplikacje monolityczne, które korzystają z modelu przetwarzania w chmurze przy użyciu kombinacji kontenerów, ciągłego dostarczania i DevOps. Jeśli istniejąca aplikacja monolityczne jest odpowiednia dla twoich celów biznesowych, możesz ją zmodernizować i uczynić zoptymalizowaną pod kątem chmury.

Podobnie jeśli aplikacje monolityczne mogą być aplikacjami zoptymalizowanymi pod kątem chmury, inne, bardziej złożone architektury, takie jak aplikacje n-warstwowe, mogą być również modernizowane jako aplikacje zoptymalizowane pod kątem chmury.

>[!div class="step-by-step"]
>[Poprzedni](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[następny](what-about-cloud-native-applications.md)
