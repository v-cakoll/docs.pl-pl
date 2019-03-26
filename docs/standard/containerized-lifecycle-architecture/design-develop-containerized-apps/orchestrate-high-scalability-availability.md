---
title: Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności
description: Aplikacje rzeczywistej produkcji mają być wdrażane i zarządzane przy użyciu koordynatorów, które obsługują kondycji, obciążenia i cyklami życia dla wszystkich kontenerów.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 834e0b91a596f489c10e4eb11b0de2b5eaeb9f1c
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466403"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności

Przy użyciu koordynatorów aplikacji gotowych do produkcji jest istotne, jeśli aplikacja jest oparta na mikrousługach lub podzielone między wiele kontenerów. Jak wprowadzona wcześniej w podejściu opartych na mikrousługach, każda mikrousługa jest właścicielem jej modelu i danych tak, aby go autonomicznego od środowisk programowania i wdrażania punktu widzenia. Ale nawet w przypadku bardziej tradycyjny aplikację która składa się z wielu usług (np. SOA), będziesz również mieć wiele kontenerów i usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone i skalowanie w poziomie i zarządzać; w związku z tym bezwzględnie konieczne koordynatora, jeśli chcesz mieć aplikację obsługującą wiele kontenerów gotowe do produkcji i skalowalny.

Rysunek 4 – 6 przedstawia wdrożenie w klastrze aplikacji składających się z wielu mikrousług (kontenery).

![Złożone aplikacje platformy Docker w klastrze: Możesz użyć jednego kontenera dla każdego wystąpienia usługi. Kontenery platformy docker są "jednostki wdrożenia" i kontener jest wystąpienie hosta Docker.A obsługuje wiele kontenerów](./media/image6.png)

**Rysunek 4 – 6**. Klaster kontenerów

Wygląda jak algorytmu. Ale jak możesz obsługi równoważenia obciążenia, routingu i organizowanie te złożone aplikacje?

Interfejsu wiersza polecenia (CLI) Docker spełnia potrzeby zarządzania jeden kontener na jednym hoście, ale znajduje się krótki w przypadku zarządzania wieloma kontenerami wdrażane na wielu hostach w przypadku bardziej złożonych aplikacji rozproszonych. W większości przypadków należy to platforma zarządzania, która będzie automatycznie uruchom kontenery, skalowanie kontenerów za pomocą wielu wystąpień na obrazie, zawiesić je lub ich zamknięcie zależności od potrzeb i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieci i danych Magazyn.

Czegoś Zarządzanie poszczególne kontenery lub proste aplikacje złożone i Przenieś kierunku większych aplikacje dla przedsiębiorstw przy użyciu mikrousług, należy go włączyć do aranżacji i klastrowanie platform.

Z architektury i projektowania punktu widzenia w przypadku tworzenia dużych przedsiębiorstw, opartych na mikrousługach, aplikacji, warto zapoznać się z następujących platform i produktów, które obsługuje zaawansowane scenariusze:

- **Klastry i koordynatorów.** Jeśli musisz skalować aplikacje na wielu hostach Docker, takich jak przy użyciu dużych aplikacji opartych na mikrousługach, bardzo ważne jest można zarządzać wszystkich tych hostów jako pojedynczy klaster, zapewniając abstrakcyjność złożoność podstawowej platformy. To, co zapewnia klastry kontenerów i koordynatorów. Przykładami koordynatorów są usługi Azure Service Fabric i Kubernetes. Rozwiązanie Kubernetes jest dostępna na platformie Azure za pomocą usługi Azure Kubernetes Service.

- **Transfery danych.** *Planowanie* oznacza, że mają możliwość dla administratora uruchomić kontenerów w klastrze, więc lotów udostępniają interfejs użytkownika, aby to zrobić. Harmonogram klastra ma kilka obowiązki: wydajnie korzystać z zasobów klastra, aby ustawić ograniczenia podana przez użytkownika, do wydajne Równoważenie obciążenia kontenerów w węzłach lub hosty i być odporne na błędy przy jednoczesnym zapewnieniu wysokiego dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczane przez różnych dostawców często podać oba zestawy funkcji. Sekcja poniżej zawiera najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Te koordynatorów powszechnie są oferowane w chmurach publicznych, takich jak platforma Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania dla kontenera, klastrowanie, aranżację i planowanie

