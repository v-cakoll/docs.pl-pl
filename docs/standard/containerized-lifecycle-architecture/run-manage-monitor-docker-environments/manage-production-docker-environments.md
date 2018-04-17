---
title: Zarządzanie środowisk produkcyjnych Docker
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72ae92c89ed9b51815016205e20b09fc4dced1e1
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-production-docker-environments"></a>Zarządzanie środowisk produkcyjnych Docker

Klaster zarządzania i aranżacji to proces kontrolowanie grupy hostów. Może to obejmować dodawanie i usuwanie hostów z klastra, informacje o bieżącym stanie hostów i kontenerów, pobieranie i uruchamianie i zatrzymywanie procesów. Klaster zarządzania i aranżacji ściśle związany planowania ponieważ planista musi mieć dostęp do każdego hosta w klastrze w celu zaplanowania usług. Z tego powodu tego samego narzędzia jest często używane zarówno w celach.

## <a name="container-service-and-management-tools"></a>Kontener usługi i narzędzia do zarządzania

Usługa kontenera zapewnia szybkie wdrażanie popularnych kontenera open source rozwiązań aranżowania i klastrowania. Aby upewnić się, czy kontenerów aplikacji są w pełni dostosowane używa obrazy usługi Docker. Przy użyciu usługi kontenera, można wdrożyć (obsługiwane przez Mesosphere i Apache Mesos) DC/OS i Docker Swarm klastrów z szablonów usługi Azure Resource Manager lub w portalu Azure, aby upewnić się, że można skalować te aplikacje do tysięcy — nawet dziesiątki tysięcy — z kontenery.

Klastry te są wdrażane za pomocą zestawów skali maszyny wirtualnej Azure, a klastry zalet Azure ofert magazynu i sieci. Aby uzyskać dostęp do usługi kontenera, potrzebujesz subskrypcji platformy Azure. Z usługą kontenera możliwość korzystania z funkcji korporacyjnej Azure zachowując przenośność aplikacji, w tym również na warstwy aranżacji.

Tabela 6-1 zawiera listę popularnych narzędzi do zarządzania związanych z ich orchestrators, planiści i klastrowania platformę.

Narzędzia do zarządzania Docker tabeli 6-1.


| Narzędzia do zarządzania      | Opis           | Orchestrators pokrewne |
|-----------------------|-----------------------|-----------------------|
| Usługi kontenera\(zarządzania interfejsu użytkownika w portalu Azure) | [Usługi kontenera](https://azure.microsoft.com/en-us/services/container-service/) zapewnia łatwy do pobrania uruchomiona w sposób, aby [wdrożyć klaster kontenera na platformie Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) oparte na popularnych orchestrators jak Mesosphere DC/OS, Kubernetes i Docker Swarm. <br /><br /> Usługi kontenera optymalizuje konfiguracji tych platform. Wystarczy wybrać rozmiar, liczby hostów, a wybór narzędzia orchestrator, a usługi kontenera obsługuje wszystkie inne elementy. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Rozwiązanie docker Swarm |
| Docker uniwersalnych płaszczyzny kontroli\(lokalnie lub w chmurze) | [Docker uniwersalnych płaszczyzny kontroli](https://docs.docker.com/v1.11/ucp/overview/) rozwiązanie do zarządzania klastrem korporacyjnej z Docker. Pomaga zarządzać cały klaster z jednego miejsca. <br /><br /> Docker uniwersalnych płaszczyzny kontroli wchodzi w skład produktu o nazwie Docker centrum danych, co zapewnia Docker Swarm, uniwersalnych płaszczyzny kontroli Docker i Docker zaufane rejestru. <br /><br /> Docker centrum danych może być zainstalowana na lokalnym lub pobranego z chmury publicznej, takich jak Azure. | Rozwiązania docker Swarm\(obsługiwane przez usługę kontenera) |
| Chmura docker\(znanej także jako Tutum; chmur SaaS) | [Chmura docker](https://docs.docker.com/docker-cloud/) to usługa zarządzania (SaaS), która zapewnia możliwości aranżacji i rejestru Docker z kompilacji i urządzeń testowych dla obrazów aplikacji Dockerized, narzędzia ułatwiające konfigurowanie i zarządzanie nimi infrastrukturę hosta i funkcje wdrażania ułatwiające automatyzację wdrażania obrazów na konkretnych infrastruktury. Twoje konto chmury Docker SaaS umożliwia nawiązywanie infrastruktury w usłudze kontenera uruchomiony klaster Docker Swarm. | Rozwiązania docker Swarm\(obsługiwane przez usługę kontenera) |
| Mesosphere Marathon\(lokalnie lub w chmurze) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) to platforma aranżacji i harmonogram kontenera klasy produkcji DC/OS i Apache Mesos Mesosphere firmy. <br /><br /> W przypadku Mesos (DC/OS jest oparty na Apache Mesos) do kontroli długotrwałe usług i udostępnia [interfejs użytkownika sieci web do zarządzania procesem i kontener](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Zapewnia narzędzia do zarządzania interfejsu użytkownika sieci web | Mesosphere DC/OS\(oparte na Apache Mesos; obsługiwane przez usługę kontenera) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) obejmuje organizowanie, planowanie i infrastruktura klastra. Jest to platforma open source do automatyzacji wdrażania, skalowanie i operacje kontenerów aplikacji w klastrach hostów, zapewniając skoncentrowane kontenera infrastruktury. | Google Kubernetes\(obsługiwane przez usługę kontenera) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Innym rozwiązaniem dla wdrożenia klastra i zarządzania jest sieć szkieletowa usług Azure. [Sieć szkieletowa usług](https://azure.microsoft.com/en-us/services/service-fabric/) jest to platforma mikrousług firmy Microsoft, która obejmuje aranżacji kontenera, jak i deweloperów programowania modeli do tworzenia wysoce skalowalnych mikrousług aplikacji. Sieć szkieletowa usług obsługuje Docker w bieżącej wersji zapoznawczych systemu Linux, podobnie jak w [Podgląd sieci szkieletowej usług w systemie Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)i kontenerów Windows [w następnej wersji](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Narzędzia do zarządzania sieci szkieletowej usług są następujące:

-   [Portal Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operacji związanych z klastrem (Tworzenie/aktualizowania/usuwania) klastra lub skonfigurować swoją infrastrukturę (maszyny wirtualne, usługi równoważenia obciążenia sieci, itp.)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) jest specjalne sieci web narzędzia interfejsu użytkownika, który zawiera informacje na temat technologii i niektóre operacje w klastrze usługi sieć szkieletowa z punktu widzenia węzłów/maszyn wirtualnych i aplikacji i usług punktu widzenia.


>[!div class="step-by-step"]
[Poprzednie] (run-microservices-based-applications-in-production.md) [dalej] (monitor konteneryzowanych aplikacji services.md)
