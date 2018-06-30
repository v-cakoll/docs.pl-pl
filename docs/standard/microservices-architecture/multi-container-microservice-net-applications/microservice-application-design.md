---
title: Projektowanie aplikacji korzystających z mikrousługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie aplikacji korzystających z mikrousługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6cbe4512c8ed89540599d1257046bd080b464165
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105962"
---
# <a name="designing-a-microservice-oriented-application"></a>Projektowanie aplikacji korzystających z mikrousługi

W tej sekcji koncentruje się na opracowanie aplikacji hipotetyczny przedsiębiorstwa po stronie serwera.

## <a name="application-specifications"></a>Specyfikacje aplikacji

Hipotetyczny aplikacji obsługuje żądania wykonywania logiki biznesowej, uzyskiwanie dostępu do bazy danych, a następnie zwracanie odpowiedzi HTML, JSON lub XML. Firma Microsoft dowiesz się, że aplikacja musi obsługiwać wielu klientów, takich jak przeglądarek klasycznych uruchomione aplikacje jednostronicowe (źródła), aplikacje sieci web tradycyjne aplikacje sieci web urządzeń przenośnych i natywnych aplikacji mobilnych. Aplikacja może narazić również stronom trzecim korzystać z interfejsu API. Należy również na możliwości integracji jego mikrousług lub aplikacji zewnętrznych asynchronicznie, dzięki czemu podejście pomoże odporności mikrousług w przypadku awarii częściowej.

Aplikacja będzie składać się z tych typów składników:

-   Składniki prezentacji. Te są zobowiązani do obsługi interfejsu użytkownika i korzystanie z usługi zdalnej.

-   Domeny lub logikę biznesową. Jest to logika domeny aplikacji.

-   Logika dostępu do bazy danych. Ten krok składa się odpowiedzialny za dostęp do bazy danych (SQL lub NoSQL) składników dostępu do danych.

-   Logika integracji aplikacji. W tym kanału wiadomości oparte głównie na brokerzy wiadomości.

Aplikacja będzie wymagać wysoką skalowalność, umożliwiając podsystemy pionowego do skalowania w poziomie autonomicznie, ponieważ pewne podsystemy będzie wymagać większą skalowalność niż inne.

Aplikacja musi mieć możliwość można wdrożyć w wielu środowiskach infrastruktury (wiele chmur publicznych i lokalnymi) i w idealnym przypadku powinien być między platformami, można łatwo przenieść z systemem Linux w systemie Windows (lub odwrotnie).

## <a name="development-team-context"></a>Programowanie kontekstu zespołowego

Przykładowa firma Microsoft również następujące kwestie dotyczące procesu tworzenia aplikacji:

-   Masz kilka zespołów deweloperów koncentrujących się na różnych firm obszarów aplikacji.

-   Nowych członków zespołu mogą stać się produktywności szybko, a aplikacja musi być łatwe do zrozumienia i modyfikować.

-   Aplikacja będzie mieć długoterminowego rozwoju i kiedykolwiek zmiana reguł biznesowych.

-   Należy dużą długoterminowej łatwość utrzymania, które oznaczają elastyczność podczas wdrażania nowych zmian w przyszłości podczas możliwość zaktualizować wiele podsystemów minimalny wpływ na inne podsystemy.

-   Chcesz praktyki ciągłej integracji i ciągłego wdrażania aplikacji.

-   Chcesz korzystać z nowych technologii (struktury programowania języków, itp.) podczas rozwijającymi aplikacji. Czy chcesz wprowadzić pełnej migracji aplikacji, podczas przenoszenia do nowych technologii, ponieważ, która może spowodować wysokich kosztów i będzie mieć wpływ przewidywalności i stabilności aplikacji.

## <a name="choosing-an-architecture"></a>Wybieranie architektury

Co należy architektura wdrożenia aplikacji Wymagania dotyczące aplikacji, wraz z kontekstu programowanie silnie sugeruje, że przez decomposing na autonomicznych podsystemy w formie brać mikrousług oraz kontenerów, gdzie mikrousługi należy projektowania aplikacji jest kontenerem.

W takie podejście każdej usługi (kontenera) implementuje zestaw funkcji spójności i ściśle powiązane. Na przykład aplikacja może obejmować usług, takich jak usługi katalogu, kolejność usługi, Usługa koszyka, usługi profilu użytkownika, itp.