| Platforma | Komentarze |
|:---:|:---|
| **Kubernetes** <br/> ![Logo rozwiązania Kubernetes](./media/kubernetes-logo.png) | [*Kubernetes* ](https://kubernetes.io/) to produkt typu open source, który zapewnia funkcje z zakresu od infrastruktury klastra i kontenerów harmonogramów, organizowanie możliwości. Dzięki temu można zautomatyzować wdrażanie, skalowanie i działanie kontenerów aplikacji w klastrach hostów. <br/> <br/> *Kubernetes* udostępnia infrastrukturę skoncentrowane na kontenera, która grupuje kontenery aplikacji w jednostki logiczne, aby ułatwić zarządzanie i odnajdywania. <br/> <br/> *Kubernetes* to dojrzała w systemie Linux, mniej dojrzałe w Windows. |
| **Usługa Azure Kubernetes Service (AKS)** <br/> ![Logo Azure Kubernetes Service](./media/aks-logo.png) | [Usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) jest zarządzanej usługi organizowania kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie klastrem Kubernetes, wdrażania i operacji. |
| **Azure Service Fabric** <br/> ![Usługa Azure Service Fabric Logo](./media/service-fabric-logo.png) | [Usługa Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do tworzenia aplikacji. Jest [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z usług i służąca do tworzenia klastrów maszyn. Usługi można wdrożyć usługi Service Fabric, jako kontenery lub procesy zwykły. Jest to możliwe nawet różne usługi w procesach usługi w kontenerach w tej samej aplikacji i klastra. <br/> <br/> *Usługa Service Fabric* klastrów można wdrożyć na platformie Azure, lokalnie lub w dowolnej chmurze. Jednak wdrożenie na platformie Azure zostało uproszczone dzięki podejściu zarządzanych. <br/> <br/> *Usługa Service Fabric* udostępnia dodatkowe i opcjonalnie przetestowanego rozwiązania ze szczegółami [modeli programowania usługi Service Fabric](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) takich jak [usług stanowych](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) i [elementów Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) . <br/> <br/> *Usługa Service Fabric* dojrzała trwa Windows (lat ewolucji w Windows), mniej dojrzałe w systemie Linux. <br/> <br/> Kontenerów systemów Linux i Windows są obsługiwane w usłudze Service Fabric od 2017 r. |
| **Usługa Azure Service Fabric siatki** <br/> ![Usługa Azure Service Fabric siatki Logo](./media/azure-service-fabric-mesh-logo.png) | [*Usługa Azure Service Fabric siatki* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferuje samą niezawodność, wydajność o kluczowym znaczeniu i skalowania, co Usługa Service Fabric, ale oferuje także platformę w pełni zarządzany i bez użycia serwera. Nie trzeba zarządzać klastrem maszyn wirtualnych, magazynu i konfiguracji sieci. Możesz skupić się na rozwoju aplikacji. <br/> <br/> *Usługa Service Fabric siatki* obsługuje kontenery systemów Windows i Linux, dzięki czemu możesz tworzyć aplikacje za pomocą dowolnego języka programowania i wybranej platformy.

## <a name="using-container-based-orchestrators-in-azure"></a>Przy użyciu koordynatorów opartych na kontenerach na platformie Azure

Kilku dostawców chmury oferują obsługę kontenerów platformy Docker oraz klastrów platformy Docker oraz obsługę aranżacji, w tym platformy Azure, Amazon EC2 Container Service i Google kontenera aparatu. System Azure oferuje Docker klastra i orchestrator na pomoc techniczną za pomocą usługi Azure Kubernetes Service (AKS), usługi Azure Service Fabric i usługi Azure Service Fabric siatki.

## <a name="using-azure-kubernetes-service"></a>Za pomocą usługi Azure Kubernetes Service

Klaster usługi Kubernetes pul kilka hostów platformy Docker i przedstawia je w postaci jednego wirtualnego hosta platformy Docker, aby umożliwić wdrażanie wielu kontenerów do klastra i skalowalnego w poziomie przy użyciu dowolnej liczby wystąpień kontenera. Klaster będzie obsługiwać wszystkie złożonego zarządzania żmudne procesy, takie jak skalowalność, kondycji i tak dalej.

AKS umożliwia uproszczenie tworzenia, konfiguracji i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania konteneryzowanych aplikacji. Użycie zoptymalizowanej konfiguracji popularnych narzędzi planowania i organizowania typu open source, AKS umożliwia używanie posiadanych umiejętności lub sięganie na treść duży i rosnący zasób wiedzy społeczności, wdrażanie i zarządzanie nimi opartych na kontenerach aplikacje w systemie Microsoft Azure .

Usługa Azure Kubernetes Service optymalizuje konfigurację popularnych narzędzi typu open-source klastrowania platformy Docker i technologii pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, która oferuje przenośność kontenerów i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a AKS zajmuje się całą resztą.

![Struktura klastra Kubernetes: Brak jednego węzła głównego, który obsługuje DNS, harmonogram, serwer proxy, itp. oraz kilka węzłów procesów roboczych, które hostują kontenery.](media/image36.png)

**Rysunek 4 – 7**. Uproszczoną strukturę i topologii klastra Kubernetes

Rysunek 4 – 7 przedstawia strukturę klastra Kubernetes, gdzie węzła głównego (VM) określa większość koordynację klastra i kontenerów można wdrożyć na pozostałe węzły, które są zarządzane jako pojedyncza pula z punktu widzenia w aplikacji. Dzięki temu można skalować do tysięcy, a nawet dziesiątków tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla platformy Kubernetes

W środowisku programistycznym, [platformy Docker z ogłoszeniem z lipca 2018 r.](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), Kubernetes można również uruchomić w maszynie deweloperskiej pojedynczego (system Windows 10 lub macOS), po prostu instalując [pulpitu platformy Docker](https://www.docker.com/community-edition). Możesz później wdrożyć do chmury (AKS) na potrzeby dalszych badań integracji, jak pokazano na rysunku 4 – 8.

![Docker ogłosiła pomoc techniczna dla deweloperów maszyny dla klastrów Kubernetes na lipca "2018 r. za pomocą programu Desktop platformy Docker.](media/kubernetes-development-environment.png)

**Rysunek 4 – 8**. Uruchamianie rozwiązania Kubernetes w komputerze deweloperskim i w chmurze

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Rozpoczynanie pracy przy użyciu usługi Azure Kubernetes Service (AKS)

Aby rozpocząć, za pomocą usługi AKS, musisz wdrożyć klaster AKS z witryny Azure portal lub za pomocą interfejsu wiersza polecenia. Aby uzyskać więcej informacji na temat wdrażania klastra usługi Azure Container Service, zobacz [wdrażanie klastra usługi Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w jako część usługi AKS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source. AKS jest dostępny dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wystąpienia obliczeniowe, które możesz wybrać, jak również inne użyte zasoby infrastruktury bazowej, takie jak storage i sieci. Są naliczane opłaty przyrostowe AKS sam.

W przypadku dalszych wdrożenia na podstawie informacji na temat wdrażanie w usłudze Kubernetes `kubectl` a wersją z oryginalnego `.yaml` plików, zobacz wpis na [Konfigurowanie ramach aplikacji eShopOnContainers w usłudze AKS (usługi Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie przy użyciu narzędzia Helm do klastrów Kubernetes

W przypadku wdrażania aplikacji w klastrze Kubernetes, można użyć oryginalnego `kubectl.exe` narzędzie interfejsu wiersza polecenia przy użyciu plików wdrożenia na podstawie natywnego formatu (`.yaml` plików), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji platformy Kubernetes, takie jak w przypadku wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się używać [Helm](https://helm.sh/).

Narzędzia Helm pomaga określić, wersji, install, udział, uaktualnienia lub wycofywania nawet najbardziej złożoną aplikację platformy Kubernetes.

Idąc dalej, użycie narzędzia Helm jest również zalecana, ponieważ dodatkowych środowisk Kubernetes na platformie Azure, takich jak [miejsca do magazynowania Azure Dev](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) również są oparte na wykresów rozwiązania Helm.

Helm jest obsługiwana przez [Foundation natywnych obliczeń w chmurze (CNCF)](https://www.cncf.io/) we współpracy z firmą Microsoft, Google, Bitnami i Helm Współautor społeczności.

Aby uzyskać dalsze implementacji informacji na temat planów narzędzia Helm i platformy Kubernetes, zobacz wpis na [przy użyciu wykresów rozwiązania Helm, aby wdrażanie w ramach aplikacji eShopOnContainers usłudze AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Użyj usługi Azure Dev miejsca do magazynowania dla Ciebie cyklem życia aplikacji w usłudze Kubernetes

[Usługa Azure Dev spacje](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne Kubernetes dla zespołów. W przypadku konfiguracji maszyny dev minimalny iteracyjne było uruchomić i debugować kontenerów bezpośrednio w usłudze Azure Kubernetes Service (AKS). Można tworzyć w Windows, Mac lub Linux przy użyciu znanych narzędzi, takich jak Visual Studio, Visual Studio Code lub wiersza polecenia.

Jak wspomniano wcześniej, podczas wdrażania aplikacji opartych na kontenerach usługi Azure Dev miejsca do magazynowania korzysta z wykresów rozwiązania Helm.

Usługa Azure Dev spacje pomaga zespołom programistycznym mu bardziej wydajnej pracy, na platformie Kubernetes, ponieważ pozwala na szybkie Iterowanie i Debuguj kod bezpośrednio w globalnych klastra Kubernetes na platformie Azure, tylko przy użyciu programu Visual Studio 2017 lub Visual Studio Code. Czy klastra Kubernetes na platformie Azure udostępnionej odbywa się klastra Kubernetes, dzięki czemu Twój zespół może wspólnie współpracują ze sobą. Można tworzyć kod w izolacji, a następnie wdrożenie w klastrze globalnych i end-to-end testowanie z innymi składnikami bez replikacji lub pozorowanie się zależności.

Jak pokazano na rysunku 4 – 9, najbardziej różnicujący funkcji w Azure Dev miejsca do magazynowania jest możliwość tworzenia miejsca do magazynowania, które można uruchomić zintegrowanego w pozostałej części globalnego wdrażania w klastrze.

![Usługa Azure Dev spacje przezroczyste mieszać i dopasowywać mikrousług w środowisku produkcyjnym z tworzenia wystąpienia kontenera, aby ułatwić testowanie nowych wersji.](media/image38.png)

**Rysunek 4 – 9**. Korzystanie z wielu miejsc do magazynowania w Azure Dev miejsca do magazynowania

Zasadniczo można skonfigurować miejsce na udostępnionym deweloperów na platformie Azure. Każdy deweloper może skupić się na ich części aplikacji, można iteracyjne tworzenie kodu "wstępnie zatwierdzone" w przestrzeni deweloperów, która już zawiera wszystkich innych usług i zasobów, które zależą od ich scenariuszy w chmurze. Zależności są zawsze aktualne, a deweloperzy pracują nad w sposób, który odzwierciedla produkcji.

Usługa Azure Dev spacje wprowadza pojęcie obszarem, co pozwala na pracę w izolacji i bez obawiać się, że przerwanie członków zespołu. Ta funkcja opiera się na przedrostki adresów URL; Korzystając z prefiks przestrzeni dev w adresie URL żądania kontenera, Azure Dev miejsca do magazynowania z wersją specjalne kontenera, w którym wdrożona to miejsce, jeśli taka istnieje. W przeciwnym razie zostaną uruchomione globalnego/skonsolidowane wersji.

Możesz zobaczyć [strony typu wiki w ramach aplikacji eShopOnContainers na miejsca do magazynowania Azure Dev](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) Aby uzyskać praktyczne widok na konkretny przykład.

Aby uzyskać więcej informacji, zobacz artykuł [programowanie zespołowe za pomocą usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do korzystania z usługi Azure Kubernetes Service (AKS)** \
  [https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

- **Azure Dev Spaces** \
  [https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)

- **Rozwiązanie Kubernetes.** Oficjalna witryna. \
  [https://kubernetes.io/](https://kubernetes.io/)

## <a name="using-azure-service-fabric"></a>Za pomocą usługi Azure Service Fabric

Usługa Azure Service Fabric, powstały od firmy Microsoft przejście od dostarczania produktów "pola", które były zazwyczaj monolitycznych w stylu, dostarczaniu usług. Środowisko tworzenia i obsługi dużych usług na dużą skalę, takich jak Azure SQL Database, Azure Cosmos DB, Azure Service Bus lub Cortany wewnętrznej bazy danych, kształt usługi Service Fabric. Platforma ewoluował wraz z upływem czasu coraz więcej usług przyjęty go. Co ważniejsze usługi Service Fabric musiał uruchomić nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Usługa Service Fabric ma na celu rozwiązywanie trudnych problemów, kompilowania i uruchamiania usługi i efektywnie wykorzystując zasoby infrastruktury tak, aby zespoły można rozwiązać problemy biznesowe przy użyciu podejścia mikrousług.

Usługa Service Fabric udostępnia dwa obszary ułatwiające tworzenie aplikacji korzystających z podejścia mikrousług:

- Platforma, która zapewnia usługi systemowe na wdrażanie, skalowanie, uaktualnienia, wykrywanie, ponowne uruchomienie usługi nie powiodło się, odnajdywanie lokalizacji usługi, zarządzanie stanem i monitorowanie kondycji. Te usługi systemu obowiązuje udostępniają wiele z właściwości opisanych powyżej mikrousług.

- Interfejsy API programowania lub struktury, ułatwiające tworzenie aplikacji zgodnie z mikrousług: [interfejsu Reliable actors oraz usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Można wybrać żadnego kodu do tworzenia usługi mikrousług, ale te interfejsy API upewnij zadania prostsze, a ich integracja z platformą dokładniej. W ten sposób można uzyskać kondycji i informacji diagnostycznych lub możesz korzystać z zalet zarządzania stanem niezawodne.

Usługa Service Fabric jest niezależny od względem jak opracować swoje usługi, a następnie można użyć dowolnej technologii. Jednak zapewnia wbudowane programowania interfejsów API, które ułatwiają tworzenie mikrousług.

Jak pokazano na rysunku 4-10, możesz utworzyć i uruchamianie mikrousług w usłudze Service Fabric, jako prosty procesy lub jako kontenery platformy Docker. Istnieje również możliwość mieszać opartych na kontenerach mikrousług przy użyciu procesu na podstawie mikrousług, w tym samym klastrze usługi Service Fabric.

![Porównanie usługi Azure Service Fabric clusters: Mikrousługi jako procesy, w którym każdy węzeł działa jeden proces dla poszczególnych mikrousług; Mikrousługi jako kontenery, w którym każdy węzeł działa platformy Docker za pomocą kilku kontenerów jednego kontenera na mikrousługach.](./media/azure-service-fabric-cluster-types.png)

**Rysunek 4 – 10**. Wdrażanie mikrousług, jako procesów lub kontenerów w usłudze Azure Service Fabric

Klastry usługi Service Fabric, oparte na hostach z systemem Linux i Windows można uruchamiać kontenery platformy Docker w systemie Linux i kontenerów Windows, odpowiednio.

Aby uzyskać aktualne informacje na temat obsługi kontenerów w usłudze Azure Service Fabric, zobacz [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Usługa Service Fabric jest dobrym przykładem platformy, w którym można zdefiniować różne architekturę logiczną (mikrousług biznesowych lub ograniczone konteksty) niż fizyczna implementacja. Na przykład w przypadku zaimplementowania [stanowych usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [usługi Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które zostały wprowadzone w następnej sekcji "[Stateless w porównaniu z mikrousług stanowych](#stateless-versus-stateful-microservices), "masz koncepcja mikrousług firmy z wieloma usługami fizycznych.

Jak pokazano na rysunku 4 – 10 i myśleć z punktu widzenia mikrousług/biznesowych podczas implementowania usługi Service Fabric Reliable usługa stanowa zazwyczaj należy zaimplementować dwie warstwy usług. Pierwszy jest zaplecza niezawodnej usługi stanowej, która obsługuje wiele partycji (każda partycja jest stanowej usługi). Drugim jest usługa frontonu, czyli usługę bramy, odpowiedzialnym za routingu i agreguje dane należące do wielu partycji lub wystąpień usługi stanowej. Usługi bramy również obsługuje komunikacji po stronie klienta za pomocą pętli ponawiania, uzyskiwanie dostępu do usługi zaplecza. Usługa bramy jest nazywane implementować niestandardowe usługi, czy też można również użyć usługi Service Fabric out-of--box [zwrotny serwer proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Usługa Service Fabric ma zgodnie z gotowymi receptami do obsługi kilku stanowych usług reliable services w kontenerach.](./media/service-fabric-stateful-business-microservice.png)

**Rysunek 4 – 11**. Mikrousługi biznesowych z wielu wystąpień usługi stanowej i bram frontonu

W każdym przypadku gdy używasz usługi Service Fabric stanowych usług Reliable Services, masz również logicznych lub pracy mikrousługi (ograniczony kontekst), który składa się z wielu usług fizycznych. Każdy z nimi, Usługa bramy i partycji usługi można można zaimplementować jako usługi interfejsu API sieci Web platformy ASP.NET, jak pokazano w rysunek 4 – 11.

W usłudze Service Fabric, grupy i wdrażanie grup usług jako [aplikacji usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), czyli jednostki pakowania i wdrażania dla programu orchestrator lub klastra. W związku z tym aplikacji usługi Service Fabric mógłby być mapowany na tego autonomicznego biznesowych i granic mikrousługi logicznych lub ograniczony kontekst, jak również, dzięki czemu można niezależnie wdrożyć te usługi.

### <a name="service-fabric-and-containers"></a>Usługa Service Fabric i kontenery

W odniesieniu do kontenerów w usłudze Service Fabric można także wdrożyć usługi w obrazów kontenerów w ramach klastra usługi Service Fabric. Jak pokazano na rysunku 4 – 12, w większości przypadków będzie istnieć tylko jeden kontener dla danej usługi.

![Aplikacja usługi Service Fabric można uruchomić kilka kontenerów, dostęp do zewnętrznej bazy danych i cały zestaw będzie logiczne granic mikrousługi biznesowych](./media/azure-service-fabric-business-microservice.png)

**Rysunek 4-12**. Mikrousługi biznesowych za pomocą kilku usług (kontenery) w usłudze Service Fabric

Jednak kontenery tak zwane "przyczepki" (dwa kontenery, które muszą zostać wdrożone razem jako część usługi logiczne) również są możliwe w usłudze Service Fabric. Ważne jest mikrousług firm logiczne obramowanie kilku elementów cohesive. W wielu przypadkach może być pojedynczą usługę za pomocą pojedynczego modelu danych, ale w innych przypadkach może być także kilka usług fizycznych.

Należy pamiętać, że można łączyć usługi w procesach i usługi w kontenerach, w tej samej aplikacji usługi Service Fabric, jak pokazano w rysunek 4 — 13.

![Aplikacja usługi Service fabric uruchamianie kontenerów i usług, w tym samym węźle.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Rysunek 4 — 13**. Mikrousługi firm mapowane do aplikacji usługi Service Fabric z kontenerami i usług stanowych

Aby uzyskać więcej informacji na temat obsługi kontenerów w usłudze Azure Service Fabric, zobacz [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousługi

Jak wspomniano wcześniej, każda mikrousługa (logiczne ograniczony kontekst) musi być właścicielem swój model domeny (dane i logikę). W przypadku mikrousługi bezstanowe bazy danych będą zewnętrznych, wykorzystujące relacyjne opcje, takie jak SQL Server lub opcje NoSQL, takie jak usługi Azure Cosmos DB lub MongoDB.

Ale samych usług może być również stanowych w usłudze Service Fabric, co oznacza, że dane znajdują się w ramach mikrousług. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousług w pamięci i utrwalane na dyskach twardych i replikowane do innych węzłów. Rysunek 4-30 przedstawia różne podejścia.

![W przypadku usług bezstanowych stanu (stan trwały, bazy danych) są przechowywane z mikrousług. W przypadku usług stanowych stanu jest przechowywana w mikrousługach.](./media/stateless-vs-stateful-microservices.png)

**Rysunek 4 – 14**. Bezstanowe i stanowe mikrousługi

Bezstanowe podejście nadaje się doskonale i jest prostsza do zaimplementowania niż mikrousług stanowych, ponieważ to podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Jednak mikrousługi bezstanowe powodować opóźnienia między źródłami danych i procesów. Wymagają one również więcej ruchomych części gdy próbujesz poprawianie wydajności za pomocą dodatkowych pamięci podręcznej i kolejki. Powoduje to, że użytkownik może wystąpić złożone architektury, które mają zbyt wiele warstw.

Z kolei [mikrousług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można programu excel w zaawansowanych scenariuszach, ponieważ nie istnieje żadne opóźnienie między domeny logikę i dane. Duże przetwarzania danych, gry ponownie kończy, baz danych jako usługa i innych scenariuszy o małych opóźnieniach, wszystkie korzystają z usług stanowych umożliwiających lokalne stan szybszy dostęp.

Uzupełniające są usługi stanowe i bezstanowe. Na przykład jak pokazano na diagramie w prawo w rysunek 4-31, usługa stanowa może zostać podzielony na wiele partycji. Aby uzyskać dostęp do tych partycji, możesz potrzebować usługę bezstanową działający jako usługę bramy, której wie, jak rozwiązywać każdej partycji na podstawie kluczy partycji.

Usługi stanowe mają wady. Nakładają ich poziomu złożoności wysoka, aby być skalowana w poziomie. Funkcje, które zazwyczaj są realizowane przez systemy zewnętrzne bazy danych muszą być kierowane zadań, takich jak replikacja danych między mikrousług stanowych i partycjonowanie danych. Jednak jest to jeden z obszarów, gdzie koordynatora, takich jak [usługi Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [stanowych usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) ułatwiają maksymalnie — poprzez uproszczenie programowania i cyklem życia stanowe przy użyciu mikrousług [interfejsu API usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [elementów Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Innych platform tworzenia mikrousług, które umożliwiają usług stanowych obsługujące wzorcem aktora i który zwiększyć odporność na uszkodzenia i opóźnienie między logiki biznesowej i danych są programy Microsoft [Orleans](https://github.com/dotnet/orleans), począwszy od Microsoft Research oraz [ Akka.NET](https://getakka.net/). Obu platform obecnie umożliwiają zwiększenie ich obsługę platformy Docker.

Należy pamiętać, że kontenery platformy Docker samodzielnie bezstanowe. Jeśli chcesz wdrożyć usługi stanowej konieczne dodatkowe struktury profesjonalnie opracowany i wyższego poziomu zanotowanej wcześniej.

## <a name="using-azure-service-fabric-mesh"></a>Za pomocą usługi Azure Service Fabric siatki

Usługa Azure Service Fabric siatki jest w pełni zarządzana usługa, która umożliwia deweloperom tworzenie i wdrażanie aplikacji krytycznych dla misji bez jakiejkolwiek infrastruktury zarządzania. Użyj usługi Service Fabric siatki, aby tworzenie i uruchamianie aplikacji bezpiecznego, rozproszonych mikrousług, które można skalować na żądanie.

Jak pokazano na rysunku 4-15, aplikacji obsługiwanej usługi Service Fabric siatki uruchamianie i skalowanie bez konieczności martwienia się o infrastrukturę wyłączania jego.

![Aplikacja wielu kontenerów, działająca na platformie Docker pulpitu można wdrożyć do usługi Azure Service Fabric siatki bez martwienia się o infrastrukturę.](media/image39.png)

**Rysunek 4 – 15**. Wdrażanie aplikacji mikrousług/kontenerów do usługi Service Fabric siatki

Dzieje się w tle Usługa Service Fabric siatki składa się z klastrami tysięcy maszyn. Wszystkie operacje klastra są ukryte od dewelopera. Po prostu musisz przekazać kontenerów, a następnie określ zasoby, których potrzebujesz, wymagania w zakresie dostępności i limity zasobów. Usługa Service Fabric siatki jest automatycznie alokowana, infrastruktury, żądane przez wdrożenie aplikacji i obsługuje także błędy infrastruktury, upewniając się, że Twoje aplikacje są o wysokiej dostępności. Należy zadbać o kondycji i szybkość reakcji aplikacji, nie na infrastrukturze.

Aby uzyskać więcej informacji, zobacz [dokumentację usługi Service Fabric siatki](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Wybieranie koordynatorów na platformie Azure

Poniższa tabela zawiera wskazówki dotyczące jakie orchestrator do użycia w zależności od obciążenia i przedstawienie systemu operacyjnego.

![Usługi platformy Azure Kubernetes jest bardziej dojrzałych w systemie Linux niż w Windows i jest najczęściej używany do wdrażania mikrousług oparte na kontenerach. Usługa Azure Service Fabric (klaster i siatki) jest bardziej dojrzałych Windows niż w systemie Linux, często używane do mikrousług w oparciu o kontenery, mikrousługi oparte na zwykły procesy i usługi stanowej.](media/image40.png)

**Rysunek 4 – 16**. Wybór koordynatora w wskazówki dotyczące platformy Azure

>[!div class="step-by-step"]
>[Poprzednie](soa-applications.md)
>[dalej](deploy-azure-kubernetes-service.md)
