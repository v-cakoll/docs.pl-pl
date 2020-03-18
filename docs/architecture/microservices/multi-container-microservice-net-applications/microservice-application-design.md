---
title: Projektowanie aplikacji opartej na mikrousługach
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumienie korzyści i wad aplikacji zorientowanej na mikrousługi, dzięki czemu można podjąć świadomą decyzję.
ms.date: 10/02/2018
ms.openlocfilehash: 619440c02c1a82e05adb2cec9ddba933cd3e0a65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76965766"
---
# <a name="design-a-microservice-oriented-application"></a>Projektowanie aplikacji zorientowanej na mikrousługi

W tej sekcji skupiono się na tworzeniu hipotetycznej aplikacji przedsiębiorstwa po stronie serwera.

## <a name="application-specifications"></a>Specyfikacje aplikacji

Hipotetyczna aplikacja obsługuje żądania, wykonując logikę biznesową, uzyskując dostęp do baz danych, a następnie zwracając odpowiedzi HTML, JSON lub XML. Powiemy, że aplikacja musi obsługiwać różnych klientów, w tym przeglądarki komputerowe z uruchomionymi aplikacjami jednostronicowymi (SPA), tradycyjne aplikacje internetowe, mobilne aplikacje internetowe i natywne aplikacje mobilne. Aplikacja może również uwidaczniać interfejs API dla osób trzecich do użycia. Powinien również być w stanie zintegrować jego mikrousług lub aplikacji zewnętrznych asynchronicznie, tak aby podejście to pomoże odporność mikrousług w przypadku błędów częściowych.

Aplikacja będzie składać się z tego typu składników:

- Składniki prezentacji. Są one odpowiedzialne za obsługę interfejsu i korzystanie z usług zdalnych.

- Logika domeny lub biznesowej. Jest to logika domeny aplikacji.

- Logika dostępu do bazy danych. Składa się ze składników dostępu do danych odpowiedzialnych za dostęp do baz danych (SQL lub NoSQL).

- Logika integracji aplikacji. Obejmuje to kanał obsługi wiadomości, głównie na podstawie brokerów komunikatów.

Aplikacja będzie wymagać wysokiej skalowalności, umożliwiając jednocześnie jej pionowe podsystemy skalować w poziomie autonomicznie, ponieważ niektóre podsystemy będą wymagać większej skalowalności niż inne.

Aplikacja musi być w stanie być wdrożony w wielu środowiskach infrastruktury (wiele chmur publicznych i lokalnie) i najlepiej powinna być między platformami, w stanie łatwo przejść z systemu Linux do systemu Windows (lub odwrotnie).

## <a name="development-team-context"></a>Kontekst zespołu programistycznego

Zakładamy również, że następujące informacje o procesie rozwoju aplikacji:

- Masz wiele zespołów deweloperskich koncentrujących się na różnych obszarach biznesowych aplikacji.

- Nowi członkowie zespołu muszą szybko stać się produktywni, a aplikacja musi być łatwa do zrozumienia i modyfikacji.

- Aplikacja będzie miała długoterminową ewolucję i ciągle zmieniające się zasady biznesowe.

- Potrzebna jest dobra długoterminowa łatwość konserwacji, co oznacza elastyczność podczas wdrażania nowych zmian w przyszłości, a jednocześnie możliwość aktualizacji wielu podsystemów o minimalnym wpływie na inne podsystemy.

- Chcesz ćwiczyć ciągłą integrację i ciągłe wdrażanie aplikacji.

- Chcesz skorzystać z nowych technologii (frameworki, języki programowania, itp.) podczas ewoluowania aplikacji. Nie chcesz, aby pełne migracje aplikacji podczas przechodzenia do nowych technologii, ponieważ spowodowałoby to wysokie koszty i wpływ na przewidywalność i stabilność aplikacji.

## <a name="choosing-an-architecture"></a>Wybór architektury

Czym powinna być architektura wdrażania aplikacji? Specyfikacje aplikacji, wraz z kontekstem rozwoju, zdecydowanie sugerują, że należy zaprojektować aplikację, rozkładając ją na autonomiczne podsystemy w postaci współpracujących mikrousług i kontenerów, gdzie mikrousługi jest kontenerem.

