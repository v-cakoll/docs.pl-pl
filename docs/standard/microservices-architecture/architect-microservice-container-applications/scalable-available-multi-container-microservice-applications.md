---
title: Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 25175e2a4409d53be412ae72be5af1c07c3ec68d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199667"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności

Przy użyciu koordynatorów aplikacji gotowych do produkcji jest istotne, jeśli aplikacja jest oparta na mikrousługach lub po prostu podzielone między wiele kontenerów. Jak wprowadzona wcześniej w podejściu opartych na mikrousługach, każda mikrousługa jest właścicielem jej modelu i danych tak, aby go autonomicznego od środowisk programowania i wdrażania punktu widzenia. Ale nawet w przypadku bardziej tradycyjny aplikację która składa się z wielu usług (np. SOA), ponadto będziesz mieć wiele kontenerów i usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone i skalowanie w poziomie i zarządzać; w związku z tym bezwzględnie konieczne koordynatora, jeśli chcesz mieć aplikację obsługującą wiele kontenerów gotowe do produkcji i skalowalny.

Rysunek 4-23 przedstawiono wdrożenie w klastrze aplikacji składających się z wielu mikrousług (kontenery).

![](./media/image23.PNG)

**Rysunek 4-23**. Klaster kontenerów

Wygląda jak algorytmu. Ale jak możesz obsługi równoważeniem obciążenia, routingu i organizowanie te składają się aplikacje?

Zwykły aparat platformy Docker w jednym hostów platformy Docker spełnia potrzeby zarządzania wystąpieniami pojedynczy obraz na jednym hoście, ale znajduje się krótki w przypadku zarządzania wieloma kontenerami wdrażane na wielu hostach w przypadku bardziej złożonych aplikacji rozproszonych. W większości przypadków należy to platforma zarządzania, która będzie automatycznie uruchom kontenery, kontenery skalowalnego w poziomie za pomocą wielu wystąpień na obrazie, zawieszać je lub wyłączać je w razie i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieci i danych Magazyn.

Czegoś Zarządzanie poszczególne kontenery lub bardzo proste aplikacje złożone i Przenieś kierunku większych aplikacje dla przedsiębiorstw przy użyciu mikrousług, należy go włączyć do aranżacji i klastrowanie platform.

Z architektury i projektowania punktu widzenia Jeśli tworzysz duże przedsiębiorstwo składa się z aplikacji opartych na mikrousługach, warto zapoznać się z następujących platform i produktów, które obsługuje zaawansowane scenariusze:

**Klastry i koordynatorów**. Kiedy należy skalować aplikacje na wielu hostach Docker, jak w przypadku dużych aplikacji opartych na mikrousługach, koniecznie będzie można zarządzać tymi hostami jako pojedynczy klaster, zapewniając abstrakcyjność złożoność podstawowej platformy. To, co zapewnia klastry kontenerów i koordynatorów. Przykładami koordynatorów są usługi Azure Service Fabric, Kubernetes, Docker Swarm i Mesosphere DC/OS. Ostatnie trzy orkiestratorów typu open source są dostępne w systemie Azure za pomocą usługi Azure Container Service.

**Planiści**. *Planowanie* oznacza, że mają możliwość, aby administrator mógł Uruchom kontenery w klastrze, dzięki czemu zapewniają także interfejs użytkownika. Harmonogram klastra ma kilka obowiązki: wydajnie korzystać z zasobów klastra, aby ustawić ograniczenia podana przez użytkownika, do wydajne Równoważenie obciążenia kontenerów w węzłach lub hosty i być odporne na błędy przy jednoczesnym zapewnieniu wysokiego dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczane przez różnych dostawców często podać oba zestawy funkcji. Na poniższej liście przedstawiono najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Te koordynatorów zazwyczaj są oferowane w chmurach publicznych, takich jak platforma Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania dla kontenera, klastrowanie, aranżację i planowanie

Rozwiązania Kubernetes

![Logo rozwiązania Kubernetes](./media/image24.png)

