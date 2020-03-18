---
title: Wzorzec bramy interfejsu API w porównaniu z bezpośrednią komunikacją klient-mikrousługi
description: Zrozumienie różnic i zastosowań wzorca bramy interfejsu API i bezpośredniej komunikacji klient-mikrousługi.
ms.date: 01/07/2019
ms.openlocfilehash: 47e9a383c1fcb6c9fec38cb376b60a4ab839077d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401726"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Wzorzec bramy interfejsu API w porównaniu z bezpośrednią komunikacją klient-mikrousługi

W architekturze mikrousług każda mikrousługa udostępnia zestaw (zazwyczaj) szczegółowych punktów końcowych. Ten fakt może mieć wpływ na komunikację klient-mikrousługi, jak wyjaśniono w tej sekcji.

## <a name="direct-client-to-microservice-communication"></a>Bezpośrednia komunikacja klient-mikrousługi

Możliwe podejście jest użycie architektury komunikacji bezpośredniego klient-mikrousługi. W tym podejściu aplikacja klienckimoże wysyłać żądania bezpośrednio do niektórych mikrousług, jak pokazano na rysunku 4-12.

![Diagram przedstawiający architekturę komunikacji klient-mikrousługi.](./media/direct-client-to-microservice-communication.png)

**Rysunek 4-12**. Korzystanie z architektury komunikacji bezpośredniej klient-mikrousługi

W tym podejściu każda mikrousługa ma publiczny punkt końcowy, czasami z innym portem TCP dla każdej mikrousługi. Przykładem adresu URL określonej usługi może być następujący adres URL na platformie Azure:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

W środowisku produkcyjnym opartym na klastrze ten adres URL będzie mapował na moduł równoważenia obciążenia używany w klastrze, który z kolei dystrybuuje żądania między mikrousługami. W środowiskach produkcyjnych może mieć kontroler dostarczania aplikacji (ADC) jak [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) między mikrousług i Internetu. Działa to jako przezroczysta warstwa, która nie tylko wykonuje równoważenie obciążenia, ale zabezpiecza usługi, oferując zakończenie SSL. Zwiększa to obciążenie hostów przez odciążenie zakończenia ssl intensywnie korzystających z procesora CPU i innych obowiązków routingu do bramy aplikacji platformy Azure. W każdym przypadku moduł równoważenia obciążenia i ADC są przezroczyste z logicznego punktu widzenia architektury aplikacji.

Bezpośrednia architektura komunikacji klient-mikrousługi może być wystarczająco dobre dla małej aplikacji opartej na mikrousługach, zwłaszcza jeśli aplikacja kliencka jest aplikacją sieci web po stronie serwera, taką jak ASP.NET aplikacji MVC. Jednak podczas tworzenia dużych i złożonych aplikacji opartych na mikrousługach (na przykład podczas obsługi dziesiątek typów mikrousług), a zwłaszcza, gdy aplikacje klienckie są zdalnymi aplikacjami mobilnymi lub aplikacjami sieci web SPA, podejście to napotyka kilka problemów.

Podczas tworzenia dużej aplikacji opartej na mikrousługach należy wziąć pod uwagę następujące pytania:

- *Jak aplikacje klienckie zminimalizować liczbę żądań do zaplecza i zmniejszyć chatty komunikacji do wielu mikrousług?*

Interakcja z wieloma mikrousługami w celu utworzenia jednego ekranu interfejsu i usług zwiększa liczbę rund w Internecie. Zwiększa to opóźnienie i złożoność po stronie interfejsu interfejsu. W idealnym przypadku odpowiedzi powinny być skutecznie agregowane po stronie serwera. Zmniejsza to opóźnienia, ponieważ wiele fragmentów danych wraca równolegle, a niektóre interfejsu jego danych mogą wyświetlać dane, gdy tylko będą gotowe.

- *Jak można obsługiwać problemy przekrojowe, takie jak autoryzacja, przekształcenia danych i dynamiczne wysyłanie żądań?*

Implementowanie zabezpieczeń i przekrojowych problemów, takich jak zabezpieczenia i autoryzacji dla każdej mikrousługi może wymagać znacznych nakładów rozwoju. Możliwym podejściem jest mieć te usługi w hoście platformy Docker lub klastrze wewnętrznym, aby ograniczyć bezpośredni dostęp do nich z zewnątrz i zaimplementować te przekrojowe problemy w scentralizowanym miejscu, takim jak brama interfejsu API.

