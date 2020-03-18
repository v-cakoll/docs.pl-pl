---
title: Zarządzanie środowiskami produkcyjnymi platformy Docker
description: Poznaj kluczowe punkty zarządzania środowiskiem produkcyjnym opartym na kontenerach.
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834504"
---
# <a name="manage-production-docker-environments"></a>Zarządzanie środowiskami produkcyjnymi platformy Docker

Zarządzanie klastrami i aranżacja to proces kontrolowania grupy hostów. Może to obejmować dodawanie i usuwanie hostów z klastra, uzyskiwanie informacji o bieżącym stanie hostów i kontenerów oraz uruchamianie i zatrzymywanie procesów. Zarządzanie klastrami i aranżacja są ściśle powiązane z harmonogramem, ponieważ harmonogram musi mieć dostęp do każdego hosta w klastrze, aby zaplanować usługi. Z tego powodu to samo narzędzie jest często używane do obu celów.

## <a name="container-service-and-management-tools"></a>Narzędzia do obsługi kontenerów i zarządzania

Usługa kontenerowa zapewnia szybkie wdrażanie popularnych rozwiązań do klastrowania kontenerów typu open source i aranżacji. Używa obrazów platformy Docker, aby upewnić się, że kontenery aplikacji są w pełni przenośne. Korzystając z usługi Container Service, można wdrożyć klasdc/os (obsługiwane przez Mezosfery i Apache Mesos) i klastry Docker Swarm z szablonami usługi Azure Resource Manager lub portal Azure, aby zapewnić skalowanie tych aplikacji do tysięcy — nawet dziesiątki tysięcy — kontenerów.

Te klastry są wdrażane za pomocą zestawów skali maszyny wirtualnej Azure, a podczas pracy korzystają z ofert magazynu i pracy w sieci na platformie Azure. Aby uzyskać dostęp do usługi container service, potrzebujesz subskrypcji platformy Azure. Usługa kontenerowa umożliwia korzystanie z funkcji platformy Azure klasy korporacyjnej przy jednoczesnym zachowaniu przenośności aplikacji, w tym na warstwach aranżacji.

Tabela 6-1 zawiera listę typowych narzędzi zarządzania związanych z ich koordynatorami, planistami i platformą klastrowania.

**Tabela 6-1**. Narzędzia do zarządzania platformą Docker

| Narzędzia do zarządzania | Opis | Podobne orkiestratory |
|------------------|-------------|-----------------------|
| [Usługa Azure Monitor dla kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Dedykowane narzędzie do zarządzania kubernetes platformy Azure | Usługi Azure Kubernetes (AKS) |
| [Interfejs użytkownika sieci Web kubernetes (pulpit nawigacyjny)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Narzędzie do zarządzania Kubernetes, może monitorować i zarządzać lokalnym klastrem Kubernetes | Azure Kubernetes Service (AKS)<br/>Lokalne Kubernetes |
| [Portal Azure dla sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Eksplorator sieci szkieletowej usługi Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Wersja online i klasyczna do zarządzania klastrami sieci szkieletowej usług na platformie Azure, lokalnie, w środowisku lokalnym i w innych chmurach | Azure Service Fabric |
| [Monitorowanie kontenerów (usługa Azure Monitor)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Ogólne rozwiązanie do monitorowania zarządzania kontenerami. Może zarządzać klastrami Kubernetes za pośrednictwem [usługi Azure Monitor dla kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mezosfery DC/OS i innych. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Innym wyborem dla wdrażania klastrów i zarządzania jest azure sieci szkieletowej usług. [Sieć szkieletowa usług](https://azure.microsoft.com/services/service-fabric/) jest platformą mikrousług firmy Microsoft, która zawiera aranżacji kontenerów, jak również deweloperów programowania modeli do tworzenia aplikacji mikrousług o wysokiej skalowalnej. Sieć szkieletowa usług obsługuje platformę Docker w kontenerach systemu Linux i Windows i może działać na serwerach Windows i Linux.

Oto narzędzia do zarządzania siecią szkieletową usług:

- Usługa Azure portal dla operacji klastra [sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) (tworzenie/aktualizowanie/usuwanie) klastra lub konfigurowania jego infrastruktury (maszyny wirtualne, moduł równoważenia obciążenia, sieci itp.)

- [Eksplorator sieci szkieletowej usługi Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) to wyspecjalizowane narzędzie wieloplatformowe interfejsu internetowego i pulpitu, które zapewnia szczegółowe informacje i niektóre operacje w klastrze sieci szkieletowej usług, z punktu widzenia węzłów/maszyn wirtualnych oraz z punktu widzenia aplikacji i usług.

>[!div class="step-by-step"]
>[Poprzedni](run-microservices-based-applications-in-production.md)
>[następny](monitor-containerized-application-services.md)
