---
title: Wzorzec bramy interfejsu API w porównaniu z bezpośrednią komunikacją klient-do-mikrousług
description: Zapoznaj się z różnicami i wykorzystaniem wzorca usługi API Gateway oraz bezpośredniej komunikacji klient-do-mikrousług.
ms.date: 01/07/2019
ms.openlocfilehash: 6b42650b2dbce093f12fe02b1605c95076dc8592
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522946"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Wzorzec bramy interfejsu API w porównaniu z bezpośrednią komunikacją klient-do-mikrousług

W architekturze mikrousług każda mikrousługa udostępnia zestaw (zazwyczaj) szczegółowych punktów końcowych. Ten fakt może mieć wpływ na komunikację między klientem i mikrousługą, zgodnie z opisem w tej sekcji.

## <a name="direct-client-to-microservice-communication"></a>Bezpośrednia komunikacja klient-usługa

Możliwym podejściem jest użycie bezpośredniej architektury komunikacji klient-mikrousług. W tym podejściu aplikacja kliencka może wprowadzać żądania bezpośrednio do niektórych mikrousług, jak pokazano na rysunku 4-12.

![Diagram przedstawiający architekturę komunikacji klient-mikrousług.](./media/direct-client-to-microservice-communication.png)

**Rysunek 4-12**. Korzystanie z bezpośredniej architektury komunikacji klient-mikrousług

W tym podejściu każda mikrousługa ma publiczny punkt końcowy, czasami z innym portem TCP dla każdej mikrousługi. Przykładem adresu URL dla określonej usługi może być następujący adres URL na platformie Azure:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

W środowisku produkcyjnym opartym na klastrze ten adres URL będzie mapowany do modułu równoważenia obciążenia używanego w klastrze, co z kolei dystrybuuje żądania dla mikrousług. W środowiskach produkcyjnych można korzystać z kontrolera dostarczania aplikacji (ADC), takiego jak [platforma Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) między mikrousługami i Internetem. Działa to jako przezroczysta warstwa, która nie tylko realizuje Równoważenie obciążenia, ale zabezpiecza usługi przez umożliwienie zakończenia protokołu SSL. Poprawia to obciążenie hostów przez Przeciążenie zakończenia protokołu SSL intensywnie korzystających z procesora CPU i innych obowiązków routingu do Application Gateway platformy Azure. W każdym przypadku moduł równoważenia obciążenia i ADC jest przezroczysty z punktu widzenia architektury aplikacji logicznej.

Bezpośrednia architektura komunikacji między klientem a mikrousługą może być wystarczająca dla małych aplikacji opartych na mikrousługach, zwłaszcza jeśli aplikacja kliencka jest aplikacją sieci Web po stronie serwera, taką jak aplikacja ASP.NET MVC. Jednak podczas kompilowania dużych i złożonych aplikacji opartych na mikrousługach (na przykład w przypadku obsługi dziesiątek typów mikrousług), a zwłaszcza gdy aplikacje klienckie to zdalne aplikacje mobilne lub aplikacje sieci Web SPA, takie podejście nadaje kilka problemów.

Podczas tworzenia dużej aplikacji na podstawie mikrousług należy wziąć pod uwagę następujące zagadnienia:

- *Jak aplikacje klienckie zmniejszają liczbę żądań do zaplecza i zmniejszają komunikację w wielu mikrousługach?*

Korzystanie z wielu mikrousług w celu utworzenia jednego ekranu interfejsu użytkownika powoduje zwiększenie liczby rund w Internecie. Zwiększa to opóźnienia i złożoność po stronie interfejsu użytkownika. Najlepiej, gdy odpowiedzi powinny być efektywnie agregowane po stronie serwera. Zmniejsza to opóźnienia, ponieważ wiele fragmentów danych jest ponownie równoległych, a niektóre interfejsu użytkownika mogą wyświetlać dane zaraz po ich przygotowaniu.

- *Jak można obsłużyć problemy z przecinaniem, takie jak autoryzacja, przekształcenia danych i dynamiczne wysyłanie żądań?*

Zaimplementowanie zagadnień związanych z zabezpieczeniami i rozwojem, takich jak zabezpieczenia i autoryzacja dla każdej mikrousługi, może wymagać znacznego nakładu pracy. Możliwym podejściem jest posiadanie tych usług na hoście platformy Docker lub w klastrze wewnętrznym, aby ograniczyć bezpośredni dostęp do nich z zewnątrz i aby zaimplementować te zagadnienia związane z wycinaniem w scentralizowanym miejscu, takim jak Brama interfejsu API.

