---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Rzeczywiste aplikacje produkcyjne muszą być wdrażane i zarządzane za pomocą koordynatorów, które obsługują kondycję, obciążenie pracą i cykle życia wszystkich kontenerów.
ms.date: 02/15/2019
ms.openlocfilehash: 369971455168026d768220dae6e2da5ce92bc698
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989002"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Za pomocą orchestrators dla aplikacji gotowych do produkcji jest niezbędne, jeśli aplikacja jest oparta na mikrousług lub podzielone na wiele kontenerów. Zgodnie z wcześniejszym wprowadzeniem w podejściu opartym na mikrousługach każda mikrousługa jest właścicielem swojego modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia rozwoju i wdrażania. Ale nawet jeśli masz bardziej tradycyjną aplikację, która składa się z wielu usług (takich jak SOA), będziesz mieć również wiele kontenerów lub usług składających się z jednej aplikacji biznesowej, które muszą zostać wdrożone jako system rozproszony. Tego rodzaju systemy są złożone do skalowania w poziomie i zarządzania; w związku z tym absolutnie potrzebujesz koordynatora, jeśli chcesz mieć gotową do produkcji i skalowalną aplikację wielokontensjalną.

Rysunek 4-6 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Diagram przedstawiający złożone aplikacje platformy Docker w klastrze.](./media/orchestrate-high-scalability-availability/composed-docker-applications-cluster.png)

**Rysunek 4-6**. Klaster kontenerów

Wygląda to na logiczne podejście. Ale jak obsługiwać równoważenie obciążenia, routing i organizowanie tych złożonych aplikacji?

Zestaw wiersza polecenia platformy Docker spełnia potrzeby zarządzania jednym kontenerem na jednym hoście, ale nie jest dostępny, jeśli chodzi o zarządzanie wieloma kontenerami wdrożonymi na wielu hostach dla bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która automatycznie uruchamia kontenery, skaluje kontenery w poziomie z wieloma wystąpieniami na obraz, zawiesza je lub zamyka je w razie potrzeby, a najlepiej kontroluje sposób uzyskiwania dostępu do zasobów, takich jak sieć i magazyn danych.

Aby wyjść poza zarządzanie poszczególnych kontenerów lub prostych składa aplikacji i przejść do większych aplikacji korporacyjnych z mikrousług, należy zwrócić się do platform aranżacji i klastrowania.

Z punktu widzenia architektury i rozwoju, jeśli budujesz dużych, przedsiębiorstw, opartych na mikrousługach, aplikacje, ważne jest, aby zrozumieć następujące platformy i produkty, które obsługują zaawansowane scenariusze:

- **Klastry i koordynatorzy.** Gdy trzeba skalować w poziomie aplikacji w wielu hostach platformy Docker, takich jak za pomocą dużych aplikacji opartych na mikrousługach, jest bardzo ważne, aby móc zarządzać wszystkimi tymi hostami jako pojedynczy klaster, abstrakcji złożoności platformy podstawowej. To, co zapewniają klastry kontenerów i orchestrators. Przykładami koordynatorów są usługa Azure Service Fabric i Kubernetes. Usługa Kubernetes jest dostępna na platformie Azure za pośrednictwem usługi Azure Kubernetes.

- **Pracownikom.** *Planowanie* oznacza, że administrator może uruchamiać kontenery w klastrze, więc harmonogramy zapewniają również interfejs użytkownika w tym celu. Harmonogram klastra ma kilka obowiązków: aby efektywnie korzystać z zasobów klastra, ustawić ograniczenia dostarczone przez użytkownika, skutecznie równoważyć obciążenia kontenerów między węzłami lub hostami i być niezawodne przed błędami, zapewniając jednocześnie wysoką dostępność.

Pojęcia klastra i harmonogramu są ściśle powiązane, więc produkty dostarczane przez różnych dostawców często zapewniają oba zestawy możliwości. W poniższej sekcji przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te orchestrators są szeroko oferowane w chmurach publicznych, takich jak Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