Mikrousług komunikacji przy użyciu protokołów, takich jak HTTP (REST), ale również asynchronicznie (na przykład za pomocą protokołu AMQP) Jeśli to możliwe, szczególnie gdy propagowanie aktualizuje zdarzeń integracji.

Mikrousług opracowany i jest wdrożona jako kontenery niezależnie od siebie. Oznacza to, że zespół deweloperów może być projektowania i wdrażania niektórych mikrousługi bez wpływania na inne podsystemy.

Każdy mikrousługi ma własną bazę danych, dzięki któremu można całkowicie całkowicie niezależna od innych mikrousług. W razie potrzeby spójności między bazami danych z różnych mikrousług uzyskuje się za pomocą zdarzeń integracji na poziomie aplikacji (przez magistralę zdarzeń logicznego), jako obsługiwane w poleceniu i podział odpowiedzialności kwerendy (CQRS). Z tego powodu, ograniczenia firm musi obejmować spójność ostateczna między wieloma mikrousług oraz powiązane baz danych.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: odwołanie aplikacji dla platformy .NET Core i mikrousług wdrażane za pomocą kontenerów

Dzięki czemu można skupić się na architekturę i technologie zamiast analiza biznesowa hypothetic domeny, która może być niemożliwe, wybraliśmy domeny dobrze znanych firm — mianowicie aplikacją uproszczony handlu elektronicznego (e Sklep) prezentuje katalog produkty, przyjmuje zamówień od klientów, sprawdza spisu i wykonuje funkcje innych firm. Ten kod źródłowy aplikacji opartej na kontenera jest dostępna w [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) repozytorium GitHub.

Aplikacja składa się z wielu podsystemami, łącznie z kilku magazynu interfejsu użytkownika frontonu zakończenia (natywnych aplikacji mobilnej i aplikacji sieci Web), wraz z mikrousług zaplecza i kontenerami dla wszystkich wymaganych operacji po stronie serwera. Architektura aplikacji odwołania przedstawiono na rysunku 8-1.

![](./media/image1.png)

**Rysunek 8-1**. EShopOnContainers zawierają odwołania do aplikacji, przedstawiający bezpośrednia komunikacja klient mikrousługi i magistrali zdarzeń

**Środowisko macierzyste**. W rysunek 8-1, zobacz kilka kontenerów wdrażana w obrębie jednego hosta Docker. Podczas wdrażania pojedynczego hosta Docker z rozwiązaniem docker z wyniesie przypadku-tworzą zapasowej polecenia. Jednak w przypadku przy użyciu programu orchestrator lub klastra kontenera, każdego kontenera mogą być wykonywane w różnych hostach (węzeł) i węzły mogą być wykonywane dowolną liczbę kontenerów, jak firma Microsoft opisem w sekcji architektury.

**Architektura komunikacji**. Aplikacja eShopOnContainers używa dwóch typów komunikacji, w zależności od rodzaju funkcjonalności akcji (zapytań i aktualizacji oraz transakcje):

-   Bezpośrednia komunikacja klient mikrousługi. Służy to zapytań i akceptując aktualizacji lub polecenia transakcyjnego z aplikacji klienta.

-   Oparty na zdarzeniach komunikacji asynchronicznej. Dzieje się tak za pośrednictwem magistrali zdarzeń propagacji aktualizacji do między mikrousług lub zintegrować z aplikacjami zewnętrznymi. W przypadku innych technologii infrastruktury brokera obsługi komunikatów, takie jak RabbitMQ lub przy użyciu wyższego poziomu magistrali usług, takich jak usługi Azure Service Bus, NServiceBus, MassTransit lub Brighter można zaimplementować magistrali zdarzeń.

Aplikacja jest wdrażana jako zestaw mikrousług w formie kontenerów. Aplikacje klienta może komunikować się z tych kontenerach także komunikacji między mikrousług. Jak wspomniano, architektura bezpośrednia komunikacja klient mikrousługi, co oznacza, że aplikacja kliencka będą mogą wysyłać żądania do każdego mikrousług bezpośrednio używa tej architektury początkowej. Każdy mikrousługi ma publiczny punkt końcowy, takich jak https://servicename.applicationname.companyname. W razie potrzeby każdego mikrousługi można użyć różnych portów TCP. W środowisku produkcyjnym, mapującej adres URL do modułu równoważenia obciążenia mikrousług, który rozdzielaj żądania między wystąpień dostępne mikrousługi.

