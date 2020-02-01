---
title: Projektowanie aplikacji opartej na mikrousługach
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z korzyściami i downsidesami aplikacji zorientowanych na mikrousługach, aby móc podejmować świadome decyzje.
ms.date: 10/02/2018
ms.openlocfilehash: 63c93f237172d80704c00472ef2d4cbf7c787ab0
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921023"
---
# <a name="designing-a-microservice-oriented-application"></a>Projektowanie aplikacji opartej na mikrousługach

Ta sekcja koncentruje się na projektowaniu hipotetycznej aplikacji korporacyjnej po stronie serwera.

## <a name="application-specifications"></a>Specyfikacje aplikacji

Aplikacja hipotetyczna obsługuje żądania przez wykonywanie logiki biznesowej, uzyskiwanie dostępu do baz danych, a następnie zwracanie odpowiedzi HTML, JSON lub XML. Będziemy informować, że aplikacja musi obsługiwać wielu klientów, w tym przeglądarek klasycznych, na których działają aplikacje jednostronicowe (aplikacji jednostronicowych), tradycyjne aplikacje sieci Web, mobilne aplikacje sieci Web i natywne aplikacje mobilne. Aplikacja może również uwidocznić interfejs API dla stron trzecich do użycia. Powinien być również w stanie zintegrować swoje mikrousługi lub aplikacje zewnętrzne asynchronicznie, dzięki czemu Metoda ta ułatwi odporność mikrousług w przypadku awarii częściowych.

Aplikacja będzie składać się z następujących typów składników:

- Składniki prezentacji. Są one odpowiedzialne za obsługę interfejsu użytkownika i zużywanie usług zdalnych.

- Logika domeny lub biznesowej. Jest to Logika domeny aplikacji.

- Logika dostępu do bazy danych. Obejmuje to składniki dostępu do danych, które są odpowiedzialne za dostęp do baz danych (SQL lub NoSQL).

- Logika integracji aplikacji. Obejmuje to kanał obsługi komunikatów, głównie oparty na brokerach komunikatów.

Aplikacja będzie wymagała wysokiej skalowalności, a jednocześnie umożliwia jej skalowanie w pionie, ponieważ niektóre podsystemy będą wymagały większej skalowalności niż inne.

Aplikacja musi być w stanie wdrożyć w wielu środowiskach infrastruktury (z wieloma chmurami publicznymi i lokalnymi), a w idealnym przypadku powinna to być platforma międzyplatformowa, w której można z łatwością przechodzić z systemów Linux do systemu Windows (lub odwrotnie).

## <a name="development-team-context"></a>Kontekst zespołu deweloperów

Przyjęto również następujące kwestie dotyczące procesu tworzenia aplikacji:

- Wiele zespołów deweloperskich koncentruje się na różnych obszarach firmowych aplikacji.

- Nowi członkowie zespołu muszą szybko działać, a aplikacja musi być łatwa do zrozumienia i modyfikacji.

- Aplikacja będzie mieć długoterminowe ewolucje i ciągle zmieniające się reguły biznesowe.

- Potrzebna jest dobra długoterminowa łatwość utrzymania, co oznacza elastyczność podczas implementowania nowych zmian w przyszłości, jednocześnie umożliwiając aktualizowanie wielu podsystemów z minimalnym wpływem na inne podsystemy.

- Chcesz przećwiczyć ciągłą integrację i ciągłe wdrażanie aplikacji.

- Chcesz korzystać z nowych technologii (struktur, języków programowania itp.) podczas rozwoju aplikacji. Nie chcesz przeprowadzać pełnych migracji aplikacji podczas przenoszenia do nowych technologii, ponieważ spowodowałoby to wysokie koszty i wpłyną na przewidywalność i stabilność aplikacji.

## <a name="choosing-an-architecture"></a>Wybieranie architektury

Jaka powinna być architektura wdrażania aplikacji? Specyfikacje dla aplikacji, wraz z kontekstem programistycznym, zdecydowanie sugerują, że należy utworzyć architekta aplikacji, tworząc ją w autonomicznych podsystemach w formie współpracy mikrousług i kontenerów, gdzie mikrousługa jest kontenerem.