> Kubernetes to produkt typu open source, który zapewnia funkcje z zakresu od infrastruktury klastra i harmonogramów możliwości organizowanie kontenerów. Dzięki temu można zautomatyzować wdrażanie, skalowanie i działanie kontenerów aplikacji w klastrach hostów.
>
> Usługa Kubernetes zapewnia kontener skoncentrowane na infrastrukturę, która grupuje kontenery aplikacji w jednostki logiczne, aby ułatwić zarządzanie i odnajdywania.
>
> Kubernetes to dojrzała w systemie Linux, mniej dojrzałe w Windows.

Rozwiązanie docker Swarm

![Docker Swarm logo](./media/image25.png)

> Docker Swarm umożliwia planowanie kontenerów platformy Docker i klastra. Przy użyciu koordynatora Swarm, można włączyć pulę hostów platformy Docker do pojedynczego wirtualnego hosta platformy Docker. Klientów można wprowadzać żądań interfejsu API do Swarm w taki sam sposób, czy działają na hostach, co oznacza, że Swarm ułatwia aplikacji do skalowania na wielu hostach.
>
> Rozwiązanie docker Swarm jest produktem docker, firma.
>
> V1.12 platformy docker lub nowszej można uruchomić trybu macierzystego i wbudowanych Swarm.

System mesosphere DC/OS

![System mesosphere DC/OS logo](./media/image26.png)

> Mesosphere Enterprise DC/OS (oparte na Apache Mesos) to platforma gotowe do produkcji do uruchamiania kontenerów i aplikacji rozproszonych.
>
> DC/OS polega na abstrakcyjność zbiór zasobów dostępnych w klastrze oraz udostępniania tych zasobów korzystających z jego składników. Platforma Marathon zwykle jest używana harmonogramu zintegrowana z usługą platformy DC/OS.
>
> DC/OS jest dojrzała w systemie Linux, mniej dojrzałe w Windows.

Azure Service Fabric

![Logo usługi Azure Service Fabric](./media/image27.png)

