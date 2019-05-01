---
title: Korzystanie z usługi Azure Service Fabric
description: Dowiedz się, jakie modeli aplikacji usługi Azure Service Fabric, możesz użyć, oprócz tylko za pomocą do aranżacji kontenerów.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: b29be05f5ab353ddfae0d23211efaf57979d0604
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025799"
---
# <a name="using-azure-service-fabric"></a>Korzystanie z usługi Azure Service Fabric

Usługa Azure Service Fabric, powstały od firmy Microsoft przejście od dostarczania produktów, pole, które były zazwyczaj monolitycznych w stylu, dostarczaniu usług. Środowisko tworzenia i obsługi dużych usług na dużą skalę, takich jak Azure SQL Database, Azure Cosmos DB, Azure Service Bus lub Cortany back-end, kształt usługi Service Fabric. Platforma ewoluował wraz z upływem czasu coraz więcej usług przyjęty go. Co ważniejsze usługi Service Fabric musiał uruchomić nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Usługa Service Fabric ma na celu rozwiązywanie trudnych problemów, kompilowania i uruchamiania usługi i efektywnie wykorzystując zasoby infrastruktury tak, aby zespoły można rozwiązać problemy biznesowe przy użyciu podejścia mikrousług.

Usługa Service Fabric udostępnia dwa obszary ułatwiające tworzenie aplikacji korzystających z podejścia mikrousług:

- Platforma, która zapewnia usługi systemowe na wdrażanie, skalowanie, uaktualnienia, wykrywanie, ponowne uruchomienie usługi nie powiodło się, odnajdywanie lokalizacji usługi, zarządzanie stanem i monitorowanie kondycji. Te usługi systemu obowiązuje udostępniają wiele z właściwości opisanych powyżej mikrousług.

