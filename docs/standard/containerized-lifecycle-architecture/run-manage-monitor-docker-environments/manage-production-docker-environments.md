---
title: Zarządzanie środowiskami produkcyjnymi platformy Docker
description: Ustal, jakimi kluczowych zagadnieniach związanych z zarządzaniem do środowiska produkcyjnego opartych na kontenerach.
ms.date: 02/15/2019
ms.openlocfilehash: 7d10f670745f8bac1084b8c33c5acde67bac6229
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641075"
---
# <a name="manage-production-docker-environments"></a>Zarządzanie środowiskami produkcyjnymi platformy Docker

Zarządzanie klastrami i Aranżacja to proces nadzoru nad grupy hostów. Może to obejmować dodawanie i usuwanie hostów z klastra, uzyskiwanie informacji o bieżącym stanie hostów i kontenerów i uruchamianie i zatrzymywanie procesów. Zarządzanie klastrami i Aranżacja są ściśle powiązane planowania, ponieważ Harmonogram musi mieć dostęp do każdego hosta w klastrze w celu planowania usług. Z tego powodu tego samego narzędzia jest często używane zarówno w celach.

## <a name="container-service-and-management-tools"></a>Narzędzia zarządzania i usługi kontenerów

Container Service umożliwia szybkie wdrażanie rozwiązań klastrów i organizowania popularnych kontenerów typu open source. Aby upewnić się, że kontenery Twojej aplikacji są całkowicie przenośne używa obrazów platformy Docker. Za pomocą usługi Container Service, można wdrażać (obsługiwane przez system Mesosphere i Apache Mesos) DC/OS i Docker Swarm klastrów przy użyciu szablonów usługi Azure Resource Manager lub witryny Azure portal, aby upewnić się, że możesz skalować te aplikacje do tysięcy — nawet dziesiątków tysięcy — z kontenery.

Klastry te są wdrażane przy użyciu usługi Azure Virtual Machine Scale Sets i korzystają z ofert sieci i magazynu na platformie Azure. Aby uzyskać dostęp do usługi Container Service, musisz mieć subskrypcję platformy Azure. Usługa Container Service możesz korzystać z zalet funkcji przeznaczonych dla przedsiębiorstw platformy Azure zachowując jednocześnie przenośność aplikacji, w tym w warstwach aranżacji.

Tabela 6-1 zawiera listę popularnych narzędzi do zarządzania związanych z ich koordynatorów, harmonogramów i klastrowania platformy.

**Tabela 6-1**. Narzędzia do zarządzania platformy docker

| Narzędzia do zarządzania | Opis | Powiązane koordynatorów |
|------------------|-------------|-----------------------|
| [Usługa Azure Monitor dla kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Narzędzie do zarządzania usługi Kubernetes usługi Azure w wersji dedykowanej | Usługi Azure Kubernetes (AKS) |
| [Interfejs użytkownika sieci Web rozwiązania Kubernetes (pulpit nawigacyjny)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Narzędzia do zarządzania usługi Kubernetes, monitorowania i zarządzania lokalnego klastra Kubernetes | Usługa Azure Kubernetes Service (AKS)<br/>Lokalne usługi Kubernetes |
| [Witryna Azure portal dla usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Wersja online i klasycznych za zarządzanie klastrami usługi Service Fabric, na platformie Azure, lokalnie, rozwoju lokalnych i innych chmur | Azure Service Fabric |
| [(Usługa Azure Monitor) do monitorowania kontenerów](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Y zarządzania kontener ogólnego rozwiązania do monitorowania. Można zarządzać klastrami usługi Kubernetes za pomocą [usługi Azure Monitor dla kontenerów](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Usługa Azure Kubernetes Service (AKS)<br/>System mesosphere DC/OS i innych. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

W przypadku wdrażania klastra i Zarządzanie inną możliwością jest usługi Azure Service Fabric. [Usługa Service Fabric](https://azure.microsoft.com/services/service-fabric/) jest to platforma mikrousług firmy Microsoft zawiera aranżacji kontenerów, a także dla deweloperów programowania modele do tworzenia aplikacji mikrousług o wysokim stopniu skalowalności. Usługa Service Fabric obsługuje platformę Docker w systemie Linux i Windows kontenery i mogą być uruchamiane w przypadku serwerów z systemami Windows i Linux.

Poniżej przedstawiono narzędzia do zarządzania usługi Service Fabric:

- [Witryna Azure portal dla usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operacji związanych z klastrem (Tworzenie/aktualizowanie/usuwanie) klastra lub skonfigurować jego infrastruktury (maszyny wirtualne, usługi równoważenia obciążenia, sieci itp.)

- [Usługa Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) to wyspecjalizowana sieci web interfejsu użytkownika i narzędzi dla wielu platform z pulpitu, który zawiera szczegółowe informacje i niektóre operacje w klastrze usługi Service Fabric z punktu widzenia węzły/maszyny wirtualne i usługi aplikacji i punktu widzenia.

>[!div class="step-by-step"]
>[Poprzednie](run-microservices-based-applications-in-production.md)
>[dalej](monitor-containerized-application-services.md)
