---
title: Zarządzanie środowiskami produkcyjnymi platformy Docker
description: Poznaj najważniejsze kwestie związane z zarządzaniem środowiskiem produkcyjnym opartym na kontenerach.
ms.date: 02/15/2019
ms.openlocfilehash: 7d10f670745f8bac1084b8c33c5acde67bac6229
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295623"
---
# <a name="manage-production-docker-environments"></a>Zarządzanie środowiskami produkcyjnymi platformy Docker

Zarządzanie klastrem i aranżacja to proces sterowania grupą hostów. Może to dotyczyć dodawania i usuwania hostów z klastra, uzyskiwania informacji o bieżącym stanie hostów i kontenerów oraz uruchamiania i zatrzymywania procesów. Zarządzanie klastrem i aranżacja są ściśle powiązane z planowaniem, ponieważ harmonogram musi mieć dostęp do każdego hosta w klastrze w celu zaplanowania usług. Z tego powodu to samo narzędzie jest często używane w obu celach.

## <a name="container-service-and-management-tools"></a>Usługa kontenerów i narzędzia do zarządzania

Usługa Container Service umożliwia szybkie wdrażanie popularnych rozwiązań typu "klaster" typu "open source" i "aranżacja". Używa obrazów platformy Docker, aby upewnić się, że kontenery aplikacji są w pełni przenośne. Za pomocą usługi Container Service można wdrożyć systemy DC/OS (obsługiwane przez mesosphere i Apache Mesos) oraz klastry Docker Swarm z szablonami Azure Resource Manager lub Azure Portal, aby mieć pewność, że można skalować te aplikacje do tysięcy — nawet dziesiątki tysięcy — z opakowania.

Te klastry są wdrażane przy użyciu usługi Azure Virtual Machine Scale Sets, a klastry wykorzystują oferty dotyczące sieci i magazynu platformy Azure. Aby uzyskać dostęp do usługi Container Service, musisz mieć subskrypcję platformy Azure. Usługa Container Service umożliwia korzystanie z funkcji klasy korporacyjnej platformy Azure z zachowaniem możliwości przenoszenia aplikacji, w tym w warstwach aranżacji.

W tabeli 6-1 przedstawiono typowe narzędzia do zarządzania związane z koordynatorami, harmonogramami i platformą klastrowania.

**Tabela 6-1**. Narzędzia do zarządzania platformy Docker

| Narzędzia do zarządzania | Opis | Powiązane usługi Orchestrator |
|------------------|-------------|-----------------------|
| [Azure Monitor kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Dedykowane narzędzie do zarządzania Kubernetes platformy Azure | Usługi Azure Kubernetes Services (AKS) |
| [Interfejs użytkownika sieci Web Kubernetes (pulpit nawigacyjny)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Narzędzie do zarządzania Kubernetes, które umożliwia monitorowanie lokalnego klastra Kubernetes i zarządzanie nim | Usługa Azure Kubernetes Service (AKS)<br/>Kubernetes lokalny |
| [Azure Portal Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Service Fabric Explorer platformy Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Wersja online i klasyczna do zarządzania klastrami Service Fabric, na platformie Azure, lokalnie i w innych chmurach | Azure Service Fabric |
| [Monitorowanie kontenerów (Azure Monitor)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Ogólne rozwiązanie do monitorowania zarządzania kontenerami. Może zarządzać klastrami Kubernetes za [Azure monitor kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Usługa Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS i innych. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Kolejną opcją dla wdrożenia klastra i zarządzania jest usługa Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) to platforma mikrousług firmy Microsoft, która obejmuje aranżację kontenera, a także modele programowania dla deweloperów, które umożliwiają tworzenie wysoce skalowalnych aplikacji mikrousług. Service Fabric obsługuje platformę Docker w kontenerach systemu Linux i Windows oraz mogą działać na serwerach z systemami Windows i Linux.

Poniżej przedstawiono Service Fabric narzędzia do zarządzania:

- [Azure Portal dla Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operacji związanych z klastrem (Tworzenie/aktualizowanie/usuwanie) klastra lub Konfigurowanie jego infrastruktury (maszyn wirtualnych, modułu równoważenia obciążenia, sieci itp.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) to WYSPECJALIZOWANY interfejs użytkownika sieci Web i narzędzie do obsługi wielu platform, które zapewnia wgląd w dane i pewne operacje w klastrze Service Fabric, z punktu widzenia węzłów/maszyn wirtualnych oraz z punktu widzenia aplikacji i usług.

>[!div class="step-by-step"]
>[Poprzedni](run-microservices-based-applications-in-production.md)Następny
>[](monitor-containerized-application-services.md)