W tym podejściu każda usługa (kontener) implementuje zestaw spójnych i wąskich funkcji powiązanych. Na przykład aplikacja może składać się z usług, takich jak usługa wykazu, zamawianie usługi, koszyk, usługa profilu użytkownika itp.

Mikrousługi komunikują się przy użyciu protokołów, takich jak HTTP (REST), ale również asynchronicznie (na przykład przy użyciu AMQP), zwłaszcza w przypadku propagowania aktualizacji przy użyciu zdarzeń integracji.

Mikrousługi są opracowywane i wdrażane jako kontenery niezależnie od siebie. Oznacza to, że zespół programistyczny może opracowywać i wdrażać pewną mikrousługę bez wpływu na inne podsystemy.

Każda mikrousługa ma własną bazę danych, dzięki czemu można ją całkowicie oddzielić od innych mikrousług. W razie potrzeby spójność między bazami danych z różnych mikrousług zostaje osiągnięta przy użyciu zdarzeń integracji na poziomie aplikacji (za pośrednictwem logicznej magistrali zdarzeń), jak zostało to obsłużone w Command and Query Responsibility Segregation (CQRS). Z tego względu ograniczenia biznesowe muszą obejmować spójność ostateczną między wieloma mikrousługami i powiązanymi bazami danych.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: aplikacja referencyjna dla platformy .NET Core i mikrousług wdrożona przy użyciu kontenerów

Dzięki temu można skoncentrować się na architekturze i technologiach, zamiast zastanawiać się nad hipotetyczną domeną biznesową, która może nie być znana, dlatego została wybrana dobrze znana domena biznesowa — a mianowicie uproszczona aplikacja e-Handle (e-Shop), która prezentuje wykaz z produktów, program przyjmuje zamówienia od klientów, weryfikuje spis i wykonuje inne funkcje biznesowe. Ten kod źródłowy aplikacji opartej na kontenerze jest dostępny w repozytorium GitHub [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) .

Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika magazynu (aplikacji sieci Web i natywnej aplikacji mobilnej) oraz mikrousług i kontenerów zaplecza dla wszystkich wymaganych operacji po stronie serwera z kilkoma bramami interfejsu API jako skonsolidowane punkty wejścia do mikrousług wewnętrznych. Rysunek 6-1 przedstawia architekturę aplikacji referencyjnej.

