---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Rzeczywiste aplikacje produkcyjne muszą być wdrażane i zarządzane przy użyciu programu Orchestrator, które obsługują kondycję, obciążenie i cykle życia wszystkich kontenerów.
ms.date: 02/15/2019
ms.openlocfilehash: 8c1161127eb6b239384444c369de7f11abd3d424
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373692"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Korzystanie z koordynatorów dla aplikacji gotowych do produkcji jest niezbędne, jeśli aplikacja jest oparta na mikrousługach lub dzielona w wielu kontenerach. Jak zostało to zrobione wcześniej, w podejściu opartym na mikrousługach każda mikrousługa jest właścicielem modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia projektowania i wdrożenia. Jednak nawet jeśli masz bardziej tradycyjną aplikację składającą się z wielu usług (na przykład SOA), będziesz mieć również wiele kontenerów lub usług składających się z jednej aplikacji biznesowej, która musi zostać wdrożona jako system rozproszony. Te rodzaje systemów są skomplikowane do skalowania w poziomie i zarządzania nimi. w związku z tym, jeśli chcesz korzystać z gotowej do produkcji i skalowalnej aplikacji z obsługą kontenerów, musisz mieć absolutną wartość Orchestrator.

Rysunek 4-6 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Składają się aplikacje platformy Docker w klastrze: Dla każdego wystąpienia usługi należy użyć jednego kontenera. Kontenery platformy Docker to "jednostki wdrożenia", a kontener jest wystąpieniem platformy Docker. host obsługuje wiele kontenerów](./media/image6.png)

**Rysunek 4-6**. Klaster kontenerów

Wygląda podobnie do podejścia logicznego. Ale w jaki sposób obsługujesz Równoważenie obciążenia, Routing i organizowanie tych aplikacji złożonych?

Interfejs wiersza polecenia platformy Docker (CLI) spełnia wymagania zarządzania jednym kontenerem na jednym hoście, ale jest on krótki, gdy przyjdzie do zarządzania wieloma kontenerami wdrożonymi na wielu hostach w celu uzyskania bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która będzie automatycznie uruchamiać kontenery, skalować kontenery z wieloma wystąpieniami na obraz, wstrzymywać je lub wyłączać je w razie potrzeby i najlepiej kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieć i dane Chowan.

Aby przekroczyć możliwości zarządzania indywidualnymi kontenerami lub prostymi aplikacjami złożonymi i przenieść się do większej liczby aplikacji przedsiębiorstwa przy użyciu mikrousług, musisz włączyć aranżację i klastrowanie platform.

Jeśli tworzysz duże, korporacyjne i wielousługowe aplikacje oparte na architekturze i punkcie projektowania, ważne jest, aby zrozumieć następujące platformy i produkty, które obsługują zaawansowane scenariusze:

- **Klastry i usługi Orchestrator.** Gdy konieczne jest skalowanie aplikacji w poziomie na wielu hostach platformy Docker, takich jak w przypadku dużych aplikacji opartych na mikrousługach, krytyczne jest, aby zarządzać wszystkimi tymi hostami jako pojedynczym klastrem przez abstrakcję złożoności podstawowej platformy. To właśnie zapewnia klaster kontenerów i koordynatorów. Przykłady koordynatorów to Azure Service Fabric i Kubernetes. Usługa Kubernetes jest dostępna na platformie Azure za pomocą usługi Azure Kubernetes Service.

- **Planiści.** *Planowanie* oznacza możliwość, aby administrator mógł uruchamiać kontenery w klastrze, dlatego program Schedulers udostępnia również interfejs użytkownika. Harmonogram klastrów ma kilka obowiązków: aby wydajnie korzystać z zasobów klastra, ustaw ograniczenia udostępniane przez użytkownika w celu wydajnego równoważenia obciążenia kontenerów w węzłach lub hostach, a także zazawodności przed błędami, zapewniając wysoką opóźnienie.

