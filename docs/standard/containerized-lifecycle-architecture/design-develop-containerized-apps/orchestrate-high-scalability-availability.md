---
title: Organizowanie mikrousług oraz multicontainer aplikacji o wysokiej skalowalności i dostępności
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59c03755bebce98e018f56fc7213b00a0d3eae38
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Organizowanie mikrousług oraz multicontainer aplikacji o wysokiej skalowalności i dostępności

Aplikacje gotowe do produkcji przy użyciu orchestrators jest niezbędne, gdy aplikacja jest oparta na mikrousług lub po prostu podzielić na wiele kontenerów. Wcześniej, wprowadzonego w podejściu na podstawie mikrousługi każdego mikrousługi właścicielem jego modelu i danych, dzięki czemu będzie ona autonomicznego projektowanie i wdrażanie punktu widzenia. Ale nawet, jeśli masz bardziej tradycyjnej aplikacją, która składa się z wielu usług (takich jak SOA), możesz również będą miały wiele kontenerów lub usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone, aby skalować w poziomie oraz zarządzanie nimi; w związku z tym bezwzględnie konieczne orchestrator, jeśli chcesz mieć gotowe do produkcji i skalowalność aplikacji multicontainer.

Rysunek 4 – 6 przedstawia wdrożenie w klastrze aplikacja składa się z wielu mikrousług (kontenery).

![](./media/image6.png)

Rysunek 4 – 6: klastrowania kontenerów

Prawdopodobnie algorytmu. Jednak jak są możesz Obsługa równoważenia obciążenia, routingu i organizowanie te aplikacje składają?

Docker interfejsu wiersza polecenia (CLI) spełnia potrzeby Zarządzanie jeden kontener na jednym hoście, ale wypada krótkie, jeśli chodzi o zarządzanie wielu kontenerów wdrożonego na wielu hostach bardziej złożonych aplikacji rozproszonych. W większości przypadków należy platformy zarządzania, która będzie automatycznie uruchomić kontenerów, Wstrzymaj, lub zamykać je w razie potrzeby i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieci i danych magazynu.

Aby wykracza poza zarządzania poszczególnych kontenerów lub bardzo proste składa aplikacji i przeniesienie kierunku większych aplikacji przedsiębiorstwa z mikrousług, należy wyłączyć aranżacji i klastrów platformy.

Z architektury i rozwoju punktu widzenia Jeśli jesteś enterprise duży, kompilowanie, na podstawie mikrousług aplikacji, jest wziąć pod uwagę następujące platform i produktów, które obsługują zaawansowanych scenariuszy:

-   **Klastry i orchestrators** Aby skalować-aplikacji na wielu hostach Docker, takich jak o dużych aplikacji opartej na mikrousług, jest krytyczne, aby można było zarządzać wszystkimi tymi hostami jako jednym klastrem przez abstrakcyjność złożoność podstawowej platformy. To, czego klastrów kontenera i orchestrators zawiera. Przykładem orchestrators są Docker Swarm, Mesosphere DC/OS Kubernetes (pierwsze trzy dostępne za pośrednictwem usługi kontenera platformy Azure) i sieci szkieletowej usług Azure.

-   **Planiści** *Planowanie* oznacza, że funkcja dla administratora, można uruchomić kontenery w klastrze, dzięki czemu zapewniają także interfejsu użytkownika. Harmonogram klastra ma kilka obowiązki: efektywnie korzystać z zasobów klastra, aby ustawić ograniczenia podanego przez użytkownika, do wydajnie kontenerów Równoważenie obciążenia między węzłami lub hostów i aby było odporna błędy zapewniając wysoki dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczonych przez różnych dostawców często podać obie możliwości. Tabela 4-1 wymieniono najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Te klastry są zwykle dostępne w chmur publicznych, takich jak Azure.

Tabela 4-1: platform oprogramowania dla kontenera, klaster, aranżacji i planowania

