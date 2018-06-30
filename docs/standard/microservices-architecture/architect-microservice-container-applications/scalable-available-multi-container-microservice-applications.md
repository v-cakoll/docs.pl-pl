---
title: Organizowanie mikrousług i kontener wielu aplikacji o wysokiej skalowalności i dostępności
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Organizowanie mikrousług i kontener wielu aplikacji o wysokiej skalowalności i dostępności
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: aab939af29849ceeef76d6f61b3d4f59d701094c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105465"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie mikrousług i kontener wielu aplikacji o wysokiej skalowalności i dostępności

Aplikacje gotowe do produkcji przy użyciu orchestrators jest niezbędne, gdy aplikacja jest oparta na mikrousług lub po prostu podzielić na wiele kontenerów. Wcześniej, wprowadzonego w podejściu na podstawie mikrousługi każdego mikrousługi właścicielem jego modelu i danych, dzięki czemu będzie ona autonomicznego projektowanie i wdrażanie punktu widzenia. Jednak nawet jeśli bardziej tradycyjnej aplikacją, która składa się z wielu usług (takich jak SOA), zostanie również wiele kontenerów lub usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone, aby skalować w poziomie oraz zarządzanie nimi; w związku z tym bezwzględnie konieczne orchestrator, jeśli chcesz mieć gotowe do produkcji i skalowalność aplikacji usługi kontenera.

Rysunek 4-23 przedstawia wdrożenie w klastrze aplikacja składa się z wielu mikrousług (kontenery).

![](./media/image23.PNG)

**Rysunek 4-23**. Klaster kontenerów

Prawdopodobnie algorytmu. Jednak sposób możesz równoważenia obciążenia obsługi routingu i organizowanie te składają się aplikacji?

Zwykły aparatem platformy Docker na hostach Docker pojedynczego spełnia potrzeby zarządzaniem wystąpieniami jednego obrazu na jednym hoście, ale wypada krótkie, jeśli chodzi o zarządzanie wielu kontenerów wdrożonego na wielu hostach bardziej złożonych aplikacji rozproszonych. W większości przypadków należy platformy zarządzania, która będzie automatycznie uruchomić kontenery, kontenery skalowalnego w poziomie z wielu wystąpień na obraz, wstrzymać je lub zamykać je w razie potrzeby i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieci i danych Magazyn.

Aby wykracza poza zarządzania poszczególnych kontenerów lub bardzo proste składa aplikacji i przeniesienie kierunku większych aplikacji przedsiębiorstwa z mikrousług, należy wyłączyć aranżacji i klastrów platformy.

Z architektury i rozwoju punktu widzenia Jeśli tworzysz dużych przedsiębiorstw składa się z aplikacji opartych na mikrousług jest wziąć pod uwagę następujące platform i produktów, które obsługują zaawansowanych scenariuszy:

**Klastry i orchestrators**. Gdy są potrzebne do skalowania aplikacji na wielu hostach Docker, podczas dużych aplikacji opartej na mikrousługi, jest krytyczne, aby można było zarządzać tymi hostami jako jednym klastrem za abstrakcyjność złożoność podstawowej platformy. To, czego klastrów kontenera i orchestrators zawiera. Przykłady orchestrators to sieć szkieletowa usług Azure, Kubernetes, Docker Swarm i Mesosphere DC/OS. Ostatnie trzy orchestrators open source dostępnych na platformie Azure za pośrednictwem usługi kontenera platformy Azure.

