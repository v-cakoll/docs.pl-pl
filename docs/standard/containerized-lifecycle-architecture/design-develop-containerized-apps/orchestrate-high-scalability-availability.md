---
title: Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności
description: Aplikacje rzeczywistej produkcji mają być wdrażane i zarządzane przy użyciu koordynatorów, które obsługują kondycji, obciążenia i cyklami życia dla wszystkich kontenerów.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 749b613ac847c57eb993bff90b36f02a0b39477f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221163"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Organizowanie mikrousług i aplikacji wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Przy użyciu koordynatorów aplikacji gotowych do produkcji jest istotne, jeśli aplikacja jest oparta na mikrousługach lub po prostu podzielone między wiele kontenerów. Jak wprowadzona wcześniej w podejściu opartych na mikrousługach, każda mikrousługa jest właścicielem jej modelu i danych tak, aby go autonomicznego od środowisk programowania i wdrażania punktu widzenia. Ale nawet w przypadku bardziej tradycyjny aplikację która składa się z wielu usług (np. SOA), należy również będzie wiele kontenerów i usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone i skalowanie w poziomie i zarządzać; w związku z tym bezwzględnie konieczne koordynatora, jeśli chcesz mieć gotowy do produkcji i skalowalnych aplikacji wieloma kontenerami w celu.

Rysunek 4 – 6 przedstawia wdrożenie w klastrze aplikacji składających się z wielu mikrousług (kontenery).

![](./media/image6.png)

Rysunek 4 – 6: Klaster kontenerów

Wygląda jak algorytmu. Ale jak możesz obsługi równoważenia obciążenia, routingu i organizowanie te złożone aplikacje?

Interfejsu wiersza polecenia (CLI) Docker spełnia potrzeby zarządzania jeden kontener na jednym hoście, ale znajduje się krótki w przypadku zarządzania wieloma kontenerami wdrażane na wielu hostach w przypadku bardziej złożonych aplikacji rozproszonych. W większości przypadków należy to platforma zarządzania, która będzie automatycznie uruchom kontenery, zawieszać, lub zamknij je w razie i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieć i magazyn.

Czegoś Zarządzanie poszczególne kontenery lub bardzo proste aplikacje złożone i Przenieś kierunku większych aplikacje dla przedsiębiorstw przy użyciu mikrousług, należy go włączyć do aranżacji i klastrowanie platform.

Z architektury i projektowania punktu widzenia Jeśli tworzenie dużych przedsiębiorstw, opartych na mikrousługach, aplikacji, warto zapoznać się z następujących platform i produktów, które obsługuje zaawansowane scenariusze:

-   **Klastry i koordynatorów** konieczność skalowanie — aplikacji na wielu hostach Docker, takich jak przy użyciu dużych aplikacji opartych na mikrousługach, ważne jest aby można było zarządzać wszystkimi tymi hostami jako jednym klastrem przez abstrakcyjność złożoność podstawowej platformy. To, co zapewnia klastry kontenerów i koordynatorów. Przykłady koordynatorów Docker Swarm, Mesosphere DC/OS, Kubernetes (pierwsze trzy dostępne za pośrednictwem usługi Azure Container Service) i usługi Azure Service Fabric.

-   **Planiści** *Planowanie* oznacza, że mają możliwość na uruchamianie kontenerów w klastrze, dzięki czemu zapewniają także interfejs użytkownika przez administratora. Harmonogram klastra ma kilka obowiązki: wydajnie korzystać z zasobów klastra, aby ustawić ograniczenia podana przez użytkownika, do wydajne Równoważenie obciążenia kontenerów w węzłach lub hosty i być odporne na błędy przy jednoczesnym zapewnieniu wysokiego dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczane przez różnych dostawców często podać oba zestawy funkcji. Tabela 4-1 wymieniono najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Klastry te zwykle są oferowane w chmurach publicznych, takich jak platforma Azure.

Tabela 4-1: Platformy oprogramowania dla kontenera, klastrowanie, aranżację i planowanie

