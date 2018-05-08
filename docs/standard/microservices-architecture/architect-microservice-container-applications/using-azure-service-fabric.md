---
title: Za pomocą usługi Azure Service Fabric
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Za pomocą usługi Azure Service Fabric
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: d65968e3d37f53cceee55120110ad4bb3c13d304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-azure-service-fabric"></a>Za pomocą usługi Azure Service Fabric

Sieć szkieletowa usług Azure powstały od firmy Microsoft przejście z dostarczeniem pole produktów, które były najczęściej wbudowanymi w stylu, do dostarczania usług. Środowisko tworzenia i obsługi dużej usług na dużą skalę, takich jak bazy danych SQL Azure, bazy danych rozwiązania Cosmos Azure, Azure Service Bus lub zaplecza na funkcję Cortana w kształcie sieci szkieletowej usług. Platforma ewoluował w czasie przyjęta coraz więcej usług go. Ważne sieci szkieletowej usług było uruchomić nie tylko na platformie Azure, ale także w autonomicznych wdrożeniach systemu Windows Server.

Sieć szkieletowa usług ma na celu rozwiązania problemów twardych tworzenia oraz z usługą i wydajne, wykorzystania zasobów infrastruktury, tak, aby zespoły można rozwiązać problemy biznesowe przy użyciu metody mikrousług.

Usługa Service Fabric realizuje dwa obszary do tworzenia aplikacji, które używają podejście mikrousług:

-   Platforma, która zapewnia usługi systemowe, aby wdrożyć, skalowania, uaktualniania, wykrywanie, ponowne uruchomienie usługi nie powiodło się, odnajdywanie lokalizacji usługi, zarządzanie stanem i monitorowanie kondycji. Te usługi systemu Włącz obowiązywać wielu cech mikrousług opisanych powyżej.