- *Jak aplikacje klienckie komunikują się z usługami korzystającymi z nieprzyjaznych dla Internetu protokołów?*

Protokoły używane na stronie serwera (takie jak AMQP lub protokoły binarne) nie są zwykle obsługiwane w aplikacjach klienckich. W związku z tym żądania muszą być wykonywane za pośrednictwem protokołów, takich jak HTTP/HTTPS, a następnie tłumaczone na inne protokoły. Podejście typu *man-in-the-Middle* może pomóc w takiej sytuacji.

- *Jak można kształtować elewację szczególnie utworzoną dla aplikacji mobilnych?*

Interfejs API wielu mikrousług może być niewłaściwie zaprojektowany dla potrzeb różnych aplikacji klienckich. Na przykład wymagania aplikacji mobilnej mogą być inne niż potrzeby aplikacji sieci Web. W przypadku aplikacji mobilnych może być konieczne jeszcze bardziej zoptymalizowanie, aby odpowiedzi na dane mogły być bardziej wydajne. Można to zrobić poprzez agregowanie danych z wielu mikrousług i zwracanie jednego zestawu danych, a czasem eliminuje wszelkie dane w odpowiedzi, które nie są potrzebne w przypadku aplikacji mobilnej. Oczywiście można skompresować te dane. Ponownie elewacja lub interfejs API w ramach aplikacji mobilnej i mikrousług może być wygodny dla tego scenariusza.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Dlaczego warto rozważyć użycie bram interfejsu API zamiast bezpośredniej komunikacji klient-usługa

W architekturze mikrousług aplikacje klienckie zazwyczaj wymagają użycia funkcji z więcej niż jednej mikrousług. Jeśli zużycie jest wykonywane bezpośrednio, klient musi obsłużyć wiele wywołań punktów końcowych mikrousług. Co się stanie po rozwojem i wprowadzeniu nowych mikrousług lub zaktualizowaniu istniejących mikrousług? Jeśli aplikacja ma wiele mikrousług, obsługa tak wielu punktów końcowych z aplikacji klienckich może być okropnej. Ze względu na to, że aplikacja kliencka będzie dołączona do tych wewnętrznych punktów końcowych, rozwój mikrousług w przyszłości może mieć duży wpływ na aplikacje klienckie.

W związku z tym, że posiadanie poziomu pośredniego lub warstwy pośredni (brama) może być bardzo wygodne w przypadku aplikacji opartych na mikrousługach. Jeśli nie masz bram interfejsu API, aplikacje klienckie muszą wysyłać żądania bezpośrednio do mikrousług i zgłaszać problemy, takie jak następujące problemy:

- **Sprzęganie**: bez wzorca interfejsu API, aplikacje klienckie są połączone z mikrousługami wewnętrznymi. Aplikacje klienckie muszą wiedzieć, jak wiele obszarów aplikacji jest rozłożonych na mikrousługi. Podczas rozwoju i refaktoryzacji wewnętrznych mikrousług te działania mają wpływ na niepowodzenie konserwacji, ponieważ powodują istotne zmiany w aplikacjach klienckich z powodu bezpośredniego odniesienia do mikrousług wewnętrznych z aplikacji klienckich. Aplikacje klienckie należy często aktualizować, dzięki czemu rozwiązanie jest trudniejsze do roztworzenia.

- **Zbyt wiele rund**: pojedyncza strona/ekran w aplikacji klienckiej może wymagać kilku wywołań do wielu usług. Może to prowadzić do wielu operacji sieciowych między klientem a serwerem, co zwiększa znaczne opóźnienia. Agregacja obsługiwana na poziomie pośrednim może poprawić wydajność i środowisko użytkownika dla aplikacji klienckiej.

- **Problemy z zabezpieczeniami**: bez bramy wszystkie mikrousługi muszą być narażone na "zewnętrzny świat", co sprawia, że obszar ataku jest większy niż w przypadku ukrycia wewnętrznych mikrousług, które nie są bezpośrednio używane przez aplikacje klienckie. Im mniejsza jest powierzchnia narażona na ataki, tym bezpieczniejsze może być aplikacja.

- **Zagadnienia dotyczące krzyżowego wycinania**: Każda publicznie publikowana mikrousługa musi obsługiwać takie kwestie, jak autoryzacja, SSL itp. W wielu sytuacjach te problemy mogą być obsługiwane w jednej warstwie, dzięki czemu wewnętrzne mikrousługi są uproszczone.