| Platforma | Komentarze |
|:---:|:---|
| **Kubernetes** <br/> ![Obraz logo Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt typu open source, który zapewnia funkcje, które waha się od infrastruktury klastra i planowania kontenerów do możliwości aranżacji. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji w klastrach hostów. <br/> <br/> *Kubernetes* zapewnia kontenerozajęzykową, która grupuje kontenery aplikacji w jednostki logiczne w celu łatwego zarządzania i odnajdywania. <br/> <br/> *Kubernetes* jest dojrzały w Linuksie, mniej dojrzały w systemie Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Obraz logo usługi Azure Kubernetes.](./media/orchestrate-high-scalability-availability/azure-kubernetes-service-logo.png) | [Usługa Kubernetes azure (AKS)](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |
| **Azure Service Fabric** <br/> ![Obraz logo sieci szkieletowej usług Azure.](./media/orchestrate-high-scalability-availability/azure-service-fabric-logo.png) | [Sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) jest platformą mikrousług firmy Microsoft do tworzenia aplikacji. Jest [koordynatorem](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) usług i tworzy klastry maszyn. Sieci szkieletowej usług można wdrożyć usługi jako kontenery lub jako zwykłych procesów. Może nawet mieszać usługi w procesach z usługami w kontenerach w ramach tej samej aplikacji i klastra. <br/> <br/> *Klastry sieci szkieletowej usług* można wdrożyć na platformie Azure, lokalnie lub w dowolnej chmurze. Jednak wdrażanie na platformie Azure jest uproszczone dzięki podejściu zarządzanemu. <br/> <br/> *Usługa Sieci szkieletowej* zapewnia dodatkowe i opcjonalne modele [programowania sieci szkieletowej usług nakazowych,](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) takie jak [usługi stanowe](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) i [niezawodne aktorzy.](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) <br/> <br/> *Usługa Fabric* jest dojrzała w systemie Windows (lata ewoluujące w systemie Windows), mniej dojrzała w systemie Linux. <br/> <br/> Kontenery Linux i Windows są obsługiwane w sieci szkieletowej usług od 2017 roku. |
| **Azure Service Fabric Mesh** <br/> ![Obraz logo sieci szkieletowej usługi Azure.](./media/orchestrate-high-scalability-availability/azure-service-fabric-mesh-logo.png) | [*Usługa Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferuje taką samą niezawodność, wydajność o znaczeniu krytycznym i skalę jak sieć szkieletowa usług, ale oferuje również w pełni zarządzaną i bezserwerową platformę. Nie trzeba zarządzać klastrem, maszynami wirtualnymi, magazynem ani konfiguracją sieci. Wystarczy skupić się na rozwoju aplikacji. <br/> <br/> *Usługa Mesh sieci szkieletowej* obsługuje kontenery systemu Windows i Linux, co pozwala na tworzenie z dowolnego języka programowania i struktury do wyboru.

## <a name="using-container-based-orchestrators-in-azure"></a>Korzystanie z koordynatorów opartych na kontenerach na platformie Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry platformy Docker i obsługę aranżacji, w tym platformę Azure, usługę kontenerów Amazon EC2 i usługę kontenerów Google. Platforma Azure zapewnia obsługę klastra i koordynatora platformy Docker za pośrednictwem usługi Azure Kubernetes Service (AKS), sieci szkieletowej azure service fabric i usługi Azure Service Fabric Mesh.

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes

Klaster usługi Kubernetes buforuje kilka hostów platformy Docker i udostępnia je jako pojedynczy wirtualny host platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalować w poziomie z dowolną liczbą wystąpień kontenerów. Klaster będzie obsługiwać wszystkie złożone instalacji wodno-kanalizacyjne zarządzania, takich jak skalowalność, kondycja i tak dalej.

Usługa AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Korzystając ze zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu open source, usługa AKS umożliwia korzystanie z istniejących umiejętności lub korzystanie z dużej i rosnącej wiedzy specjalistycznej społeczności w celu wdrażania aplikacji opartych na kontenerach i zarządzania nimi na platformie Microsoft Azure.

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi i technologii typu open source klastrowania platformy Docker specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia aranżatora, a AKS obsługuje wszystko inne.

![Diagram przedstawiający strukturę klastra Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-cluster-simplified-structure.png)

**Rysunek 4-7**. Uproszczona struktura i topologia klastra Kubernetes

Rysunek 4-7 przedstawia strukturę klastra Kubernetes, gdzie węzeł główny (VM) kontroluje większość koordynacji klastra i można wdrożyć kontenery do pozostałych węzłów, które są zarządzane jako pojedyncza pula z punktu widzenia aplikacji. Dzięki temu można skalować do tysięcy, a nawet dziesiątki tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla kubernetes

W środowisku programistycznym, które [firma Docker ogłosiła w lipcu 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)r., kubernetes może również działać na jednym komputerze deweloperskim (Windows 10 lub macOS), instalując program [Docker Desktop.](https://www.docker.com/community-edition) Później można wdrożyć w chmurze (AKS) do dalszych testów integracji, jak pokazano na rysunku 4-8.

![Diagram przedstawiający kubernetes na komputerze deweloperskim, a następnie wdrożony w u usługi AKS.](./media/orchestrate-high-scalability-availability/kubernetes-development-environment.png)

**Rysunek 4-8**. Uruchamianie kubernetes na komputerze deweloperskim i chmurze

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z usługi AKS, należy wdrożyć klaster AKS z witryny Azure portal lub przy użyciu interfejsu wiersza polecenia. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [Wdrażanie klastra usługi Azure Kubernetes (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Nie ma żadnych opłat za oprogramowanie zainstalowane domyślnie w ramach usługi AKS. Wszystkie opcje domyślne są implementowane z oprogramowaniem open source. Usługa AKS jest dostępna dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wybraną instancję obliczeniową, a także za inne używane zasoby infrastruktury, takie jak magazynowanie i sieć. Nie ma żadnych opłat przyrostowych dla samego AKS.

Aby uzyskać dalsze informacje na temat implementacji w usłudze Kubernetes na `kubectl` podstawie i oryginalnych `.yaml` plików, zobacz post w sprawie [Ustawianie eShopOnContainers w AKS (Usługa Azure Kubernetes)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z wykresami helm w klastrach Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można `kubectl.exe` użyć oryginalnego narzędzia interfejsu wiersza`.yaml` polecenia przy użyciu plików wdrażania opartych na formacie macierzystym (plikach), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się użycie [helm.](https://helm.sh/)

Wykresy helm ułatwia definiowanie, wersja, instalowanie, udostępnianie, uaktualnianie lub wycofywanie nawet najbardziej złożonej aplikacji Kubernetes.

Idąc dalej, użycie helmu jest również zalecane, ponieważ dodatkowe środowiska kubernetes na platformie Azure, takie jak [usługi Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach helm.

Helm jest utrzymywany przez [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) we współpracy z Microsoft, Google, Bitnami i społecznością współpracowników Helm.

Aby uzyskać więcej informacji na temat implementacji wykresów Helm i Kubernetes, zobacz post na [korzystanie z wykresów helm do wdrażania eShopOnContainers do AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Korzystanie z usługi Azure Dev Spaces w cyklu życia aplikacji Kubernetes

[Usługa Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne Kubernetes dla zespołów. W przypadku minimalnej konfiguracji maszyny deweloperskiej możesz iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Można tworzyć na windows, Mac lub Linux przy użyciu znanych narzędzi, takich jak Visual Studio, Visual Studio Code lub wiersza polecenia.

Jak wspomniano, usługa Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Usługa Azure Dev Spaces pomaga zespołom deweloperskim zwiększyć produktywność w witrynie Kubernetes, ponieważ umożliwia szybkie iterację i debugowanie kodu bezpośrednio w globalnym klastrze kubernetes na platformie Azure, używając tylko programu Visual Studio 2017 lub kodu programu Visual Studio. Ten klaster Kubernetes na platformie Azure jest udostępnionym klastrem kubernetes zarządzanym, dzięki czemu zespół może współpracować ze sobą. Można opracować kod w izolacji, a następnie wdrożyć w klastrze globalnym i zrobić end-to-end testowania z innymi składnikami bez replikowania lub mocking się zależności.

Jak pokazano na rysunku 4-9, najbardziej wyróżniającą się funkcją w usłudze Azure Dev Spaces jest możliwość tworzenia "przestrzeni", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze:

![Diagram przedstawiający użycie wielu spacji w przestrzeniach deweloperów platformy Azure.](./media/orchestrate-high-scalability-availability/use-multiple-spaces-azure-dev.png)

**Rysunek 4-9**. Korzystanie z wielu spacji w przestrzeniach deweloperskich platformy Azure

Usługa Azure Dev Spaces można w sposób przejrzysty mieszać i dopasować mikrousług produkcyjnych z wystąpieniem kontenera deweloperów, aby ułatwić testowanie nowych wersji. Zasadniczo można skonfigurować udostępnionego obszaru deweloperów na platformie Azure. Każdy deweloper może skupić się tylko na swojej części aplikacji i może iteratively rozwijać "wstępnie zatwierdzone" kod w przestrzeni deweloperów, który zawiera już wszystkie inne usługi i zasoby w chmurze, które ich scenariusze zależą od. Zależności są zawsze aktualne, a deweloperzy pracują w sposób odzwierciedlający środowisko produkcyjne.

Usługa Azure Dev Spaces udostępnia koncepcję miejsca, która umożliwia pracę w izolacji i bez obawy przed złamaniem członków zespołu. Ta funkcja jest oparta na prefiksach adresów URL; Jeśli używasz prefiksu miejsca dev w adresie URL dla żądania kontenera, usługa Azure Dev Spaces uruchamia specjalną wersję kontenera, który został wdrożony dla tego miejsca, jeśli istnieje. W przeciwnym razie uruchomi wersję globalną/skonsolidowaną.

Możesz zobaczyć [stronę wiki eShopOnContainers w usłudze Azure Dev Spaces,](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) aby uzyskać praktyczny widok na konkretnym przykładzie.

Aby uzyskać więcej informacji, zobacz artykuł na [temat rozwoju zespołu za pomocą usługi Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Miejsca deweloperów platformy Azure** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficjalna strona. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Korzystanie z usługi Azure Service Fabric

Usługa Azure Service Fabric powstała z przejścia firmy Microsoft z dostarczania produktów "box", które były zazwyczaj monolityczne w stylu, do dostarczania usług. Środowisko tworzenia i obsługi dużych usług na dużą skalę, takich jak Azure SQL Database, Azure Cosmos DB, Azure Service Bus lub Cortana's Backend, ukształtowane sieci szkieletowej usług. Platforma ewoluowała z czasem, gdy coraz więcej usług ją przyjmowało. Co ważne, sieci szkieletowej usług musiał działać nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Celem sieci szkieletowej usług jest rozwiązanie trudnych problemów związanych z tworzeniem i uruchamianiem usługi oraz efektywnym wykorzystaniem zasobów infrastruktury, dzięki czemu zespoły mogą rozwiązywać problemy biznesowe przy użyciu podejścia mikrousług.

Sieci szkieletowej usług zawiera dwa szerokie obszary, które ułatwią tworzenie aplikacji, które używają podejścia mikrousług:

- Platforma, która zapewnia usługi systemowe do wdrażania, skalowania, uaktualniania, wykrywania i ponownego uruchamiania usług, odnajdowania lokalizacji usługi, zarządzania stanem i monitorowania kondycji. Te usługi systemowe w efekcie włączyć wiele cech mikrousług opisanych wcześniej.

- Programowanie interfejsów API lub struktur, aby ułatwić tworzenie aplikacji jako mikrousług: [niezawodne podmioty i niezawodne usługi.](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) Można wybrać dowolny kod do tworzenia mikrousług, ale te interfejsy API sprawiają, że zadanie bardziej proste i integrują się z platformą na głębszym poziomie. W ten sposób można uzyskać informacje o kondycji i diagnostyki lub można skorzystać z niezawodnego zarządzania stanem.

Sieci szkieletowej usług jest niezależny w odniesieniu do sposobu tworzenia usługi i można użyć dowolnej technologii. Jednak zapewnia wbudowane programowanie interfejsów API, które ułatwiają tworzenie mikrousług.

Jak pokazano na rysunku 4-10, można tworzyć i uruchamiać mikrousług w sieci szkieletowej usług jako proste procesy lub jako kontenery platformy Docker. Istnieje również możliwość mieszania mikrousług opartych na kontenerach z mikrousług opartych na procesach w ramach tego samego klastra sieci szkieletowej usług.

![Diagram przedstawiający porównanie klastrów sieci szkieletowej usług Azure.](./media/orchestrate-high-scalability-availability/azure-service-fabric-cluster-types.png)

**Rysunek 4-10**. Wdrażanie mikrousług jako procesów lub kontenerów w sieci szkieletowej usług Azure

Na pierwszym obrazie zobaczysz mikrousług jako procesy, gdzie każdy węzeł uruchamia jeden proces dla każdej mikrousługi. Na drugim obrazie widać mikrousług jako kontenery, gdzie każdy węzeł uruchamia docker z kilku kontenerów, jeden kontener na mikrousługi. Klastry sieci szkieletowej usług oparte na hostach systemu Linux i Windows mogą uruchamiać kontenery Systemu Windows i kontenery systemu Windows.

Aby uzyskać aktualne informacje na temat obsługi kontenerów w sieci szkieletowej usług Azure, zobacz [Sieci szkieletowej usług i kontenerów.](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)

Sieci szkieletowej usług jest dobrym przykładem platformy, gdzie można zdefiniować inną architekturę logiczną (mikrousług biznesowych lub ograniczone konteksty) niż implementacji fizycznej. Na przykład jeśli implementujesz [stateful niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [sieci szkieletowej usług Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które są wprowadzane w następnej sekcji "[Bezstanowe versus stanowe mikrousługi](#stateless-versus-stateful-microservices)", masz koncepcji mikrousług biznesowych z wieloma usługami fizycznymi.

Jak pokazano na rysunku 4-10 i myślenia z punktu widzenia mikrousług logicznych/biznesowych, podczas implementowania usługi stateful niezawodnej usługi sieci szkieletowej usługi zwykle trzeba będzie zaimplementować dwie warstwy usług. Pierwszym z nich jest zaplecza stanowej niezawodnej usługi, która obsługuje wiele partycji (każda partycja jest usługą stanową). Drugi to usługa frontonu lub usługa bramy, odpowiedzialna za routing i agregację danych między wieloma partycjami lub wystąpieniami usługi stanowej. Ta usługa bramy obsługuje również komunikację po stronie klienta z pętlami ponawiania prób uzyskujących dostęp do usługi zaplecza. Jest to usługa bramy, jeśli zaimplementujesz usługę niestandardową lub alternatywnie można również użyć out-of-the-box Service Fabric [reverse proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Diagram przedstawiający kilka usług stanowych w kontenerach.](./media/orchestrate-high-scalability-availability/service-fabric-stateful-business-microservice.png)

**Rysunek 4-11**. Mikrousługa biznesowa z kilkoma wystąpieniami usługi stanowej i frontołową bramą niestandardową

W każdym przypadku podczas korzystania z usługi Service Fabric Stateful Niezawodne usługi, masz również mikrousługi logiczne lub biznesowe (ograniczony kontekst), który składa się z wielu usług fizycznych. Każdy z nich, usługa bramy i usługa partycji mogą być implementowane jako ASP.NET usług interfejsu API sieci Web, jak pokazano na rysunku 4-11. Usługa Sieci szkieletowej ma receptę do obsługi kilku stanowych niezawodnych usług w kontenerach.

W sieci szkieletowej usług można grupować i wdrażać grupy usług jako [aplikację sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), która jest jednostką pakowania i wdrażania dla koordynatora lub klastra. W związku z tym aplikacja sieci szkieletowej usług może być mapowane do tej autonomicznej biznesowej i logicznej granicy mikrousług lub ograniczonego kontekstu, więc można wdrożyć te usługi autonomicznie.

### <a name="service-fabric-and-containers"></a>Tkanina serwisowa i kontenery

W odniesieniu do kontenerów w sieci szkieletowej usług, można również wdrożyć usługi w obrazach kontenerów w klastrze sieci szkieletowej usług. Jak pokazano na rysunku 4-12, przez większość czasu będzie tylko jeden kontener na usługę.

![Diagram przedstawiający jeden kontener na usługę podawanie do bazy danych.](./media/orchestrate-high-scalability-availability/azure-service-fabric-business-microservice.png)

**Rysunek 4-12**. Mikrousługa biznesowa z kilkoma usługami (kontenerami) w sieci szkieletowej usług

Aplikacja sieci szkieletowej usług można uruchomić kilka kontenerów dostępu do zewnętrznej bazy danych i cały zestaw będzie logiczną granicą mikrousługi biznesowej. Jednak tak zwane kontenery "sidecar" (dwa kontenery, które muszą być wdrożone razem jako część usługi logicznej) są również możliwe w sieci szkieletowej usług. Ważną rzeczą jest to, że mikrousługa biznesowa jest logiczną granicą wokół kilku spójnych elementów. W wielu przypadkach może to być pojedyncza usługa z pojedynczym modelem danych, ale w niektórych innych przypadkach może mieć kilka usług fizycznych, jak również.

Należy zauważyć, że można mieszać usługi w procesach i usług w kontenerach, w tej samej aplikacji sieci szkieletowej usług, jak pokazano na rysunku 4-13.

![Diagram przedstawiający usługi w procesach i w kontenerach w tej samej aplikacji.](./media/orchestrate-high-scalability-availability/business-microservice-mapped-to-service-fabric-application.png)

**Rysunek 4-13**. Mikrousługa biznesowa zamapowana na aplikację sieci szkieletowej usług z kontenerami i usługami stanowymi

Aby uzyskać więcej informacji na temat obsługi kontenerów w sieci szkieletowej usług Azure, zobacz [Sieci szkieletowej usług i kontenerów.](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousługi

Jak wspomniano wcześniej, każda mikrousługa (logiczny ograniczony kontekst) musi posiadać swój model domeny (dane i logika). W przypadku mikrousług bezstanowych bazy danych będą zewnętrzne, wykorzystując opcje relacyjne, takie jak SQL Server lub opcje NoSQL, takie jak Usługa Azure Cosmos DB lub MongoDB.

Ale same usługi mogą być również stanowe w sieci szkieletowej usług, co oznacza, że dane znajdują się w mikrousługi. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousług, w pamięci i utrwalone na dyskach twardych i replikowane do innych węzłów. Rysunek 4-14 przedstawia różne podejścia.

![Diagram przedstawiający porównanie usługi bezstanowej i stanowej.](./media/orchestrate-high-scalability-availability/stateless-vs-stateful-microservices.png)

**Rysunek 4-14**. Bezstanowe i stanowe mikrousługi

W usługach bezstanowych stan (trwałość, baza danych) jest przechowywany z mikrousługi. W usługi stanowe stan jest przechowywany wewnątrz mikrousługi. Podejście bezstanowe jest całkowicie prawidłowe i jest łatwiejsze do zaimplementowania niż mikrousług stanowych, ponieważ podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Ale bezstanowe mikrousługi nakładają opóźnienia między procesem a źródłami danych. Obejmują one również więcej ruchomych elementów, gdy próbujesz poprawić wydajność dzięki dodatkowej pamięci podręcznej i kolejek. W rezultacie można skończyć ze złożonymi architekturami, które mają zbyt wiele warstw.

Z drugiej strony [mikrousług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można excel w zaawansowanych scenariuszach, ponieważ nie ma opóźnienia między logiką domeny i danych. Przetwarzanie danych o dużym obciążeniu, zaplecze gier, bazy danych jako usługa i inne scenariusze o małych opóźnieniach korzystają z usług stanowych, które umożliwiają stan lokalny w celu szybszego dostępu.

Usługi bezstanowe i stanowe uzupełniają się. Na przykład, jak widać na prawym diagramie na rysunku 4-14, usługi stanowej można podzielić na wiele partycji. Aby uzyskać dostęp do tych partycji, może być konieczne usługi bezstanowej działającej jako usługa bramy, która wie, jak rozwiązać każdą partycję na podstawie kluczy partycji.

Usługi stanowe mają wady. Nakładają one wysoki poziom złożoności, które mają być skalowane w poziomie. Funkcje, które zwykle są implementowane przez systemy zewnętrznej bazy danych, muszą być rozwiązane dla zadań, takich jak replikacja danych w ramach mikrousług stanowych i partycjonowanie danych. Jest to jednak jeden z obszarów, w których koordynator, taki jak [usługa Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jej [stanowymi niezawodnymi usługami,](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) może najbardziej pomóc — upraszczając rozwój i cykl życia mikrousług stanowych przy użyciu [interfejsu API niezawodnych usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [wiarygodnych aktorów.](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)

Inne struktury mikrousług, które umożliwiają usługi stanowe, obsługują wzorzec aktora i poprawiają odporność na uszkodzenia i opóźnienia między logiką biznesową a danymi, to Microsoft [Orleans](https://github.com/dotnet/orleans), z microsoft research i [Akka.NET](https://getakka.net/). Obie struktury są obecnie poprawy ich obsługi platformy Docker.

Należy pamiętać, że kontenery platformy Docker same są bezstanowe. Jeśli chcesz zaimplementować usługi stanowej, potrzebujesz jednego z dodatkowych ram nakazowych i wyższego poziomu, o których wspomniano wcześniej.

## <a name="using-azure-service-fabric-mesh"></a>Korzystanie z siatki sieci szkieletowej usług Azure

Usługa Azure Service Fabric Mesh to w pełni zarządzana usługa, która umożliwia deweloperom tworzenie i wdrażanie aplikacji o znaczeniu krytycznym bez zarządzania infrastrukturą. Usługa Service Fabric Mesh pozwala tworzyć i uruchamiać bezpieczne rozproszone aplikacje mikrousług, które można skalować na żądanie.

Jak pokazano na rysunku 4-15, aplikacje hostowane w sieci szkieletowej usługi działają i skalują się bez martwienia się o infrastrukturę, która ją zasila.

![Diagram przedstawiający wdrożenie z lokalnego repozytorium do sieci szkieletowej usług.](media/orchestrate-high-scalability-availability/deploy-microservice-containers-apps-service-fabric-mesh.png)

**Rysunek 4-15**. Wdrażanie aplikacji mikrousług/kontenerów w sieci szkieletowej usługi

W ramach pokrywy usługi Sieci szkieletowej mesh składa się z klastrów tysięcy maszyn. Wszystkie operacje klastrów są ukryte przed deweloperem. Wystarczy przekazać kontenery i określić zasoby, których potrzebujesz, wymagania dotyczące dostępności i limity zasobów. Usługa Service Fabric Mesh automatycznie alokuje infrastrukturę żądaną przez wdrożenie aplikacji i obsługuje także błędy infrastruktury, zapewniając wysoką dostępność aplikacji. Musisz zadbać jedynie o kondycję i szybkość reakcji aplikacji, nie martwiąc się o infrastrukturę.

Aby uzyskać więcej informacji, zobacz [dokumentację siatki sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Wybieranie koordynatorów na platformie Azure

W poniższej tabeli przedstawiono wskazówki dotyczące tego, jakiego programu orchestrator użyć w zależności od obciążeń i fokusu systemu operacyjnego.

![Obraz tabeli, która porównuje kubernetes i sieci szkieletowej usług.](media/orchestrate-high-scalability-availability/orchestrator-selection-azure-guidance.png)

**Rysunek 4-16**. Wybór koordynatora w wskazówki dotyczące platformy Azure

>[!div class="step-by-step"]
>[Poprzedni](soa-applications.md)
>[następny](deploy-azure-kubernetes-service.md)