**Ważna uwaga na vs bramy interfejsu API. Bezpośrednia komunikacja w eShopOnContainers.** Zgodnie z objaśnieniem w architektury części tego przewodnika, architektura bezpośrednia komunikacja klient mikrousługi mogą mieć wady podczas tworzenia dużych i złożonych mikrousługi aplikacji sieci. Ale może być dobrym dla małych aplikacji, takie jak w eShopOnContainers aplikacji, której celem jest skupić się na pobieranie prostsze uruchomiła aplikację na podstawie kontenera Docker i nie chcemy, aby utworzyć pojedynczą wbudowanymi bramą interfejsu API, która może wpłynąć na Autonomia programowanie mikrousług.

Ale, jeśli zamierzasz projektowania dużych aplikacji na podstawie mikrousługi dzięki mikrousług, zdecydowanie zaleca się wziąć pod uwagę wzorzec bramy interfejsu API, możemy opisane w sekcji architektury.
Tej architektury decyzji mogą być refaktoryzowane po pomyśleć o aplikacje gotowe do produkcji i fasad wprowadzone specjalnie dla klientów zdalnych. O wiele niestandardowych bram interfejsu API w zależności od aplikacji klienckich obudowie zapewniają korzyści w zakresie różnych danych agregacji dla aplikacji klienckich oraz można ukryć mikrousług wewnętrzny lub interfejsów API do aplikacji klienckich i autoryzacji w tym pojedynczej warstwie. 

Jednak i jak wspomniano należy wziąć pod względem duży i wbudowanymi bram interfejsu API, który może kill Autonomia programowanie z mikrousług.

### <a name="data-sovereignty-per-microservice"></a>Suwerenności danych na mikrousługi

W przykładowej aplikacji każda mikrousługi właścicielem własną bazę danych lub źródła danych, a każda baza danych lub źródło danych jest wdrożona jako innego kontenera. Tej decyzji projektowej, została wprowadzona tylko do ułatwiają deweloperom Pobierz kod z serwisu GitHub, sklonować go i otwórz go w programie Visual Studio lub Visual Studio Code. Lub też jego ułatwia skompilować niestandardowych obrazów Docker przy użyciu interfejsu wiersza polecenia platformy .NET Core i interfejsu wiersza polecenia Docker, a następnie wdrożyć i uruchamiać je w środowisku projektowania rozwiązania Docker. W obu przypadkach za pomocą kontenerów danych źródeł umożliwia deweloperom tworzenie i wdrażanie w ciągu kilku minut bez konieczności obsługi administracyjnej zewnętrznej bazy danych lub inne źródła danych z twardych zależne od infrastruktury (chmurze lub lokalnie).

W środowisku produkcyjnym prawdziwe, wysokiej dostępności i skalowalności baz danych powinny być oparte na serwerach bazy danych w chmurze lub lokalnie, ale nie w kontenerach.

W związku z tym jednostki wdrożenia mikrousług (a nawet w przypadku baz danych w tej aplikacji) są kontenerami Docker i aplikacja referencyjna jest mikrousług zasady wdrażania aplikacji usługi kontenera.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **eShopOnContainers GitHub repo. Kod źródłowy aplikacji odwołania**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Korzyści wynikające z rozwiązaniem opartym na mikrousługi

Takie rozwiązanie mikrousługi na podstawie ma wiele korzyści:

**Każdy mikrousługi jest stosunkowo mały — łatwe zarządzanie i rozwijać**. W szczególności:

-   To proste dla deweloperów do zrozumienia i szybko rozpocząć pracę z dobrą wydajność.

-   Kontenery Uruchom szybkie, która zwiększa wydajność deweloperów.

-   IDE, takimi jak Visual Studio może ładować mniejsze projekty szybki, co produktywności deweloperów.

-   Każdy mikrousługi można zaprojektowane, opracowany i wdrożyć niezależnie od innych mikrousług, co zapewnia elastyczność, ponieważ ułatwia wdrażanie nowych wersji mikrousług często.