- *Jak aplikacje klienckie mogą komunikować się z usługami korzystającymi z protokołów nieprzyjaznych dla Internetu?*

Protokoły używane po stronie serwera (takie jak AMQP lub protokoły binarne) zwykle nie są obsługiwane w aplikacjach klienckich. W związku z tym żądania muszą być wykonywane za pośrednictwem protokołów, takich jak HTTP/HTTPS i przetłumaczone na inne protokoły później. W tej sytuacji może pomóc podejście *"man-in-the-middle".*

- *Jak można kształtować fasadę specjalnie dla aplikacji mobilnych?*

Interfejs API wielu mikrousług może nie być dobrze zaprojektowany dla potrzeb różnych aplikacji klienckich. Na przykład potrzeby aplikacji mobilnej mogą być inne niż potrzeby aplikacji sieci web. W przypadku aplikacji mobilnych może być konieczne jeszcze bardziej zoptymalizowane optymalizacja, aby odpowiedzi na dane mogły być bardziej wydajne. Można to zrobić przez agregowanie danych z wielu mikrousług i zwracanie pojedynczego zestawu danych, a czasami eliminując wszystkie dane w odpowiedzi, która nie jest potrzebna przez aplikację mobilną. I, oczywiście, można skompresować te dane. Ponownie fasady lub interfejsu API pomiędzy aplikacją mobilną i mikrousług może być wygodne w tym scenariuszu.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Dlaczego warto rozważyć bramy interfejsu API zamiast bezpośredniej komunikacji klient-mikrousługi

W architekturze mikrousług aplikacje klienckie zwykle muszą korzystać z funkcji z więcej niż jednej mikrousługi. Jeśli to zużycie jest wykonywane bezpośrednio, klient musi obsługiwać wiele wywołań do punktów końcowych mikrousług. Co się stanie, gdy aplikacja ewoluuje i nowe mikrousługi są wprowadzane lub istniejące mikrousługi są aktualizowane? Jeśli aplikacja ma wiele mikrousług, obsługa tak wielu punktów końcowych z aplikacji klienckich może być koszmarem. Ponieważ aplikacja klienckie będzie sprzęgła z tych wewnętrznych punktów końcowych, ewoluuje mikrousług w przyszłości może spowodować duży wpływ na aplikacje klienckie.

W związku z tym o poziomie pośrednim lub warstwy pośredniego (Gateway) może być bardzo wygodne dla aplikacji opartych na mikrousługach. Jeśli nie masz bram interfejsu API, aplikacje klienckie muszą wysyłać żądania bezpośrednio do mikrousług, co powoduje problemy, takie jak następujące problemy:

- **Sprzężenie:** bez wzorca bramy interfejsu API aplikacje klienckie są sprzęgane z mikrousług wewnętrznych. Aplikacje klienckie muszą wiedzieć, jak wiele obszarów aplikacji są rozłożone w mikrousługach. Podczas ewoluowania i refaktoryzacji mikrousług wewnętrznych, te akcje mają wpływ na konserwację bardzo źle, ponieważ powodują one przełomowe zmiany w aplikacjach klienckich ze względu na bezpośrednie odwołanie do mikrousług wewnętrznych z aplikacji klienckich. Aplikacje klienckie muszą być często aktualizowane, co utrudnia rozwój rozwiązania.

- **Zbyt wiele rund:** Pojedyncza strona/ekran w aplikacji klienckiej może wymagać kilku wywołań wielu usług. Może to spowodować wiele rund sieciowych między klientem a serwerem, dodając znaczne opóźnienia. Agregacja obsługiwana na poziomie pośrednim może poprawić wydajność i środowisko użytkownika dla aplikacji klienckiej.

- **Problemy z zabezpieczeniami:** bez bramy wszystkie mikrousługi muszą być udostępniane "światzewnętrzny", dzięki czemu powierzchnia ataku jest większa niż w przypadku ukrycia wewnętrznych mikrousług, które nie są bezpośrednio używane przez aplikacje klienckie. Im mniejsza jest powierzchnia ataku, tym bardziej bezpieczna może być aplikacja.

- **Problemy przekrojowe:** Każda publicznie opublikowana mikrousługa musi obsługiwać takie problemy, jak autoryzacja, ssl itp. W wielu sytuacjach te problemy mogą być obsługiwane w jednej warstwie, dzięki czemu mikrousługi wewnętrzne są uproszczone.