## <a name="what-is-the-api-gateway-pattern"></a>Co to jest wzorzec bramy interfejsu API?

Podczas projektowania i kompilowania dużych lub złożonych aplikacji opartych na mikrousługach z wieloma aplikacjami klienckimi dobrym podejściem do rozważenia może być [brama interfejsu API](https://microservices.io/patterns/apigateway.html). Jest to usługa, która zapewnia pojedynczy punkt wejścia dla niektórych grup mikrousług. Jest to podobne do [wzorca zaufana fasady](https://en.wikipedia.org/wiki/Facade_pattern) z projektu zorientowanego obiektowo, ale w tym przypadku jest częścią systemu rozproszonego. Wzorzec bramy interfejsu API jest również czasami znany jako "zaplecze dla frontonu" ([BFF](https://samnewman.io/patterns/architectural/bff/)), ponieważ można go skompilować przy użyciu aplikacji klienta.

W związku z tym Brama interfejsu API znajduje się między aplikacjami klienta i mikrousługami. Działa jako zwrotny serwer proxy, żądania routingu od klientów do usług. Może również udostępniać dodatkowe funkcje, takie jak uwierzytelnianie, kończenie połączeń SSL i pamięci podręcznej.

Rysunek 4-13 pokazuje, jak niestandardowa Brama interfejsu API może pasować do uproszczonej architektury opartej na mikrousługach i zaledwie kilku mikrousług.

![Diagram przedstawiający bramę interfejsu API zaimplementowaną jako usługa niestandardowa.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/custom-service-api-gateway.png)

**Rysunek 4-13**. Korzystanie z bramy interfejsu API wdrożonej jako usługa niestandardowa

Aplikacje nawiązują połączenie z jednym punktem końcowym, który jest skonfigurowany do przesyłania żądań do poszczególnych mikrousług. W tym przykładzie Brama interfejsu API zostanie zaimplementowana jako niestandardowa ASP.NET Core usługi WebHost działającej jako kontener.

Ważne jest, aby podkreślić, że na tym diagramie jest używana jedna niestandardowa Usługa bramy API z wieloma aplikacjami klienckimi. Ten fakt może być ważnym ryzykiem, ponieważ usługa bramy interfejsu API będzie rośnie i rozwijana na podstawie wielu różnych wymagań aplikacji klienckich. Na koniec będzie bloated z powodu tych różnych potrzeb i efektywnie może być całkiem podobny do monolitycznej aplikacji lub monolitycznej usługi. Z tego względu zdecydowanie zaleca się poddzielenie bramy interfejsu API w wielu usługach lub wielu mniejszych bramach interfejsu API, a na przykład jeden typ czynnika na aplikację klienta.

Należy zachować ostrożność podczas implementowania wzorca interfejsu API. Zwykle nie jest dobrym pomysłem na agregowanie wszystkich mikrousług wewnętrznych aplikacji przez pojedynczą bramę interfejsu API. Jeśli tak, działa jako agregator monolityczny lub Koordynator i narusza autonomię mikrousług przez Sprzęganie wszystkich mikrousług.

W związku z tym bramy interfejsu API powinny być segregowane na podstawie granic firmy i aplikacji klienckich, a nie działają jako pojedyncze agregatory dla wszystkich mikrousług wewnętrznych.

Podczas dzielenia warstwy bramy interfejsu API na wiele bram interfejsu API, jeśli aplikacja ma wiele aplikacji klienckich, które mogą być głównym obszarem wystawcy podczas identyfikowania wielu typów bram interfejsu API, dzięki czemu można mieć inną fasadę dla potrzeb każdej aplikacji klienckiej. Ten przypadek jest wzorcem o nazwie "zaplecze dla frontonu" ([BFF](https://samnewman.io/patterns/architectural/bff/)), gdzie każda Brama interfejsu API może zapewnić inny interfejs API dostosowany do każdego typu aplikacji klienta, prawdopodobnie nawet w oparciu o współczynnik formularza klienta przez zaimplementowanie określonego kodu karty, który jest zgodny z wywołaniami wiele mikrousług wewnętrznych, jak pokazano na poniższej ilustracji:

![Diagram przedstawiający wiele niestandardowych bram interfejsu API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/multiple-custom-api-gateways.png)

**Rysunek 4 — 13.1**. Używanie wielu niestandardowych bram interfejsu API

Rysunek 4.13.1 zawiera bramy interfejsu API, które są segregowane według typu klienta; jeden dla klientów mobilnych i jeden dla klientów sieci Web. Tradycyjna aplikacja internetowa łączy się z mikrousługą MVC korzystającą z bramy internetowego interfejsu API. W przykładzie przedstawiono uproszczoną architekturę z wieloma szczegółowymi bramami interfejsu API. W takim przypadku granice zidentyfikowane dla każdej bramy interfejsu API są oparte wyłącznie na wzorcu zaplecza dla frontonu ([BFF](https://samnewman.io/patterns/architectural/bff/)), dlatego są oparte tylko na interfejsie API, który jest wymagany dla aplikacji klienckiej. Jednak w większych aplikacjach należy również utworzyć dodatkowe bramy interfejsu API oparte na granicach firmy jako drugi przestawkę projektowania.

## <a name="main-features-in-the-api-gateway-pattern"></a>Główne funkcje w wzorcu bramy interfejsu API

Brama interfejsu API może oferować wiele funkcji. W zależności od produktu może on oferować bogatsze lub prostsze funkcje, jednak najważniejsze i podstawowe funkcje dla każdej bramy interfejsu API są następujące:

**Zwrotny serwer proxy lub Routing bramy.** Brama interfejsu API oferuje zwrotny serwer proxy do przekierowywania lub kierowania żądań (Routing warstwy 7, zazwyczaj żądania HTTP) do punktów końcowych mikrousług wewnętrznych. Brama zawiera pojedynczy punkt końcowy lub adres URL dla aplikacji klienckich, a następnie wewnętrznie mapuje żądania do grupy mikrousług wewnętrznych. Ta funkcja routingu pomaga rozdzielić aplikacje klienckie z mikrousług, ale jest również dość wygodne podczas modernizacji monolitycznego interfejsu API przez zapełnienie bramy interfejsu API między INTERFEJSem monolitycznym a aplikacjami klienckimi, a następnie dodawanie nowych interfejsów API jako nowych mikrousług Nadal korzystasz ze starszego monolitycznego interfejsu API, dopóki nie zostanie on podzielony na wiele mikrousług w przyszłości. Ze względu na bramę interfejsu API aplikacje klienckie nie będą wyszukiwane, jeśli używane interfejsy API są implementowane jako mikrousługi wewnętrzne lub monolityczny interfejs API, a co ważniejsze, podczas rozwijania i refaktoryzacji monolitycznego interfejsu API do mikrousług, dzięki routingu bramy interfejsu API nie będzie to miało wpływu na aplikacje klienckie z żadną zmianą identyfikatora URI.

Aby uzyskać więcej informacji, zobacz [wzorzec routingu bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Żąda agregacji.** W ramach wzorca bramy można agregować wiele żądań klientów (zazwyczaj żądania HTTP) ukierunkowane na wiele mikrousług wewnętrznych na jedno żądanie klienta. Ten wzorzec jest szczególnie wygodniejszy, gdy strona/ekran klienta potrzebuje informacji z kilku mikrousług. W tym podejściu aplikacja kliencka wysyła pojedyncze żądanie do bramy interfejsu API, która rozsyła kilka żądań do wewnętrznych mikrousług, a następnie agreguje wyniki i wysyła wszystko z powrotem do aplikacji klienckiej. Główną korzyścią i celem tego wzorca projektowego jest zredukowanie chattiness między aplikacjami klienckimi i interfejsem API zaplecza, co jest szczególnie ważne w przypadku aplikacji zdalnych z centrum danych, w których działają mikrousługi, takie jak aplikacje mobilne lub żądania przychodzące z aplikacji SPA, które pochodzą z języka JavaScript w przeglądarkach zdalnych klienta. W przypadku zwykłych aplikacji sieci Web, które wykonują żądania w środowisku serwera (na przykład w aplikacji sieci Web ASP.NET Core MVC), ten wzorzec nie jest tak ważny, ponieważ opóźnienie jest bardzo mniejsze niż w przypadku zdalnych aplikacji klienckich.

W zależności od używanego produktu bramy API może być możliwe przeprowadzenie tego agregacji. Jednak w wielu przypadkach bardziej elastyczne jest tworzenie mikrousług agregacji w zakresie bramy interfejsu API, dlatego należy zdefiniować agregację w kodzie (czyli C# kodzie):

Aby uzyskać więcej informacji, zobacz [wzorzec agregacji bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Problemy z wycinaniem lub odciążanie bramy.** W zależności od funkcji oferowanych przez każdy produkt bramy interfejsu API można odciążyć funkcje z poszczególnych mikrousług do bramy, co upraszcza implementację każdej mikrousługi przez konsolidowanie zagadnień związanych z przecinaniem do jednej warstwy. Jest to szczególnie wygodne w przypadku wyspecjalizowanych funkcji, które mogą być skomplikowane do prawidłowego wdrożenia w każdej wewnętrznej mikrousług, takiej jak następujące:

- Uwierzytelnianie i autoryzacja
- Integracja odnajdowania usług
- Buforowanie odpowiedzi
- Zasady ponawiania, wyłącznik i jakość usług (QoS)
- Ograniczanie i ograniczanie szybkości
- Równoważenie obciążenia
- Rejestrowanie, śledzenie, korelacja
- Nagłówki, ciągi zapytań i przekształcenia oświadczeń
- Listy dozwolonych IP

Aby uzyskać więcej informacji, zobacz [wzorzec odciążania bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Korzystanie z produktów z funkcjami bramy interfejsu API

W zależności od implementacji można uzyskać wiele dodatkowych zagadnień związanych z obcinaniem, które są oferowane przez bramy interfejsu API. Będziemy tutaj eksplorować następujące informacje:

- [API Management platformy Azure](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>API Management platformy Azure

[API Management platformy Azure](https://azure.microsoft.com/services/api-management/) (jak pokazano na rysunku 4-14) nie tylko rozwiązuje potrzeby bramy interfejsu API, ale udostępnia funkcje, takie jak gromadzenie szczegółowych informacji z interfejsów API. W przypadku korzystania z rozwiązania do zarządzania INTERFEJSami API Brama interfejsu API jest tylko składnikiem tego pełnego rozwiązania do zarządzania interfejsem API.

![Diagram przedstawiający sposób używania platformy Azure API Management jako bramy interfejsu API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/api-gateway-azure-api-management.png)

**Rysunek 4-14**. Korzystanie z API Management platformy Azure dla bramy interfejsu API

Usługa Azure API Management rozwiązuje zarówno bramę interfejsu API, jak i potrzeby związane z zarządzaniem, takie jak rejestrowanie, zabezpieczenia, pomiary itp. W tym przypadku, gdy korzystasz z produktu, takiego jak Azure API Management, oznacza to, że użytkownik może mieć pojedynczą bramę interfejsu API, ponieważ nie jest to ryzykowne, ponieważ tego rodzaju bramy interfejsu API są "cieńsze" C# , co oznacza, że nie implementuje niestandardowego kodu, który może się rozwijać monolityczny składnik. 

Produkty bramy interfejsu API zwykle działają podobnie jak zwrotny serwer proxy dla komunikacji przychodzącej, gdzie można również filtrować interfejsy API z wewnętrznych mikrousług i stosować autoryzację do opublikowanych interfejsów API w tej pojedynczej warstwie.

Szczegółowe informacje dostępne w systemie API Management pomagają w zrozumieniu sposobu używania interfejsów API i sposobu ich wykonywania. Służą one do wyświetlania raportów analizy niemal w czasie rzeczywistym i identyfikowania trendów, które mogą mieć wpływ na Twoją firmę. Ponadto możesz mieć dzienniki dotyczące aktywności żądań i odpowiedzi w celu dalszej analizy w trybie online i offline.

Za pomocą usługi Azure API Management można zabezpieczyć interfejsy API przy użyciu klucza, tokenu i filtrowania adresów IP. Te funkcje pozwalają wymuszać elastyczne i szczegółowe limity przydziałów, modyfikować kształt i zachowanie interfejsów API przy użyciu zasad oraz zwiększyć wydajność z buforowaniem odpowiedzi.

W tym przewodniku i aplikacji przykładowej odniesienia (eShopOnContainers) architektura jest ograniczona do prostszej i niestandardowej architektury kontenerów, która umożliwia skoncentrowanie się na zwykłych kontenerach bez używania produktów PaaS, takich jak Azure API Management. Jednak w przypadku dużych aplikacji opartych na mikrousługach wdrożonych w Microsoft Azure zachęcamy do ocenienia API Management platformy Azure jako podstawy dla bram interfejsu API w środowisku produkcyjnym.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) to uproszczona Brama interfejsu API, zalecana dla uproszczenia podejścia. Ocelot to brama interfejsu API typu open source oparta na platformie .NET Core, szczególnie dla architektury mikrousług, która wymaga ujednoliconych punktów wejścia w ich system. Jest to uproszczone, szybkie i skalowalne oraz zapewnia Routing i uwierzytelnianie między wieloma innymi funkcjami.

Głównym powodem wyboru Ocelot [aplikacji referencyjnej eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) jest fakt, że Ocelot jest bramą interfejsu API platformy .NET Core, którą można wdrożyć w tym samym środowisku wdrażania aplikacji, w którym są wdrażane mikrousługi/ kontenery, takie jak Host platformy Docker, Kubernetes itp. I ponieważ jest ona oparta na platformie .NET Core, to na wielu platformach można wdrożyć w systemie Linux lub Windows.

Poprzednie diagramy pokazujące niestandardowe bramy interfejsu API działające w kontenerach są precyzyjnie, jak można także uruchomić Ocelot w aplikacji opartej na kontenerach i mikrousługach.

Ponadto istnieje wiele innych produktów na rynku oferujących funkcje bram interfejsu API, takie jak Apigee, Hongkong, MuleSoft, WSO2 i inne produkty, takie jak konsolidator i Istio dla funkcji kontrolera usług transferu danych w sieci.

Po wstępnym rozpoczęciu architektury i wzorców sekcjach w następnych sekcjach opisano sposób implementacji bram interfejsu API w programie [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Wady wzorca interfejsu API

- Najważniejszym wadą jest to, że po zaimplementowaniu bramy interfejsu API przyłączasz ją do warstwy wewnętrznej mikrousług. Sprzęganie takie może spowodować poważne problemy dla aplikacji. Blogu clemensay, architekt w zespole Azure Service Bus, odnosi się do tego potencjalnego trudności jako "nowe ESB" w sesji "[Obsługa i mikrousługi](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" w lokalizacji goto 2016.

- Za pomocą bramy interfejsu API mikrousług tworzy dodatkowe możliwe single point of failure.

- Brama interfejsu API może wprowadzić zwiększony czas odpowiedzi ze względu na dodatkowe połączenie sieciowe. Jednak takie dodatkowe wywołanie zwykle ma mniej wpływu niż interfejs klienta, który jest zbyt rozmawiany bezpośrednio z mikrousług wewnętrznych.

- W przypadku poprawnego skalowania bramy interfejsu API może stać się wąskim gardłem.

- Brama interfejsu API wymaga dodatkowego kosztu rozwoju i przyszłej konserwacji, jeśli obejmuje logikę niestandardową i agregację danych. Deweloperzy muszą zaktualizować bramę interfejsu API, aby uwidocznić poszczególne punkty końcowe mikrousług. Ponadto zmiany implementacji w wewnętrznych mikrousługach mogą spowodować zmiany kodu na poziomie bramy interfejsu API. Jeśli jednak Brama interfejsu API właśnie stosuje zabezpieczenia, rejestrowanie i przechowywanie wersji (tak jak w przypadku korzystania z usługi Azure API Management), ten dodatkowy koszt programistyczny może nie mieć zastosowania.

- Jeśli Brama interfejsu API jest opracowana przez jednego zespołu, może to być wąskie gardło. Jest to kolejny powód, dla którego lepszym rozwiązaniem jest posiadanie kilku bram interfejsów API z ograniczeniami, które reagują na różne potrzeby klientów. Bramę interfejsu API można również podzielić wewnętrznie na wiele obszarów lub warstw, które są własnością różnych zespołów pracujących nad mikrousługami wewnętrznymi.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Krzysztof Richardson. Wzorzec: Brama interfejsu API/zaplecze dla frontonu**  \
  <https://microservices.io/patterns/apigateway.html>

- **Wzorzec bramy interfejsu API**  \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Agregacja i wzorzec kompozycji**  \
  <https://microservices.io/patterns/data/api-composition.html>

- @No__t_1 **API Management platformy Azure**
  <https://azure.microsoft.com/services/api-management/>

- **UDI Dahan. @No__t_1 kompozycji zorientowanej na usługę**
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Blogu Clemensa. Obsługa komunikatów i mikrousług w programie GOTO 2016 (wideo)**  \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Brama interfejsu API w usłudze Nutshell** (seria samouczków podstawowej interfejsu API ASP.NET) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Poprzedni](identify-microservice-domain-model-boundaries.md)
>[Następny](communication-in-microservice-architecture.md)