**Istnieje możliwość skalowania w poziomie poszczególne obszary aplikacji**. Na przykład usługi wykazu lub koszyka może być konieczne można skalować w poziomie, ale nie zamawiania. Infrastruktura mikrousług będzie bardziej efektywnego względem zasobów używanych w trakcie skalowania byłoby wbudowanymi architektury.

**Można podzielić projektach między kilka zespołów**. Zespół deweloperów pojedynczego można należeć do każdej usługi. Każdego zespołu można zarządzać, tworzenie, wdrażanie i skalowanie usługi niezależnie od reszty zespołów.

**Więcej odizolowanych problemów**. Jeśli występuje problem w jednej usłudze, początkowo dotyczy to tylko tej usługi (chyba że niewłaściwy projekt jest używana, bezpośrednie zależności między mikrousług) i innych usług mogą w dalszym ciągu obsługuje żądania. Z kolei jeden nieprawidłowo działający składnik w architekturze wbudowanymi wdrożenia można obniżyć całego systemu, szczególnie w przypadku, gdy obejmuje zasoby, takie jak przeciek pamięci. Ponadto po rozwiązaniu problemu w mikrousługi bez wpływu na pozostałe aplikacji można wdrożyć tylko odpowiednich mikrousługi.

**Korzystając z najnowszych technologii**. Ponieważ można rozpocząć tworzenie usług niezależnie i uruchamiać je jednocześnie (dzięki użyciu kontenerów i .NET Core), można uruchomić przy użyciu najnowszych technologii i platform rzetelny zamiast jest zablokowany na starszych stosu lub framework dla całej aplikacja.

## <a name="downsides-of-a-microservice-based-solution"></a>Downsides mikrousługi rozwiązania

Takie rozwiązanie mikrousługi na podstawie ma również kilka wad:

**Aplikację rozproszoną**. Dystrybucja aplikacji dodaje złożoności dla deweloperów, podczas projektowania i tworzenia usług. Na przykład deweloperzy musi implementować różnych komunikacji przy użyciu protokołów, takich jak HTTP lub AMPQ, który dodaje złożoność do testowania i obsługi wyjątków. Dodaje również czas oczekiwania do systemu.

**Złożoność wdrożenia**. Aplikacja, która ma dziesiątki mikrousług typów i potrzeby wysoką skalowalność (musi to być może tworzyć wiele wystąpień poszczególnych usług i równoważenie tych usług na wielu hostach) oznacza, że wysokiego stopnia złożoności wdrażania dla operacji IT i zarządzania. Jeśli nie używasz zorientowane na mikrousługi infrastruktury (np. programu orchestrator i harmonogram), czy dodatkową złożoność może wymagać dużo więcej programistycznych od samej aplikacji biznesowych.

**Transakcje Atomic**. Niepodzielne transakcji między wieloma mikrousług zazwyczaj nie są możliwe. Wymagania biznesowe muszą obejmować spójność ostateczna między wieloma mikrousług.

**Zwiększone zapotrzebowanie na zasoby globalne** (całkowita liczba pamięci, dysków i zasobów sieciowych dla serwerów lub hostów). W wielu przypadkach podczas zastępowania aplikacji wbudowanymi z podejście mikrousług ilość globalne zasoby wymagane przez nową aplikację na podstawie mikrousługi będzie większy niż potrzeb infrastruktury wbudowanymi oryginalnej aplikacji. Jest to spowodowane wyższy stopień szczegółowości i usług rozproszonych wymaga zasobów globalnych. Jednak podane niskich kosztów zasobów w ogólne i korzyści o możliwość skalowania w poziomie tylko niektórych obszarach aplikacji w porównaniu do długoterminowego kosztów, gdy zmieniających się wbudowanymi aplikacjami, zwiększenie wykorzystania zasobów jest zwykle dobre rozwiązanie dla dużych, długoterminowe aplikacji.

**Problemy z komunikacją bezpośredniego client‑to‑microservice**. Gdy aplikacja jest duży, dzięki mikrousług, istnieją problemy i ograniczenia Jeśli aplikacja wymaga bezpośredniej komunikacji klient mikrousługi. Jednym z problemów jest potencjalna niezgodność pomiędzy potrzeb klienta i interfejsach API udostępnianych przez każdą mikrousług. W niektórych przypadkach aplikacja kliencka konieczne może być wiele oddzielnych żądań utworzenie interfejsu użytkownika, który może być mało wydajne za pośrednictwem Internetu, a będzie niepraktyczne za pośrednictwem sieci komórkowej. W związku z tym można zminimalizować żądań od aplikacji klienta do sieci wewnętrznej.

