---
title: Projektowanie aplikacji opartej na mikrousługach
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, zalet i wad aplikacji opartej na mikrousługach, aby można było podjąć świadomą decyzję.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 160eba2c7249793592caf13622b01c597d7feec7
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613866"
---
# <a name="designing-a-microservice-oriented-application"></a>Projektowanie aplikacji opartej na mikrousługach

Ta sekcja koncentruje się na projektowaniu aplikacji hipotetyczny enterprise po stronie serwera.

## <a name="application-specifications"></a>Specyfikacje aplikacji

Hipotetycznej aplikacji obsługuje żądania, wykonywania logiki biznesowej, uzyskiwanie dostępu do bazy danych, a następnie zwracanie odpowiedzi HTML, JSON lub XML. Firma Microsoft będzie Załóżmy, że aplikacja musi obsługiwać różnych klientów, w tym przeglądarek komputerowych uruchomione aplikacje jednostronicowe (źródła), aplikacje sieci web tradycyjne, aplikacje mobilne i natywne aplikacje mobilne. Aplikacja również może udostępniać stronom trzecim korzystanie z interfejsu API. Należy również możliwości integracji jego mikrousług lub aplikacjami zewnętrznymi asynchronicznie, tak aby podejście ułatwi odporności mikrousług w przypadku częściowej awarii.

Aplikacja będzie składać się z tych typów składników:

- Składniki prezentacji. Są odpowiedzialne za obsługę interfejsu użytkownika i korzystanie z usługi zdalnej.

- Domeny lub logikę biznesową. Jest to logika domeny aplikacji.

- Logika dostępu do bazy danych. Składa się z odpowiedzialna za uzyskiwanie dostępu do bazy danych (bazy danych SQL lub NoSQL) składniki dostępu do danych.

- Logika integracji aplikacji. Obejmuje to kanał obsługi komunikatów, głównie oparte na brokerami.

Aplikacja będzie wymagać wysoką skalowalność, zapewniając podsystemy pionowy skalowania w poziomie autonomicznie, ponieważ pewne podsystemy będzie wymagać lepszą skalowalność niż inne.

Aplikacja musi być w stanie do wdrożenia w wielu środowiskach infrastruktury (wiele chmur publicznych i w środowisku lokalnym) i najlepiej powinna być dla wielu platform, można umożliwiają łatwe przejście z systemu Linux, Windows (lub odwrotnie).

## <a name="development-team-context"></a>Kontekst zespołu rozwoju

Przyjęto również założenie, że następujące kwestie dotyczące proces tworzenia aplikacji:

- Masz wiele zespołów deweloperskich, skupiając się na różnych firm obszarów aplikacji.

- Nowi członkowie zespołu mogą stać się produktywność szybko, a aplikacja musi być łatwe do zrozumienia i modyfikować.

- Aplikacja będzie miała długoterminowe ewolucji i ciągle zmieniające reguł biznesowych.

- Konieczne jest dobrym długoterminowe łatwość utrzymania, która oznacza elastyczność podczas wdrażania nowych zmian w przyszłości, będąc może zaktualizować wiele podsystemów minimalne wpływu na inne podsystemy.

- Chcesz rozwiązaniem ciągłej integracji i ciągłego wdrażania aplikacji.

- Chcesz korzystać z nowych technologii (środowisk programowania, języków itp.) podczas zmieniających się aplikacja. Czy chcesz wprowadzić pełnej migracji aplikacji, podczas przenoszenia do nowych technologii, ponieważ, może spowodować wysokie koszty i wpływać na przewidywalności i stabilność aplikacji.

## <a name="choosing-an-architecture"></a>Wybieranie architekturę

Co należy architektura wdrożenia aplikacji Specyfikacje dotyczące aplikacji, wraz z kontekstu rozwoju Zaproponuj silnie, należy zaprojektować aplikacji przez podzielenie na autonomicznych podsystemy w formularzu, współpracujących mikrousług i kontenerów, w przypadku, gdy mikrousługi jest kontenerem.

W tym podejściu każdej usługi (kontenera) implementuje zestaw spójnych i ściśle powiązanych funkcji. Na przykład aplikacja może składać się z usługami, takimi jak usługi katalogu, porządkowanie usługi, Usługa koszyka, Usługa profilu użytkownika, itp.