> [Usługa Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do tworzenia aplikacji. Jest [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z usług i służąca do tworzenia klastrów maszyn. Usługi można wdrożyć usługi Service Fabric, jako kontenery lub procesy zwykły. Jest to możliwe nawet różne usługi w procesach usługi w kontenerach w tej samej aplikacji i klastra.
>
> Usługa Service Fabric udostępnia dodatkowe i opcjonalnie normatywne [modeli programowania usługi Service Fabric ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) takich jak [usług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) i [elementów Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric to dojrzała w Windows (lat ewolucji w Windows), mniej dojrzałe w systemie Linux. 
> Kontenerów systemów Linux i Windows są obsługiwane w usłudze Service Fabric od 2017 r.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Przy użyciu koordynatorów opartych na kontenerach, w systemie Microsoft Azure

Kilku dostawców chmury oferują obsługę kontenerów platformy Docker oraz klastrów platformy Docker oraz obsługę aranżacji, w tym Microsoft Azure, Amazon EC2 Container Service i Google kontenera aparatu. Microsoft Azure obsługuje Docker klastra i programu orchestrator za pomocą usługi Azure Container Service (ACS), zgodnie z opisem w następnej sekcji.

Inną możliwością jest Microsoft Azure Service Fabric (jest to platforma mikrousług), który również obsługuje platformę Docker oparty na systemie Linux i kontenerów Windows używać. Usługa Service Fabric działa na platformie Azure lub innych chmur i działa także [lokalnych](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Za pomocą usługi Azure Container Service

Klaster Docker pul wielu hostów platformy Docker i przedstawia je w postaci jednego wirtualnego hosta platformy Docker, aby umożliwić wdrażanie wielu kontenerów do klastra. Klaster będzie obsługiwać wszystkie złożonego zarządzania żmudne procesy, takie jak skalowalność, kondycji i tak dalej. Rysunek 4-24 reprezentuje, jak klastra platformy Docker dla aplikacji złożone mapuje do usługi Azure Container Service (ACS).

Usługi ACS umożliwia uproszczenie tworzenia, konfiguracji i zarządzania klastrem maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania konteneryzowanych aplikacji. Użycie zoptymalizowanej konfiguracji popularnych narzędzi planowania i organizowania typu open source, ACS umożliwia używanie posiadanych umiejętności lub sięganie na treść duży i rosnący zasób wiedzy społeczności, wdrażanie i zarządzanie nimi opartych na kontenerach aplikacje w systemie Microsoft Azure .

Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi typu open source klastrowania platformy Docker i technologii pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, która oferuje przenośność kontenerów i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a usługa kontenerów zajmuje się całą resztą.

![](./media/image28.png)

**Rysunek 4-24**. Klastrowanie opcje dostępne w usłudze Azure Container Service

Usługi ACS korzysta z obrazów platformy Docker, aby upewnić się, że kontenery Twojej aplikacji są całkowicie przenośne. Obsługuje ona wybranych platform aranżacji typu open source, takich jak (obsługiwane przez rozwiązania Apache Mesos) DC/OS, Kubernetes (pierwotnie utworzona przez firmę Google) i Docker Swarm, aby upewnić się, że te aplikacje mogą być skalowane do tysięcy lub nawet dziesiątków tysięcy kontenerów.

Azure Container service pozwala móc korzystać z funkcji przeznaczonych dla przedsiębiorstw platformy Azure, zachowując jednocześnie przenośność aplikacji, w tym w warstwach aranżacji.

![](./media/image29.png)

**Rysunek 4-25**. Orkiestratorów w usłudze ACS

Jak pokazano w rysunek 4-25, Azure Container Service jest po prostu infrastrukturę platformy Azure w celu wdrożenia rozwiązania DC/OS, Kubernetes lub Docker Swarm, ale ACS nie implementuje żadnych dodatkowych programu orchestrator. W związku z tym usługi ACS nie jest orkiestratorem jako takie, infrastruktury, który wykorzystuje istniejące orkiestratorów typu open source dla kontenerów.

Z punktu widzenia użycia celem usługi Azure Container Service jest zapewnienie środowiska hostingu kontenerów za pomocą popularnych narzędzi typu open source i technologii. W tym celu udostępnia standardowe punkty końcowe interfejsu API dla wybranego koordynatora. Korzystając z tych punktów końcowych można wykorzystać dowolne oprogramowanie, który może komunikować się z tymi punktami końcowymi. Na przykład w przypadku punktu końcowego Docker Swarm można użyć interfejsu wiersza polecenia (CLI) platformy Docker. DC/OS można użyć interfejsu wiersza polecenia DC/OS.

### <a name="getting-started-with-azure-container-service"></a>Wprowadzenie do usługi Azure Container Service 

Aby rozpocząć korzystanie z usługi Azure Container Service, wdrażanie klastra usługi Azure Container Service w witrynie Azure portal przy użyciu szablonu usługi Azure Resource Manager lub [interfejsu wiersza polecenia](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostępne szablony to [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), i [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Szablony szybkiego startu można zmodyfikować w taki sposób, aby uwzględnić dodatkowej lub zaawansowanej konfiguracji platformy Azure. Aby uzyskać więcej informacji na temat wdrażania klastra usługi Azure Container Service, zobacz [wdrażanie klastra usługi Azure Container Service](https://docs.microsoft.com/azure/container-service/container-service-deployment) w witrynie internetowej platformy Azure.

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w ramach usług ACS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source.

Usługi ACS jest obecnie dostępna dla maszyn wirtualnych systemu Linux na platformie Azure z serii standardowa A, D, DS, G i GS. Opłaty są naliczane tylko za wystąpienia obliczeniowe, które możesz wybrać, jak również inne użyte zasoby infrastruktury bazowej, takie jak storage i sieci. Nie ma żadnych opłat przyrostowych za samą usługę ACS.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wprowadzenie do rozwiązania przy użyciu usługi Azure Container Service do hostowania kontenerów platformy Docker**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker Swarm — omówienie**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Omówienie trybu swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **System mesosphere DC/OS Przegląd**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Rozwiązanie Kubernetes.** Oficjalna witryna. \
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Poprzednie](resilient-high-availability-microservices.md)
[dalej](using-azure-service-fabric.md)