Inny problem z bezpośredniej komunikacji klient mikrousługi jest może korzystać z protokołów, które nie są przyjaznych dla sieci Web niektórych mikrousług. Jedna usługa może używać protokołu binarnego, podczas innej usługi mogą używać protokołu AMQP wiadomości. Te protokoły nie są firewall‑friendly i najlepiej jest używana wewnętrznie. Zazwyczaj aplikacji należy używać protokołów, takich jak HTTP i technologia WebSockets komunikacji poza zaporą.

Jeszcze inną wadą tego podejścia bezpośredniego client‑to‑service przy jest fakt, że jej trudno Refaktoryzuj kontrakty dla tych mikrousług. Wraz z upływem czasu deweloperzy mogą chcesz zmienić, jak system jest podzielona na partycje do usług. Na przykład może scalić dwóch usług lub Podziel usługi na dwóch lub więcej usług. Jednak jeśli klienci komunikują się bezpośrednio z usługami, wykonywanie tego rodzaju refaktoryzacji mogą być dzielone zgodności z aplikacjami klienta.

Jak wspomniano w sekcji architektura podczas projektowania i tworzenia złożonych aplikacji oparte na mikrousług, można rozważyć użycie wielu szczegółowych bram interfejsu API, zamiast bezpośredniego client‑to‑microservice prostsze komunikacji.

**Partycjonowanie mikrousług**. Na koniec niezależnie od tego, które należy wykonać w przypadku architektury mikrousługi rozwiązanie, inne wyzwanie jest podjęcie decyzji o sposobie partycji aplikacji na trasie do wielu mikrousług. Jak wspomniano w sekcji architektura przewodnika, istnieje kilka technik i metod, które można wykonać. Zasadniczo trzeba będzie zidentyfikować obszarów aplikacji, które są całkowicie niezależna od innych obszarów, które mają małej liczbie twardych zależności. W wielu przypadkach jest to wyrównany do partycji usług w przypadku użycia. Na przykład w naszej aplikacji sklepu e mamy porządkowania usługa, która jest odpowiedzialna za logiki biznesowej związane z procesem kolejności. Mamy także usługi wykazu i koszyka że wdrożenia innych funkcji. Najlepiej każda usługa ma niewielki zestaw obowiązki. Efekt jest podobny do jednej zasady odpowiedzialności (SRP) stosowany do klasy, które stwierdza, że klasa powinien mieć tylko jedną z przyczyn można zmienić. Ale w takim przypadku jest o mikrousług, więc zakres będzie większy niż jednej klasy. Najbardziej, mikrousługi musi być całkowicie autonomicznych, kompleksowe, włączając odpowiedzialność za własnych źródeł danych.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Zewnętrzne i wewnętrzne wzorce architektury i projektu

Architektura zewnętrzne jest architektury mikrousługi składane przez wielu usług, następujące zasady opisane w sekcji architektura tego przewodnika. Jednak w zależności od charakteru każdego mikrousługi i niezależnie od architektury mikrousługi wysokiego poziomu, możesz wybrać jest typowe i czasami wskazane mają różne architektury wewnętrznego, każdy na podstawie różnych wzorców dla różnych mikrousług. Mikrousług może za pomocą różnych technologii i języków programowania. Rysunek 8-2 przedstawia Ta różnorodność.

![](./media/image2.png)

**Rysunek 8-2**. Zewnętrzne i wewnętrzne architektury i projektu

Na przykład w naszym *eShopOnContainers* mikrousług profilu próbki katalogu, koszyka oraz użytkowników są proste (zasadniczo podsystemów CRUD). W związku z tym ich wewnętrzny architektury i projektu jest proste. Jednak może mieć inne mikrousług, takich jak mikrousługi porządkowania, która jest bardziej złożone i reprezentuje kiedykolwiek zmiana reguł biznesowych o wysokim stopniu złożoności domeny. W takich przypadkach można wdrożyć bardziej zaawansowane wzorców w szczególności mikrousługi, takich jak te zdefiniowane z podejść projektowanie oparte na domenie (DDD) zgodnie z tym *eShopOnContainers* kolejności mikrousługi. (Zapoznamy się z tych wzorców DDD w sekcji później wyjaśniający wykonania *eShopOnContainers* porządkowanie mikrousługi.)