| Platforma | Opis |
|---|---|
| Docker Swarm<br/> ![Docker Swarm logo](./media/image7.png) | Rozwiązanie docker Swarm daje możliwość klastra i harmonogramu kontenerów platformy Docker. Przy użyciu koordynatora Swarm, można włączyć pulę hostów platformy Docker do pojedynczego wirtualnego hosta platformy Docker. Klientów można wprowadzać żądania interfejsu API Swarm w taki sam sposób, jak na hostach, co oznacza, że Swarm umożliwia łatwe skalowanie aplikacji na wielu hostach. <br /><br /> Rozwiązanie docker Swarm jest produktem docker, firma. <br /><br /> V1.12 platformy docker lub nowszej można uruchomić trybu macierzystego i wbudowanych Swarm. |
| System mesosphere DC/OS<br/>![System mesosphere DC/OS logo](./media/image8.png) |  Mesosphere Enterprise DC/OS (oparte na Apache Mesos) to platforma gotowe do produkcji do uruchamiania kontenerów i aplikacji rozproszonych. <br /><br /> DC/OS polega na abstrakcyjność zbiór zasobów dostępnych w klastrze oraz udostępniania tych zasobów korzystających z jego składników. Platforma Marathon zwykle jest używana harmonogramu zintegrowana z usługą platformy DC/OS. |
| Google Kubernetes<br />![Logo usługi Google Kubernetes](./media/image9.png) | Kubernetes to produkt typu open source, który zapewnia funkcje z zakresu od infrastruktury klastra i harmonogramów możliwości organizowanie kontenerów. Dzięki niemu można zautomatyzować wdrażanie, skalowanie i działanie kontenerów aplikacji w klastrach hostów. <br /><br /> Usługa Kubernetes zapewnia kontener skoncentrowane na infrastrukturę, która grupuje kontenery aplikacji w jednostki logiczne, aby ułatwić zarządzanie i odnajdywania. |
| Azure Service Fabric<br />![Logo usługi Azure Service Fabric](./media/image10.png) | [Usługa Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do tworzenia aplikacji. Jest [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z usług i służąca do tworzenia klastrów maszyn. Domyślnie Usługa Service Fabric wdraża i aktywuje usług jako procesy, ale usługi Service Fabric można wdrażać usług w obrazów kontenerów platformy Docker. Co ważniejsze, można łączyć usługi w procesach usługi w kontenerach w tej samej aplikacji. <br /><br /> Od maja 2017 r. funkcji usługi Service Fabric, która obsługuje wdrażanie usługi jako kontenery platformy Docker jest w stanie wersji zapoznawczej. <br /><br /> Możesz tworzyć usługi Service Fabric na wiele sposobów korzystania z [modeli programowania usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) wdrażanie [pliki wykonywalne gościa](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) oraz kontenerów. Usługa Service Fabric obsługuje modele normatywnych aplikacji np. [usług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) i [elementów Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Przy użyciu koordynatorów opartych na kontenerach na platformie Azure

Kilku dostawców chmury oferują obsługę kontenerów platformy Docker oraz klastrów platformy Docker oraz obsługę aranżacji, w tym platformy Azure, Amazon EC2 Container Service i Google kontenera aparatu. System Azure oferuje Docker klastra i orchestrator na pomoc techniczną za pomocą usługi Azure Container Service, jak wyjaśniono w następnej sekcji.

Inną możliwością jest używać usługi Azure Service Fabric, który również obsługuje platformę Docker oparty na systemie Linux i kontenerów Windows. Usługa Service Fabric działa na platformie Azure lub inne chmury oraz [lokalnych](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Za pomocą usługi Azure Container Service

Klaster Docker pul wielu hostów platformy Docker i przedstawia je w postaci jednego wirtualnego hosta platformy Docker, aby umożliwić wdrażanie wielu kontenerów do klastra. Klaster będzie obsługiwać wszystkie żmudne zarządzania złożone procesy takie jak skalowalność i kondycji. Rysunek 4 – 7 przedstawia sposób mapowania klastra platformy Docker dla aplikacji złożone Container Service.

Container Service umożliwia uproszczenie tworzenia, konfiguracji i zarządzania klastrem maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania konteneryzowanych aplikacji. Używanie zoptymalizowanej konfiguracji popularnych narzędzi planowania i organizowania typu open source, usługi Container Service zapewnia możliwość używanie posiadanych umiejętności lub sięganie na treść duży i rosnący zasób wiedzy społeczności, wdrażanie i zarządzanie nimi opartych na kontenerach aplikacje na platformie Azure.

Container Service optymalizuje konfigurację popularnych narzędzi typu open-source klastrowania platformy Docker i technologii pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, która oferuje przenośność kontenerów i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a usługa kontenerów zajmuje się całą resztą.

Container Service używa obrazów platformy Docker, aby upewnić się, że kontenery Twojej aplikacji są całkowicie przenośne. Obsługuje ona wybranych platformach aranżacji typu open source, np. DC/OS, Kubernetes i Docker Swarm aby upewnić się, że te aplikacje mogą być skalowane do tysięcy lub nawet dziesiątków tysięcy kontenerów.

Usługa Azure Container Service może potrwać korzystać z funkcji przeznaczonych dla przedsiębiorstw, platformy Azure, zachowując jednocześnie przenośność aplikacji, w tym w warstwach aranżacji.

![](./media/image11.png)

Rysunek 4 – 7: Klastrowanie opcje dostępne w usłudze Azure Container Service

Jak pokazano w rysunek 4 – 8, usługi Container Service jest po prostu infrastrukturę platformy Azure w celu wdrożenia rozwiązania DC/OS, Kubernetes lub Docker Swarm, ale nie implementuje żadnych dodatkowych programu orchestrator. W związku z tym usługi Container Service jest nie koordynatora, jako takie; jest infrastruktury, która korzysta z istniejących orkiestratorów typu open source dla kontenerów.

![](./media/image12.png)

Rysunek 4 – 8: Orkiestratorów w usłudze Container Service

Z punktu widzenia użycia celem usługi Container Service jest zapewnienie środowiska hostingu kontenerów za pomocą popularnych narzędzi typu open source i technologii. W tym celu udostępnia standardowe punkty końcowe interfejsu API dla wybranego koordynatora. Korzystając z tych punktów końcowych, można użyć dowolnego oprogramowania, który może komunikować się z tymi punktami końcowymi. Na przykład w przypadku punktu końcowego Docker Swarm można użyć interfejsu wiersza polecenia platformy Docker. DC/OS można użyć interfejsu wiersza polecenia DC/OS.

### <a name="getting-started-with-container-service"></a>Wprowadzenie do usługi Container Service

Aby rozpocząć korzystanie z usługi Container Service, wdrożyć klaster usługi Container Service w witrynie Azure portal przy użyciu szablonu usługi Azure Resource Manager lub [interfejsu wiersza polecenia](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostępne szablony to [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), i [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Można zmodyfikować szablony szybkiego startu, aby uwzględnić dodatkowej lub zaawansowanej konfiguracji platformy Azure.

**Więcej informacji o** Aby dowiedzieć się więcej na temat wdrażania klaster usługi Container Service w witrynie sieci Web platformy Azure, przeczytaj [wdrażanie klastra usługi Azure Container Service](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w ramach usług ACS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source.

Container Service jest obecnie dostępna dla standardowych A, D, DS, G i maszyn wirtualnych systemu Linux serii GS na platformie Azure. Opłaty są naliczane tylko za wystąpienia obliczeniowe, które możesz wybrać, a także inne użyte zasoby infrastruktury bazowej, takie jak storage i sieci. Istnieją ma opłat przyrostowych za usługi kontenera sama.

### <a name="additional-resources"></a>Dodatkowe zasoby

Poniżej przedstawiono lokalizacje, gdzie można znaleźć dodatkowe informacje:

-   Wprowadzenie do rozwiązania z usługą Container Service do hostowania kontenerów platformy Docker:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker Swarm — omówienie:  
    <https://docs.docker.com/swarm/overview/>

-   Omówienie trybu swarm:  
    <https://docs.docker.com/engine/swarm/>

-   Omówienie mesosphere DC/OS    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (oficjalna witryna):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Za pomocą usługi Service Fabric

Usługa Service Fabric powstały od firmy Microsoft przejście od dostarczania produktów "pola", które były zazwyczaj monolitycznych w stylu, dostarczaniu usług. Środowisko tworzenia i obsługi dużych usług na dużą skalę, takich jak Azure SQL Database, baza danych Documentdb Azure, Azure Service Bus lub zaplecza Cortany kształt usługi Service Fabric. Platforma ewoluował wraz z upływem czasu coraz więcej usług przyjęty go. Co ważniejsze usługi Service Fabric musiał uruchomić nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Usługa Service Fabric ma na celu rozwiązywanie trudnych problemów, kompilowania i uruchamiania usługi i efektywnie wykorzystując zasoby infrastruktury tak, aby zespoły można rozwiązać problemy biznesowe przy użyciu podejścia mikrousług.

Usługa Service Fabric udostępnia dwa obszary ułatwiające tworzenie aplikacji korzystających z podejścia mikrousług:

-   Platforma, która zapewnia usługi systemowe na wdrażanie, skalowanie, uaktualnienia, wykrywanie, ponowne uruchomienie usługi nie powiodło się, odnajdywanie lokalizacji usługi, zarządzanie stanem i monitorowanie kondycji. Te usługi systemu obowiązuje zapewniają wiele właściwości mikrousług z opisem w poprzedniej sekcji.

-   Interfejsy API programowania lub struktury, ułatwiające tworzenie aplikacji zgodnie z mikrousług: [interfejsu Reliable actors oraz usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Oczywiście można wybrać żadnego kodu do tworzenia usługi mikrousług, ale te interfejsy API upewnij zadania prostsze, a ich integracja z platformą dokładniej. W ten sposób można uzyskać kondycji i informacji diagnostycznych lub możesz korzystać z zalet zarządzania stanem niezawodne.

Usługa Service Fabric jest niezależny od względem jak opracować swoje usługi, a następnie można użyć dowolnej technologii. Jednak zapewnia wbudowane programowania interfejsów API, które ułatwiają tworzenie mikrousług.

Rysunek 4 – 9 pokazuje, jak utworzyć i uruchamianie mikrousług w usłudze Service Fabric, jako prosty procesy lub jako kontenery platformy Docker. Istnieje również możliwość mieszać opartych na kontenerach mikrousług przy użyciu procesu na podstawie mikrousług, w tym samym klastrze usługi Service Fabric.

![](./media/image13.png)

Rysunek 4 – 9: Wdrażanie mikrousług, jako procesów lub kontenerów w usłudze Azure Service Fabric

Klastry usługi Service Fabric, oparte na hostach z systemem Linux i Windows można uruchamiać kontenery platformy Docker w systemie Linux i Windows kontenery.

**Więcej informacji o** uzyskać aktualne informacje dotyczące obsługi kontenerów w usłudze Service Fabric, w witrynie sieci Web platformy Azure, przeczytaj [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Usługa Service Fabric jest dobrym przykładem platformy, z którym można zdefiniować różne architekturę logiczną (mikrousług biznesowych lub ograniczone konteksty) niż fizyczna implementacja. Na przykład w przypadku zaimplementowania [stanowych usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [usługi Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które zostały wprowadzone w następnej sekcji "[Stateless w porównaniu z mikrousług stanowych](#stateless-versus-stateful-microservices), "masz koncepcja mikrousług firmy z wieloma usługami fizycznych.

Jak pokazano na rysunku 4 – 10 i myśleć z punktu widzenia mikrousług/biznesowych podczas implementowania usługi Service Fabric Reliable usługa stanowa zazwyczaj należy zaimplementować dwie warstwy usług. Pierwszy jest zaplecza niezawodnej usługi stanowej, która obsługuje wiele partycji. Drugim jest usługa frontonu, czyli usługę bramy, odpowiedzialnym za routingu i agreguje dane należące do wielu partycji lub wystąpień usługi stanowej. Usługi bramy również obsługuje komunikację klienta z pętli ponawiania, uzyskiwanie dostępu do usługi zaplecza, używany w połączeniu z usługą Service Fabric [zwrotny serwer proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Rysunek 4-10: Mikrousługi biznesowych za pomocą kilku usługi stanowe i bezstanowe w usłudze Service Fabric

W każdym przypadku gdy używasz usługi Service Fabric stanowych usług Reliable Services, masz również logicznych lub pracy mikrousługi (ograniczony kontekst), zwykle składa się z wielu usług fizycznych. Każda z ich, Usługa bramy i partycji usługi można można zaimplementować jako usługi interfejsu API sieci Web platformy ASP.NET, jak pokazano na rysunku 4-10.

W usłudze Service Fabric, grupy i wdrażanie grup usług jako [aplikacji usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), czyli jednostki pakowania i wdrażania dla programu orchestrator lub klastra. W związku z tym aplikacja usługi Service Fabric mógłby być mapowany na ten autonomicznego biznesowych i granic mikrousługi logicznych lub ograniczony kontekst, jak również.

### <a name="service-fabric-and-containers"></a>Usługa Service Fabric i kontenery

W odniesieniu do kontenerów w usłudze Service Fabric możesz również usługi można wdrożyć w obrazów kontenerów w ramach klastra usługi Service Fabric. Rysunek 4 – 11 pokazano tego w większości przypadków, który będzie istnieć tylko jeden kontener na usługę.

![](./media/image15.png)

Rysunek 4-11: Mikrousługi biznesowych za pomocą kilku usług (kontenery) w usłudze Service Fabric

Jednak kontenery tak zwane "przyczepki" (dwa kontenery, które muszą zostać wdrożone razem jako część usługi logiczne) również są możliwe w usłudze Service Fabric. Ważne jest mikrousług firm logiczne obramowanie kilku elementów cohesive. W wielu przypadkach może być pojedynczą usługę za pomocą pojedynczego modelu danych, ale w innych przypadkach może być fizyczny kilka usług, jak również.

Począwszy od pisania niniejszej (kwietnia 2017 r.) w usłudze Service Fabric nie można wdrożyć SF niezawodne usługi stanowe kontenerów — można wdrożyć w kontenerach gościa, bezstanowych usług lub usług aktora w kontenerach. Ale pamiętaj, że można łączyć usługi w procesach i usługi w kontenerach w tej samej aplikacji usługi Service Fabric, jak pokazano na rysunku 4-12.

![](./media/image16.png)

Rysunek 4-12: Mikrousługi firm mapowane do aplikacji usługi Service Fabric z kontenerami i usług stanowych

Obsługa jest także różnić w zależności od tego, czy używasz kontenerów platformy Docker w systemie Linux lub Windows kontenery. Obsługa kontenerów w usłudze Service Fabric będzie rozszerzać w przyszłych wydaniach. Aktualne najnowsze wiadomości dotyczące obsługi kontenerów w usłudze Service Fabric, w witrynie sieci Web platformy Azure, przeczytaj [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousługi

Jak wspomniano wcześniej, każda mikrousługa (logiczne ograniczony kontekst) musi być właścicielem swój model domeny (dane i logikę). W przypadku mikrousługi bezstanowe bazy danych będą zewnętrznych, wykorzystujące relacyjne opcje, takie jak SQL Server lub opcje NoSQL, takie jak MongoDB lub Azure DocumentDB.

Ale uwierzytelnienia usługi również może być stanowe, co oznacza, że dane znajdują się w ramach mikrousług. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousług w pamięci i utrwalane na dyskach i replikowane do innych węzłów. Rysunek 4 — 13 przedstawiono różne podejścia.

![](./media/image17.png)

Rysunek 4 — 13: Bezstanowe i stanowe mikrousługi

Bezstanowe podejście nadaje się doskonale i jest prostsza do zaimplementowania niż mikrousług stanowych, ponieważ to podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Jednak mikrousługi bezstanowe powodować opóźnienia między źródłami danych i procesów. Wymagają one również więcej ruchomych części próbując zwiększyć wydajność dzięki dodatkowej pamięci podręcznej i kolejek. Powoduje to, że użytkownik może wystąpić złożone architektury, które mają zbyt wiele warstw.

Z kolei [mikrousług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można programu excel w zaawansowanych scenariuszach, ponieważ nie istnieje żadne opóźnienie między domeny logikę i dane. Duże przetwarzania danych, gry zapleczy, baz danych jako usługa i innych scenariuszy o małych opóźnieniach, wszystkie korzyści z usług stanowych, które zapewniają szybszy dostęp do stanu lokalnego.

Uzupełniające są usługi stanowe i bezstanowe. Na przykład usługa stanowa może zostać podzielony na wiele partycji. Aby uzyskać dostęp do tych partycji, możesz potrzebować usługę bezstanową działający jako usługę bramy, której wie, jak rozwiązywać każdej partycji na podstawie kluczy partycji.

Usługi stanowe mają wady. Jakie nakłada stopień złożoności, które umożliwia skalowanie w poziomie. Funkcje, które zazwyczaj są realizowane przez systemy zewnętrzne bazy danych muszą być kierowane zadań, takich jak replikacja danych między mikrousług stanowych i partycjonowanie danych. Jednak jest to jeden z obszarów, gdzie koordynatora, takich jak [usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [stanowych usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) ułatwiają maksymalnie — poprzez uproszczenie programowania i cyklem życia stanowe przy użyciu mikrousług [interfejsu API usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [elementów Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Innych platform tworzenia mikrousług, które umożliwiają usług stanowych obsługujące wzorcem aktora i który zwiększyć odporność na uszkodzenia i opóźnienie między logiki biznesowej i danych są programy Microsoft [Orleans](https://github.com/dotnet/orleans), począwszy od Microsoft Research oraz [ Akka.NET](https://getakka.net/). Obu platform obecnie umożliwiają zwiększenie ich obsługę platformy Docker.

Należy zauważyć, że kontenery platformy Docker samodzielnie bezstanowe. Jeśli chcesz wdrożyć usługi stanowej konieczne dodatkowe struktury profesjonalnie opracowany i wyższego poziomu zanotowanej wcześniej. Jednak w trakcie tworzenia tej dokumentacji usług stanowych w usłudze Service Fabric nie są obsługiwane jako kontenery tylko jako zwykły mikrousług. Obsługa interfejsu Reliable services w kontenerach będzie dostępna w przyszłych wersjach usługi Service Fabric.

>[!div class="step-by-step"]
>[Poprzednie](soa-applications.md)
>[dalej](deploy-azure-kubernetes-service.md)