- Interfejsy API programowania lub struktury, ułatwiające tworzenie aplikacji zgodnie z mikrousług: [interfejsu Reliable actors oraz usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Można wybrać żadnego kodu do tworzenia usługi mikrousług, ale te interfejsy API upewnij zadania prostsze, a ich integracja z platformą dokładniej. W ten sposób można uzyskać kondycji i informacji diagnostycznych lub możesz korzystać z zalet zarządzania stanem niezawodne.

Usługa Service Fabric jest niezależny od względem jak opracować swoje usługi, a następnie można użyć dowolnej technologii. Jednak zapewnia wbudowane programowania interfejsów API, które ułatwiają tworzenie mikrousług.

Jak pokazano w rysunek 4-27, można tworzyć i uruchamianie mikrousług w usłudze Service Fabric, jako prosty procesy lub jako kontenery platformy Docker. Istnieje również możliwość mieszać opartych na kontenerach mikrousług przy użyciu procesu na podstawie mikrousług, w tym samym klastrze usługi Service Fabric.

![Porównanie usługi Azure Service Fabric clusters: Mikrousługi jako procesy, w którym każdy węzeł działa jeden proces dla poszczególnych mikrousług; Mikrousługi jako kontenery, w którym każdy węzeł działa platformy Docker za pomocą kilku kontenerów jednego kontenera na mikrousługach.](./media/image30.png)

**Rysunek 4-27**. Wdrażanie mikrousług, jako procesów lub kontenerów w usłudze Azure Service Fabric

Klastry usługi Service Fabric, oparte na hostach z systemem Linux i Windows można uruchamiać kontenery platformy Docker w systemie Linux i kontenerów Windows, odpowiednio.

Aby uzyskać aktualne informacje na temat obsługi kontenerów w usłudze Azure Service Fabric, zobacz [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Usługi Service Fabric jest dobrym przykładem platformy, w którym można zdefiniować różne architekturę logiczną (mikrousług biznesowych lub ograniczone konteksty) niż fizyczna implementacja, które zostały wprowadzone w [architektura logiczna a fizycznych Architektura](logical-versus-physical-architecture.md) sekcji. Na przykład w przypadku zaimplementowania [stanowych usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction), które zostały wprowadzone w sekcji [Stateless w porównaniu z mikrousług stanowych](#stateless-versus-stateful-microservices) później, masz koncepcji biznesowych mikrousług przy użyciu wiele usług fizycznych.

Jak pokazano na rysunku 4-28 i myśleć z punktu widzenia mikrousług/biznesowych podczas implementowania usługi Service Fabric Reliable usługa stanowa zazwyczaj należy zaimplementować dwie warstwy usług. Pierwszy jest zaplecza niezawodnej usługi stanowej, która obsługuje wiele partycji (każda partycja jest stanowej usługi). Drugim jest usługa frontonu, czyli usługę bramy, odpowiedzialnym za routingu i agreguje dane należące do wielu partycji lub wystąpień usługi stanowej. Usługi bramy również obsługuje komunikacji po stronie klienta za pomocą pętli ponawiania, uzyskiwanie dostępu do usługi zaplecza. Usługa bramy jest nazywane implementować niestandardowe usługi, czy też można również użyć usługi Service Fabric out-of--box [zwrotny serwer proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Rysunek 4-28**. Mikrousługi biznesowych z wielu wystąpień usługi stanowej, jak i niestandardowe bramy frontonu

W każdym przypadku gdy używasz usługi Service Fabric stanowych usług Reliable Services, masz również logicznych lub pracy mikrousługi (ograniczony kontekst), zwykle składa się z wielu usług fizycznych. Można je usługi bramy i partycji usługi można zaimplementować jako usług interfejsu API sieci Web platformy ASP.NET, jak pokazano w rysunek 4-28.

W usłudze Service Fabric, grupy i wdrażanie grup usług jako [aplikacji usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), czyli jednostki pakowania i wdrażania dla programu orchestrator lub klastra. W związku z tym aplikacji usługi Service Fabric mógłby być mapowany na tego autonomicznego biznesowych i granic mikrousługi logicznych lub ograniczony kontekst, jak również, dzięki czemu można niezależnie wdrożyć te usługi.

## <a name="service-fabric-and-containers"></a>Usługa Service Fabric i kontenery

W odniesieniu do kontenerów w usłudze Service Fabric można także wdrożyć usługi w obrazów kontenerów w ramach klastra usługi Service Fabric. Jak pokazano na rysunku 4-29, w większości przypadków będzie istnieć tylko jeden kontener dla danej usługi.

![Aplikacja usługi Service Fabric można uruchomić kilka kontenerów, uzyskiwanie dostępu do bazy danych extern i cały zestaw będzie logiczne granic mikrousługi biznesowych](./media/image32.png)

**Rysunek 4-29**. Mikrousługi biznesowych za pomocą kilku usług (kontenery) w usłudze Service Fabric

Jednak kontenery tak zwane "przyczepki" (dwa kontenery, które muszą zostać wdrożone razem jako część usługi logiczne) również są możliwe w usłudze Service Fabric. Ważne jest mikrousług firm logiczne obramowanie kilku elementów cohesive. W wielu przypadkach może być pojedynczą usługę za pomocą pojedynczego modelu danych, ale w innych przypadkach może być także kilka usług fizycznych.

Należy pamiętać, że można łączyć usługi w procesach i usługi w kontenerach w tej samej aplikacji usługi Service Fabric, jak pokazano w rysunek 4-30.

![Aplikacja usługi Service Fabric, uruchamianie kontenerów i usług, w tym samym węźle.](./media/image33.png)

**Rysunek 4-30**. Mikrousługi firm mapowane do aplikacji usługi Service Fabric z kontenerami i usług stanowych

Aby uzyskać więcej informacji na temat obsługi kontenerów w usłudze Azure Service Fabric, zobacz [usługi Service Fabric i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousługi

Jak wspomniano wcześniej, każda mikrousługa (logiczne ograniczony kontekst) musi być właścicielem swój model domeny (dane i logikę). W przypadku mikrousługi bezstanowe bazy danych będą zewnętrznych, wykorzystujące relacyjne opcje, takie jak SQL Server lub opcje NoSQL, takie jak usługi Azure Cosmos DB lub MongoDB.

Ale samych usług może być również stanowych w usłudze Service Fabric, co oznacza, że dane znajdują się w ramach mikrousług. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousług w pamięci i utrwalane na dyskach twardych i replikowane do innych węzłów. Rysunek 4-30 przedstawia różne podejścia.

![W przypadku usług bezstanowych stanu (stan trwały, bazy danych) są przechowywane z mikrousług. W przypadku usług stanowych stany są przechowywane w mikrousługach.](./media/image34.png)

**Rysunek 4-31**. Bezstanowe i stanowe mikrousługi

Bezstanowe podejście nadaje się doskonale i jest prostsza do zaimplementowania niż mikrousług stanowych, ponieważ to podejście jest podobne do tradycyjnych i dobrze znanych wzorców. Jednak mikrousługi bezstanowe powodować opóźnienia między źródłami danych i procesów. Wymagają one również więcej ruchomych części gdy próbujesz poprawianie wydajności za pomocą dodatkowych pamięci podręcznej i kolejki. Powoduje to, że użytkownik może wystąpić złożone architektury, które mają zbyt wiele warstw.

Z kolei [mikrousług stanowych](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można programu excel w zaawansowanych scenariuszach, ponieważ nie istnieje żadne opóźnienie między domeny logikę i dane. Duże przetwarzania danych, gry ponownie kończy, baz danych jako usługa i innych scenariuszy o małych opóźnieniach, wszystkie korzystają z usług stanowych umożliwiających lokalne stan szybszy dostęp.

Uzupełniające są usługi stanowe i bezstanowe. Na przykład widać w rysunek 4-31, prawo diagramie, czy usługa stanowa może zostać podzielony na wiele partycji. Aby uzyskać dostęp do tych partycji, możesz potrzebować usługę bezstanową działający jako usługę bramy, której wie, jak rozwiązywać każdej partycji na podstawie kluczy partycji.

Usługi stanowe mają wady. Jakie nakłada stopień złożoności, która umożliwia skalowanie w poziomie. Funkcje, które zazwyczaj są realizowane przez systemy zewnętrzne bazy danych muszą być kierowane zadań, takich jak replikacja danych między mikrousług stanowych i partycjonowanie danych. Jednak jest to jeden z obszarów, gdzie koordynatora, takich jak [usługi Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [stanowych usług reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) ułatwiają maksymalnie — poprzez uproszczenie programowania i cyklem życia stanowe przy użyciu mikrousług [interfejsu API usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [elementów Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Innych platform tworzenia mikrousług, które umożliwiają usług stanowych obsługujące wzorcem aktora i który zwiększyć odporność na uszkodzenia i opóźnienie między logiki biznesowej i danych są programy Microsoft [Orleans](https://github.com/dotnet/orleans), począwszy od Microsoft Research oraz [ Akka.NET](https://getakka.net/). Obu platform obecnie umożliwiają zwiększenie ich obsługę platformy Docker.

Należy zauważyć, że kontenery platformy Docker samodzielnie bezstanowe. Jeśli chcesz wdrożyć usługi stanowej konieczne dodatkowe struktury profesjonalnie opracowany i wyższego poziomu zanotowanej wcześniej.

## <a name="using-azure-service-fabric-mesh"></a>Za pomocą usługi Azure Service Fabric siatki 

Usługa Azure Service Fabric siatki jest w pełni zarządzana usługa, która umożliwia deweloperom tworzenie i wdrażanie aplikacji krytycznych dla misji bez jakiejkolwiek infrastruktury zarządzania. Użyj usługi Service Fabric siatki, aby tworzenie i uruchamianie aplikacji bezpiecznego, rozproszonych mikrousług, które można skalować na żądanie. 

Jak pokazano na rysunku 4 – 32, aplikacjach hostowanych w systemie usługi Service Fabric siatki uruchamianie i skalowanie bez konieczności martwienia się o infrastrukturę wyłączania jego.

![Wieloma kontenerami w celu aplikacja działająca na platformie Docker desktop można wdrożyć do usługi Azure Service Fabric siatki bez martwienia się o infrastrukturę.](media/image39.png)

**Rysunek 4-32**. Wdrażanie aplikacji mikrousług/kontenerów do usługi Service Fabric siatki

Dzieje się w tle Usługa Service Fabric siatki składa się z klastrami tysięcy maszyn. Wszystkie operacje klastra są ukryte od dewelopera. Po prostu musisz przekazać kontenerów, a następnie określ zasoby, których potrzebujesz, wymagania w zakresie dostępności i limity zasobów. Usługa Service Fabric siatki jest automatycznie alokowana, infrastruktury, żądane przez wdrożenie aplikacji i obsługuje także błędy infrastruktury, upewniając się, że Twoje aplikacje są o wysokiej dostępności. Należy zadbać o kondycji i szybkość reakcji aplikacji, nie na infrastrukturze.

Aby uzyskać więcej informacji, zobacz [dokumentację usługi Service Fabric siatki](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Wybieranie koordynatorów na platformie Azure

Poniższa tabela zawiera wskazówki dotyczące jakie orchestrator do użycia w zależności od obciążenia i przedstawienie systemu operacyjnego.

![Usługi platformy Azure Kubernetes jest bardziej dojrzałych w systemie Linux niż w Windows i jest najczęściej używany do wdrażania microsevices oparte na kontenerach. Usługa Azure Service Fabric (klaster i siatki) jest bardziej dojrzałych Windows niż w systemie Linux, często używane do mikrousług w oparciu o kontenery, mikrousługi oparte na zwykły procesy i usługi stanowej.](media/image40.png)

**Rysunek 4-33**. Wybór koordynatora w wskazówki dotyczące platformy Azure

>[!div class="step-by-step"]
>[Poprzednie](scalable-available-multi-container-microservice-applications.md)
>[dalej](../docker-application-development-process/index.md)