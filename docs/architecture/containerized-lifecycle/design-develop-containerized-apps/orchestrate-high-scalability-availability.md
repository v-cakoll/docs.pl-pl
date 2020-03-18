---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Prawdziwe aplikacje produkcyjne muszą być wdrażane i zarządzane za pomocą koordynatorów, które obsługują kondycję, obciążenie i cykle życia wszystkich kontenerów.
ms.date: 02/15/2019
ms.openlocfilehash: e548e6b3816dec1e56c273c53c9fd052443eb09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76919542"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Przy użyciu koordynatorów dla aplikacji gotowych do produkcji jest niezbędna, jeśli aplikacja jest oparta na mikrousług lub podzielone na wiele kontenerów. Jak wprowadzono wcześniej w podejściu opartym na mikrousługach, każda mikrousługa jest właścicielem swojego modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia rozwoju i wdrażania. Ale nawet jeśli masz bardziej tradycyjną aplikację, która składa się z wielu usług (takich jak SOA), będziesz mieć również wiele kontenerów lub usług obejmujących jedną aplikację biznesową, które muszą zostać wdrożone jako system rozproszony. Tego rodzaju systemy są złożone do skalowania w sposób skalowany i zarządzania; w związku z tym absolutnie potrzebujesz koordynatora, jeśli chcesz mieć gotowe do produkcji i skalowalne aplikacji wielokontenerowej.

Rysunek 4-6 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Diagram przedstawiający złożone aplikacje platformy Docker w klastrze.](./media/orchestrate-high-scalability-availability/composed-docker-applications-cluster.png)

**Rysunek 4-6**. Skupisko kontenerów

Wygląda na to logiczne podejście. Ale jak obsługiwać równoważenie obciążenia, routingu i organizowanie tych złożonych aplikacji?

Docker CLI spełnia potrzeby zarządzania jednym kontenerem na jednym hoście, ale nie spełnia, jeśli chodzi o zarządzanie wieloma kontenerami wdrożonymi na wielu hostach dla bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która automatycznie uruchamia kontenery, skalowanie kontenerów z wieloma wystąpieniami na obraz, zawieszanie ich lub zamykanie ich w razie potrzeby, a najlepiej także kontrolowanie sposobu uzyskiwania dostępu do zasobów, takich jak sieć i dane Magazynu.

Aby wyjść poza zarządzanie poszczególnych kontenerów lub prostych złożonych aplikacji i przejść w kierunku większych aplikacji przedsiębiorstwa z mikrousług, należy zwrócić się do platform aranżacji i klastrowania.

Z punktu widzenia architektury i rozwoju, jeśli budujesz duże, korporacyjne, oparte na mikrousługach, aplikacje, ważne jest, aby zrozumieć następujące platformy i produkty obsługujące zaawansowane scenariusze:

- **Klastry i koordynatorów.** Gdy trzeba skalować w sposób skalowalny aplikacji na wielu hostach platformy Docker, takich jak w przypadku aplikacji opartej na dużych mikrousług, ważne jest, aby móc zarządzać wszystkimi tymi hostami jako jeden klaster przez abstrakcję złożoności platformy źródłowej. To, co klastry kontenerów i koordynatorów zapewniają. Przykładami koordynatorów są azure sieci szkieletowej usług i Kubernetes. Usługa Kubernetes jest dostępna na platformie Azure za pośrednictwem usługi Azure Kubernetes.

- **Pracownikom.** *Planowanie* oznacza możliwość uruchamiania kontenerów w klastrze przez administratora, więc planiści zapewniają również interfejs użytkownika. Harmonogram klastra ma kilka obowiązków: efektywne korzystanie z zasobów klastra, ustawianie ograniczeń oferowanych przez użytkownika, efektywne równoważenie obciążenia kontenerów między węzłami lub hostami oraz niezawodne korzystanie z błędów przy jednoczesnym zapewnieniu wysokiej jakości Dostępność.

Pojęcia klastra i harmonogramu są ściśle powiązane, więc produkty dostarczane przez różnych dostawców często zapewniają oba zestawy możliwości. W poniższej sekcji przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te koordynatory są powszechnie oferowane w chmurach publicznych, takich jak Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