W tym podejściu każda usługa (kontener) implementuje zestaw funkcji spójności i wąsko powiązanych. Na przykład aplikacja może składać się z usług, takich jak usługa katalogu, usługa zamawiania, usługa koszyka, usługa profilu użytkownika itp.

Mikrousługi komunikują się przy użyciu protokołów, takich jak HTTP (REST), ale także asynchronicznie (na przykład przy użyciu protokołu AMQP), gdy jest to możliwe, szczególnie podczas propagowania aktualizacji za pomocą zdarzeń integracji.

Mikrousługi są opracowywane i wdrażane jako kontenery niezależnie od siebie. Oznacza to, że zespół programista może być tworzenie i wdrażanie niektórych mikrousług bez wpływu na inne podsystemy.

Każda mikrousługa ma własną bazę danych, dzięki czemu można w pełni oddzielić od innych mikrousług. W razie potrzeby spójność między bazami danych z różnych mikrousług jest osiągana przy użyciu zdarzeń integracji na poziomie aplikacji (za pośrednictwem magistrali zdarzeń logicznych), zgodnie z usługą Command and Query Responsibility Segregation (CQRS). Z tego powodu ograniczenia biznesowe muszą obejmować spójność ostateczną między wieloma mikrousługami i powiązanymi bazami danych.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: Aplikacja referencyjna dla .NET Core i mikrousług wdrożonych przy użyciu kontenerów