## <a name="what-is-the-api-gateway-pattern"></a>Co to jest wzorzec bramy interfejsu API?

Podczas projektowania i tworzenia dużych lub złożonych aplikacji opartych na mikrousługach z wieloma aplikacjami klienckimi dobrym podejściem do rozważenia może być [brama interfejsu API.](https://microservices.io/patterns/apigateway.html) Jest to usługa, która zapewnia pojedynczy punkt wejścia dla niektórych grup mikrousług. Jest podobny do [wzoru fasady](https://en.wikipedia.org/wiki/Facade_pattern) z projektu obiektowego, ale w tym przypadku jest częścią systemu rozproszonego. Wzorzec bramy interfejsu API jest również czasami znany jako "backend for frontend"[(BFF),](https://samnewman.io/patterns/architectural/bff/)ponieważ tworzysz go podczas myślenia o potrzebach aplikacji klienckiej.

W związku z tym brama interfejsu API znajduje się między aplikacjami klienckimi i mikrousług. Działa jako zwrotny serwer proxy, routing żądań od klientów do usług. Może również zapewnić dodatkowe funkcje przekrojowe, takie jak uwierzytelnianie, zakończenie protokołu SSL i pamięć podręczna.

Rysunek 4-13 pokazuje, jak niestandardowa brama interfejsu API może zmieścić się w uproszczonej architekturze opartej na mikrousługach za pomocą zaledwie kilku mikrousług.

![Diagram przedstawiający bramę interfejsu API zaimplementowane jako usługę niestandardową.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/custom-service-api-gateway.png)

**Rysunek 4-13**. Korzystanie z bramy interfejsu API zaimplementowane jako usługa niestandardowa

Aplikacje łączą się z jednym punktem końcowym, bramą interfejsu API, która jest skonfigurowana do przesyłania dalej żądań do poszczególnych mikrousług. W tym przykładzie brama interfejsu API zostanie zaimplementowana jako niestandardowa ASP.NET usługi Core WebHost działającej jako kontener.

Ważne jest, aby podkreślić, że na tym diagramie będzie używać jednej niestandardowej usługi Bramy interfejsu API skierowanej do wielu i różnych aplikacji klienckich. Fakt ten może być ważnym ryzykiem, ponieważ usługa bramy interfejsu API będzie się rozwijać i ewoluować w oparciu o wiele różnych wymagań z aplikacji klienckich. Ostatecznie, będzie nadęty ze względu na te różne potrzeby i skutecznie może być bardzo podobny do monolitycznego aplikacji lub usługi monolityczne. Dlatego jest bardzo zalecane, aby podzielić bramy interfejsu API w wielu usług lub wielu mniejszych bram interfejsu API, jeden na klienta aplikacji typu czynnika formularza, na przykład.

Należy zachować ostrożność podczas implementowania wzorca bramy interfejsu API. Zazwyczaj nie jest dobrym pomysłem, aby mieć jedną bramę interfejsu API agregujące wszystkie mikrousługi wewnętrzne aplikacji. Jeśli tak, działa jako monolityczny agregator lub koordynator i narusza autonomię mikrousług przez sprzężenie wszystkich mikrousług.

W związku z tym bramy interfejsu API powinny być segregowane na podstawie granic biznesowych i aplikacji klienckich i nie działać jako pojedynczy agregator dla wszystkich mikrousług wewnętrznych.

Podczas dzielenia warstwy bramy interfejsu API na wiele bram interfejsu API, jeśli aplikacja ma wiele aplikacji klienckich, które mogą być podstawowym punktem zwrotnym podczas identyfikowania wielu typów bram interfejsu API, dzięki czemu można mieć inną fasadę dla potrzeb każdej aplikacji klienckiej. W tym przypadku jest wzorzec o nazwie "Backend for Frontend"[(BFF),](https://samnewman.io/patterns/architectural/bff/)gdzie każda brama interfejsu API może zapewnić inny interfejs API dostosowany do każdego typu aplikacji klienta, prawdopodobnie nawet na podstawie formularza klienta, implementując określony kod karty, który pod wywołuje wiele mikrousług wewnętrznych, jak pokazano na poniższym obrazie:

![Diagram przedstawiający wiele niestandardowych bram interfejsu API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/multiple-custom-api-gateways.png)

**Rysunek 4-13,1**. Korzystanie z wielu niestandardowych bram interfejsu API

Rysunek 4-13.1 przedstawia bramy interfejsu API, które są segregowane według typu klienta; jeden dla klientów mobilnych i jeden dla klientów internetowych. Tradycyjna aplikacja sieci web łączy się z mikrousługą MVC, która używa bramy interfejsu API sieci Web. W przykładzie przedstawiono uproszczoną architekturę z wieloma szczegółowymi bramami interfejsu API. W takim przypadku granice zidentyfikowane dla każdej bramy interfejsu API są oparte wyłącznie na wzorzec "Backend for Frontend"[(BFF),](https://samnewman.io/patterns/architectural/bff/)dlatego oparte tylko na interfejsie API potrzebnym na aplikację klienta. Ale w większych aplikacjach należy również pójść dalej i utworzyć dodatkowe bramy interfejsu API na podstawie granic biznesowych jako drugiego przestawiania projektu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Główne cechy wzorca bramy interfejsu API

Brama interfejsu API może oferować wiele funkcji. W zależności od produktu może oferować bogatsze lub prostsze funkcje, jednak najważniejsze i podstawowe funkcje dla każdej bramy interfejsu API są następujące wzorce projektowe:

**Odwróć routing serwera proxy lub bramy.** Brama interfejsu API oferuje zwrotny serwer proxy do przekierowania lub trasy żądań (warstwy 7 routingu, zwykle żądania HTTP) do punktów końcowych mikrousług wewnętrznych. Brama udostępnia pojedynczy punkt końcowy lub adres URL dla aplikacji klienckich, a następnie wewnętrznie mapuje żądania do grupy mikrousług wewnętrznych. Ta funkcja routingu pomaga oddzielić aplikacje klienckie od mikrousług, ale jest również dość wygodne podczas modernizacji monolitycznego interfejsu API, siedząc bramy interfejsu API pomiędzy monolitycznym interfejsem API i aplikacjami klienckimi, a następnie można dodać nowe interfejsy API jako nowe mikrousługi nadal przy użyciu starszego monolitycznego interfejsu API, dopóki nie jest podzielony na wiele mikrousług w przyszłości. Ze względu na bramę interfejsu API aplikacje klienckie nie zauważą, czy używane interfejsy API są implementowane jako wewnętrzne mikrousługi lub monolityczny interfejs API, a co ważniejsze, podczas ewoluowania i refaktoryzacji monolitycznego interfejsu API w mikrousługach, dzięki routingowi bramy interfejsu API , aplikacje klienckie nie będą miały wpływu na żadną zmianę identyfikatora URI.

Aby uzyskać więcej informacji, zobacz [Wzorzec routingu bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Żąda agregacji.** W ramach wzorca bramy można agregować wiele żądań klientów (zwykle żądań HTTP) przeznaczonych dla wielu mikrousług wewnętrznych w jednym żądaniu klienta. Ten wzorzec jest szczególnie wygodne, gdy strona klienta/ekran potrzebuje informacji z kilku mikrousług. Dzięki takiemu podejściu aplikacja klienczowa wysyła pojedyncze żądanie do bramy interfejsu API, która wysyła kilka żądań do mikrousług wewnętrznych, a następnie agreguje wyniki i wysyła wszystko z powrotem do aplikacji klienckiej. Główną zaletą i celem tego wzorca projektowania jest zmniejszenie chattiness między aplikacjami klienckimi i interfejsu API zaplecza, co jest szczególnie ważne dla aplikacji zdalnych z centrum danych, w którym żyją mikrousługi, takie jak aplikacje mobilne lub żądania pochodzące z aplikacji SPA, które z JavaScript w przeglądarkach zdalnych klienta. W przypadku zwykłych aplikacji sieci Web wykonujących żądania w środowisku serwera (takich jak ASP.NET core MVC web app) ten wzorzec nie jest tak ważny, ponieważ opóźnienie jest znacznie mniejsze niż w przypadku zdalnych aplikacji klienckich.

W zależności od używanego produktu bramy interfejsu API może być w stanie wykonać tę agregację. Jednak w wielu przypadkach jest bardziej elastyczne do tworzenia mikrousług agregacji w zakresie bramy interfejsu API, więc zdefiniować agregacji w kodzie (czyli kod C#):

Aby uzyskać więcej informacji, zobacz [Wzorzec agregacji bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Problemy przekrojowe lub odciążanie bramy.** W zależności od funkcji oferowanych przez każdy produkt bramy interfejsu API można odciążyć funkcje z poszczególnych mikrousług do bramy, co upraszcza implementację każdej mikrousługi, konsolidując problemy przekrojowe w jednej warstwie. Jest to szczególnie wygodne w przypadku specjalistycznych funkcji, które mogą być złożone do prawidłowego wdrożenia w każdej mikrousługi wewnętrznej, takich jak następujące funkcje:

- Uwierzytelnianie i autoryzacja
- Integracja z odnajdowaniem usług
- Buforowanie odpowiedzi
- Zasady ponawiania, wyłącznika i QoS
- Ograniczanie szybkości i ograniczanie przepustowości
- Równoważenie obciążenia
- Rejestrowanie, śledzenie, korelacja
- Nagłówki, ciągi zapytań i transformacja oświadczeń
- Biała lista adresów IP

Aby uzyskać więcej informacji, zobacz [Wzorzec odciążania bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Korzystanie z produktów z funkcjami bramy interfejsu API

W zależności od każdej implementacji może istnieć wiele innych problemów przekrojowych oferowanych przez produkty bramy interfejsu API. Poznamy tutaj:

- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Usługa Azure API Management

[Usługa Azure API Management](https://azure.microsoft.com/services/api-management/) (jak pokazano na rysunku 4-14) nie tylko rozwiązuje potrzeby bramy interfejsu API, ale zapewnia funkcje, takie jak zbieranie szczegółowych informacji z interfejsów API. Jeśli używasz rozwiązania do zarządzania interfejsem API, brama interfejsu API jest tylko składnikiem w tym pełnym rozwiązaniu do zarządzania interfejsem API.

![Diagram przedstawiający sposób korzystania z usługi Azure API Management jako bramy interfejsu API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/api-gateway-azure-api-management.png)

**Rysunek 4-14**. Korzystanie z usługi Azure API Management dla bramy interfejsu API

Usługa Azure API Management rozwiązuje zarówno bramy interfejsu API, jak i potrzeby zarządzania, takie jak rejestrowanie, zabezpieczenia, pomiary itp. W takim przypadku podczas korzystania z produktu, takiego jak usługa Azure API Management, fakt, że możesz mieć jedną bramę interfejsu API, nie jest tak ryzykowny, ponieważ tego rodzaju bramy interfejsu API są "cieńsze", co oznacza, że nie implementujesz niestandardowego kodu C#, który może ewoluować w kierunku składnika monolitycznego.

Produkty bramy interfejsu API zwykle działają jak zwrotny serwer proxy dla komunikacji ciągłego składania wniosków, gdzie można również filtrować interfejsy API z mikrousług wewnętrznych oraz stosować autoryzację do opublikowanych interfejsów API w tej pojedynczej warstwie.

Szczegółowe informacje dostępne w systemie zarządzania interfejsami API pomagają zrozumieć, w jaki sposób są używane interfejsy API i jak działają. Robią to, umożliwiając wyświetlanie raportów analitycznych w czasie zbliżeń w czasie rzeczywistym i identyfikowanie trendów, które mogą mieć wpływ na Twoją firmę. Ponadto możesz mieć dzienniki dotyczące aktywności w zakresie żądań i odpowiedzi w celu dalszej analizy online i offline.

Za pomocą usługi Azure API Management można zabezpieczyć interfejsy API przy użyciu klucza, tokenu i filtrowania adresów IP. Te funkcje umożliwiają wymuszanie elastycznych i szczegółowych przydziałów i limitów szybkości, modyfikowanie kształtu i zachowania interfejsów API przy użyciu zasad oraz zwiększanie wydajności za pomocą buforowania odpowiedzi.

W tym przewodniku i przykładowej aplikacji referencyjnej (eShopOnContainers), architektura jest ograniczona do prostszej i niestandardowej architektury konteneryzowanej, aby skupić się na zwykłych kontenerach bez używania produktów PaaS, takich jak usługa Azure API Management. Jednak w przypadku aplikacji opartych na dużych mikrousługach, które są wdrażane na platformie Microsoft Azure, zachęcamy do oceny usługi Azure API Management jako podstawy bram interfejsu API w środowisku produkcyjnym.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) to lekka brama interfejsu API, zalecana w przypadku prostszych metod. Ocelot jest open source .NET Core oparte bramy interfejsu API specjalnie dla architektury mikrousług, które wymagają ujednoliconych punktów wejścia do ich systemu. Jest lekki, szybki, skalowalny i zapewnia routing i uwierzytelnianie wśród wielu innych funkcji.

Głównym powodem, aby wybrać Ocelot dla [aplikacji referencyjnej eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) jest, ponieważ Ocelot jest .NET Core lekka brama interfejsu API, które można wdrożyć w tym samym środowisku wdrażania aplikacji, gdzie wdrażasz mikrousług/kontenerów, takich jak Host platformy Docker, Kubernetes, itp. A ponieważ jest on oparty na .NET Core, jest to wieloplatformowa możliwość wdrażania w systemie Linux lub Windows.

Poprzednie diagramy przedstawiające niestandardowe bramy interfejsu API działające w kontenerach są dokładnie tym, jak można również uruchomić Ocelot w aplikacji opartej na kontenerach i mikrousługach.

Ponadto na rynku dostępnych jest wiele innych produktów oferujących funkcje bram API, takie jak Apigee, Kong, MuleSoft, WSO2 i inne produkty, takie jak Linkerd i Istio dla funkcji kontrolera danych przychodzących siatki serwisowej.

Po początkowej architektury i wzorców wyjaśnienie sekcje, następne sekcje wyjaśnić, jak zaimplementować bramy interfejsu API z [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Wady wzorca bramy interfejsu API

- Najważniejszą wadą jest to, że podczas implementowania bramy interfejsu API, są sprzężenia tej warstwy z mikrousług wewnętrznych. Sprzężenie takie jak to może spowodować poważne trudności dla aplikacji. Clemens Vaster, architekt z zespołu usługi Azure Service Bus, odnosi się do tej potencjalnej trudności jako "nowy ESB" w sesji "[Wiadomości i mikrousługi](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" na GOTO 2016.

- Przy użyciu bramy interfejsu API mikrousług tworzy dodatkowe możliwe pojedynczy punkt awarii.

- Brama interfejsu API może wprowadzić zwiększony czas odpowiedzi ze względu na dodatkowe wywołanie sieciowe. Jednak to dodatkowe wywołanie zwykle ma mniejszy wpływ niż posiadanie interfejsu klienta, który jest zbyt gadatliwy bezpośrednio wywołując mikrousług wewnętrznych.

- Jeśli nie skalowane w sposób prawidłowy, brama interfejsu API może stać się wąskim gardłem.

- Brama interfejsu API wymaga dodatkowych kosztów rozwoju i przyszłej konserwacji, jeśli zawiera niestandardową logikę i agregację danych. Deweloperzy muszą zaktualizować bramy interfejsu API w celu udostępnienia punktów końcowych każdej mikrousługi. Ponadto zmiany implementacji w mikrousługach wewnętrznych może spowodować zmiany kodu na poziomie bramy interfejsu API. Jednak jeśli brama interfejsu API tylko stosuje zabezpieczenia, rejestrowanie i przechowywanie wersji (tak jak w przypadku korzystania z usługi Azure API Management), ten dodatkowy koszt rozwoju może nie zostać zastosowany.

- Jeśli brama interfejsu API jest rozwijany przez jeden zespół, może być wąskie gardło rozwoju. Jest to kolejny powód, dla którego lepszym podejściem jest kilka ukaranych bram interfejsu API, które odpowiadają na różne potrzeby klientów. Brama interfejsu API można również segregować wewnętrznie do wielu obszarów lub warstw, które są własnością różnych zespołów pracujących nad mikrousługami wewnętrznymi.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Chris Richardson. Wzorzec: Brama interfejsu API / zaplecze frontonu** \
  <https://microservices.io/patterns/apigateway.html>

- **Wzorzec bramy interfejsu API** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Agregacja i wzorzec kompozycji** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Zarządzanie interfejsem API platformy Azure** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan. Skład zorientowany na usługi** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemens Vasters. Wiadomości i mikrousługi na GOTO 2016 (wideo)** \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Brama interfejsu API w skrócie** (ASP.net core API Gateway Tutorial Series) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Poprzedni](identify-microservice-domain-model-boundaries.md)
>[następny](communication-in-microservice-architecture.md)