Mikrousługi komunikują się przy użyciu protokołów, takich jak HTTP (REST), ale również asynchronicznie (na przykład za pomocą protokołu AMQP) zawsze, gdy jest to możliwe, szczególnie gdy propagowanie zostaje zaktualizowana o zdarzenia integracji.

Mikrousługi są opracowane i wdrażane jako kontenery, niezależnie od siebie nawzajem. Oznacza to, czy zespół programistyczny może być opracowywania i wdrażania niektórych mikrousługi bez wywierania wpływu na inne podsystemy.

Każda mikrousługa ma własną bazę danych, dzięki któremu można w pełni całkowicie niezależna od innych mikrousług. Gdy jest to konieczne, spójności między bazami danych z różnych mikrousług odbywa się przy użyciu zdarzeń integracji na poziomie aplikacji (za pośrednictwem magistrali zdarzeń logicznych), jako obsługiwane w poleceniu i podział odpowiedzialności zapytania (CQRS). Z tego powodu, ograniczeń biznesowych należy Uwzględniaj spójność ostateczną, między wiele mikrousług i związanych z bazami danych.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: Odwołanie do stosowania platformy .NET Core i mikrousług, wdrażać za pomocą kontenerów

Dzięki czemu można skupić się na temat architektury i technologii, zamiast myśleć o domeny hipotetyczny biznesowych, która może być, wybraliśmy domeny dobrze znanych firm — to znaczy, uproszczone handlu elektronicznego (e Sklep) aplikację która przedstawia informacje o katalogu produktów, przyjmuje zamówień klientów, sprawdza spisu i wykonuje funkcje innych firm. Ten kod źródłowy aplikacji opartych na kontenerach jest dostępna w [ramach aplikacji eShopOnContainers](https://aka.ms/MicroservicesArchitecture) repozytorium GitHub.

Aplikacja składa się z wiele podsystemów, w tym kilka magazynu interfejsu użytkownika Frontony aplikacji sieci Web i natywnych aplikacji mobilnych, wraz z zaplecza mikrousług i kontenerów dla wszystkich wymaganych operacji po stronie serwera za pomocą kilku bramy interfejsu API jako skonsolidowane punkty wejścia do wewnętrznego mikrousług. Rysunek 6-1 przedstawiono architekturę aplikacji referencyjnej.

![Klienci urządzeń przenośnych i SPA komunikują się do jednej bramy punkty końcowe interfejsu API, następnie komunikujących się mikrousług. Tradycyjny web klienci komunikują się do mikrousług MVC, która komunikuje się mikrousług](./media/image1.png)

**Rysunek 6-1**. Architektury aplikacji w środowisku deweloperskim referencyjnej ramach aplikacji eShopOnContainers

**Środowisko hostingu**. W rysunek 6-1, będzie widocznych wiele kontenerów wdrożonego w ramach jednego hosta platformy Docker. Byłoby przypadek, w przypadku wdrażania jednego hosta platformy Docker z platformą docker-compose się polecenia. Jednak jeśli przy użyciu koordynatora lub klastra kontenera, każdy kontener może działać w różnych hostach (node) i dowolny węzeł może być uruchomiony dowolną liczbę kontenerów, zgodnie z opisem firma Microsoft we wcześniejszej sekcji architektury.

**Architektura komunikacji**. Aplikacja w ramach aplikacji eShopOnContainers używa dwóch typów komunikacji, w zależności od rodzaju akcji funkcjonalności (zapytań i aktualizacji oraz transakcje):

- Komunikacja klienta z mikrousługą HTTP za pośrednictwem bramy interfejsu API. Służy do zapytań i akceptując aktualizacji lub transakcyjnych poleceń usługi aplikacji klienta. Podejście przy użyciu bramy interfejsu API jest omówiona szczegółowo w kolejnych sekcjach.

- Oparte na zdarzeniach komunikacji asynchronicznej. Dzieje się to za pośrednictwem magistrali zdarzeń propagowanie aktualizacje mikrousług lub Integracja z aplikacjami zewnętrznymi. W przypadku innych technologii infrastruktury obsługi komunikatów brokera, RabbitMQ lub przy użyciu wyższego poziomu magistrali usługi (poziom abstrakcji), takich jak usługi Azure Service Bus, NServiceBus, MassTransit lub Brighter można zaimplementować magistrali zdarzeń.

Aplikacja jest wdrażana jako zbiór mikrousług w postaci kontenerów. Aplikacje klienckie mogą komunikować się z tymi mikrousług, uruchomione jako kontenery przy użyciu publicznych adresów URL opublikowany przez bramy interfejsu API.

### <a name="data-sovereignty-per-microservice"></a>Suwerenność danych przypadająca na mikrousługę

W przykładowej aplikacji każda mikrousługa jest właścicielem własną bazę danych lub źródła danych, mimo że wszystkie bazy danych programu SQL Server są wdrażane jako jeden kontener. Tej decyzji projektowej została wprowadzona tylko po to, aby ułatwić deweloperom Pobieranie kodu z usługi GitHub, sklonować ten projekt i otworzyć go w programie Visual Studio lub Visual Studio Code. Lub też ułatwia go skompilować niestandardowych obrazów platformy Docker przy użyciu interfejsu wiersza polecenia platformy .NET Core i interfejsu wiersza polecenia platformy Docker, a następnie wdrożyć i uruchomić je w Środowisko deweloperskie platformy Docker. W obu przypadkach przy użyciu kontenerów dla danych źródeł umożliwia deweloperom tworzenie i wdrażanie w ciągu kilku minut bez konieczności aprowizowania zewnętrznej bazy danych lub dowolnego innego źródła danych za pomocą twardych zależności w infrastrukturze (w chmurze lub lokalnie).

W środowisku produkcyjnym rzeczywistych, wysokiej dostępności i skalowalności bazy danych powinna być oparta na serwerach bazy danych w chmurze lub lokalnie, ale nie w kontenerach.

Dlatego jednostki wdrożenia mikrousługi (a nawet w przypadku baz danych w tej aplikacji) są kontenery platformy Docker i aplikacja referencyjna jest aplikację obsługującą wiele kontenerów, która korzysta z zasad mikrousług.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **eShopOnContainers GitHub repo. Kod źródłowy aplikacji odwołanie**\
    <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Zalety rozwiązania oparte na mikrousługach

Rozwiązania na podstawie mikrousług, takiego jak to ma wiele zalet:

**Każda mikrousługa jest stosunkowo niewielka — łatwe zarządzanie i rozwój**. W szczególności:

- To proste dla deweloperów zrozumieć i szybko rozpocząć pracę z dobrą wydajność.

- Kontenery rozpocząć szybkie, który zwiększa wydajność deweloperów.

- Środowisko IDE, takie jak Visual Studio można załadować mniejsze projekty szybkiego działania, dzięki czemu produktywności deweloperów.

- Poszczególne mikrousługi można zaprojektowane, opracowane i wdrażane niezależnie od innych mikrousług, która zapewnia elastyczność, ponieważ ułatwia wdrażanie nowych wersji mikrousług często.

**Istnieje możliwość skalowania w poziomie poszczególnych obszarów aplikacji**. Na przykład usługi katalogu lub koszyka może być konieczne być skalowana w poziomie, ale nie zamawiania. Infrastruktura mikrousług będzie znacznie bardziej skuteczny w odniesieniu do zasobów używane podczas skalowania w poziomie, niż byłoby monolityczne architektury.

**Można podzielić tworzonym między wiele zespołów**. Każda usługa może być własnością jeden zespół deweloperów. Każdy zespół może zarządzać, programowanie, wdrażanie i skalowanie ich usług, niezależnie od pozostałej części zespoły.

**Problemy są bardziej odizolowane**. Jeśli występuje problem w jednej usłudze, tylko usługi początkowo ma wpływ na (z wyjątkiem sytuacji, gdy niewłaściwy projekt jest używany, za pomocą bezpośrednich zależności między mikrousługami) i innych usług mogą w dalszym ciągu obsługuje żądania. Z kolei jeden nieprawidłowo działający składnik w architekturze monolityczne wdrożenia może przynieść wyłączenia całego systemu, zwłaszcza w przypadku, gdy obejmuje zasoby, takie jak przeciek pamięci. Ponadto po usunięciu problemu w mikrousługach, bez wywierania wpływu na pozostałe części aplikacji można wdrożyć po prostu wykorzystywanych mikrousług.

**Można użyć najnowszej technologii**. Ponieważ można rozpocząć tworzenie usług niezależnie i uruchamiaj je obok siebie (dzięki gotowej do kontenerów i platformy .NET Core), możesz zacząć używać najnowszych technologii i platform rzetelny zamiast jest zablokowany na starszych stosu lub strukturę do całego aplikacja.

## <a name="downsides-of-a-microservice-based-solution"></a>Wad to rozwiązanie oparte na mikrousługach

Rozwiązania na podstawie mikrousług, takiego jak to ma również pewne wady:

**Aplikacji rozproszonej**. Dystrybucja aplikacji zwiększa złożoność dla deweloperów, podczas projektowania i tworzenia usługi. Na przykład deweloperzy muszą implementować nasilenia komunikacji między usługami przy użyciu protokołów, takich jak HTTP lub AMPQ, który dodaje złożoności do testowania i obsługi wyjątków. Również dodaje opóźnienie do systemu.

**Złożoność wdrożenia**. Aplikacja, która ma wielu typów mikrousług i potrzebuje wysokiej skalowalności (musi to być może tworzyć wiele wystąpień poszczególnych usług i równoważenie tych usług na wielu hostach) oznacza wysoki stopień złożoności wdrożenia dla działu operacji IT i zarządzania. Jeśli nie używasz infrastruktury opartej na mikrousługach (np. programu orchestrator i harmonogram), tej dodatkowej złożoności może wymagać znacznie zwiększa wspierające prace deweloperów tworzących niż samej aplikacji biznesowych.

**Transakcje niepodzielne**. Transakcje niepodzielne między wiele mikrousług zwykle nie są możliwe. Wymagania biznesowe muszą Uwzględniaj spójność ostateczną między wiele mikrousług.

**Zwiększenie zapotrzebowania na zasoby globalne** (całkowita pamięć, dyski i zasobów sieciowych dla serwerów lub hostów). W wielu przypadkach podczas zastępowania aplikacji monolitycznej dzięki podejściu mikrousług, ilość początkowej zasobów globalnych wymagane przez nowej aplikacji opartych na mikrousługach będzie większy niż potrzeb oryginalnej aplikacji monolitycznych w zakresie infrastruktury. Jest to spowodowane wyższy stopień szczegółowości i usług rozproszonych wymaga zasobów globalnych. Jednak podane niskie koszty zasobów na ogólny, jak i korzyści, które można skalować tylko określonych obszarów aplikacji w porównaniu do długoterminowego kosztów, gdy ewoluują aplikacji monolitycznych, zwiększenie wykorzystania zasobów jest zwykle dobre rozwiązanie dla dużych długoterminowe aplikacji.

**Problemy związane z bezpośrednia komunikacja klienta z mikrousługą**. Gdy aplikacja jest duży, korzystając z dziesiątek mikrousług, istnieją problemy i ograniczenia Jeśli aplikacja wymaga bezpośredniego komunikacji klienta z mikrousługą. Jednym z problemów jest potencjalna niezgodność między potrzeb klienta i interfejsach API udostępnianych przez każdą z mikrousług. W niektórych przypadkach aplikacja kliencka może być konieczne wielu osobnych żądań do tworzenia interfejsu użytkownika, który może być nieefektywne w Internecie i byłoby to niepraktyczne za pośrednictwem sieci komórkowej. W związku z tym można zminimalizować żądania od aplikacji klienckiej do systemu zaplecza.

Inny problem z bezpośredniej komunikacji klienta z mikrousługą jest, może korzystać z protokołów, które nie są przyjazne dla sieci Web niektórych mikrousług. Jedna usługa może korzystać z protokołu binarne, podczas gdy inna usługa może używać wiadomości protokołu AMQP. Te protokoły nie są przyjaznego dla zapory i najlepiej są używane wewnętrznie. Zazwyczaj aplikacja powinna używać protokołów, takich jak HTTP i Websocket dla komunikacji poza zaporą.

Jeszcze inną wadą w tym bezpośrednie podejściu Usługa klienta jest fakt, że jej trudne do refaktoryzacji kontrakty dla tych mikrousług. Wraz z upływem czasu deweloperzy zechcieć zmienić sposób system jest podzielona na partycje do usług. Na przykład może scalić dwóch usług lub Podziel usługę na co najmniej dwóch usług. Jednak jeśli klienci komunikują się bezpośrednio z usługami, wykonywanie tego rodzaju Refaktoryzacja może przerwać zgodności z aplikacji klienckich.

Jak wspomniano w sekcji architektury podczas projektowania i tworzenia złożonych aplikacji opartego na mikrousługach, można rozważyć użycie wielu szczegółowych bramy interfejsu API, zamiast prostszej metody bezpośrednia komunikacja klienta z mikrousługą.

**Partycjonowanie mikrousługi**. Na koniec niezależnie od tego, które podejścia do architektury mikrousług, inne wyzwanie to podejmowania decyzji o sposobie partycjonowania aplikacja end-to-end na wielu mikrousługi. Jak wspomniano w sekcji architektura przewodnika, istnieje kilka technik i metod, które można wykonać. Zasadniczo należy zidentyfikować obszarów aplikacji, które są całkowicie niezależni od innych obszarów, które mają małej liczbie twardych zależności. W wielu przypadkach jest to wyrównany do partycji usługi w przypadku użycia. Na przykład w naszej aplikacji sklepu e mamy szeregowania usługa, która jest odpowiedzialna za logikę biznesową związane z procesem zamówienia. Możesz także skorzystać z usługi wykazu i usługi koszyka, która implementuje innych funkcji. W idealnym przypadku każdej usługi powinien mieć tylko niewielki zestaw obowiązki. Jest to podobne do pojedynczej odpowiedzialności zasady (SRP) stosowane do klasy, która stwierdza, że klasa powinien mieć tylko jedną z przyczyn można zmienić. Ale w tym przypadku jest o mikrousługach, więc zakres będzie większy niż jednej klasy. Przede wszystkim mikrousługi musi być całkowicie autonomicznego, kompleksowe, włączając odpowiedzialność za swój własny źródła danych.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Zewnętrzne i wewnętrzne wzorce architektury i projektowania

Architektura zewnętrznych jest architekturze mikrousług, składający się przez wiele usług, zgodnie z zasadami opisanymi w architekturze części tego przewodnika. Jednak w zależności od charakteru poszczególne mikrousługi i niezależnie od architektury mikrousługi wysokiego poziomu, możesz wybrać to typowe i czasami wskazane zapewnienie różnych architektur wewnętrznego, każdy na podstawie różnych wzorców dla różnych mikrousługi. Mikrousługi może za pomocą różnych technologii i języków programowania. Na rysunku 6-2 przedstawiono tę różnorodność.

![Różnica między architektury zewnętrznych: mikrousług wzorców bramy interfejsu API, odporne na błędy komunikacji, publikowania/subskrybowania, itp. i architekturę wewnętrzną: opartych na danych/CRUD wzorców DDD, wstrzykiwanie zależności, wiele bibliotek, itp.](./media/image2.png)

**Rysunek 6-2**. Zewnętrzne i wewnętrzne architektury i projektowania

Na przykład w naszym *ramach aplikacji eShopOnContainers* przykładowe wykazu, koszyk oraz użytkownika mikrousług profilu są proste (zasadniczo podsystemów CRUD). W związku z tym ich wewnętrzne architektury i projektu jest bardzo proste. Jednakże może mieć inne mikrousług, takich jak szeregowania mikrousług, co jest bardziej złożona i reprezentuje kolejne zmiany reguł biznesowych o wysokim stopniu złożoności domeny. W takich przypadkach możesz chcieć zaimplementować bardziej zaawansowane wzorców w szczególności mikrousług, takich jak te zdefiniowane przy użyciu metody projektowania opartego na domenach (DDD), ponieważ Radzimy sobie *ramach aplikacji eShopOnContainers* porządkowanie mikrousługi. (Zapoznamy się z tych wzorców DDD w sekcji później wyjaśniający wykonania *ramach aplikacji eShopOnContainers* porządkowanie mikrousługi.)

Kolejnym powodem, dla różnych technologii na mikrousługach, może być charakter poszczególne mikrousługi. Na przykład może być lepiej używać funkcjonalny język programowania, takich jak F\#, a nawet języków R, jeśli są przeznaczone dla sztucznej Inteligencji i usługi machine learning domen, zamiast bardziej obiektowy język programowania takich jak C\#.

Mierzenie jest poszczególne mikrousługi można innej architektury wewnętrznego na podstawie wzorców projektowania. Nie wszystkie mikrousługi powinny zostać wdrożone za pomocą zaawansowanych wzorców DDD, ponieważ, może być nadmiernie inżynierii je. Podobnie złożonych mikrousług z logiką biznesową ciągle zmieniające nie powinny być implementowane jako części operacji CRUD lub można znajdą się z kodem niskiej jakości.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nowy świat: wiele wzorce architektury i mikrousług polyglot

Istnieje wiele wzorców architektonicznych, używany przez oprogramowanie architektów i deweloperów. Poniżej przedstawiono kilka (mieszanie style architektury i wzorce architektury):

- Proste CRUD, jednowarstwowa, pojedynczej warstwy.

- [Tradycyjny N-warstwowe](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Domain-Driven projektu N-warstwowe](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Wyczyść architektury](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jak używać z [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [Polecenia i zapytania podział odpowiedzialności](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektury sterowane zdarzeniami](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Możesz również tworzyć mikrousługi przy użyciu wielu technologii i języków, takich jak interfejsy API sieci Web programu ASP.NET Core, NancyFx, podstawowe biblioteki SignalR platformy ASP.NET (dostępne za pomocą platformy .NET Core 2), F\#, Node.js, Python, Java, C++, języka GoLang i więcej.

Istotne jest to wzorzec nie określonej architektury lub stylu ani żadnych określonej technologii jest odpowiednia dla wszystkich sytuacjach. Rysunek 6-3 przedstawiono niektóre podejścia i technologii (ale nie w określonej kolejności), można używać w różnych mikrousług.

![Wzorzec wielu architektury i mikrousług polyglot oznacza, że można mieszać i zgodne, języków i technologii na potrzeby poszczególne mikrousługi i występuje nadal komunikować się ze sobą.](./media/image3.png)

**Rysunek 6-3**. Wielu wzorce architektury i świata polyglot mikrousług

Jak pokazano na rysunku 6-3, w aplikacjach złożone z wielu mikrousług (ograniczone konteksty w terminologii projektowania opartego na domenie lub po prostu "podsystemy" jako autonomiczny mikrousług), poszczególne mikrousługi można wdrożyć w inny sposób. Każdy może mają wzorzec innej architektury i korzystać z różnych języków i baz danych w zależności od charakteru aplikacji, wymagań biznesowych i priorytety. W niektórych przypadkach może być podobne mikrousług. Ale to nie zazwyczaj tak, ponieważ kontekst granic i wymagania dotyczące każdego podsystemu są zazwyczaj inne.

Na przykład dla prostej aplikacji obsługi operacji CRUD, może nie mieć sensu projektowanie i implementowanie wzorców DDD. Ale podstawowej domeny lub podstawowej działalności, może być konieczne stosowanie wzorów bardziej zaawansowane rozwiązania dla firm złożoności ciągle zmieniające reguły biznesowe.

Szczególnie w przypadku, gdy dotyczą dużych aplikacji poprzez wiele podsystemów, nie ma zastosowania jednego architektura najwyższego poziomu, oparte na wzorcu architektury jednego. Na przykład CQRS nie powinny być stosowane jako architektura najwyższego poziomu dla całej aplikacji, ale mogą być przydatne do określonych usług.

Istnieje bez silver punktora lub wzorzec architektury odpowiednie dla każdego przypadku danego. Nie może mieć "jeden wzorzec architektury by wszystkimi rządzić." W zależności od priorytetów poszczególne mikrousługi możesz wybrać różne podejścia dla poszczególnych usług, zgodnie z opisem w poniższych sekcjach.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](data-driven-crud-microservice.md)
