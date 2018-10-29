---
title: Zarządzanie środowiskami produkcyjnymi platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3bafdd9f6a6aa4f850fd28b6315e68c643d1f8c0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202858"
---
# <a name="manage-production-docker-environments"></a>Zarządzanie środowiskami produkcyjnymi platformy Docker

Zarządzanie klastrami i Aranżacja to proces nadzoru nad grupy hostów. Może to obejmować dodawanie i usuwanie hostów z klastra, uzyskiwanie informacji o bieżącym stanie hostów i kontenerów i uruchamianie i zatrzymywanie procesów. Zarządzanie klastrami i Aranżacja są ściśle powiązane planowania, ponieważ Harmonogram musi mieć dostęp do każdego hosta w klastrze w celu planowania usług. Z tego powodu tego samego narzędzia jest często używane zarówno w celach.

## <a name="container-service-and-management-tools"></a>Narzędzia zarządzania i usługi kontenerów

Container Service umożliwia szybkie wdrażanie rozwiązań klastrów i organizowania popularnych kontenerów typu open source. Aby upewnić się, że kontenery Twojej aplikacji są całkowicie przenośne używa obrazów platformy Docker. Za pomocą usługi Container Service, można wdrażać (obsługiwane przez system Mesosphere i Apache Mesos) DC/OS i Docker Swarm klastrów przy użyciu szablonów usługi Azure Resource Manager lub witryny Azure portal, aby upewnić się, że możesz skalować te aplikacje do tysięcy — nawet dziesiątków tysięcy — z kontenery.

Klastry te są wdrażane przy użyciu usługi Azure Virtual Machine Scale Sets i korzystają z ofert sieci i magazynu na platformie Azure. Aby uzyskać dostęp do usługi Container Service, musisz mieć subskrypcję platformy Azure. Usługa Container Service możesz korzystać z zalet funkcji przeznaczonych dla przedsiębiorstw platformy Azure zachowując jednocześnie przenośność aplikacji, w tym w warstwach aranżacji.

Tabela 6-1 zawiera listę popularnych narzędzi do zarządzania związanych z ich koordynatorów, harmonogramów i klastrowania platformy.

Tabela 6-1: narzędzia do zarządzania platformy Docker


| Narzędzia do zarządzania      | Opis           | Powiązane koordynatorów |
|-----------------------|-----------------------|-----------------------|
| Container Service\(zarządzania interfejsu użytkownika w witrynie Azure portal) | [Usługa kontenera](https://azure.microsoft.com/services/container-service/) zapewnia łatwy w użyciu można pobrać uruchomiona w sposób, aby [wdrażanie klastra kontenera platformy Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) oparte na popularnych koordynatorów, takich jak Mesosphere DC/OS, Kubernetes i Docker Swarm. <br /><br /> Container Service optymalizuje konfigurację z tych platform. Wystarczy wybrać rozmiar, liczbę hostów i narzędzia koordynatora, a usługa kontenerów zajmuje się całą resztą. | System mesosphere DC/OS <br /><br /> Rozwiązania Kubernetes <br /><br /> Rozwiązanie docker Swarm |
| Uniwersalne płaszczyznę kontroli platformy docker\(w środowisku lokalnym lub w chmurze) | [Uniwersalne płaszczyznę kontroli platformy docker](https://docs.docker.com/v1.11/ucp/overview/) jest rozwiązaniem do zarządzania klastrem przeznaczonych dla przedsiębiorstw z platformy Docker. Ułatwia ona zarządzanie cały klaster z jednego miejsca. <br /><br /> Uniwersalne płaszczyznę kontroli platformy docker jest zawarte w ramach produktu o nazwie Docker Datacenter, która zapewnia rozwiązania Docker Swarm, Docker Universal płaszczyznę kontroli i Docker Trusted Registry. <br /><br /> Docker Datacenter mogą być zainstalowane w środowisku lokalnym lub z chmury publicznej, takich jak platforma Azure. | Docker Swarm\(obsługiwane przez usługę kontenera) |
| Rozwiązań docker Cloud\(znany także jako Tutum; w chmurze SaaS) | [Rozwiązań docker Cloud](https://docs.docker.com/docker-cloud/) to usługa zarządzania (SaaS), która oferuje możliwości aranżacji i rejestr platformy Docker przy użyciu kompilacji i testowania urządzenia w przypadku obrazów aplikacji Dockerized narzędzia ułatwiające konfigurowanie i zarządzanie nimi infrastrukturę hosta i funkcje wdrażania, ułatwiające automatyzację wdrażania obrazów na konkretnych infrastruktury. Możesz połączyć swoje konto SaaS rozwiązań Docker Cloud do infrastruktury w usłudze kontenera uruchomiony klaster Docker Swarm. | Docker Swarm\(obsługiwane przez usługę kontenera) |
| Mesosphere Marathon\(w środowisku lokalnym lub w chmurze) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) platformę klasy produkcyjnej kontenera aranżacji i harmonogram dotyczy Mesosphere DC/OS i Apache Mesos. <br /><br /> Współdziała ona z Mesos (DC/OS opiera się na Apache Mesos) do sterowania długotrwałych usług i zapewnia [interfejs użytkownika sieci web do zarządzania procesem i kontener](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Zapewnia narzędzia do zarządzania interfejsu użytkownika sieci web | System mesosphere DC/OS\(oparciu Apache Mesos; obsługiwane przez usługi Container Service) |
| Google Kubernetes | [Kubernetes](https://kubernetes.io/docs/user-guide/ui/#dashboard-access) obejmuje organizowanie, planowanie i infrastruktura klastra. Jest to platforma typu open source do automatyzacji wdrażania, skalowania i działanie kontenerów aplikacji w klastrach hostów, zapewniając zorientowany kontenera infrastruktury. | Google Kubernetes\(obsługiwane przez usługę kontenera) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

W przypadku wdrażania klastra i Zarządzanie inną możliwością jest usługi Azure Service Fabric. [Usługa Service Fabric](https://azure.microsoft.com/services/service-fabric/) jest to platforma mikrousług firmy Microsoft zawiera aranżacji kontenerów, a także dla deweloperów programowania modele do tworzenia aplikacji mikrousług w wysokim stopniu skalowalności. Usługa Service Fabric obsługuje platformy Docker w bieżącej wersji zapoznawczych systemu Linux, podobnie jak w [w wersji zapoznawczej usługi Service Fabric w systemie Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)i kontenerów Windows [w następnej wersji](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Poniżej przedstawiono narzędzia do zarządzania usługi Service Fabric:

-   [Witryna Azure portal dla usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operacji związanych z klastrem (Tworzenie/aktualizowanie/usuwanie) klastra lub skonfigurować jego infrastruktury (maszyny wirtualne, usługi równoważenia obciążenia, sieci itp.)

-   [Usługa Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) jest web wyspecjalizowane narzędzia interfejsu użytkownika, który zawiera szczegółowe informacje i niektóre operacje w klastrze usługi Service Fabric z punktu widzenia węzły/maszyny wirtualne i usługi aplikacji i punktu widzenia.


>[!div class="step-by-step"]
[Poprzednie](run-microservices-based-applications-in-production.md)
[dalej](monitor-containerized-application-services.md)