Koncepcje klastra i harmonogramu są ściśle powiązane, dlatego produkty udostępniane przez różnych dostawców często udostępniają oba zestawy funkcji. W poniższej sekcji przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te Koordynatory są szeroko oferowane w chmurach publicznych, takich jak platforma Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

| Platforma | Komentarze |
|:---:|:---|
| **Kubernetes** <br/> ![Logo Kubernetes](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt "open source", który oferuje funkcje, które są przeznaczone dla zakresu od infrastruktury klastra i planowania kontenera do organizowania możliwości. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji między klastrami hostów. <br/> <br/> *Kubernetes* zapewnia infrastrukturę skoncentrowaną na kontenerach, która grupuje kontenery aplikacji w jednostki logiczne do łatwego zarządzania i odnajdywania. <br/> <br/> *Kubernetes* jest w systemie Linux, mniej dojrzały w systemach Windows. |
| **Usługa Azure Kubernetes Service (AKS)** <br/> ![Logo usługi Azure Kubernetes](./media/aks-logo.png) | [Usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |
| **Service Fabric platformy Azure** <br/> ![Logo Service Fabric platformy Azure](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do kompilowania aplikacji. Jest to [koordynator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) usług i tworzy klastry maszyn. Service Fabric mogą wdrażać usługi jako kontenery lub jako zwykłe procesy. Może nawet mieszać usługi w procesach z usługami w kontenerach w ramach tej samej aplikacji i klastra. <br/> <br/> Klastry *Service Fabric* można wdrożyć na platformie Azure, lokalnie lub w dowolnej chmurze. Wdrożenie na platformie Azure jest jednak uproszczone dzięki zarządzanemu podejściu. <br/> <br/> *Service Fabric* zapewnia dodatkowe i opcjonalne, [Service Fabric modele programowania](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) , takie jak [usługi stanowe](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) i [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/). <br/> <br/> *Service Fabric* jest dojrzała w systemie Windows (lata, w których trwa rozwój w systemie Windows), mniej wcześnie w systemach Linux. <br/> <br/> Kontenery systemu Linux i Windows są obsługiwane w Service Fabric od 2017. |
| **Siatka Service Fabric platformy Azure** <br/> ![Logo usługi Azure Service Fabric siatki](./media/azure-service-fabric-mesh-logo.png) | [*Siatka Service Fabric platformy Azure*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferuje taką samą niezawodność, wydajność krytyczną i skalowalność jak Service Fabric, ale również oferuje w pełni zarządzaną i bezserwerową platformę. Nie jest konieczne Zarządzanie klastrem, maszynami wirtualnymi, magazynem lub konfiguracją sieci. Wystarczy skupić się na tworzeniu aplikacji. <br/> <br/> *Siatka Service Fabric* obsługuje zarówno kontenery systemu Windows, jak i Linux, co pozwala na programowanie przy użyciu dowolnego języka programowania i wybranej platformy.

## <a name="using-container-based-orchestrators-in-azure"></a>Korzystanie z koordynatorów opartych na kontenerach na platformie Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry Docker i wsparcie w zakresie aranżacji, w tym Azure, Amazon EC2 Container Service i aparat usługi Google Container Engine. Platforma Azure zapewnia obsługę klastrów platformy Docker i programu Orchestrator za pomocą usługi Azure Kubernetes Service (AKS), platformy Azure Service Fabric i siatki Service Fabric platformy Azure.

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes Service

Klastry Kubernetes są pulami kilku hostów platformy Docker i uwidaczniają je jako jeden wirtualny Host platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalować je z dowolną liczbą wystąpień kontenerów. Klaster będzie obsługiwał wszystkie złożone instalacje administracyjne, takie jak skalowalność, kondycja i tak dalej.

AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji kontenerowych. Dzięki zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu "open source" AKS umożliwia korzystanie z istniejących umiejętności lub narysowanie dużej i rosnącej treści wiedzy społecznościowej w celu wdrażania aplikacji opartych na kontenerach i zarządzania nimi na Microsoft Azure .

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi typu "open source" i technologii platformy Docker przeznaczonych dla platformy Azure. Uzyskasz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierasz rozmiar, liczbę hostów i narzędzia programu Orchestrator, a AKS obsługuje wszystkie inne.

![Struktura klastra Kubernetes: Istnieje jeden węzeł główny, który obsługuje usługi DNS, Scheduler, proxy itp. i kilka węzłów procesu roboczego, które obsługują kontenery.](media/image36.png)

**Rysunek 4-7**. Uproszczona struktura i topologia klastra Kubernetes

Rysunek 4-7 przedstawia strukturę klastra Kubernetes, w którym węzeł główny (VM) kontroluje większość koordynacji klastra, i można wdrożyć kontenery do pozostałych węzłów zarządzanych jako jedna pula z punktu widzenia aplikacji. Dzięki temu można skalować do tysięcy lub nawet dziesiątki tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla Kubernetes

W środowisku programistycznym [ogłoszonym przez platformę Docker w lipcu 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)Kubernetes można również uruchomić na jednym komputerze deweloperskim (Windows 10 lub macOS), instalując program [Docker Desktop](https://www.docker.com/community-edition). Później można wykonać wdrożenie w chmurze (AKS) w celu przeprowadzenia dalszych testów integracji, jak pokazano na rysunku 4-8.

![Platforma Docker ogłosiła obsługę komputerów deweloperskich dla klastrów Kubernetes w lipcu 2018 r z pulpitem Docker.](media/kubernetes-development-environment.png)

**Rysunek 4-8**. Uruchamianie Kubernetes na komputerze deweloperskim i w chmurze

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z AKS, należy wdrożyć klaster AKS z poziomu Azure Portal lub przy użyciu interfejsu wiersza polecenia. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [wdrażanie klastra usługi Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nie są naliczane opłaty za żadne oprogramowanie instalowane domyślnie w ramach usługi AKS. Wszystkie opcje domyślne są implementowane za pomocą oprogramowania open source. AKS jest dostępny dla wielu maszyn wirtualnych na platformie Azure. Opłata jest naliczana tylko za wybrane wystąpienia obliczeniowe, a także dla innych użytych zasobów infrastruktury, takich jak magazyn i sieć. Nie są naliczane opłaty przyrostowe za AKS.

Aby uzyskać więcej informacji na temat wdrażania Kubernetes na podstawie `kubectl` oryginalnych `.yaml` plików, zobacz wpis post on [eShopOnContainers up in AKS (Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z użyciem wykresów Helm do klastrów Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można użyć oryginalnego `kubectl.exe` narzędzia interfejsu wiersza polecenia przy użyciu plików wdrożenia na podstawie formatu natywnego (`.yaml` pliki), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji Kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się korzystanie z [Helm](https://helm.sh/).

Wykresy Helm ułatwiają Definiowanie, wersję, instalowanie, udostępnianie, Uaktualnianie lub wycofywanie nawet najbardziej złożonej aplikacji Kubernetes.

Ponadto zaleca się użycie Helm, ponieważ dodatkowe środowiska Kubernetes na platformie Azure, takie jak [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach Helm.

Helm jest obsługiwany przez firmę [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) we współpracy z firmą Microsoft, Google, Bitnami i społecznością współautora Helm.

Aby uzyskać więcej informacji o implementacji na wykresach Helm i Kubernetes, zobacz artykuł post on [using Helm Charts to Deploy eShopOnContainers to AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Użyj Azure Dev Spaces dla cyklu życia aplikacji Kubernetes

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie i iteracyjne środowisko programistyczne Kubernetes dla zespołów. Dzięki minimalnej konfiguracji komputera dev można iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Program można opracowywać w systemie Windows, Mac lub Linux przy użyciu znanych narzędzi, takich jak Visual Studio, Visual Studio Code lub wiersz polecenia.

Jak wspomniano, Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Azure Dev Spaces ułatwia zespołom programistycznym wydajniejszą pracę w Kubernetes, ponieważ umożliwia szybkie iteracyjne i debugowanie kodu bezpośrednio w globalnym klastrze Kubernetes na platformie Azure za pomocą programu Visual Studio 2017 lub Visual Studio Code. Ten klaster Kubernetes na platformie Azure jest udostępnionym zarządzanym klastrem Kubernetes, dzięki czemu zespół może wspólnie współpracować. Możesz opracować swój kod w izolacji, a następnie wdrożyć go w klastrze globalnym i przeprowadzić kompleksowe testowanie z innymi składnikami bez replikowania lub makietowania zależności.

Jak pokazano na rysunku 4-9, najbardziej odróżniający się funkcja w Azure Dev Spaces jest możliwością tworzenia "spacji", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze.

![Azure Dev Spaces mogą w przejrzysty sposób mieszać i dopasowywać mikrousługi produkcyjne przy użyciu wystąpienia kontenera programowania, aby ułatwić testowanie nowych wersji.](media/image38.png)

**Rysunek 4-9**. Używanie wielu spacji w Azure Dev Spaces

W zasadzie można skonfigurować udostępnione miejsce deweloperskie na platformie Azure. Każdy deweloper może skupić się na części aplikacji i może w sposób iteracyjny opracowywać "wstępnie przydzielony" kod w obszarze deweloperskim, który zawiera już wszystkie inne usługi i zasoby w chmurze, od których zależą te scenariusze. Zależności są zawsze aktualne, a deweloperzy działają w sposób odzwierciedlający produkcję.

Azure Dev Spaces oferuje koncepcję obszaru, która pozwala na współpracę w izolacji i bez obaw o rozdzielenie członków zespołu. Ta funkcja jest oparta na prefiksach adresów URL; Jeśli używasz prefiksu obszaru dev w adresie URL żądania kontenera, Azure Dev Spaces uruchamia specjalną wersję kontenera, który został wdrożony dla tego miejsca, jeśli taki istnieje. W przeciwnym razie zostanie uruchomiona wersja globalna/skonsolidowana.

Na Azure Dev Spaces można zobaczyć [stronę typu wiki eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) , aby uzyskać praktyczny widok w konkretnym przykładzie.

Aby uzyskać więcej informacji, zobacz artykuł na temat [opracowywania zespołu w programie Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficjalna lokacja. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Korzystanie z usługi Azure Service Fabric

Usługa Azure Service Fabric powstała w wyniku przechodzenia firmy Microsoft w celu dostarczania produktów "Box", które zazwyczaj były wbudowane w stylu, aby dostarczać usługi. Środowisko tworzenia i obsługi dużych usług na dużą skalę, takie jak Azure SQL Database, Azure Cosmos DB, Azure Service Bus lub zaplecze Cortany, w Service Fabric. Platforma rozwijająca się wraz z upływem czasu, gdy coraz więcej usług je zastosowało. Ważne, Service Fabric musiały działać nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Celem Service Fabric jest rozwiązanie problemów twardych kompilowania i uruchamiania usługi oraz wydajne wykorzystanie zasobów infrastruktury, dzięki czemu zespoły mogą rozwiązywać problemy biznesowe przy użyciu podejścia mikrousług.

Service Fabric oferuje dwa szerokie obszary, które ułatwiają tworzenie aplikacji korzystających z rozwiązań mikrousług:

- Platforma udostępniająca usługi systemowe do wdrażania, skalowania, uaktualniania, wykrywania i ponownego uruchamiania usług zakończonych niepowodzeniem, odnajdywania lokalizacji usługi, zarządzania stanem i monitorowania kondycji. Te usługi systemowe w systemie umożliwiają włączenie wielu opisanych wcześniej cech mikrousług.

- Programowanie interfejsów API lub platform, które ułatwiają tworzenie aplikacji jako mikrousług: [niezawodne aktory i niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Można wybrać dowolny kod w celu utworzenia mikrousługi, ale te interfejsy API sprawiają, że zadanie jest bardziej proste i integruje się z platformą na wyższym poziomie. W ten sposób można uzyskać informacje dotyczące kondycji i diagnostyki lub można wykorzystać niezawodne zarządzanie stanami.

Service Fabric jest niezależny od w odniesieniu do sposobu tworzenia usługi i można użyć dowolnej technologii. Zapewnia ona jednak wbudowane interfejsy API programowania, które ułatwiają tworzenie mikrousług.

Jak pokazano na rysunku 4-10, można tworzyć i uruchamiać mikrousługi w Service Fabric jako proste procesy lub jako kontenery platformy Docker. Istnieje również możliwość mieszania mikrousług opartych na kontenerach z mikrousługami opartymi na procesach w ramach tego samego klastra Service Fabric.

![Porównanie klastrów usługi Azure Service Fabric: Mikrousługi jako procesy, w których każdy węzeł uruchamia jeden proces dla każdej mikrousługi; Mikrousługi jako kontenery, w których każdy węzeł uruchamia platformę Docker z kilkoma kontenerami, jeden kontener dla mikrousług.](./media/azure-service-fabric-cluster-types.png)

**Rysunek 4-10**. Wdrażanie mikrousług jako procesów lub kontenerów na platformie Azure Service Fabric

Klastry Service Fabric oparte na hostach z systemem Linux i Windows mogą uruchamiać odpowiednio kontenery platformy Docker Linux i kontenery systemu Windows.

Aby uzyskać aktualne informacje o obsłudze kontenerów w usłudze Azure Service Fabric, zobacz [Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric jest dobrym przykładem platformy, w której można zdefiniować inną architekturę logiczną (mikrousługi biznesowe lub konteksty ograniczone) niż implementacja fizyczna. Na przykład w przypadku zaimplementowania [stanowych Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [platformie Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które są wprowadzone w następnej sekcji "mikrousługi bezstanowe i[mikrousług](#stateless-versus-stateful-microservices)", firma z wieloma usługami usługi fizyczne.

Jak pokazano na rysunku 4-10, i zastanawiasz się, że w przypadku implementowania Service Fabric stanowej usługi niezawodnej, zazwyczaj konieczne będzie wdrożenie dwóch warstw usług. Pierwsza to niezawodna usługa bezstanowa zaplecza, która obsługuje wiele partycji (każda partycja jest usługą stanową). Druga to usługa frontonu lub Usługa bramy, która jest odpowiedzialna za Routing i agregację danych w wielu partycjach lub wystąpieniach usługi stanowej. Ta usługa bramy obsługuje również komunikację po stronie klienta z pętlami ponawiania próby dostępu do usługi zaplecza. Jest on nazywany usługą bramy w przypadku zaimplementowania niestandardowej usługi lub Alternatywnie można również użyć wbudowanej Service Fabric [zwrotnego serwera proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Service Fabric ma receptę do obsługi kilku niezawodnych usług stanowych w kontenerach.](./media/service-fabric-stateful-business-microservice.png)

**Rysunek 4-11**. Mikrousługa biznesowa z kilkoma wystąpieniami usługi stanowej i frontonem bramy niestandardowej

W każdym przypadku, gdy używane są Service Fabric stanowe Reliable Services, istnieje również usługa logiczna lub mikrousługowa, która składa się z wielu usług fizycznych. Każdy z nich, Usługa bramy i usługa partycji można zaimplementować jako ASP.NET Web API Services, jak pokazano na rysunku 4-11.

W Service Fabric można grupować i wdrażać grupy usług jako [aplikację Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), która jest jednostką pakowania i wdrożenia dla programu Orchestrator lub klaster. W związku z tym aplikacja Service Fabric może zostać zmapowana na tę autonomiczną granicę biznesową i logiczną mikrousług lub ograniczony kontekst, również dlatego można wdrożyć te usługi autonomicznie.

### <a name="service-fabric-and-containers"></a>Service Fabric i kontenery

W odniesieniu do kontenerów w Service Fabric można również wdrażać usługi w obrazach kontenera w klastrze Service Fabric. Jak pokazano na rysunku 4-12, większość czasu będzie zawierać tylko jeden kontener dla każdej usługi.

![Aplikacja Service Fabric może uruchamiać kilka kontenerów uzyskujących dostęp do zewnętrznej bazy danych, a cały zestaw będzie logiczną granicą mikrousługi biznesowej](./media/azure-service-fabric-business-microservice.png)

**Rysunek 4-12**. Mikrousługa biznesowa z wieloma usługami (kontenery) w Service Fabric

Jednak w Service Fabric są również dostępne kontenery "przyczepki" (dwa kontenery, które muszą zostać wdrożone razem w ramach usługi logicznej). Ważne jest, aby mikrousługa biznesowa była granicą logiczną wokół kilku spójnych elementów. W wielu przypadkach może to być jedna usługa z pojedynczym modelem danych, ale w niektórych innych przypadkach może istnieć również kilka usług fizycznych.

Należy zauważyć, że można mieszać usługi w procesach i usługi w kontenerach w tej samej aplikacji Service Fabric, jak pokazano na rysunku 4-13.

![Aplikacja usługi Service Fabric uruchamia obie usługi i kontenery w tym samym węźle.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Rysunek 4-13**. Mikrousługa biznesowa zamapowana na Service Fabric aplikacji z kontenerami i usługami stanowymi

Aby uzyskać więcej informacji na temat obsługi kontenerów w usłudze Azure Service Fabric, zobacz [Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Mikrousługi bezstanowe a stanowe

Jak wspomniano wcześniej, każda mikrousługa (związany z logicznym kontekstem) musi być własnym modelem domeny (dane i logika). W przypadku mikrousług bezstanowych baza danych będzie zewnętrzna, przy użyciu opcji relacyjnych, takich jak SQL Server, lub opcji NoSQL, takich jak Azure Cosmos DB lub MongoDB.

Jednak same usługi mogą być również stanowe Service Fabric, co oznacza, że dane znajdują się w mikrousłudze. Te dane mogą znajdować się nie tylko na tym samym serwerze, ale w ramach procesu mikrousług, w pamięci i utrwalane na dyskach twardych i replikowane do innych węzłów. Rysunek 4-14 pokazuje różne podejścia.

![W usługach bezstanowych stan (trwałość, baza danych) jest zachowywany z mikrousługi. W stanie usługi stanowe są przechowywane wewnątrz mikrousługi.](./media/stateless-vs-stateful-microservices.png)

**Rysunek 4-14**. Mikrousługi bezstanowe a stanowe

Podejście bezstanowe jest doskonale ważne i jest łatwiejsze do wdrożenia niż mikrousługi stanowe, ponieważ podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Ale bezstanowe mikrousługi nakładają opóźnienia między procesem i źródłami danych. Obejmują one również więcej elementów, które należy wykonać, gdy próbujesz poprawić wydajność za pomocą dodatkowej pamięci podręcznej i kolejek. W efekcie można zakończyć z użyciem złożonych architektur, które mają zbyt wiele warstw.

Z kolei [mikrousługi stanowe](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) mogą programu Excel w zaawansowanych scenariuszach, ponieważ nie ma opóźnienia między logiką domeny a danymi. Duże przetwarzanie danych, zaplecze gier, bazy danych jako usługa i inne scenariusze o niskich opóźnieniach korzystają z usług stanowych, które pozwalają na szybszy dostęp do stanu lokalnego.

Bezstanowe i bezstanowe usługi są uzupełniane. Na przykład, jak widać na rysunku z właściwym diagramem 4-14, usługa stanowa może zostać podzielona na wiele partycji. Aby uzyskać dostęp do tych partycji, może być potrzebna usługa bezstanowa działająca jako Usługa bramy, która wie, jak rozwiązać każdą partycję na podstawie kluczy partycji.

Usługi stanowe mają wady. Umożliwiają skalowanie w poziomie wysokiego poziomu złożoności. Funkcje, które zwykle są implementowane przez zewnętrzne systemy baz danych, muszą być objęte zadaniami, takimi jak replikacja danych na mikrousługi stanowe i partycjonowanie danych. Jednak jest to jeden z obszarów, w których program Orchestrator, taki jak [platforma Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z [niezawodnymi usługami stanowymi](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) , może pomóc w większości — upraszczając rozwój i cykl życia MIKROUSŁUG za pomocą [interfejsu API Reliable Services ](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)i [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Inne platformy mikrousług, które zezwalają na usługi stanowe, które obsługują wzorzec aktora i zwiększają odporność na uszkodzenia i opóźnienia między logiką biznesową i danymi, to Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research i [Akka.NET](https://getakka.net/). Obie platformy obecnie ulepszają obsługę platformy Docker.

Pamiętaj, że kontenery platformy Docker nie są bezstanowe. Jeśli chcesz zaimplementować usługę stanową, musisz mieć jedną z dodatkowych, opisanych wcześniej platform i wyższego poziomu.

## <a name="using-azure-service-fabric-mesh"></a>Korzystanie z usługi Azure Service Fabric siatka

Siatka Service Fabric platformy Azure to w pełni zarządzana usługa, która umożliwia deweloperom tworzenie i wdrażanie aplikacji o znaczeniu strategicznym bez konieczności zarządzania infrastrukturą. Używaj siatki Service Fabric, aby kompilować i uruchamiać bezpieczne, rozproszone aplikacje mikrousług, które skalują na żądanie.

Jak pokazano na rysunku 4-15, aplikacje hostowane na Service Fabric siatki są uruchamiane i skalowane bez narażania się na infrastrukturę IT.

![Aplikację z obsługą kontenera uruchomioną na pulpicie Docker można wdrożyć na platformie Azure Service Fabric siatkę bez obaw o infrastrukturę.](media/image39.png)

**Rysunek 4-15**. Wdrażanie aplikacji mikrousług/kontenerów do Service Fabric siatki

W obszarze okładek Service Fabric siatka składa się z klastrów tysięcy maszyn. Wszystkie operacje klastra są ukryte przed deweloperem. Wystarczy przekazać kontenery i określić potrzebne zasoby, wymagania dotyczące dostępności i limity zasobów. Service Fabric siatka automatycznie przydzieli infrastrukturę żądaną przez wdrożenie aplikacji, a także obsługuje awarie infrastruktury, upewniając się, że aplikacje są wysoce dostępne. Musisz tylko zadbać o kondycję i czas odpowiedzi aplikacji, a nie infrastruktury.

Aby uzyskać więcej informacji, zobacz [dokumentację siatki Service Fabric](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Wybieranie koordynatorów na platformie Azure

Poniższa tabela zawiera wskazówki dotyczące programu Orchestrator, który ma być używany w zależności od obciążeń i fokus systemu operacyjnego.

![Usługi Azure Kubernetes Services są bardziej dojrzałe w systemie Linux niż w przypadku systemu Windows i są najczęściej używane do wdrażania mikrousług na podstawie kontenerów. Usługa Azure Service Fabric (zarówno klaster, jak i siatka) jest bardziej dojrzała w systemie Windows niż system Linux, powszechnie używany w przypadku mikrousług opartych na kontenerach i mikrousługach opartych na zwykłych procesach i usługach stanowych.](media/image40.png)

**Rysunek 4-16**. Wybór programu Orchestrator w wskazówki dotyczące platformy Azure

>[!div class="step-by-step"]
>[Poprzedni](soa-applications.md)Następny
>[](deploy-azure-kubernetes-service.md)