![Diagram aplikacji klienckich korzystających z eShopOnContainers w ramach jednego hosta platformy Docker.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Rysunek 6-1**. Architektura aplikacji eShopOnContainers Reference dla środowiska programistycznego

Powyższy diagram pokazuje, że klienci mobilni i SPA komunikują się z punktami końcowymi bramy interfejsu API Single, które następnie komunikują się z mikrousługami. Tradycyjni klienci sieci Web komunikują się z mikrousługą MVC, która komunikuje się z mikrousługami za pomocą bramy interfejsu API.

**Środowisko hostingu**. Na rysunku 6-1 widzisz kilka kontenerów wdrożonych w ramach jednego hosta platformy Docker. W przypadku wdrożenia na pojedynczym hoście platformy Docker przy użyciu polecenia "Docker-Utwórz" w przypadku programu. Jeśli jednak używany jest program Orchestrator lub klaster kontenerów, każdy kontener może być uruchomiony na innym hoście (węzeł), a w każdym węźle można uruchomić dowolną liczbę kontenerów, jak wyjaśniono wcześniej w sekcji architektury.

**Architektura komunikacji**. Aplikacja eShopOnContainers używa dwóch typów komunikacji, w zależności od rodzaju akcji funkcjonalnej (zapytania a aktualizacje i transakcje):

- Komunikacja klient-do-mikrousług za pośrednictwem bram interfejsu API. Ta wartość jest używana w przypadku zapytań i w przypadku przyjmowania aktualizacji lub poleceń transakcyjnych z aplikacji klienckich. Podejście wykorzystujące bramy interfejsu API zostało szczegółowo opisane w kolejnych sekcjach.

- Asynchroniczna komunikacja oparta na zdarzeniach. Odbywa się to przez magistralę zdarzeń do propagowania aktualizacji w mikrousługach lub integracji z aplikacjami zewnętrznymi. Magistralę zdarzeń można zaimplementować z każdą technologią infrastruktury usługi Messaging, taką jak RabbitMQ, lub przy użyciu magistrali usług wyższego poziomu (np. Azure Service Bus, NServiceBus, MassTransit lub jaśniejszy).

Aplikacja jest wdrażana jako zestaw mikrousług w postaci kontenerów. Aplikacje klienckie mogą komunikować się z tymi mikrousługami działającymi jako kontenery za pomocą publicznych adresów URL publikowanych przez bramy interfejsu API.

### <a name="data-sovereignty-per-microservice"></a>Suwerenność danych przypadająca na mikrousługę

W aplikacji przykładowej każda mikrousługa jest właścicielem własnej bazy danych lub źródła danych, chociaż wszystkie SQL Server baz danych są wdrażane jako pojedynczy kontener. Ta decyzja projektowa została wprowadzona tylko w celu ułatwienia deweloperowi pobrania kodu z usługi GitHub, klonowania go i otwierania w programie Visual Studio lub Visual Studio Code. Można też łatwo kompilować niestandardowe obrazy platformy Docker przy użyciu interfejs wiersza polecenia platformy .NET Core i interfejsu wiersza polecenia platformy Docker, a następnie wdrożyć i uruchomić je w środowisku deweloperskim platformy Docker. W obu przypadkach korzystanie z kontenerów dla źródeł danych pozwala deweloperom tworzyć i wdrażać je w ciągu kilku minut bez konieczności aprowizacji zewnętrznej bazy danych lub innego źródła danych z twardą zależnością od infrastruktury (w chmurze lub lokalnie).

W rzeczywistym środowisku produkcyjnym, aby zapewnić wysoką dostępność i skalowalność, bazy danych powinny opierać się na serwerach bazy danych w chmurze lub lokalnie, ale nie w kontenerach.

W związku z tym jednostki wdrożenia dla mikrousług (a nawet dla baz danych w tej aplikacji) są kontenerami platformy Docker, a aplikacja referencyjna jest aplikacją obejmującą wiele kontenerów, która obejmuje zasady mikrousług.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **eShopOnContainers repozytorium GitHub. Kod źródłowy aplikacji odniesienia** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Zalety rozwiązań opartych na mikrousługach

Rozwiązanie oparte na mikrousługach, takie jak ta, ma wiele korzyści:

**Każda mikrousługa jest stosunkowo mała — łatwość zarządzania i rozwijania**. Opracowany

- Deweloperzy mogą łatwo zrozumieć i szybko zacząć korzystać z dobrej produktywności.

- Kontenery zaczynają się szybko, co sprawia, że deweloperzy zwiększają produktywność.

- Środowisko IDE, takie jak Visual Studio, może szybko ładować mniejsze projekty, zwiększając produktywność deweloperów.

- Każda mikrousługa może zostać zaprojektowana, opracowana i wdrożona niezależnie od innych mikrousług, która zapewnia elastyczność, ponieważ ułatwia wdrażanie nowych wersji mikrousług.

**Możliwe jest skalowanie poszczególnych obszarów aplikacji**. Na przykład może być konieczne skalowanie usługi katalogowej lub usługi koszyka, ale nie procesu porządkowania. Infrastruktura mikrousług będzie znacznie bardziej wydajna w odniesieniu do zasobów używanych w przypadku skalowania na zewnątrz architektury.

**Możesz podzielić prace programistyczne między wieloma zespołami**. Każda usługa może należeć do jednego zespołu programistycznego. Każdy zespół może zarządzać, opracowywać, wdrażać i skalować swoją usługę niezależnie od pozostałej części zespołów.

**Problemy są bardziej izolowane**. Jeśli wystąpi problem w jednej usłudze, tylko ta usługa jest na początku objęta usługą (z wyjątkiem sytuacji, w której jest używany niewłaściwy projekt z bezpośrednimi zależnościami między mikrousługami), a inne usługi mogą nadal obsługiwać żądania. Natomiast jeden niedziałający składnik w monolitycznej architekturze wdrażania może wyłączać cały system, szczególnie w przypadku zasobów, takich jak przeciek pamięci. Ponadto po rozwiązaniu problemu w mikrousłudze można wdrożyć tylko mikrousługę, której dotyczy problem, bez wpływu na pozostałą część aplikacji.

**Możesz użyć najnowszych technologii**. Ponieważ możesz zacząć opracowywać usługi niezależnie i uruchamiać je obok siebie (dzięki kontenerom i platformie .NET Core), możesz zacząć korzystać z najnowszych technologii i platform, zamiast wyłączać się na starszym stosie lub w strukturze dla całego Aplikacja.

## <a name="downsides-of-a-microservice-based-solution"></a>Downsides rozwiązania opartego na mikrousługach

Rozwiązanie oparte na mikrousługach, takie jak to również ma pewne wady:

**Aplikacja rozproszona**. Dystrybucja aplikacji zwiększa złożoność dla deweloperów podczas projektowania i kompilowania usług. Na przykład deweloperzy muszą zaimplementować komunikację między usługami przy użyciu protokołów, takich jak HTTP lub AMPQ, które zwiększają złożoność testowania i obsługi wyjątków. Powoduje również dodanie opóźnienia do systemu.

**Złożoność wdrożenia**. Aplikacja, która ma dziesiątki typów mikrousług i wymaga wysokiej skalowalności (musi być w stanie utworzyć wiele wystąpień na usługę i zrównoważyć te usługi na wielu hostach), oznacza wysoki stopień złożoności wdrożenia dla operacji IT i zarządzania. Jeśli nie korzystasz z infrastruktury z mikrousługą (na przykład Orchestrator i Scheduler), ta dodatkowa złożoność może wymagać znacznie większej liczby działań programistycznych niż sama aplikacja biznesowa.

**Transakcje niepodzielne**. Transakcje niepodzielne między wieloma mikrousługami zwykle nie są możliwe. Wymagania biznesowe muszą obejmować spójność ostateczną między wieloma mikrousługami.

**Zwiększono potrzeby zasobów globalnych** (całkowita pamięć, dyski i zasoby sieciowe dla wszystkich serwerów lub hostów). W wielu przypadkach, gdy zastąpisz wbudowaną aplikację z podejściem mikrousług, ilość początkowych zasobów globalnych wymaganych przez nową aplikację opartą na mikrousługach będzie większa niż potrzeby infrastruktury oryginalnej aplikacji monolitycznej. Wynika to z tego, że wyższy stopień szczegółowości i usług rozproszonych wymaga większej liczby zasobów globalnych. Jednak ze względu na niski koszt zasobów i korzyści wynikające z możliwości skalowania w poziomie tylko określonych obszarów aplikacji w porównaniu do długoterminowych kosztów podczas rozwoju aplikacji monolitycznych zwiększone wykorzystanie zasobów jest zwykle dobrym kompromisem dla dużych, długoterminowe aplikacje.

**Problemy związane z bezpośrednią komunikacją z klientem do mikrousług**. Gdy aplikacja jest duża, z szeroką częścią mikrousług, istnieją problemy i ograniczenia, jeśli aplikacja wymaga bezpośredniej komunikacji z klientem do mikrousług. Jednym z problemów jest potencjalna niezgodność między potrzebami klienta i interfejsami API udostępnianymi przez poszczególne mikrousługi. W niektórych przypadkach aplikacja kliencka może potrzebować wielu oddzielnych żądań, aby utworzyć interfejs użytkownika, który może być nieefektywny przez Internet i byłoby niepraktyczny w odniesieniu do sieci komórkowej. W związku z tym należy zminimalizować żądania z aplikacji klienckiej do systemu zaplecza.

Innym problemem związanym z bezpośrednią komunikacją z klientem do mikrousług jest to, że niektóre mikrousługi mogą korzystać z protokołów, które nie są przyjazne dla sieci Web. Jedna usługa może korzystać z protokołu binarnego, podczas gdy inna usługa może korzystać z komunikatów AMQP. Protokoły te nie są przyjazne dla zapory i najlepiej są używane wewnętrznie. Zwykle aplikacja powinna używać protokołów takich jak HTTP i WebSockets do komunikacji poza zaporą.

Jednak kolejną wadą tego bezpośredniego podejścia klient-usługa jest trudne do refaktoryzacji kontraktów dla tych mikrousług. W czasie deweloperzy mogą chcieć zmienić sposób partycjonowania systemu do usług. Na przykład mogą scalić dwie usługi lub podzielić usługę na dwie lub więcej usług. Jeśli jednak klienci komunikują się bezpośrednio z usługami, wykonanie tego rodzaju refaktoryzacji może spowodować przerwanie zgodności z aplikacjami klienckimi.

Jak wspomniano w sekcji architektura podczas projektowania i kompilowania złożonej aplikacji opartej na mikrousługach, można rozważyć użycie wielu bram interfejsów API, zamiast uprościć bezpośrednie podejście do komunikacji klient-mikrousług.

**Partycjonowanie mikrousług**. Bez względu na to, które podejście należy podjąć w przypadku architektury mikrousług, inne wyzwanie decyduje o tym, jak podzielić kompleksową aplikację na wiele mikrousług. Jak wspomniano w sekcji architektura przewodnika, istnieje kilka technik i metod, które można wykonać. W zasadzie należy określić obszary aplikacji, które są oddzielone od innych obszarów i które mają małą liczbę stałych zależności. W wielu przypadkach jest to wyrównane do partycjonowania usług według przypadku użycia. Na przykład w naszej aplikacji e-shop mamy usługę porządkowania, która jest odpowiedzialna za wszelką logikę biznesową powiązaną z procesem zamówienia. Mamy również usługę katalogową i usługę koszyka, która implementuje inne możliwości. W idealnym przypadku każda usługa powinna mieć tylko niewielki zestaw obowiązków. Jest to podobne do zasady pojedynczej odpowiedzialności (SRP) stosowanej do klas, co oznacza, że klasa powinna mieć tylko jedną przyczynę do zmiany. Ale w tym przypadku jest to informacje o mikrousługach, więc zakres będzie większy niż pojedyncza Klasa. Większość z nich to mikrousługa, która musi być całkowicie autonomiczna i kompleksowa, w tym odpowiedzialności za własne źródła danych.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Zewnętrzna a wewnętrzna architektura i wzorce projektowe

Zewnętrzna architektura to architektura mikrousług złożona przez wiele usług, zgodnie z zasadami opisanymi w sekcji architektura tego przewodnika. Jednakże, w zależności od rodzaju mikrousług i niezależnie od wybranej architektury mikrousług, jest to typowy i czasami zaleca się posiadanie różnych wewnętrznych architektur, z których każda jest oparta na różnych wzorcach, dla różnych mikrousług. Mikrousługi mogą nawet korzystać z różnych technologii i języków programowania. Rysunek 6-2 ilustruje tę różnorodność.

![Diagram porównujący wzorce architektury zewnętrznej i wewnętrznej.](./media/microservice-application-design/external-versus-internal-architecture.png)

**Rysunek 6-2**. Zewnętrzna a wewnętrzna architektura i projekt

Przykładowo w naszym *eShopOnContainers* przykładzie, wykaz, koszyk i mikrousługi profilu użytkownika są proste (zasadniczo CRUD podsystemy). W związku z tym ich wewnętrzna architektura i projekt są proste. Mogą jednak istnieć inne mikrousługi, takie jak mikrousługa porządkowania, która jest bardziej złożona i reprezentuje wszelkie zmiany reguł firmy o wysokim stopniu złożoności domeny. W takich przypadkach można zaimplementować bardziej zaawansowane wzorce w ramach konkretnej mikrousługi, takie jak te, które zostały zdefiniowane z podejściem projektowania opartym na domenie (DDD), tak jak w przypadku mikrousługi porządkowania *eShopOnContainers* . (W dalszej części omówiono implementację mikrousługi porządkowania *eShopOnContainers* ).

Kolejną przyczyną innej technologii na mikrousługi może być charakter każdej mikrousługi. Na przykład lepszym rozwiązaniem jest użycie języka programowania funkcjonalnego, takiego jak F\#, a nawet języka, takiego jak R, w przypadku docelowych domen systemu AI i uczenia maszynowego zamiast bardziej zorientowanego obiektowo języka programowania, takiego jak C\#.

Dolna linia polega na tym, że każda mikrousługa może mieć inną architekturę wewnętrzną opartą na różnych wzorcach projektowych. Nie wszystkie mikrousługi powinny być implementowane przy użyciu zaawansowanych wzorców DDD, ponieważ byłyby one przekroczenia inżynierów. Podobnie złożone mikrousługi z kiedykolwiek zmieniającą się logiką biznesową nie należy implementować jako składniki CRUD lub można zakończyć przy użyciu kodu o niskiej jakości.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nowy świat: wiele wzorców architektonicznych i mikrousług Polyglot

Istnieje wiele wzorców architektonicznych używanych przez architektów oprogramowania i deweloperów. Poniżej przedstawiono kilka (Mieszanie stylów architektury i wzorców architektury):

- Prosta CRUD, jednowarstwowa, jednowarstwowa.

- [Tradycyjne N warstwowe](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Projektowanie oparte na domenie N warstwowo](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Czysta architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (używana z [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [Command and Query Responsibility Segregation](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektura sterowana zdarzeniami](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Można również tworzyć mikrousługi z wieloma technologiami i językami, takimi jak ASP.NET Core Web API, NancyFx, ASP.NET Core Signaler (dostępne z .NET Core 2), F\#, Node. js, Python, Java C++,, GoLang i inne.

Ważnym punktem jest to, że żaden wzorzec architektury lub styl ani żadna konkretna technologia nie są odpowiednie dla wszystkich sytuacji. Rysunek 6-3 zawiera kilka metod i technologii (choć nie w określonej kolejności), które mogą być używane w różnych mikrousługach.

![Diagram przedstawiający 12 złożonych mikrousług w architekturze światowej Polyglot.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Rysunek 6-3**. Wzorce wieloarchitekturowe i Polyglot mikrousługi na świecie

Wieloarchitekturowy wzorzec i mikrousługi Polyglot oznacza, że można mieszać i dopasowywać Języki i technologie do potrzeb każdej mikrousługi i nadal muszą one się od siebie wzajemnie rozmawiać. Jak pokazano na rysunku 6-3 w aplikacjach składających się z wielu mikrousług (powiązanych kontekstów w terminologii projektowej opartej na domenie lub po prostu "podsystemów" jako autonomicznych mikrousług), można zaimplementować każdą mikrousługę w inny sposób. Każdy z nich może mieć inny wzorzec architektury i używać różnych języków i baz danych w zależności od rodzaju aplikacji, wymagań firmy i priorytetów. W niektórych przypadkach mikrousługi mogą być podobne. Jednak zazwyczaj nie jest to przypadek, ponieważ granica i wymagania kontekstu każdego podsystemu są zwykle różne.

Na przykład w przypadku prostej aplikacji do konserwacji CRUD może nie mieć sensu projektowania i implementowania wzorców DDD. Jednak w przypadku podstawowej domeny lub podstawowej firmy może być konieczne zastosowanie bardziej zaawansowanych wzorców w celu zajęcia się złożonością biznesową z ciągle zmieniającymi się regułami biznesowymi.

Szczególnie w przypadku, gdy zajmujesz się dużymi aplikacjami składającymi się z wielu podsystemów, nie należy stosować jednej architektury najwyższego poziomu w oparciu o pojedynczy wzorzec architektury. Na przykład CQRS nie powinna być stosowana jako architektura najwyższego poziomu dla całej aplikacji, ale może być przydatna dla określonego zestawu usług.

Dla każdego z tych przypadków nie ma punktora Silver lub odpowiedniego wzorca architektury. Nie można mieć "jednego wzorca architektury, aby była dla nich stosowana reguła". W zależności od priorytetów każdej mikrousługi należy wybrać różne podejście dla każdej z nich, jak wyjaśniono w poniższych sekcjach.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](data-driven-crud-microservice.md)