**Planiści**. *Planowanie* oznacza, że funkcja dla administratora uruchomić kontenery w klastrze, udostępniają interfejs użytkownika. Harmonogram klastra ma kilka obowiązki: efektywnie korzystać z zasobów klastra, aby ustawić ograniczenia podanego przez użytkownika, do wydajnie kontenerów Równoważenie obciążenia między węzłami lub hostów i aby było odporna błędy zapewniając wysoki dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczonych przez różnych dostawców często podać obie możliwości. Poniżej wymieniono najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Orchestrators te są zwykle dostępne w chmur publicznych, takich jak Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania dla kontenera, klaster, aranżacji i planowania

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes jest to produkt typu open source, który zawiera funkcję, która infrastruktura klastra i kontener planowania organizowanie możliwości w zakresie od. Umożliwia automatyzację wdrożenia, skalowanie i operacje kontenery aplikacji w klastrach hostów.
>
> Kubernetes udostępnia infrastrukturę skoncentrowane kontenera, która grupy kontenerów aplikacji do jednostek logicznych łatwe zarządzanie i odnajdywania.
>
> Kubernetes jest dojrzałe w systemie Linux mniej dojrzałe w systemie Windows.

Rozwiązanie docker Swarm

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Rozwiązanie docker Swarm umożliwia klastra i Zaplanuj kontenery Docker. Przy użyciu Swarm, można przekształcić w puli hostów Docker pojedynczego, wirtualnego host Docker. Klientów można wprowadzać interfejsu API żądania wysyłane na Swarm tak samo jak na hostach, co oznacza, że Swarm ułatwia aplikacji można skalować na wielu hostach.
>
> Rozwiązanie docker Swarm jest to produkt z Docker, firma.
>
> Docker v1.12 lub nowszej można uruchomić tryb macierzysty i wbudowane Swarm.

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Mesosphere Enterprise DC/OS (oparte na Apache Mesos) to platforma gotowe do produkcji dla działających kontenerów i aplikacji rozproszonych.
>
> DC/OS polega na abstrakcyjność kolekcji zasobów dostępnych w klastrze i udostępnianie tych zasobów oparty na jego składniki. Marathon zwykle jest używana jako harmonogramu zintegrowany z DC/OS.
>
> DC/OS jest dojrzałe w systemie Linux mniej dojrzałe w systemie Windows.

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Sieć szkieletowa usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do tworzenia aplikacji. Jest [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z usług i tworzy klastry maszyn. Sieć szkieletowa usług można wdrożyć usługi jako kontenery lub zwykłych procesów. Można nawet różnych usług w procesach z usługami w kontenerach w tej samej aplikacji i klastra.
>
> Usługa Service Fabric realizuje dodatkowe i opcjonalne przetestowanego [modele programowania sieci szkieletowej usług ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) jak [stanowych usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) i [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Sieć szkieletowa usług to dojrzałe w systemie Windows (lata rozwijającymi w systemie Windows), mniej dojrzałe w systemie Linux. 
> Kontenery zarówno systemu Linux i Windows są obsługiwane w sieci szkieletowej usług od 2017 r.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Za pomocą orchestrators na podstawie kontenera w Microsoft Azure

Kilku dostawców chmury oferuje Obsługa kontenerów Docker oraz klastrów Docker i obsługę orchestration, w tym Microsoft Azure, Amazon EC2 kontenera usług i aparat kontenera Google. Microsoft Azure obsługuje Docker klastra i orchestrator za pomocą usługi kontenera platformy Azure (ACS) zgodnie z objaśnieniem w następnej sekcji.

Wybór innego polega na użyciu Azure sieć szkieletowa usług Microsoft (platformę mikrousług), który również obsługuje Docker oparte na systemie Linux i kontenery systemu Windows. Sieć szkieletowa usług działa na platformie Azure lub innych chmur i działa także [lokalnymi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Przy użyciu usługi kontenera platformy Azure

Klaster Docker pul wielu hostach Docker i udostępnia je jako pojedynczego wirtualnego hosta Docker, aby umożliwić wdrażanie wielu kontenerów do klastra. Klaster będzie obsługiwać wszystkie złożonych zarządzania żmudne procesy, takie jak skalowalność, kondycji i tak dalej. Rysunek 4 – 24 reprezentuje sposób mapowania do usługi kontenera platformy Azure (ACS) w klastrze Docker składa aplikacji.

Usługi ACS umożliwia uprościć tworzenie, konfiguracji i zarządzania klastrowania maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Za pomocą zoptymalizowanego konfiguracji popularnych narzędzi planowania i aranżacji open source, ACS umożliwia korzystać z istniejących umiejętności lub Rysuj duże i rosnącym treści specjalizacji społeczności, wdrażanie i zarządzanie nimi na podstawie kontenera aplikacji w systemie Microsoft Azure .

Usługa kontenera platformy Azure optymalizuje konfiguracji popularnych Docker klastrowania typu open source narzędzia i technologie specjalnie dla platformy Azure. Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność dla kontenerów i konfigurację aplikacji. Wybierz rozmiar, liczby hostów i narzędzia programu orchestrator, a usługi kontenera obsługuje wszystkie inne elementy.

![](./media/image28.png)

**Rysunek 4 – 24**. Opcje klastra usługi kontenera platformy Azure

Usługi ACS korzysta obrazy usługi Docker do zapewnienia pełni dostosowane kontenerów aplikacji. Obsługuje ona wybranym platform aranżacji open source, takie jak DC/OS (obsługiwane przez Apache Mesos), Kubernetes (pierwotnie utworzone przez firmę Google) i rozwiązania Docker Swarm, aby upewnić się, że te aplikacje mogą być skalowane do tysięcy lub nawet dziesiątki tysięcy kontenerów.

Usługi kontenera platformy Azure pozwala korzystać z funkcji korporacyjnej Azure zachowując przenośność aplikacji, w tym również na warstwy aranżacji.

![](./media/image29.png)

**Rysunek 4-25**. Orchestrators usługi ACS

Jak pokazano na rysunku 4-25, usługi kontenera platformy Azure jest po prostu infrastrukturę platformy Azure w celu wdrożenia DC/OS, Kubernetes lub Docker Swarm, ale ACS nie implementuje wszelkie dodatkowe orchestrator. W związku z tym usługa ACS nie jest orchestrator, tylko infrastrukturę, która wykorzystuje istniejące orchestrators open source dla kontenerów.

Z punktu widzenia użycia celem usługi kontenera platformy Azure jest zapewnienie środowiska macierzystego kontenera za pomocą technologii i popularnych narzędzi open source. W tym celu przedstawia standardowe punkty końcowe interfejsu API dla programu orchestrator wybrany. Korzystając z tych punktów końcowych, można wykorzystać dowolne oprogramowanie, które mogą komunikować się z tych punktów końcowych. Na przykład w przypadku punktu końcowego Docker Swarm można użyć Docker interfejsu wiersza polecenia (CLI). DC/OS można użyć interfejsu wiersza polecenia DC/OS.

### <a name="getting-started-with-azure-container-service"></a>Wprowadzenie do korzystania z usługi kontenera platformy Azure 

Aby rozpocząć korzystanie z usługi kontenera platformy Azure, wdrażanie klastra usługi kontenera platformy Azure w portalu Azure za pomocą szablonu usługi Azure Resource Manager lub [interfejsu wiersza polecenia](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostępne szablony obejmują [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), i [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Szablony szybkiego startu można zmodyfikować w taki sposób, aby dołączyć dodatkowe lub zaawansowanej konfiguracji platformy Azure. Aby uzyskać więcej informacji dotyczących wdrażania klastra usługi kontenera platformy Azure, zobacz [wdrażanie klastra usługi kontenera platformy Azure](https://docs.microsoft.com/azure/container-service/container-service-deployment) w witrynie systemu Azure.

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w ramach usług ACS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source.

Usługi ACS jest obecnie dostępny dla serii Standard A, D DS, G i GS maszyn wirtualnych systemu Linux na platformie Azure. Naliczane są opłaty tylko dla wybranego wystąpienia obliczeniowe, jak również inne podstawowej infrastruktury zasoby używane, takich jak magazynu i sieci. Nie ma nie przyrostowe opłat za ACS sam.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wprowadzenie do kontenera Docker hosting rozwiązania z usługą kontenera Azure**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Informacje o docker Swarm**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Omówienie trybu swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Omówienie DC/OS mesosphere**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Oficjalna witryna. \
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Poprzednie](resilient-high-availability-microservices.md)
[dalej](using-azure-service-fabric.md)