Aby można było skupić się na architekturze i technologiach, zamiast myśleć o hipotetycznej domenie biznesowej, której być może nie znasz, wybraliśmy znaną domenę biznesową, a mianowicie uproszczoną aplikację e-commerce (e-shop), która prezentuje katalog produktów, przyjmuje zamówienia od klientów, weryfikuje zapasy i wykonuje inne funkcje biznesowe. Ten kod źródłowy aplikacji oparty na kontenerze jest dostępny w reppo [githubie eShopOnContainers.](https://aka.ms/MicroservicesArchitecture)

Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika magazynu (aplikacji sieci Web i natywnej aplikacji mobilnej) wraz z mikrousługzaplecza i kontenerów dla wszystkich wymaganych operacji po stronie serwera z kilku bram interfejsu API jako skonsolidowane punkty wejścia do mikrousług wewnętrznych. Rysunek 6-1 przedstawia architekturę aplikacji referencyjnej.

![Diagram aplikacji klienckich przy użyciu eShopOnContainers w jednym hoście platformy Docker.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Rysunek 6-1**. Architektura aplikacji referencyjnej eShopOnContainers dla środowiska programistycznego

Powyższy diagram pokazuje, że klienci mobilni i SPA komunikują się z pojedynczymi punktami końcowymi bramy interfejsu API, które następnie komunikują się z mikrousługami. Tradycyjni klienci sieci web komunikują się z mikrousługą MVC, która komunikuje się z mikrousługami za pośrednictwem bramy interfejsu API.

**Środowisko hostingowe**. Na rysunku 6-1 zostanie wyświetlonych kilka kontenerów wdrożonych w ramach jednego hosta platformy Docker. Tak byłoby w przypadku wdrażania na jednym hoście platformy Docker za pomocą polecenia docker-compose up. Jednak jeśli używasz koordynatora lub klastra kontenera, każdy kontener może być uruchomiony w innym hosta (węzeł), a każdy węzeł może być uruchomiony dowolną liczbę kontenerów, jak wyjaśniono wcześniej w sekcji architektury.

**Architektura komunikacji**. Aplikacja eShopOnContainers używa dwóch typów komunikacji, w zależności od rodzaju akcji funkcjonalnej (zapytania i aktualizacje i transakcje):

- Http klient-mikrousługi komunikacji za pośrednictwem bram interfejsu API. Jest to używane w przypadku kwerend i akceptowania poleceń aktualizacji lub transakcyjnych z aplikacji klienckich. Podejście przy użyciu bram interfejsu API jest szczegółowo wyjaśnione w kolejnych sekcjach.

- Komunikacja asynchroniczna oparta na zdarzeniach. Dzieje się tak za pośrednictwem magistrali zdarzeń do propagowania aktualizacji w mikrousługach lub integracji z aplikacjami zewnętrznymi. Magistrala zdarzeń może być implementowana za pomocą dowolnej technologii infrastruktury brokera obsługi wiadomości, takiej jak RabbitMQ, lub przy użyciu magistrali usług wyższego poziomu (na poziomie abstrakcji), takich jak usługa Azure Service Bus, NServiceBus, MassTransit lub Brighter.

Aplikacja jest wdrażana jako zestaw mikrousług w postaci kontenerów. Aplikacje klienckie mogą komunikować się z tymi mikrousługami działao jako kontenery za pośrednictwem publicznych adresów URL opublikowanych przez bramy interfejsu API.

### <a name="data-sovereignty-per-microservice"></a>Suwerenność danych przypadająca na mikrousługę

W przykładowej aplikacji każda mikrousługa jest właścicielem własnej bazy danych lub źródła danych, chociaż wszystkie bazy danych programu SQL Server są wdrażane jako pojedynczy kontener. Ta decyzja projektowa została podjęta tylko po to, aby ułatwić deweloperowi uzyskanie kodu z usługi GitHub, sklonowanie go i otwarcie go w programie Visual Studio lub Visual Studio Code. Lub alternatywnie ułatwia kompilowanie niestandardowych obrazów platformy Docker przy użyciu .NET Core CLI i docker CLI, a następnie wdrożyć i uruchomić je w środowisku programistycznym platformy Docker. Tak czy inaczej, przy użyciu kontenerów dla źródeł danych umożliwia deweloperom tworzenie i wdrażanie w ciągu kilku minut bez konieczności aprowizacji zewnętrznej bazy danych lub innego źródła danych z twardych zależności na infrastrukturze (w chmurze lub lokalnie).

W rzeczywistym środowisku produkcyjnym, dla wysokiej dostępności i skalowalności, bazy danych powinny być oparte na serwerach baz danych w chmurze lub lokalnie, ale nie w kontenerach.

W związku z tym jednostki wdrażania dla mikrousług (a nawet dla baz danych w tej aplikacji) są kontenery platformy Docker, a aplikacja referencyjna jest aplikacją wielokontenerową, która obejmuje zasady mikrousług.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **reppo githuba eShopOnContainers. Kod źródłowy dla aplikacji referencyjnej** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Korzyści z rozwiązania opartego na mikrousługach

Rozwiązanie oparte na mikrousługach, takie jak to, ma wiele zalet:

**Każda mikrousługa jest stosunkowo mała — łatwa w zarządzaniu i ewoluować.** Są to:

- Deweloper owi łatwo jest zrozumieć i szybko zacząć pracę z dobrą wydajnością.

- Kontenery rozpoczynają się szybko, co sprawia, że deweloperzy są bardziej produktywni.

- IDE jak Visual Studio można szybko załadować mniejsze projekty, dzięki czemu deweloperzy produktywne.

- Każda mikrousługa może być projektowana, rozwijana i wdrażana niezależnie od innych mikrousług, co zapewnia elastyczność, ponieważ często można wdrożyć nowe wersje mikrousług.

**Możliwe jest skalowanie w poziomie poszczególnych obszarów aplikacji.** Na przykład usługa katalogu lub usługi koszyka może być konieczne skalowanie w sposób skalowany w sposób skalowany, ale nie proces zamawiania. Infrastruktury mikrousług będzie znacznie bardziej wydajne w odniesieniu do zasobów używanych podczas skalowania w sposób poza architekturą monolityczną będzie.

**Można podzielić prace programistyczne między wiele zespołów**. Każda usługa może być własnością jednego zespołu deweloperów. Każdy zespół może zarządzać, rozwijać, wdrażać i skalować swoje usługi niezależnie od reszty zespołów.

**Problemy są bardziej odosobnione.** Jeśli występuje problem w jednej usłudze, tylko tej usługi jest początkowo wpływ (z wyjątkiem, gdy używany jest niewłaściwy projekt, z bezpośrednich zależności między mikrousług) i innych usług można kontynuować obsługę żądań. Z drugiej strony jeden składnik nieprawidłowo działający w architekturze wdrażania monolitycznego może obniżyć cały system, zwłaszcza gdy obejmuje zasoby, takie jak przeciek pamięci. Ponadto po rozwiązaniu problemu w mikrousługach można wdrożyć tylko mikrousługi, których dotyczy problem, bez wpływu na pozostałą część aplikacji.

**Możesz korzystać z najnowszych technologii.** Ponieważ można rozpocząć tworzenie usług niezależnie i uruchamiać je obok siebie (dzięki kontenerom i .NET Core), można rozpocząć przy użyciu najnowszych technologii i struktur celowo zamiast tkwić na starszym stosie lub framework dla całego Aplikacji.

## <a name="downsides-of-a-microservice-based-solution"></a>Wady rozwiązania opartego na mikrousługach

Rozwiązanie oparte na mikrousługach, takie jak to, ma również pewne wady:

**Aplikacja rozproszona**. Dystrybucja aplikacji zwiększa złożoność dla deweloperów podczas projektowania i tworzenia usług. Na przykład deweloperzy muszą zaimplementować komunikację między usługami przy użyciu protokołów, takich jak HTTP lub AMPQ, co zwiększa złożoność testowania i obsługi wyjątków. Zwiększa również opóźnienie w systemie.

**Złożoność wdrożenia**. Aplikacja, która ma dziesiątki typów mikrousług i wymaga wysokiej skalowalności (musi być w stanie utworzyć wiele wystąpień na usługę i zrównoważyć te usługi na wielu hostach) oznacza wysoki stopień złożoności wdrożenia dla operacji IT i zarządzania. Jeśli nie używasz infrastruktury zorientowanej na mikrousługi (jak koordynator i harmonogram), że dodatkowa złożoność może wymagać znacznie więcej wysiłków na rzecz rozwoju niż sama aplikacja biznesowa.

**Transakcje atomowe**. Transakcje atomowe między wieloma mikrousługami zwykle nie są możliwe. Wymagania biznesowe muszą objąć spójność ostateczną między wieloma mikrousługami.

**Zwiększone globalne zapotrzebowanie na zasoby** (całkowita ilość pamięci, dysków i zasobów sieciowych dla wszystkich serwerów lub hostów). W wielu przypadkach po zastąpieniu aplikacji monolityczne podejście mikrousług, ilość początkowych zasobów globalnych wymaganych przez nową aplikację opartą na mikrousługach będzie większa niż potrzeby infrastruktury oryginalnej aplikacji monolityczne. Dzieje się tak, ponieważ wyższy stopień szczegółowości i usług rozproszonych wymaga więcej zasobów globalnych. Biorąc jednak pod uwagę niski koszt zasobów w ogóle i korzyści wynikające z możliwości skalowania tylko niektórych obszarów zastosowania w porównaniu z kosztami długoterminowymi przy ewoluowaniu monolitycznych zastosowań, zwiększone wykorzystanie zasobów jest zwykle dobrym kompromisem dla dużych, długoterminowych zastosowań.

**Problemy z bezpośrednią komunikacją klient-mikrousługi**. Gdy aplikacja jest duża, z dziesiątkami mikrousług, istnieją wyzwania i ograniczenia, jeśli aplikacja wymaga bezpośredniej komunikacji klient-mikrousługi. Jednym z problemów jest potencjalne niezgodność między potrzebami klienta i interfejsów API udostępniane przez każdego z mikrousług. W niektórych przypadkach aplikacja kliencka może być konieczne do wykonania wielu oddzielnych żądań do tworzenia interfejsu, które mogą być nieefektywne za pośrednictwem Internetu i byłoby niepraktyczne za pośrednictwem sieci komórkowej. W związku z tym żądania od aplikacji klienckiej do systemu zaplecza powinny być zminimalizowane.

Innym problemem z bezpośrednią komunikacją klient-mikrousługi jest to, że niektóre mikrousługi mogą używać protokołów, które nie są przyjazne dla sieci Web. Jedna usługa może używać protokołu binarnego, podczas gdy inna usługa może używać wiadomości AMQP. Protokoły te nie są przyjazne dla zapory i najlepiej są używane wewnętrznie. Zazwyczaj aplikacja powinna używać protokołów, takich jak HTTP i WebSockets do komunikacji poza zaporą.

Jeszcze inną wadą z tego bezpośredniego klienta do usługi podejście jest, że utrudnia refaktoryzacji umów dla tych mikrousług. Wraz z urazem deweloperzy mogą chcieć zmienić sposób podziału systemu na usługi. Na przykład mogą scalić dwie usługi lub podzielić usługę na dwie lub więcej usług. Jednak jeśli klienci komunikują się bezpośrednio z usługami, wykonywanie tego rodzaju refaktoryzacji może przerwać zgodność z aplikacjami klienckimi.

Jak wspomniano w sekcji architektury podczas projektowania i tworzenia złożonych aplikacji na podstawie mikrousług, można rozważyć użycie wielu szczegółowych bram interfejsu API zamiast prostsze bezpośrednie podejście komunikacji klient-mikrousługi.

**Partycjonowanie mikrousług**. Na koniec bez względu na to, które podejście należy podjąć dla architektury mikrousług, innym wyzwaniem jest podjęcie decyzji, jak podzielić aplikację end-to-end na wiele mikrousług. Jak wspomniano w sekcji architektury przewodnika, istnieje kilka technik i metod, które można podjąć. Zasadniczo należy zidentyfikować obszary aplikacji, które są oddzielone od innych obszarów i które mają małą liczbę twardych zależności. W wielu przypadkach jest to wyrównane do partycjonowania usług według przypadków użycia. Na przykład w naszej aplikacji sklepu internetowego mamy usługę zamawiania, która jest odpowiedzialna za całą logikę biznesową związaną z procesem zamówienia. Mamy również usługę katalogu i usługi koszyka, które implementują inne możliwości. W idealnym przypadku każda usługa powinna mieć tylko niewielki zestaw obowiązków. Jest to podobne do zasady pojedynczej odpowiedzialności (SRP) stosowanej do klas, która stanowi, że klasa powinna mieć tylko jeden powód do zmiany. Ale w tym przypadku chodzi o mikrousług, więc zakres będzie większy niż jednej klasy. Przede wszystkim mikrousługi musi być całkowicie autonomiczne, end-to-end, w tym odpowiedzialność za własne źródła danych.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Architektura zewnętrzna a wewnętrzna i wzorce projektowe

Architektura zewnętrzna jest architektura mikrousług składa się z wielu usług, zgodnie z zasadami opisanymi w sekcji architektury tego przewodnika. Jednak w zależności od charakteru każdej mikrousługi i niezależnie od architektury mikrousług wysokiego poziomu, które wybierzesz, jest to typowe i czasami wskazane, aby mieć różne architektury wewnętrzne, każdy na podstawie różnych wzorców dla różnych Mikrousług. Mikrousług można nawet używać różnych technologii i języków programowania. Rysunek 6-2 ilustruje tę różnorodność.

![Diagram porównujący wzorce architektury zewnętrznej i wewnętrznej.](./media/microservice-application-design/external-versus-internal-architecture.png)

**Rysunek 6-2**. Architektura zewnętrzna a wewnętrzna i projektowanie

Na przykład w naszym *eShopOnContainers* próbki katalogu, koszyka i mikrousług profilu użytkownika są proste (w zasadzie podsystemy CRUD). Dlatego ich wewnętrzna architektura i design są proste. Jednak może mieć inne mikrousługi, takie jak mikrousługi porządkowania, który jest bardziej złożony i reprezentuje stale zmieniających się reguł biznesowych o wysokim stopniu złożoności domeny. W takich przypadkach można zaimplementować bardziej zaawansowane wzorce w ramach określonej mikrousługi, takich jak te zdefiniowane z metodami projektowania opartego na domenie (DDD), jak robimy w *eShopOnContainers* zamawiania mikrousługi. (Będziemy przeglądać te wzorce DDD w sekcji później, który wyjaśnia implementację *eShopOnContainers* zamawiania mikrousługi.)

Innym powodem innej technologii na mikrousługi może być charakter każdej mikrousługi. Na przykład może być lepiej użyć funkcjonalnego języka\#programowania, takiego jak F , lub nawet języka takiego jak R, jeśli kierujesz reklamy\#na domeny AI i uczenia maszynowego, zamiast bardziej obiektowego języka programowania, takiego jak C .

Najważniejsze jest to, że każda mikrousługa może mieć inną architekturę wewnętrzną na podstawie różnych wzorców projektu. Nie wszystkie mikrousługi powinny być implementowane przy użyciu zaawansowanych wzorców DDD, ponieważ byłoby to ich nadmiernej inżynierii. Podobnie złożonych mikrousług z logiki biznesowej stale zmieniających się nie powinny być implementowane jako składniki CRUD lub może skończyć się kod niskiej jakości.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nowy świat: wiele wzorców architektonicznych i mikrousług polyglot

Istnieje wiele wzorców architektonicznych używanych przez architektów oprogramowania i deweloperów. Oto kilka z nich (mieszanie stylów architektury i wzorców architektury):

- Prosty CRUD, jednowarstwowy, jednowarstwowy.

- [Tradycyjne N-warstwowe](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Projekt oparty na domenie n-warstwowy](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Czysta architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (używana z [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [Segregacja odpowiedzialności za polecenia i kwerendy](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektura oparta na zdarzeniach](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Można również tworzyć mikrousługi z wielu technologii i języków, takich jak ASP.NET Core Web API, NancyFx, ASP.NET Core SignalR (dostępne z .NET Core 2), F\#, Node.js, Python, Java, C ++, GoLang i więcej.

Ważne jest to, że żaden konkretny wzór architektury lub styl, ani żadna konkretna technologia, nie jest odpowiedni a dla wszystkich sytuacji. Rysunek 6-3 przedstawia niektóre podejścia i technologie (chociaż nie w określonej kolejności), które mogą być używane w różnych mikrousług.

![Diagram przedstawiający 12 złożonych mikrousług w architekturze świata polyglot.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Rysunek 6-3**. Wzorce wieloarchitekturowe i świat mikrousług polyglot

Wieloarchitekturowe wzorzec i mikrousługi polyglot oznacza, że można mieszać i dopasowywać języki i technologie do potrzeb każdej mikrousługi i nadal je rozmawiać ze sobą. Jak pokazano na rysunku 6-3, w aplikacjach składających się z wielu mikrousług (ograniczone konteksty w terminologii projektowania opartego na domenie lub po prostu "podsystemy" jako autonomiczne mikrousługi), można zaimplementować każdą mikrousługę w inny sposób. Każdy może mieć inny wzorzec architektury i używać różnych języków i baz danych w zależności od charakteru aplikacji, wymagania biznesowe i priorytety. W niektórych przypadkach mikrousług może być podobny. Ale zwykle tak nie jest, ponieważ granice kontekstu każdego podsystemu i wymagania są zwykle różne.

Na przykład dla prostej aplikacji do konserwacji CRUD może nie mieć sensu projektowanie i implementowanie wzorców DDD. Jednak w przypadku podstawowej domeny lub podstawowej działalności może być konieczne zastosowanie bardziej zaawansowanych wzorców, aby poradzić sobie ze złożonością biznesową za pomocą ciągle zmieniających się reguł biznesowych.

Zwłaszcza w przypadku dużych aplikacji składających się z wielu podsystemów, nie należy stosować jednej architektury najwyższego poziomu na podstawie jednego wzorca architektury. Na przykład CQRS nie powinny być stosowane jako architektury najwyższego poziomu dla całej aplikacji, ale może być przydatne dla określonego zestawu usług.

Nie ma srebrnej kuli ani właściwego wzoru architektury dla każdego danego przypadku. Nie można mieć "jeden wzorzec architektury, aby rządzić nimi wszystkimi." W zależności od priorytetów każdej mikrousługi należy wybrać inne podejście dla każdego z nich, jak wyjaśniono w poniższych sekcjach.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](data-driven-crud-microservice.md)