-   Interfejsów API programowania lub struktury, ułatwiające tworzenie aplikacji jako mikrousług: [podmiotów niezawodnych i niezawodne usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Oczywiście można wybrać dowolny kod do kompilacji z mikrousługi, ale te interfejsy API upewnij bardziej bezpośrednie zadanie, a integrują się z platformą jest dokładniejsze. W ten sposób można uzyskać kondycji i informacje diagnostyczne lub mogą wykorzystać do zarządzania stanem niezawodnej.

Sieć szkieletowa usług jest niezależny względem sposobie tworzenia usługi, a można użyć innych technologii. Niemniej jednak zawiera wbudowane programowania interfejsów API, które ułatwiają tworzenie mikrousług.

Jak pokazano w rysunek 4-26, możesz tworzyć i uruchamiać mikrousług w sieci szkieletowej usług jako procesy prostego lub kontenery Docker. Użytkownik może również mieszać na podstawie kontenera mikrousług z mikrousług na podstawie proces w ramach tego samego klastra sieci szkieletowej usług.

![](./media/image30.png)

**Rysunek 4-26**. Wdrażanie mikrousług jako procesy lub kontenerów w sieci szkieletowej usług Azure

Klastrów sieci szkieletowej usług oparte na hostach z systemem Linux i Windows można uruchamiać odpowiednio kontenery Docker Linux i kontenery systemu Windows.

Aby uzyskać aktualne informacje o obsłudze kontenery w sieci szkieletowej usług Azure, zobacz [sieci szkieletowej usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Sieci szkieletowej usług jest dobrym przykładem platformy, w którym można zdefiniować innej logicznej architektury (mikrousług biznesowych lub ograniczonych kontekstów) niż implementacji fizycznych, które zostały wprowadzone w systemie [architektura logiczna i fizyczna Architektura](#logical-architecture-versus-physical-architecture) sekcji. Na przykład w przypadku zastosowania [stanowych usług Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) w [sieć szkieletowa usług Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), które zostały wprowadzone w sekcji [Stateless i mikrousług stanowe](#stateless-versus-stateful-microservices) później może mieć koncepcja mikrousługi firmy z wieloma usługami fizycznych.

Jak pokazano na rysunku 4-27 i planowania z punktu widzenia mikrousługi/biznesowych, podczas wdrażania usługi Usługa niezawodnej Stateful sieci szkieletowej zazwyczaj należy zaimplementować dwie warstwy usług. Pierwsza to zaplecza stanowe niezawodnej usługi, która obsługuje wiele partycji (każda partycja jest usługi stanowej). Drugim jest usługa frontonu lub Usługa bramy odpowiedzialnym za routingu i danych agregacji wielu partycji lub wystąpienia usługi stanowej. Czy Usługa bramy również obsługuje komunikację klienta z pętli ponawiania uzyskiwanie dostępu do usługi zaplecza.
W przypadku zastosowania usługi niestandardowej lub alternatevely można również użyć usługi sieć szkieletowa poza pole jest to Usługa bramy [wstecznego serwera Proxy usługi](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Rysunek 4-27**. Mikrousługi biznesowe z kilku wystąpień usługi stanowej i niestandardowych frontonu bramy

W każdym przypadku gdy używasz usługi sieć szkieletowa stanowych usług Reliable Services, masz również logicznych lub pracy mikrousługi (kontekst ograniczone), który zazwyczaj składa się z wielu fizycznych usług. Można je Usługa bramy i partycji usługi można zaimplementować jako usługi interfejsu API sieci Web platformy ASP.NET, jak pokazano w rysunek 4-26.

W sieci szkieletowej usług, grupy i wdrażanie grup usług jako [aplikacji sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), która jest jednostki pakowania i wdrażania dla klastra lub orchestrator. W związku z tym aplikacji sieci szkieletowej usług mogą zostać zamapowane do tego autonomicznego biznesowych i granic mikrousługi logicznych lub ograniczonych kontekstu również tak mogłaby autonomicznie wdrożenia tych usług.

## <a name="service-fabric-and-containers"></a>Sieć szkieletowa usług i kontenerów

W odniesieniu do kontenerów w sieci szkieletowej usług można także wdrożyć usługi kontenera obrazów w ramach klastra sieci szkieletowej usług. Jak pokazano na rysunku 4-28, w większości przypadków będą istnieć tylko jeden kontener dla danej usługi.

![](./media/image32.png)

**Rysunek 4-28**. Mikrousługi biznesowe z kilku usług (kontenery) w sieci szkieletowej usług

Jednak kontenery tak zwane "boczną" (dwa kontenerów, które muszą zostać wdrożone razem w ramach usługi logicznej) są również dostępne w sieci szkieletowej usług. Ważne jest mikrousługi firm logicznej obramowanie kilku elementów spójności. W wielu przypadkach może być pojedynczą usługę z modelem danych, ale w innych przypadkach może być fizyczny również kilka usług.

Począwszy od połowy 2017 w sieci szkieletowej usług nie można wdrożyć rz niezawodne Stateful usługi kontenerów — można wdrożyć tylko usługi bezstanowej oraz usługi aktora w kontenerach. Jednak pamiętaj, że można mieszać usług w procesach i usług w kontenerach w tej samej aplikacji usługi Service Fabric, jak pokazano w rysunek 4-29.

![](./media/image33.png)

**Rysunek 4-29**. Mapowany do aplikacji sieci szkieletowej usług z kontenerami usługi stanowej mikrousługi biznesowa

Aby uzyskać więcej informacji na temat obsługi kontenera w sieci szkieletowej usług Azure, zobacz [sieci szkieletowej usług i kontenery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstanowe i stanowe mikrousług

Jak wspomniano wcześniej, każdy mikrousługi (logiczne ograniczone kontekst) musi być właścicielem jego model domeny (dane i logiki). W przypadku mikrousług bezstanowych bazy danych będzie zewnętrznych wykorzystujących relacyjne opcje, takie jak SQL Server lub opcji NoSQL, takie jak bazy danych MongoDB lub bazy danych Azure rozwiązania Cosmos.

Ale uwierzytelnienia usługi można też stanowe w sieci szkieletowej usług, co oznacza, że dane znajdują się w obrębie mikrousługi. Te dane mogą istnieć nie tylko na tym samym serwerze, ale w ramach procesu mikrousługi w pamięci i utrwalony na dyskach twardych i replikowane do innych węzłów. Rysunek 4-30 zawiera różne podejścia.

![](./media/image34.png)

**Rysunek 4-30**. Bezstanowe i stanowe mikrousług

Podejście bezstanowych nadaje się doskonale i jest łatwiejsze do zaimplementowania niż mikrousług stanową, ponieważ podejście jest podobne do tradycyjnych i dobrze znane wzorców. Ale bezstanowych mikrousług nałożyć opóźnienia między procesu i źródeł danych. Wymagają one również więcej przenoszenie części próbując zwiększyć wydajność z kolejkami i dodatkowe pamięci podręcznej. Wynik jest, że można na końcu złożonych architektury, które ma zbyt wiele poziomów.

Z kolei [mikrousług stanowe](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) można programu excel w zaawansowanych scenariuszach, ponieważ nie istnieje żadne opóźnienia między domeny logikę i dane. Duże przetwarzania danych, ponownie gry kończy, baz danych jako usługa, i wszystkie inne scenariusze, małe opóźnienia korzystać z usług stanowych, które włączyć stan lokalnego szybszy dostęp.

Uzupełniają usług bezstanowych i stanowych. Na przykład widać 4 rysunek-30, prawo diagramie, że usługa stanowa może zostać podzielony na wiele partycji. Aby uzyskać dostęp do tych partycji, może być konieczne usługi bezstanowej działający jako Usługa bramy, który potrafi w celu rozwiązania każdej partycji w oparciu kluczy partycji.

Usługi stanowej mają wady. Jakie nakłada poziom złożoności, który pozwala na skalowanie w poziomie. Funkcje, które zazwyczaj są realizowane przez systemy zewnętrzne bazy danych należy rozwiązać kwestie dotyczące zadań, takich jak replikacja danych między mikrousług stanowe i partycjonowanie danych. Jednak to jedno z obszarów, w którym orchestrator, takich jak [sieć szkieletowa usług Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) z jego [niezawodne usługi stanowej](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) może pomóc w najbardziej — dzięki uproszczeniu opracowywania i cyklem życia stateful przy użyciu mikrousług [niezawodnej usługi interfejsu API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) i [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Inne platformy mikrousługi, które umożliwiają stanowych usług, który obsługuje wzorca aktora i poprawiających odporność na uszkodzenia i opóźnienia między logikę biznesową i danych są Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research i [ Akka.NET](https://getakka.net/). Obu platform obecnie umożliwiają zwiększenie ich obsługę Docker.

Należy zauważyć, że kontenery Docker bezstanowego same. Jeśli chcesz wdrożyć usługi stanowej, konieczne dodatkowe porady i wyższego poziomu struktur wspomniano wcześniej. 

>[!div class="step-by-step"]
[Poprzednie] (scalable-available-multi-container-microservice-applications.md) [dalej] (.. /docker-Application-Development-Process/index.MD)