Inną przyczyną różne technologie na mikrousługi może być rodzaju każdego mikrousługi. Na przykład może być lepiej jest użyć funkcjonalny język programowania, takich jak F\#, lub nawet języka, takich jak R, jeśli ma być przeznaczona dla AI i domen, zamiast więcej zorientowany obiektowo język programowania takich jak C uczenia maszynowego\#.

Mierzenie jest każdego mikrousługi można innej architektury wewnętrznego, na podstawie wzorców projektowania. Nie wszystkie mikrousług powinny być implementowane przy użyciu zaawansowanych DDD wzorców, ponieważ, który może być nadmiernie inżynierii je. Podobnie mikrousług złożonych z kiedykolwiek zmiana logiki biznesowej nie powinny być implementowane jako składniki CRUD lub zakończeniem o niskiej jakości kodu.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nowe world: wiele architektury wzorców i mikrousług polyglot

Istnieje wiele wzorców architektury używanych przez oprogramowanie architektów i deweloperów. Poniżej przedstawiono kilka (mieszanie style architektury i architektura wzorce):

-   Proste CRUD, jednowarstwową, pojedynczej warstwy.

-   [Tradycyjny N-warstwowych](https://msdn.microsoft.com/library/ee658109.aspx#Layers).

-   [Domeny oparte na projekt N-warstwowych](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Wyczyść architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jak używać z [eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [Poleceń i zapytań podział odpowiedzialności](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Architektura sterowane zdarzeniami](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Można również tworzyć mikrousług z wielu technologii i języków, takich jak interfejsów API platformy ASP.NET Core sieci Web, NancyFx, ASP.NET SignalR Core (dostępne z .NET Core 2), F\#, Node.js, Python, Java, C++, GoLang i inne.

Istotne jest nie wzorzec architektury określonego lub styl ani innych technologii określonego nieprawidłowość odpowiednie dla wszystkich sytuacji. Rysunek 8-3 przedstawiono niektóre podejścia i technologii (ale nie w określonej kolejności) które mogą być używane w różnych mikrousług.

![](./media/image3.png)

**Rysunek 8-3**. Wzorce wielu architektury i mikrousług polyglot świata

Pokazane na rysunku 8-3, w aplikacjach składa się z wielu mikrousług (ograniczone kontekstów w terminologii projektowanie oparte na domenie lub po prostu "podsystemy" jako autonomiczny mikrousług), każdy mikrousługi może zastosować w inny sposób. Każdy może mieć wzorzec innej architektury i używać różnych języków i baz danych w zależności od charakteru aplikacji, wymagań biznesowych i priorytety. W niektórych przypadkach może być podobne mikrousług. Ale nie jest to zazwyczaj przypadek, ponieważ granicy kontekstu i wymagania dotyczące każdego podsystemu są inne niż zwykle.

Na przykład dla prostej aplikacji obsługi CRUD, może nie mieć warto projektowanie i implementowanie DDD wzorców. Jednak domeny rdzeni lub core biznesowych, może być konieczne zastosowanie bardziej zaawansowanych wzorców w celu rozwiązania biznesowe złożoności kiedykolwiek zmiana reguł biznesowych.

Szczególnie, gdy zaradzenia dużych aplikacji składane przez wiele systemów podrzędnego, nie należy stosować jedną architekturę najwyższego poziomu na podstawie wzorca jedną architekturę. Na przykład CQRS nie powinny być stosowane jako architektura najwyższego poziomu dla całej aplikacji, ale mogą być przydatne do określonych usług.

Brak bez srebrny punktora lub wzorzec architektury prawo dla każdego przypadku danego. Nie można umieścić "jeden wzorzec architektury do reguły je wszystkie." W zależności od priorytetów każdego mikrousługi należy wybrać różne podejścia dla poszczególnych usług, zgodnie z objaśnieniem w poniższych sekcjach.


>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](data-driven-crud-microservice.md)