| Platforma | Opis |
|---|---|
| Rozwiązanie docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Rozwiązanie docker Swarm daje możliwość klastra i Zaplanuj kontenery Docker. Przy użyciu Swarm, można przekształcić w puli hostów Docker pojedynczego, wirtualnego host Docker. Klienci mogą wysyłać żądania interfejsu API do Swarm w taki sam sposób, jak na hostach, co oznacza, że Swarm ułatwia skalowania aplikacji na wielu hostach. <br /><br /> Rozwiązanie docker Swarm jest to produkt z Docker, firma. <br /><br /> Docker v1.12 lub nowszej można uruchomić tryb macierzysty i wbudowane Swarm. |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  Mesosphere Enterprise DC/OS (oparte na Apache Mesos) to platforma gotowe do produkcji dla działających kontenerów i aplikacji rozproszonych. <br /><br /> DC/OS polega na abstrakcyjność kolekcji zasobów dostępnych w klastrze i udostępnianie tych zasobów oparty na jego składniki. Marathon zwykle jest używana jako harmonogramu zintegrowany z DC/OS. |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes jest to produkt typu open source, który zawiera funkcję, która infrastruktura klastra i kontener planowania organizowanie możliwości w zakresie od. Można zautomatyzować wdrożenie skalowanie i operacje kontenery aplikacji w klastrach hostów. <br /><br /> Kubernetes udostępnia infrastrukturę skoncentrowane kontenera, która grupy kontenerów aplikacji do jednostek logicznych łatwe zarządzanie i odnajdywania. |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Sieć szkieletowa usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) to platforma mikrousług firmy Microsoft do tworzenia aplikacji. Jest [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z usług i tworzy klastry maszyn. Domyślnie usługi sieć szkieletowa wdraża i aktywuje usługi jako procesów, ale sieci szkieletowej usług można wdrożyć usługi w obrazach kontenera Docker. Bardziej istotne, można mieszać usług w procesach z usługami w kontenerach w tej samej aplikacji. <br /><br /> Począwszy od 2017 maja funkcji sieci szkieletowej usług, który obsługuje wdrażanie usługi jako kontenery Docker jest w stanie podglądu. <br /><br /> Można tworzyć usługi sieć szkieletowa usług na wiele sposobów korzystania z [usługi sieć szkieletowa modele programowania](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) wdrażanie [pliki wykonywalne gościa](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) oraz kontenerów. Sieć szkieletowa usług obsługuje modele przetestowanego aplikacji, takich jak [usługi stanowej](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) i [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Za pomocą orchestrators na podstawie kontenera na platformie Azure

Kilku dostawców chmury oferuje Obsługa kontenerów Docker oraz klastrów Docker i obsługę orchestration, w tym Azure, Amazon EC2 kontenera usług i aparat kontenera Google. Platforma Azure udostępnia Docker obsługi klastra i orchestrator za pomocą usługi kontenera platformy Azure, zgodnie z objaśnieniem w następnej sekcji.

Wybór innego polega na użyciu sieć szkieletowa usług Azure, który również obsługuje Docker oparte na systemie Linux i kontenery systemu Windows. Sieć szkieletowa usług działa na platformie Azure lub innych chmury oraz [lokalnymi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Przy użyciu usługi kontenera platformy Azure

Klaster Docker pul wielu hostach Docker i udostępnia je jako pojedynczego wirtualnego hosta Docker, aby umożliwić wdrażanie wielu kontenerów do klastra. Klaster będzie obsługiwać wszystkie żmudne złożonych zarządzania procesy, takie jak skalowalność i kondycji. Rysunek 4-7 przedstawia sposób mapowania klastrze Docker składa aplikacji usługi kontenera.

Usługi kontenera umożliwia uprościć tworzenie, konfiguracji i zarządzania klastrowania maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Za pomocą zoptymalizowanego konfiguracji popularnych narzędzi planowania i aranżacji open source, usługi kontenera daje możliwość użycia swoje umiejętności istniejących lub Rysuj duże i rosnącym treści specjalizacji społeczności, wdrażanie i zarządzanie nimi na podstawie kontenera aplikacje na platformie Azure.

Usługi kontenera optymalizuje konfiguracji popularnych Docker klastrowania open source narzędzia i technologie specjalnie dla platformy Azure. Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność dla kontenerów i konfigurację aplikacji. Wybierz rozmiar, liczby hostów i narzędzia programu orchestrator, a usługi kontenera obsługuje wszystkie inne elementy.

Kontener usługi upewnij się, że kontenerów aplikacji pełni przenośne przy użyciu obrazów Docker. Obsługuje ona wybór platform aranżacji open source, takie jak DC/OS, Kubernetes i Docker Swarm upewnij się, że te aplikacje można skalować do tysięcy lub nawet dziesiątki tysięcy kontenerów.

Bez usługi kontenera platformy Azure należy wykonać skorzystać z funkcji korporacyjnej systemu Azure, zachowując przenośność aplikacji, w tym również na warstwy aranżacji.

![](./media/image11.png)

Rysunek 4-7: klastrowanie opcje dostępne w usłudze kontenera platformy Azure

Jak pokazano na rysunku 4-8, usługi kontenera jest po prostu infrastrukturę platformy Azure w celu wdrożenia DC/OS, Kubernetes lub Docker Swarm, ale nie implementuje wszelkie dodatkowe orchestrator. W związku z tym usługi kontenera jest nie orchestrator jest tylko infrastrukturę, która korzysta z istniejącej orchestrators open source dla kontenerów.

![](./media/image12.png)

Rysunek 4 — 8: Orchestrators w usłudze kontenera

Z punktu widzenia użycia celem usługi kontenera jest zapewnienie środowiska macierzystego kontenera za pomocą technologii i popularnych narzędzi open source. W tym celu przedstawia standardowe punkty końcowe interfejsu API dla programu orchestrator wybrany. Korzystając z tych punktów końcowych, można użyć oprogramowania, który może komunikować się z tych punktów końcowych. Na przykład w przypadku rozwiązania Docker Swarm punkt końcowy, można użyć interfejsu wiersza polecenia Docker. DC/OS można użyć interfejsu wiersza polecenia DC/OS.

### <a name="getting-started-with-container-service"></a>Wprowadzenie do korzystania z usługi kontenera

Aby rozpocząć korzystanie z usługi kontenera, w przypadku wdrażania klastra usługi kontenera przy użyciu portalu Azure za pomocą szablonu usługi Azure Resource Manager lub [interfejsu wiersza polecenia](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostępne szablony obejmują [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), i [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Można zmodyfikować szablony szybkiego startu uwzględnienie dodatkowych lub zaawansowanej konfiguracji platformy Azure.

**Więcej informacji o** Aby dowiedzieć się więcej o wdrażaniu klastra usługi kontenera, w witrynie sieci Web platformy Azure, przeczytaj [wdrażanie klastra usługi kontenera platformy Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w ramach usług ACS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source.

Kontener usługi jest obecnie dostępny dla standardowych A, D DS, G i maszyn wirtualnych systemu Linux serii GS na platformie Azure. Naliczane są opłaty tylko w przypadku wystąpienia obliczeniowe, które możesz wybrać oraz innych podstawowych zasoby infrastruktury wykorzystany, takich jak magazynu i sieci. Nie ma żadnych przyrostowe opłat za usługi kontenera samej siebie.

### <a name="additional-resources"></a>Dodatkowe zasoby

Poniżej przedstawiono lokalizacje, gdzie można znaleźć dodatkowe informacje:

-   Wprowadzenie do kontenera Docker hosting rozwiązania z usługą kontenera:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker Swarm omówienie:  
    <https://docs.docker.com/swarm/overview/>

-   Omówienie trybu swarm:  
    <https://docs.docker.com/engine/swarm/>

-   Omówienie DC/OS mesosphere:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (oficjalna witryna):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Za pomocą sieci szkieletowej usług

Sieć szkieletowa usług powstały od firmy Microsoft przejście z dostarczeniem "pola" produktów, które były najczęściej wbudowanymi w stylu, do dostarczania usług. Środowisko tworzenia i obsługi dużej usług na dużą skalę, takich jak bazy danych SQL Azure, bazy danych dokumentów platformy Azure, Azure Service Bus lub zaplecza na funkcję Cortana w kształcie sieci szkieletowej usług. Platforma ewoluował w czasie przyjęta coraz więcej usług go. Ważne sieci szkieletowej usług było uruchomić nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Sieć szkieletowa usług ma na celu rozwiązywanie problemów trudne, tworzenia i uruchamiania usługi i wydajne wykorzystanie zasobów infrastruktury tak, aby zespoły można rozwiązać problemy biznesowe przy użyciu metody mikrousług.

Usługa Service Fabric realizuje dwa obszary do tworzenia aplikacji, które używają podejście mikrousług:

-   Platforma, która zapewnia usługi systemowe, aby wdrożyć, skalowania, uaktualniania, wykrywanie, ponowne uruchomienie usługi nie powiodło się, odnajdywanie lokalizacji usługi, zarządzanie stanem i monitorowanie kondycji. Tych usług systemu w celu zawierają wiele właściwości mikrousług opisanych powyżej.

-   Interfejsów API programowania lub struktury, ułatwiające tworzenie aplikacji jako mikrousług: [podmiotów niezawodnych i niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Oczywiście można wybrać dowolny kod do kompilacji z mikrousługi, ale te interfejsy API upewnij bardziej bezpośrednie zadanie, a integrują się z platformą jest dokładniejsze. W ten sposób można uzyskać kondycji i informacje diagnostyczne lub mogą wykorzystać do zarządzania stanem niezawodnej.

Sieć szkieletowa usług jest niezależny względem sposobie tworzenia usługi, a można użyć innych technologii. Niemniej jednak zawiera wbudowane programowania interfejsów API, które ułatwiają tworzenie mikrousług.

Rysunek 4-9 przedstawiono sposób tworzenia i uruchamiania mikrousług w sieci szkieletowej usług, procesów prostego lub jako kontenery Docker. Użytkownik może również mieszać na podstawie kontenera mikrousług z mikrousług na podstawie proces w ramach tego samego klastra sieci szkieletowej usług.

![](./media/image13.png)

Rysunek 4 — 9: Wdrażanie mikrousług jako procesy lub kontenerów w sieci szkieletowej usług Azure

Klastry usługi sieć szkieletowa oparte na hostach z systemem Linux i Windows można uruchamiać kontenery Docker Linux i kontenery systemu Windows.

**Więcej informacji o** uzyskać aktualne informacje o obsłudze kontenery w sieci szkieletowej usług, w witrynie sieci Web platformy Azure, przeczytaj [sieci szkieletowej usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Sieć szkieletowa usług jest dobrym przykładem platformy, z którym można zdefiniować innej logicznej architektury (mikrousług biznesowych lub ograniczonych kontekstów) niż fizycznego wykonania. Na przykład w przypadku zastosowania [stanowych usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [sieć szkieletowa usług Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które zostały wprowadzone w następnej sekcji "[Stateless i stanowe mikrousług](#stateless-versus-stateful-microservices), "masz koncepcja mikrousługi firmy z wieloma usługami fizycznych.

Jak pokazano na rysunku nr 4-10 i planowania z punktu widzenia mikrousługi/biznesowych, podczas wdrażania usługi Usługa niezawodnej Stateful sieci szkieletowej zazwyczaj należy zaimplementować dwie warstwy usług. Pierwsza to zaplecza stanowe niezawodnej usługi, która obsługuje wiele partycji. Drugim jest usługa frontonu lub Usługa bramy odpowiedzialnym za routingu i danych agregacji wielu partycji lub wystąpienia usługi stanowej. Czy Usługa bramy również obsługuje komunikację klienta z pętli ponawiania, uzyskiwanie dostępu do usługi zaplecza, używany w połączeniu z sieci szkieletowej usług [odwrotny serwer proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Rysunek 4 — 10: mikrousługi biznesowych z kilku usług stanowe i bezstanowe w sieci szkieletowej usług

W każdym przypadku gdy używasz usługi sieć szkieletowa stanowych usług Reliable Services, masz również logicznych lub pracy mikrousługi (kontekst ograniczone), który zazwyczaj składa się z wielu fizycznych usług. Każdej z nich, Usługa bramy i partycji usługi można można zaimplementować jako usługi interfejsu API sieci Web platformy ASP.NET, jak pokazano na rysunku 4-10.

W sieci szkieletowej usług, grupy i wdrażanie grup usług jako [aplikacji sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), która jest jednostki pakowania i wdrażania dla klastra lub orchestrator. W związku z tym aplikacji sieci szkieletowej usług mogą zostać zamapowane do tego autonomicznego biznesowych i granic mikrousługi logicznych lub ograniczonych kontekstu również.

### <a name="service-fabric-and-containers"></a>Sieć szkieletowa usług i kontenerów

W odniesieniu do kontenerów w sieci szkieletowej usług również można wdrożyć usługi kontenera obrazów w ramach klastra sieci szkieletowej usług. Rysunek 4-11 przedstawiono że większość czasu, jaki będzie tylko jeden kontener dla danej usługi.

![](./media/image15.png)

Rysunek 4 — 11: mikrousługi biznesowych z kilku usług (kontenery) w sieci szkieletowej usług

Jednak kontenery tak zwane "boczną" (dwa kontenerów, które muszą zostać wdrożone razem w ramach usługi logicznej) są również dostępne w sieci szkieletowej usług. Ważne jest mikrousługi firm logicznej obramowanie kilku elementów spójności. W wielu przypadkach może być pojedynczą usługę z modelem danych, ale w innych przypadkach może być fizyczny kilka usług, a także.

Począwszy od tej zapisywanie (kwietnia 2017), w sieci szkieletowej usług nie można wdrożyć rz niezawodne Stateful usługi kontenerów — można wdrożyć tylko kontenery gościa, usług bezstanowych lub usługi aktora w kontenerach. Jednak pamiętaj, że można mieszać usług w procesach i usług w kontenerach w tej samej aplikacji sieci szkieletowej usług, jak pokazano na rysunku 4-12.

![](./media/image16.png)

Rysunek 4-12: firm mikrousługi zamapowane do aplikacji sieci szkieletowej usług z kontenerami usługi stanowej

Obsługa różni się również w zależności od tego, czy używasz kontenery Docker w systemie Linux lub kontenery systemu Windows. Obsługa kontenerów w sieci szkieletowej usług będzie rozszerzanie w kolejnych wersjach. Aby uzyskać aktualne informacje o obsługę kontenera w sieci szkieletowej usług, w witrynie sieci Web platformy Azure, przeczytaj [sieci szkieletowej usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousług

Jak wspomniano wcześniej, każdy mikrousługi (logiczne ograniczone kontekst) musi być właścicielem jego model domeny (dane i logiki). W przypadku mikrousług bezstanowych bazy danych będzie zewnętrznych wykorzystujących relacyjne opcje, takie jak SQL Server lub opcji NoSQL, takie jak bazy danych MongoDB lub usługi Azure DocumentDB.

Jednak uwierzytelnienia usługi również może być stanowe, co oznacza, że dane znajdują się w obrębie mikrousługi. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousługi w pamięci i utrwalony na dyskach i replikowane do innych węzłów. Rysunek 4-13 przedstawiono różne podejścia.

![](./media/image17.png)

Rysunek 4 — 13: bezstanowe i stanowe mikrousług

Podejście bezstanowych nadaje się doskonale i łatwiejsze do zaimplementowania niż mikrousług stanową, ponieważ podejście jest podobny do tradycyjnych i dobrze znane wzorców. Ale bezstanowych mikrousług nałożyć opóźnienia między procesu i źródeł danych. Wymagają one również więcej przenoszenie części próbując zwiększyć wydajność z kolejkami i dodatkowe pamięci podręcznej. Wynik jest, że można na końcu złożonych architektury, które ma zbyt wiele poziomów.

Z kolei [mikrousług stanowe](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można programu excel w zaawansowanych scenariuszach, ponieważ nie istnieje żadne opóźnienia między domeny logikę i dane. Duże przetwarzania danych, gier zapleczy, baz danych jako usługę i innych scenariuszy małe opóźnienia wszystkich korzystać z usług stanowych, które zapewniają stanu lokalnego szybszy dostęp.

Uzupełniają usług bezstanowych i stanowych. Na przykład usługi stanowej może zostać podzielony na wiele partycji. Aby uzyskać dostęp do tych partycji, może być konieczne usługi bezstanowej działający jako Usługa bramy, który potrafi w celu rozwiązania każdej partycji w oparciu kluczy partycji.

Usługi stanowej mają wady. Jakie nakłada poziom złożoności, która pozwala na skalowanie w poziomie. Funkcje, które zazwyczaj są realizowane przez systemy zewnętrzne bazy danych należy rozwiązać kwestie dotyczące zadań, takich jak replikacja danych między mikrousług stanowe i partycjonowanie danych. Jednak to jedno z obszarów, w którym orchestrator, takich jak [sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [niezawodne usługi stanowej](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) może pomóc w najbardziej — dzięki uproszczeniu opracowywania i cyklem życia stateful przy użyciu mikrousług [niezawodnej usługi interfejsu API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Inne platformy mikrousługi, które umożliwiają stanowych usług, który obsługuje wzorca aktora i poprawiających odporność na uszkodzenia i opóźnienia między logikę biznesową i danych są Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research i [ Akka.NET](https://getakka.net/). Obu platform obecnie umożliwiają zwiększenie ich obsługę Docker.

Należy zauważyć, że kontenery Docker bezstanowego same. Jeśli chcesz wdrożyć usługi stanowej, konieczne dodatkowe porady i wyższego poziomu struktur wspomniano wcześniej. Jednak opracowywania tego tekstu usługi stanowej w sieci szkieletowej usług nie są obsługiwane jako kontenery tylko jako zwykły mikrousług. Niezawodne usługi pomocy technicznej, w pojemnikach będą dostępne w nadchodzących wersjach usługi sieć szkieletowa usług.


>[!div class="step-by-step"]
[Poprzednie] (soa-applications.md) [dalej] (docker aplikacje development-environment.md)