| Platforma | Komentarze |
|:---:|:---|
| **Kubernetes** <br/> ![Obraz logo Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt typu open source, który udostępnia funkcje, które wahają się od infrastruktury klastra i planowania kontenerów do aranżowania możliwości. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji w klastrach hostów. <br/> <br/> *Kubernetes* zapewnia infrastrukturę zorientowaną na kontenery, która grupuje kontenery aplikacji w jednostki logiczne w celu łatwego zarządzania i odnajdywania. <br/> <br/> *Kubernetes* jest dojrzały w Linuksie, mniej dojrzały w systemie Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Obraz logo usługi Azure Kubernetes.](./media/orchestrate-high-scalability-availability/azure-kubernetes-service-logo.png) | [Usługa Azure Kubernetes (AKS)](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |
| **Azure Service Fabric** <br/> ![Obraz logo sieci Szkieletowej usługi Azure.](./media/orchestrate-high-scalability-availability/azure-service-fabric-logo.png) | [Sieć szkieletowa usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) jest platformą mikrousług firmy Microsoft do tworzenia aplikacji. Jest [koordynatorem](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) usług i tworzy klastry maszyn. Sieć szkieletowa usług można wdrażać usługi jako kontenery lub jako zwykłe procesy. Można nawet mieszać usługi w procesach z usługami w kontenerach w tej samej aplikacji i klastra. <br/> <br/> *Klastry sieci szkieletowej usług* można wdrażać na platformie Azure, lokalnie lub w dowolnej chmurze. Jednak wdrożenie na platformie Azure jest uproszczone za pomocą podejścia zarządzanego. <br/> <br/> *Sieć szkieletowa usług* udostępnia dodatkowe i opcjonalne nakazowe [modele programowania sieci szkieletowej usług,](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) takie jak [usługi stanowe](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) i [niezawodne podmioty.](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) <br/> <br/> *Sieć szkieletowa usług* jest dojrzała w systemie Windows (lata ewoluujące w systemie Windows), mniej dojrzałe w systemie Linux. <br/> <br/> Kontenery systemu Linux i Windows są obsługiwane w sieci szkieletowej usług od 2017 r. |
| **Azure Service Fabric Mesh** <br/> ![Obraz logo usługi Azure Fabric Mesh.](./media/orchestrate-high-scalability-availability/azure-service-fabric-mesh-logo.png) | [*Usługa Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferuje taką samą niezawodność, wydajność o krytycznym znaczeniu i skalowanie jak sieć szkieletowa usług, ale oferuje również w pełni zarządzaną i bezserwerową platformę. Nie trzeba zarządzać klastrem, maszynami wirtualnymi, magazynem ani konfiguracją sieci. Wystarczy skupić się na rozwoju aplikacji. <br/> <br/> *Siatka sieci szkieletowej usług* obsługuje kontenery systemu Windows i Linux, co pozwala na tworzenie z dowolnym językiem programowania i struktury do wyboru.

## <a name="using-container-based-orchestrators-in-azure"></a>Korzystanie z koordynatorów opartych na kontenerach na platformie Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry platformy Docker i obsługę aranżacji, w tym azure, amazon EC2 Container Service i Google Container Engine. Platforma Azure zapewnia obsługę klastra platformy Docker i koordynatora za pośrednictwem usługi Azure Kubernetes Service (AKS), sieci szkieletowej usług Azure i usługi Azure Service Fabric Mesh.

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes

Klastra Kubernetes puluje kilka hostów platformy Docker i udostępnia je jako jeden wirtualny host platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalowania w sposób skalowania w sposób z dowolną liczbą wystąpień kontenera. Klaster będzie obsługiwać wszystkie złożone instalacji wodociągowej zarządzania, takich jak skalowalność, kondycja i tak dalej.

Usługa AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Korzystając ze zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu open source, usługa AKS umożliwia korzystanie z istniejących umiejętności lub korzystanie z dużej i rosnącej wiedzy społeczności w celu wdrażania aplikacji opartych na kontenerach na platformie Microsoft Azure i zarządzania nimi .

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi i technologii typu docker klastrowania typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a AKS obsługuje wszystko inne.

![Diagram przedstawiający strukturę klastra Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-cluster-simplified-structure.png)

**Rysunek 4-7**. Uproszczona struktura i topologia klastra Kubernetes

Rysunek 4-7 przedstawia strukturę klastra Kubernetes, w którym węzeł główny (VM) kontroluje większość koordynacji klastra i można wdrożyć kontenery do pozostałych węzłów, które są zarządzane jako pojedyncza pula z punktu widzenia aplikacji. Pozwala to skalować do tysięcy, a nawet dziesiątek tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla Kubernetes

W środowisku programistycznym, które [Docker ogłosił w lipcu 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)r., Kubernetes może również działać na jednym komputerze deweloperskim (Windows 10 lub macOS), instalując [docker Desktop](https://www.docker.com/community-edition). Później można wdrożyć w chmurze (AKS) do dalszych testów integracji, jak pokazano na rysunku 4-8.

![Diagram przedstawiający Kubernetes na komputerze deweloperskim, a następnie wdrożony w usłudze AKS.](./media/orchestrate-high-scalability-availability/kubernetes-development-environment.png)

**Rysunek 4-8**. Uruchamianie Kubernetes w maszynie deweloperskiej i chmurze

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z usługi AKS, można wdrożyć klaster AKS z witryny Azure portal lub przy użyciu interfejsu ósemki. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [Wdrażanie klastra usługi Azure Kubernetes Service (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Nie ma żadnych opłat za oprogramowanie zainstalowane domyślnie jako część Usługi AKS. Wszystkie opcje domyślne są implementowane za pomocą oprogramowania open source. Usługa AKS jest dostępna dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wybrane wystąpienia obliczeniowe, a także inne zużywane zasoby infrastruktury, takie jak magazyn i sieć. Nie ma żadnych opłat przyrostowych dla samego Usługi AKS.

Aby uzyskać dalsze informacje dotyczące implementacji `kubectl` dotyczące `.yaml` wdrażania w środowisku Kubernetes na podstawie oryginalnych plików, zobacz wpis [dotyczący ustawiania eShopOnContainers w usłudze AKS (usługa Azure Kubernetes).](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service))

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z wykresami Helma w klastrach Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można `kubectl.exe` użyć oryginalnego narzędzia cli przy`.yaml` użyciu plików wdrażania opartych na formacie macierzystym (pliki), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji Kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się użycie [Helm](https://helm.sh/).

Wykresy helm ułatwiają definiowanie, wersja, instalowanie, udostępnianie, uaktualnianie lub wycofywanie nawet najbardziej złożonej aplikacji Kubernetes.

Idąc dalej, użycie helm jest również zalecane, ponieważ dodatkowe środowiska Kubernetes na platformie Azure, takie jak [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach Helm.

Helm jest utrzymywany przez [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) we współpracy z firmami Microsoft, Google, Bitnami i społecznością współautorów Helm.

Aby uzyskać dalsze informacje dotyczące implementacji wykresów Helm i Kubernetes, zobacz post na [Temat Używania wykresów helm do wdrażania eShopOnContainers do AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Korzystanie z usługi Azure Dev Spaces dla ciebie Cykl życia aplikacji Kubernetes

[Usługa Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne kubernetes dla zespołów. W przypadku minimalnej konfiguracji maszyny deweloperskiej możesz iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Program można tworzyć w systemie Windows, Mac lub Linux przy użyciu znanych narzędzi, takich jak Visual Studio, Visual Studio Code lub wiersza polecenia.

Jak wspomniano, usługi Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Usługa Azure Dev Spaces pomaga zespołom programistycznym zwiększyć produktywność w programie Kubernetes, ponieważ umożliwia szybkie iterowanie i debugowanie kodu bezpośrednio w globalnym klastrze Kubernetes na platformie Azure przy użyciu programu Visual Studio 2017 lub kodu programu Visual Studio. Ten klaster Kubernetes na platformie Azure jest udostępnionym zarządzanym klastrem Kubernetes, dzięki czemu twój zespół może współpracować. Można opracować kod w izolacji, a następnie wdrożyć do klastra globalnego i zrobić testowanie end-to-end z innymi składnikami bez replikowania lub makiety zależności.

Jak pokazano na rysunku 4–9, najbardziej wyróżniającą się funkcją w usłudze Azure Dev Spaces jest możliwość tworzenia "spacji", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze:

![Diagram przedstawiający użycie wielu spacji w przestrzeniach deweloperskich platformy Azure.](./media/orchestrate-high-scalability-availability/use-multiple-spaces-azure-dev.png)

**Rysunek 4-9**. Korzystanie z wielu spacji w przestrzeniach deweloperskich platformy Azure

Usługi Azure Dev Spaces można w przejrzysty sposób mieszać i dopasowywać mikrousług produkcyjnych z wystąpieniem kontenera dewelopera, aby ułatwić testowanie nowych wersji. Zasadniczo można skonfigurować współużytkowane miejsce deweloperów na platformie Azure. Każdy deweloper może skupić się tylko na swojej części aplikacji i można iteracyjne rozwijać "wstępnie zatwierdzone" kod w przestrzeni dewelopera, który już zawiera wszystkie inne usługi i zasoby w chmurze, które zależą od ich scenariuszy. Zależności są zawsze aktualne, a deweloperzy pracują w sposób odzwierciedlający środowisko produkcyjne.

Usługa Azure Dev Spaces udostępnia koncepcję przestrzeni, która umożliwia pracę w izolacji i bez obawy o zerwanie członków zespołu. Ta funkcja jest oparta na prefiksach adresów URL; Jeśli używasz prefiksu miejsca dewelopera w adresie URL dla żądania kontenera, usługi Azure Dev Spaces uruchamia specjalną wersję kontenera, który został wdrożony dla tego miejsca, jeśli istnieje. W przeciwnym razie uruchomi wersję globalną/skonsolidowaną.

Możesz zobaczyć [eShopOnContainers wiki strony na Platformie Azure Dev Spaces,](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) aby uzyskać praktyczny widok na konkretny przykład.

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [tworzenia zespołu za pomocą platformy Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Przestrzenie deweloperów platformy Azure** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficjalna strona. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Korzystanie z usługi Azure Service Fabric

Sieć szkieletowa usług platformy Azure powstała w wyniku przejścia firmy Microsoft z dostarczania produktów "box", które były zazwyczaj monolityczne w stylu, do dostarczania usług. Doświadczenie tworzenia i obsługi dużych usług na dużą skalę, takich jak Azure SQL Database, Azure Cosmos DB, Azure Service Bus lub Cortana's Backend, w kształcie sieci szkieletowej usług. Platforma ewoluowała z czasem, gdy coraz więcej usług ją przyjmowało. Co ważne, sieć szkieletowa usług musiała działać nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Celem sieci szkieletowej usług jest rozwiązanie trudnych problemów związanych z tworzeniem i uruchamianiem usługi oraz efektywne korzystanie z zasobów infrastruktury, dzięki czemu zespoły mogą rozwiązywać problemy biznesowe przy użyciu podejścia mikrousług.

Sieć szkieletowa usług udostępnia dwa szerokie obszary ułatwiające tworzenie aplikacji korzystających z podejścia mikrousług:

- Platforma, która zapewnia usługi systemowe do wdrażania, skalowania, uaktualniania, wykrywania i ponownego uruchamiania usług, odnajdowania lokalizacji usługi, zarządzania stanem i monitorowania kondycji. Te usługi systemowe w efekcie włączyć wiele właściwości mikrousług opisanych wcześniej.

- Programowanie interfejsów API lub struktur, aby ułatwić tworzenie aplikacji jako mikrousług: [niezawodne podmioty i niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Można wybrać dowolny kod do tworzenia mikrousług, ale te interfejsy API sprawiają, że zadanie bardziej proste i integrują się z platformą na poziomie głębszym. W ten sposób można uzyskać informacje o kondycji i diagnostyki lub można skorzystać z niezawodnego zarządzania stanem.

Sieć szkieletowa usług jest niezgodna z możliwością tworzenia usługi i można korzystać z dowolnej technologii. Jednak zapewnia wbudowane interfejsy API programowania, które ułatwiają tworzenie mikrousług.

Jak pokazano na rysunku 4-10, można tworzyć i uruchamiać mikrousług w sieci szkieletowej usług jako proste procesy lub kontenery platformy Docker. Istnieje również możliwość mieszania mikrousług opartych na kontenerach z mikrousługopartych na procesach w tym samym klastrze sieci szkieletowej usług.

![Diagram przedstawiający porównanie klastrów sieci szkieletowej usługi Azure.](./media/orchestrate-high-scalability-availability/azure-service-fabric-cluster-types.png)

**Rysunek 4-10**. Wdrażanie mikrousług jako procesów lub kontenerów w sieci szkieletowej usługi Azure

Na pierwszym obrazie są widoczne mikrousługi jako procesy, w których każdy węzeł uruchamia jeden proces dla każdej mikrousługi. Na drugim obrazie są widoczne mikrousługi jako kontenery, gdzie każdy węzeł uruchamia platformę Docker z kilkoma kontenerami, jeden kontener na mikrousługę. Klastry sieci szkieletowej usług oparte na hostach systemu Linux i Windows mogą uruchamiać odpowiednio kontenery systemu Docker Linux i kontenery systemu Windows.

Aby uzyskać aktualne informacje o obsłudze kontenerów w sieci szkieletowej usług Azure, zobacz [Sieć szkieletowa usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Sieć szkieletowa usług jest dobrym przykładem platformy, gdzie można zdefiniować inną architekturę logiczną (mikrousług biznesowych lub ograniczone konteksty) niż implementacja fizyczna. Na przykład jeśli zaimplementujesz [stateful niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [sieci szkieletowej usług platformy Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które są wprowadzane w następnej sekcji "[Stateless vs stateful mikrousług](#stateless-versus-stateful-microservices)," masz koncepcji mikrousług biznesowych z wielu usług fizycznych.

Jak pokazano na rysunku 4-10 i myślenia z logicznego/biznesowego mikrousługi perspektywy podczas implementowania usługi stateful niezawodneusługi sieci szkieletowej usługi, zwykle należy zaimplementować dwie warstwy usług. Pierwszym z nich jest zaplecza stanowej niezawodnej usługi, która obsługuje wiele partycji (każda partycja jest usługą stanową). Drugi to usługa frontonu lub usługa Gateway odpowiedzialna za routing i agregację danych na wielu partycjach lub wystąpieniach usługi stanowej. Ta usługa Bramy obsługuje również komunikację po stronie klienta za pomocą pętli ponawiania dostępu do usługi zaplecza. Jest to nazywane usługą Gateway, jeśli zaimplementujesz usługę niestandardową lub alternatywnie można również użyć nieszablonowego serwera proxy sieci szkieletowej [usług.](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)

![Diagram przedstawiający kilka usług stanowych w kontenerach.](./media/orchestrate-high-scalability-availability/service-fabric-stateful-business-microservice.png)

**Rysunek 4-11**. Mikrousługi biznesowe z kilkoma wystąpieniami usługi stanowej i frontonem bramy niestandardowej

W każdym przypadku, gdy używasz sieci szkieletowej usługi stateful usług niezawodne, masz również mikrousługi logiczne lub biznesowe (ograniczony kontekst), który składa się z wielu usług fizycznych. Każdy z nich usługi bramy i partycji usługi mogą być implementowane jako ASP.NET usług interfejsu API sieci Web, jak pokazano na rysunku 4-11. Sieć szkieletowa usług ma receptę do obsługi kilku stanowych niezawodnych usług w kontenerach.

W sieci szkieletowej usług można grupować i wdrażać grupy usług jako [aplikację sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), która jest jednostką pakowania i wdrażania dla koordynatora lub klastra. W związku z tym aplikacja sieci szkieletowej usług może być mapowane do tej autonomicznej firmy i logicznych granic mikrousług lub ograniczony kontekst, jak również, dzięki czemu można wdrożyć te usługi autonomicznie.

### <a name="service-fabric-and-containers"></a>Sieć szkieletowa usług i kontenery

W odniesieniu do kontenerów w sieci szkieletowej usług można również wdrożyć usługi w obrazach kontenerów w klastrze sieci szkieletowej usług. Jak pokazuje rysunek 4-12, przez większość czasu będzie tylko jeden kontener na usługę.

![Diagram przedstawiający jeden kontener na usługę podającą się do bazy danych.](./media/orchestrate-high-scalability-availability/azure-service-fabric-business-microservice.png)

**Rysunek 4-12**. Mikrousługi biznesowe z kilkoma usługami (kontenerami) w sieci szkieletowej usług

Aplikacja sieci szkieletowej usług można uruchomić kilka kontenerów uzyskujących dostęp do zewnętrznej bazy danych, a cały zestaw będzie logiczną granicą mikrousługi biznesowej. Jednak tak zwane kontenery "sidecar" (dwa kontenery, które muszą być wdrożone razem jako część usługi logicznej) są również możliwe w sieci szkieletowej usług. Ważną rzeczą jest to, że mikrousługi biznesowe ja logiczna jest logiczna granica wokół kilku elementów spójności. W wielu przypadkach może to być pojedyncza usługa z jednym modelem danych, ale w niektórych innych przypadkach może mieć również kilka usług fizycznych.

Należy zauważyć, że można mieszać usługi w procesach i usługach w kontenerach w tej samej aplikacji sieci szkieletowej usług, jak pokazano na rysunku 4-13.

![Diagram przedstawiający usługi w procesach i w kontenerach w tej samej aplikacji.](./media/orchestrate-high-scalability-availability/business-microservice-mapped-to-service-fabric-application.png)

**Rysunek 4-13**. Mikrousługi biznesowe mapowane na aplikację sieci szkieletowej usług z kontenerami i usługami stanowymi

Aby uzyskać więcej informacji na temat obsługi kontenerów w sieci szkieletowej usług Azure, zobacz [Sieć szkieletowa usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Mikrousługi bezstanowe i stanowe

Jak wspomniano wcześniej, każdy mikrousługi (logiczny ograniczony kontekst) musi być właścicielem modelu domeny (dane i logika). W przypadku mikrousług bezstanowych bazy danych będą zewnętrzne, wykorzystując opcje relacyjne, takie jak SQL Server lub opcje NoSQL, takie jak Usługa Azure Cosmos DB lub MongoDB.

Ale same usługi mogą być również stanowe w sieci szkieletowej usług, co oznacza, że dane znajdują się w mikrousługi. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousługi, w pamięci i utrwalił się na dyskach twardych i replikowane do innych węzłów. Rysunek 4–14 przedstawia różne podejścia.

![Diagram przedstawiający porównanie usługi bezstanowej i stanowej.](./media/orchestrate-high-scalability-availability/stateless-vs-stateful-microservices.png)

**Rysunek 4-14**. Mikrousługi bezstanowe i stanowe

W usługach bezstanowych stan (trwałość, baza danych) jest przechowywany z mikrousługi. W usługach stanowych stan jest przechowywany wewnątrz mikrousługi. Podejście bezstanowe jest całkowicie prawidłowy i jest łatwiejsze do zaimplementowania niż mikrousług stanowych, ponieważ podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Ale bezstanowe mikrousługi nakładania opóźnienia między procesem i źródeł danych. Obejmują one również więcej ruchomych elementów, gdy próbujesz zwiększyć wydajność za pomocą dodatkowej pamięci podręcznej i kolejek. W rezultacie można skończyć ze złożonymi architekturami, które mają zbyt wiele warstw.

Z drugiej strony [mikrousług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można excel w zaawansowanych scenariuszach, ponieważ nie ma żadnych opóźnień między logiki domeny i danych. Ciężkie przetwarzanie danych, zaplecze gier, bazy danych jako usługa i inne scenariusze o małym opóźnieniu korzystają z usług stanowych, które umożliwiają stan lokalny w celu uzyskania szybszego dostępu.

Usługi bezstanowe i stanowe uzupełniają się. Na przykład, jak widać na prawym diagramie na rysunku 4-14, usługa stanowa można podzielić na wiele partycji. Aby uzyskać dostęp do tych partycji, może być potrzebna usługa bezstanowa działająca jako usługa bramy, która wie, jak rozwiązać każdą partycję na podstawie kluczy partycji.

Służby państwowe mają wady. Narzucają one wysoki poziom złożoności, który należy skalować. Funkcje, które zwykle są implementowane przez zewnętrzne systemy baz danych, muszą być uwzględnione w zadaniach, takich jak replikacja danych w mikrousługach stanowych i partycjonowanie danych. Jest to jednak jeden z obszarów, w których koordynator, taki jak [azure service fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [stanowych usług niezawodne może](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pomóc najbardziej — przez uproszczenie rozwoju i cyklu życia mikrousług stanowych przy użyciu [niezawodnego interfejsu API usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i niezawodne [podmioty .](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)

Inne struktury mikrousług, które umożliwiają usługi stanowe, obsługują wzorzec aktora i poprawiają odporność na uszkodzenia i opóźnienia między logiką biznesową a danymi, to Microsoft [Orleans](https://github.com/dotnet/orleans), z firmy Microsoft Research i [Akka.NET](https://getakka.net/). Obie struktury są obecnie poprawy ich wsparcia dla platformy Docker.

Należy pamiętać, że kontenery platformy Docker są same w sobie bezstanowe. Jeśli chcesz zaimplementować usługę stanową, potrzebujesz jednej z dodatkowych ramek i struktur wyższego poziomu odnotowanych wcześniej.

## <a name="using-azure-service-fabric-mesh"></a>Korzystanie z siatki sieci szkieletowej usługi Azure

Usługa Azure Service Fabric Mesh to w pełni zarządzana usługa, która umożliwia deweloperom tworzenie i wdrażanie aplikacji o znaczeniu krytycznym bez zarządzania żadną infrastrukturą. Usługa Service Fabric Mesh pozwala tworzyć i uruchamiać bezpieczne rozproszone aplikacje mikrousług, które można skalować na żądanie.

Jak pokazano na rysunku 4-15, aplikacje hostowane w usłudze Service Fabric Mesh uruchamiają się i skalują bez martwienia się o infrastrukturę, która ją zasila.

![Diagram przedstawiający wdrożenie z lokalnego repozytorium do siatki sieci szkieletowej usług.](media/orchestrate-high-scalability-availability/deploy-microservice-containers-apps-service-fabric-mesh.png)

**Rysunek 4-15**. Wdrażanie aplikacji mikrousługi/kontenerów w usłudze Service Fabric Mesh

Pod osłonami siatka sieci szkieletowej usług składa się z klastrów tysięcy maszyn. Wszystkie operacje klastrów są ukryte przed deweloperem. Wystarczy przekazać kontenery i określić potrzebne zasoby, wymagania dotyczące dostępności i limity zasobów. Usługa Service Fabric Mesh automatycznie alokuje infrastrukturę żądaną przez wdrożenie aplikacji i obsługuje także błędy infrastruktury, zapewniając wysoką dostępność aplikacji. Musisz zadbać jedynie o kondycję i szybkość reakcji aplikacji, nie martwiąc się o infrastrukturę.

Aby uzyskać więcej informacji, zobacz [dokumentację siatki sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Wybór koordynatorów na platformie Azure

Poniższa tabela zawiera wskazówki dotyczące tego, który koordynator do użycia w zależności od obciążeń i fokus uosywu.

![Obraz tabeli, która porównuje Kubernetes i sieci szkieletowej usług.](media/orchestrate-high-scalability-availability/orchestrator-selection-azure-guidance.png)

**Rysunek 4-16**. Wybór koordynatora w wskazówki dotyczące platformy Azure

>[!div class="step-by-step"]
>[Poprzedni](soa-applications.md)
>[następny](deploy-azure-kubernetes-service.md)
