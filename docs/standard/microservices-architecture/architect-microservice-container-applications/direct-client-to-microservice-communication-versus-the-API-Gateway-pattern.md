---
title: Wzorzec bramy interfejsu API i bezpośrednia komunikacja klienta z mikrousługą
description: Dowiedz się, różnice i wykorzystuje wzorzec bramy interfejsu API i bezpośrednia komunikacja klienta z mikrousługą.
ms.date: 01/07/2019
ms.openlocfilehash: 433ad8bc8204a9a57b8b494040a9de6c533bcca8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641406"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Wzorzec bramy interfejsu API i bezpośrednia komunikacja klienta z mikrousługą

W architekturze mikrousług każda mikrousługa ujawnia zestaw punktów końcowych (zazwyczaj) szczegółowych. Ten fakt może mieć wpływ na komunikację klienta z mikrousługą, zgodnie z opisem w tej sekcji.

## <a name="direct-client-to-microservice-communication"></a>Bezpośrednia komunikacja klienta z mikrousługą

Możliwych podejść jest bezpośrednia komunikacja klienta z mikrousługą opartych na architekturze. W tej metodzie aplikacja kliencka mogą wysyłać żądania bezpośrednio do niektórych mikrousług, jak pokazano na rysunku 4-12.

![Diagram przedstawiający bezpośrednia komunikacja klienta z mikrousługą architektury, w którym każda aplikacja komunikuje się bezpośrednio z poszczególne mikrousługi.](./media/image12.png)

**Rysunek 4-12**. Przy użyciu architektury bezpośrednia komunikacja klienta z mikrousługą

W tym podejściu poszczególne mikrousługi ma publiczny punkt końcowy, czasami z różnych portów TCP dla poszczególnych mikrousług. Przykładowy adres URL dla określonej usługi może być następujący adres URL na platformie Azure:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

W środowisku produkcyjnym, oparte na klastrze mapującej adres URL do modułu równoważenia obciążenia, używany w klastrze, który z kolei rozkłada żądania na mikrousługi. W środowiskach produkcyjnych, może mieć Application Delivery kontrolera (ADC) takich jak [usługi Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mikrousługi od Internetu. Jest to zabezpieczenie przezroczyste warstwy, która nie przeprowadza równoważenia obciążenia tylko zabezpiecza usług, oferując kończenia żądań SSL. Zwiększa to obciążenie hostów, przenosząc kończenia żądań SSL mocy procesora CPU i inne opłaty routingu do usługi Azure Application Gateway. W każdym przypadku modułu równoważenia obciążenia i ADC są niewidoczne z aplikacji logicznych architektury punktu widzenia.

Architektura bezpośrednia komunikacja klienta z mikrousługą może być wystarczające dla małych aplikacji opartych na mikrousługach, zwłaszcza, jeśli aplikacja kliencka jest aplikacją sieci web po stronie serwera, np. aplikację ASP.NET MVC. Jednak podczas kompilowania dużych i złożonych aplikacji opartych na mikrousługach (na przykład podczas obsługi dziesiątek, jak mikrousługi typów), a zwłaszcza w przypadku, gdy aplikacje klienckie są zdalnej aplikacji mobilnych lub aplikacji sieci web SPA, takie podejście twarzy kilka kwestii.

Podczas tworzenia dużych aplikacji opartego na mikrousługach, należy wziąć pod uwagę następujące kwestie:

- *Jak aplikacje klienckie zminimalizować liczbę żądania do zaplecza i zmniejszyć nasilenie komunikacji do wielu mikrousług?*

Interakcja z wielu mikrousług, co umożliwia tworzenie jednego ekranu interfejsu użytkownika powoduje zwiększenie liczby rund w Internecie. Zwiększa to opóźnienie i złożoność po stronie interfejsu użytkownika. W idealnym przypadku odpowiedzi efektywnie agregowania po stronie serwera. Zmniejsza to opóźnienia, ponieważ wiele rodzajów danych możesz wrócić w sposób równoległy, a niektóre interfejsu użytkownika można wyświetlać dane, gdy tylko będzie gotowa.

- *Jak obsługiwać odciąż przekrojowe zagadnienia, takie jak autoryzacja, przekształcenia danych i wysyła żądanie dynamiczne?*

Implementowanie zabezpieczeń i odciąż przekrojowe zagadnienia, takie jak zabezpieczenia i autoryzacji w mikrousługach, co może wymagać znaczących postanowiło. Możliwych podejść jest tych usług w ramach wewnątrz klastra lub hosta platformy Docker, aby ograniczyć bezpośredni dostęp do nich z zewnątrz i do implementowania tych odciąż przekrojowe zagadnienia w centralnym miejscu, takie jak bramy interfejsu API.

- *Jak aplikacje klienckie mogą komunikować się z usługami, które używają protokołów innych niż przyjazne Internet?*

Protokoły używane po stronie serwera (na przykład protokół AMQP lub protokołów binarnych) zwykle nie są obsługiwane w aplikacjach klienckich. W związku z tym żądania musi być wykonywane za pośrednictwem protokołów, takich jak HTTP/HTTPS i przetłumaczone na inne protokoły później. A *ataków typu man-in--middle* podejście może pomóc w takiej sytuacji.

- *Jak możesz kształtować fasada szczególnie wprowadzone dla aplikacji mobilnych*

Interfejs API z wielu mikrousług może nie dobrze zaprojektowany na potrzeby różnych aplikacji klienckich. Na przykład na potrzeby aplikacji mobilnej może być inny niż na potrzeby aplikacji sieci web. Dla aplikacji mobilnych konieczne może być jeszcze bardziej zoptymalizować, tak, aby dane odpowiedzi może być bardziej efektywne. Być może w tym celu agregowania danych z wielu mikrousług, zwracając jednego zestawu danych i czasami wyeliminowanie wszelkich danych w odpowiedzi, który nie jest wymagane przez aplikację mobilną. I oczywiście, można kompresować dane. Ponownie fasady lub interfejsu API Between mikrousług i aplikacji mobilnej może być wygodna dla tego scenariusza.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Dlaczego warto wziąć pod uwagę bramy interfejsu API, zamiast bezpośredniej komunikacji klienta z mikrousługą

W architekturze mikrousług aplikacje klienckie zwykle konieczne używanie funkcji z więcej niż jeden mikrousług. Jeśli użycie tego jest wykonywana bezpośrednio, klient musi obsługiwać wiele wywołań do punktów końcowych mikrousług. Co się dzieje podczas rozwoju aplikacji i nowych mikrousług są wprowadzane lub aktualizacji istniejącej mikrousług? Jeśli aplikacja ma wiele mikrousług, obsługi tak wielu punktów końcowych z aplikacji klienta może być okropnej. Ponieważ aplikacja kliencka może zostać dołączone do tych wewnętrznych punktów końcowych, ewoluują mikrousługi w przyszłości może spowodować duży wpływ na aplikacje klienckie.

W związku z tym poziom pośredni lub warstwy pośredni (brama) może być wygodna dla aplikacji opartych na mikrousługach. Jeśli nie masz bramy interfejsu API, aplikacje klienckie musi wysyłać żądania bezpośrednio do mikrousług i która zgłasza problemy, takie jak następujące problemy:

- **Sprzężenia**: Bez wzorzec bramy interfejsu API aplikacje klienckie są połączone do wewnętrznego mikrousług. Aplikacje klienckie, trzeba wiedzieć, jak wiele obszarów aplikacji są rozłożone w mikrousługach. Gdy ewoluują i refaktoryzacji wewnętrznego mikrousług, wpływ na te akcje konserwacji wygląda niewłaściwie ponieważ powodują one przełomowe zmiany w aplikacjach klienta z powodu bezpośrednie odwołanie do wewnętrznego mikrousług z klienta aplikacji. Aplikacje klienckie muszą zostać zaktualizowane, co rozwiązanie trudniejsze ciągły rozwój.

- **Zbyt wiele rund**: Strony/jednoekranowej w aplikacji klienckiej może wymagać kilka wywołań do wielu usług. Czy można wynik na liście sieci wielu rund między klientem i serwerem oraz dodawanie znaczne opóźnienie. Obsługiwane w poziom pośredni agregacji może poprawić wydajność i środowisko użytkownika dla aplikacji klienckich.

- **Problemy z zabezpieczeniami**: Bez bramy muszą być widoczne wszystkie mikrousługi "zewnętrznych world", dzięki czemu obszar narażony na ataki większy niż ukryjesz bezpośrednio nie są używane przez aplikacje klienckie wewnętrznej mikrousług. Jest mniejszy obszar narażony na ataki, bezpieczniejsze może być aplikacji.

- **Odciąż przekrojowe zagadnienia**: Każda mikrousługa publikowanego publicznie musi obsługiwać problemy takie jak uwierzytelnianie, protokół SSL, itp. W wielu sytuacjach te problemy można obsługiwane w pojedynczej warstwie, więc wewnętrznego mikrousługi są uproszczone.

## <a name="what-is-the-api-gateway-pattern"></a>Co to jest wzorzec bramy interfejsu API?

Podczas projektowania i tworzenia aplikacji w dużej lub złożonej aplikacji opartych na mikrousługach za pomocą wielu klientów może być dobrym sposobem należy wziąć pod uwagę [bramy interfejsu API](https://microservices.io/patterns/apigateway.html). Jest to usługa, która dostarcza punktem pojedynczy wpis dla niektórych grup mikrousług. Jest on podobny do [wzorzec fasady](https://en.wikipedia.org/wiki/Facade_pattern) od projektu zorientowane obiektowo, ale w takim przypadku swoich części systemu rozproszonego. Wzorzec bramy interfejsu API jest również nazywany "wewnętrzna frontonu" ([BFF](https://samnewman.io/patterns/architectural/bff/)) a ponieważ tworzysz podczas myśleć o potrzeby aplikacji klienckiej.

W związku między aplikacjami klienta i mikrousługi znajduje się brama interfejsu API. Działa ona jako zwrotny serwer proxy kierowania żądań od klientów do usługi. Można też podać dodatkowe funkcje przekrojowe, takie jak uwierzytelnianie, kończenie żądań SSL i pamięci podręcznej.

Rysunek 4 — 13 przedstawiono, jak niestandardowe bramy interfejsu API można dopasować do uproszczenia architektury oparte na mikrousługach przy użyciu zaledwie kilku mikrousług.

![Diagram przedstawiający bramy interfejsu API zaimplementowane jako to usługa niestandardowa, więc aplikacje połączenie z jednym punkcie końcowym bramę interfejsu API, który jest skonfigurowany do przesyłania żądań do poszczególnych mikrousług.](./media/image13.png)

**Rysunek 4 — 13**. Przy użyciu bramy interfejsu API zaimplementowane jako usługa niestandardowa

W tym przykładzie brama interfejsu API będzie można zaimplementować jako to usługa niestandardowa hostem sieci Web platformy ASP.NET Core uruchomionego jako kontener.

Jest ważne podkreślić że na tym diagramie, jak można przy użyciu jednej niestandardowych usługi bramy interfejsu API połączonego z wieloma i klienta w różnych aplikacjach. Czy fakt może być ważne ryzyka, ponieważ usługi bramy interfejsu API będzie stałym wzbogacaniu i zmieniających się na podstawie wielu różnych wymagań aplikacji klienckich. Po pewnym czasie będzie przeglądarek z powodu tych różnych potrzeb i skutecznie może być dość podobne do aplikacji monolitycznej lub monolityczne usługi. Dlatego bardzo dużo zalecane jest podzielenie bramy interfejsu API w wielu usługach lub wielu mniejszych bramy interfejsu API, jeden na typ współczynnika postaci aplikacji klienckich, na przykład.

Należy zachować ostrożność podczas implementowania wzorca bramy interfejsu API. Zwykle nie jest dobry pomysł, aby mieć pojedynczy interfejs API bramy agregowania wszystkie mikrousługi wewnętrznych aplikacji. Jeśli tak jest, działa jako monolityczny agregatora lub programu orchestrator i narusza Autonomia mikrousług przez wszystkie mikrousługi sprzężenia.

W związku z tym bramy interfejsu API powinno rozdzielony na podstawie granic firm i aplikacje klienckie i nie act jako pojedynczy agregatora wewnętrznego mikrousług.

W przypadku dzielenia warstwa bramy interfejsu API do wielu bram interfejsu API, jeśli aplikacja ma wiele aplikacji klienckich, które mogą być tabelę przestawną podstawowej przy identyfikowaniu wiele typów bramy interfejsu API, dzięki czemu może mieć różne fasada dla potrzeb każdej aplikacji klienta. Ten przypadek jest wzorcem o nazwie "Wewnętrznej bazy danych dla serwera sieci Web" ([BFF](https://samnewman.io/patterns/architectural/bff/)) w przypadku, gdy każda brama interfejsu API może zapewnić innego interfejsu API, dostosowane do poszczególnych typów aplikacji klienckich, potencjalnie nawet na podstawie współczynnika postaci klienta przez zaimplementowanie określonej karty kodu, który na dole wywołuje wiele mikrousług wewnętrznych, jak pokazano na poniższej ilustracji:

![Diagram przedstawiający wiele niestandardowych bramy interfejsu API, w którym bramy interfejsu API są rozdzielone według typu klienta; jeden dla klientów mobilnych i jeden dla klientów w sieci web. Łączy się mikrousług MVC, która używa bramy interfejsu API sieci web z aplikacji sieci web tradycyjnych.](./media/image13.1.png)

**Rysunek 4-13.1**. Za pomocą wielu niestandardowych bramy interfejsu API

Na poprzedniej ilustracji przedstawiono uproszczona architektura o wiele szczegółowych bramy interfejsu API. W tym przypadku granice dla każdej bramy interfejsu API są oparte wyłącznie na "Wewnętrznej bazy danych dla frontonu" ([BFF](https://samnewman.io/patterns/architectural/bff/)) wzorzec, dlatego tylko na podstawie interfejsu API potrzebne dla aplikacji klienckich. Jednak w dużych aplikacji należy również użyteczność i utworzyć dodatkowe bramy interfejsu API oparte na granice firmy jako drugi pivot projektu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Główne funkcje we wzorcu bramy interfejsu API

Brama interfejsu API oferują wiele funkcji. W zależności od produktu może zaoferować bardziej rozbudowane lub prostsze funkcje jednak najważniejsze i podstawowe funkcje dla żadnej bramy interfejsu API są następujące wzorce projektowe:

**Zwrotny serwer proxy lub routing bramy.** Brama interfejsu API oferuje zwrotny serwer proxy do przekierowania lub kierować żądania (routingu warstwy 7, zwykle żądań HTTP) do punktów końcowych wewnętrznego mikrousług. Brama zapewnia jeden punkt końcowy lub adres URL dla klienta aplikacji, a następnie wewnętrznie mapuje żądania do grupy wewnętrznej mikrousług. Ta funkcja routingu pomaga oddzielić aplikacje klienckie z mikrousług, ale jest również bardzo wygodne po modernizowanie monolityczne interfejsu API przez znajdują się brama interfejsu API Between monolityczne interfejsu API i aplikacje klienckie, a następnie możesz dodać nowe interfejsy API jako nowych mikrousług czas nadal przy użyciu starszej wersji interfejsu API z monolitycznego, dopóki dzieli się na wielu mikrousług, co w przyszłości. Ze względu na bramę interfejsu API aplikacje klienckie nie będą zauważyć, jeśli interfejsy API używane są implementowane jako wewnętrzny mikrousług lub monolityczne interfejsu API i co ważniejsze, kiedy ewolucji i refaktoryzacji monolityczne interfejsu API na mikrousługi, dziękuję routingu bramy interfejsu API , nie będzie mieć wpływ na aplikacje klienckie w przypadku każdej zmiany identyfikatora URI.

Aby uzyskać więcej informacji, zobacz [wzorzec routingu bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Agregacja żądań.** Jako część wzorca bramy można zagregować wiele żądań klientów (zazwyczaj żądań HTTP) przeznaczone dla wielu mikrousług wewnętrznego na jedno żądanie klienta. Ten wzorzec jest zwłaszcza wtedy, gdy ekran/strony klienta wymaga informacji z wielu mikrousług. Dzięki tej metodzie aplikacja kliencka wysyła pojedynczego żądania do bramy interfejsu API, która wywołuje kilka żądań do wewnętrznego mikrousług, a następnie agreguje wyniki i wysyła wszystkie elementy z powrotem do aplikacji klienckiej. Główne korzyści i celów związanych z tym wzorcu projektowym jest ograniczenie liczby operacji między aplikacjami klienta i zaplecza interfejsu API, który jest szczególnie ważne w przypadku aplikacji zdalnych poza centrum danych, gdzie mikrousług na żywo, takie jak aplikacja mobilna lub żądania pochodzące z aplikacji SPA, pochodzą z języka Javascript w przeglądarkach zdalnego klienta. Dla zwykłych aplikacji internetowych Wykonywanie żądań w środowisku serwera (na przykład aplikacja sieci web platformy ASP.NET Core MVC) ten wzorzec nie jest tak ważne, ponieważ opóźnienie jest znacznie mniejszy niż w przypadku aplikacji klienta zdalnego.

W zależności od produktu bramy interfejsu API, których używasz może być możliwe do wykonania tej agregacji. Jednak w wielu przypadkach jest bardziej elastyczna, że można utworzyć mikrousługi agregacji w zakresie bramy interfejsu API, aby zdefiniować agregacji w kodzie (czyli C# kodu):

Aby uzyskać więcej informacji, zobacz [wzorzec agregacji za pomocą bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Odciąż przekrojowe zagadnienia lub Odciążanie bramy.** W zależności od funkcji oferowanych przez każdy produkt bramy interfejsu API można odciążyć działaniu między poszczególne mikrousługi bramy, która ułatwia implementację poszczególne mikrousługi konsolidując odciąż przekrojowe zagadnienia do jednej warstwy. Jest to szczególnie wygodne specjalne funkcje, które mogą być złożone, aby prawidłowo zaimplementować w każdej mikrousługi wewnętrznych, takich jak następujące funkcje:

- Uwierzytelnianie i autoryzacja
- Integracja z usługą odnajdywania
- Buforowanie odpowiedzi
- Ponów próbę wykonania zasady, wyłącznika i QoS
- Ograniczanie szybkości i ograniczania przepustowości
- Równoważenie obciążenia
- Rejestrowanie i śledzenie korelacji
- Nagłówki, ciągów zapytań i przekształcania oświadczeń
- Listy dozwolonych adresów IP

Aby uzyskać więcej informacji, zobacz [wzorzec odciążania bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Za pomocą produktów dzięki funkcjom bramy interfejsu API

Może istnieć wiele więcej odciąż przekrojowe zagadnienia oferowane przez produkty bramy interfejsu API, w zależności od każdego wdrożenia. Przyjrzymy się tutaj:

- [Usługa Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API Management

[Usługa Azure API Management](https://azure.microsoft.com/services/api-management/) (jak pokazano w rysunek 4 – 14) nie tylko rozwiązuje potrzeb bramy interfejsu API, ale zapewnia funkcje, takie jak zbieranie szczegółowych informacji z interfejsów API. Jeśli używasz interfejsu API rozwiązania do zarządzania, bramę interfejsu API jest tylko składnik w tym pełnego rozwiązania zarządzania interfejsu API.

![Usługa Azure API Management rozwiązuje oba bramy interfejsu API i zarządzanie potrzeb takich jak rejestrowanie, zabezpieczeń, zliczania itp.](./media/image14.png)

**Rysunek 4 – 14**. Za pomocą usługi Azure API Management dla swojej bramy interfejsu API

W takim przypadku korzystać z produktu, takich jak usługi Azure API Management, fakt, że może być pojedynczą bramą interfejsu API jest, więc ryzykowne ponieważ tego rodzaju bramy interfejsu API "cieńsza", co oznacza, nie Implementowanie niestandardowego kodu C#, rozwijać kierunku monolityczne składnik. 

Produkty bramy interfejsu API zazwyczaj pełnić rolę zwrotnego serwera proxy do komunikacji z transferem danych przychodzących, można gdzie też filtrować interfejsów API z wewnętrznego mikrousługi oraz dotyczą autoryzacji opublikowanych interfejsów API w tej warstwie pojedynczego.

Dostępne z usługi API Management system pomocy szczegółowe informacje zawierają opis sposobu używania interfejsów API i jak są wykonywane. Robią to, co pozwala wyświetlać niemal do użycia raportów analitycznych w czasie rzeczywistym i identyfikowania trendów, które mogą mieć wpływ na działalność. Ponadto może mieć rejestruje działanie żądania i odpowiedzi w celu dalszej analizy online i offline.

Dzięki usłudze Azure API Management można zabezpieczyć swoje interfejsy API przy użyciu klucza, token oraz filtrowania adresów IP. Te funkcje umożliwiają wymuszanie limitów przydziałów elastycznych i szczegółowych i limity szybkości, Modyfikuj kształt i zachowanie interfejsów API przy użyciu zasad i poprawianie wydajności za pomocą buforowanie odpowiedzi.

W tym przewodniku i odwołanie do przykładowej aplikacji (w ramach aplikacji eShopOnContainers) architektury jest ograniczona do prostszy i poza biurem architektura konteneryzowanych celu skupiania się na kontenery zwykłego bez korzystania z produktów PaaS, takich jak usługi Azure API Management. Jednak w przypadku dużych opartych na mikrousługach aplikacji, które zostały wdrożone na platformie Microsoft Azure, firma Microsoft zachęca do oceny usługi Azure API Management jako podstawy dla bram Twojego interfejsu API w środowisku produkcyjnym.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) jest uproszczona brama interfejsu API zalecane w przypadku prostszych metod. Ocelot jest Otwórz źródło .NET Core bramy interfejsu API opartych na systemie szczególnie wprowadzone dla architektury mikrousług, wymagających ujednoliconego punktów wejścia w ich systemie. Jest lekkie, szybkie i skalowalne i zapewnia routingu i uwierzytelniania między wiele innych funkcji.

Głównym celem wybierz Ocelot dla [ramach aplikacji eShopOnContainers odwołania aplikacji](https://github.com/dotnet-architecture/eShopOnContainers) jest, ponieważ Ocelot platformy .NET Core uproszczone brama interfejsu API, którą można wdrożyć na tym samym środowisku wdrożenia aplikacji, którym jest wdrażany mikrousługi/kontenerów, takich jak Host platformy Docker, Kubernetes, usługi Service Fabric itp. I ponieważ jest on oparty na platformie .NET Core, Międzyplatformowe, dzięki czemu można wdrażać w systemie Linux lub Windows.

Poprzednich diagramach, przedstawiający niestandardowe bramy interfejsu API działających w kontenerach są dokładnie, jak można również uruchomić Ocelot w kontenerze i aplikacji opartych na mikrousługach.

Ponadto w rynku, oferujący funkcje bramy interfejsu API, takich jak Apigee, Hongkong, MuleSoft WSO2, istnieje wiele innych produktów i innych produktów, takich jak Linkerd i Istio usługi siatki funkcje kontrolera danych przychodzących.

Po początkowej architektura i wzorce wyjaśnienie sekcje, w kolejnych sekcjach wyjaśniono, jak zaimplementować bramy interfejsu API za pomocą [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Wady wzorzec bramy interfejsu API

- Najważniejsze wadą jest to, że podczas implementowania bramy interfejsu API są sprzężenia tej warstwy za pomocą wewnętrznego mikrousług. Sprzężenia, np. to może powodować poważne problemy dla swojej aplikacji. Vaster Clemensa Architekt zespół usługi Azure Service Bus odwołuje się do tego potencjalnych trudności, jako "nowe ESB" w "[komunikatów i Mikrousług](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" sesji Konferencji GOTO 2016.

- Przy użyciu mikrousług bramy interfejsu API tworzy dodatkowe możliwości pojedynczy punkt awarii.

- Brama interfejsu API może wprowadzić wydłużenia czasów odpowiedzi ze względu na wywołanie dodatkowe sieci. To dodatkowe wywołanie ma zwykle mniejszym wpływem na niż w przypadku interfejsu klienta, który jest zbyt duża liczba bezpośrednie wywoływanie wewnętrznego mikrousług.

- Nie skalowana w poziomie prawidłowo, może stać się wąskim gardłem przez bramy interfejsu API.

- Bramy interfejsu API wymaga dodatkowego programowania kosztów i konserwacji w przyszłości, jeśli zawiera logikę niestandardową i agregacja danych. Deweloperzy muszą aktualizuje bramy interfejsu API w celu uwidaczniają punkty końcowe poszczególne mikrousługi. Ponadto wdrożenia zmiany w wewnętrznych mikrousług może spowodować zmiany kodu na poziomie bramy interfejsu API. Jednakże jeśli brama interfejsu API po prostu są stosowane zabezpieczenia, rejestrowanie i przechowywanie wersji (tak jak w przypadku korzystania z usługi Azure API Management), ten koszt dodatkowego programowania może nie mieć zastosowania.

- Jeśli brama interfejsu API jest opracowany przez jeden zespół, może to być "wąskie gardło" rozwoju. Jest to kolejny powód, dlaczego lepszym rozwiązaniem jest zapewnienie kilku karę szczegółowej bramy interfejsu API na potrzeby innego klienta. Brama interfejsu API można również segregowanie wewnętrznie do wielu obszarów i warstwy, które należą do różnych zespołów nad wewnętrznego mikrousług.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Charles Richardson. Wzorzec: Brama interfejsu API / zaplecza dla frontonu** \
  <https://microservices.io/patterns/apigateway.html>

- **Wzorzec bramy interfejsu API** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Wzorzec agregacji i kompozycji** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Usługa Azure API Management** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan. Kompozycja korzystający z usługi** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemensa Vastersa. Obsługa komunikatów i Mikrousług w 2016 GOTO (wideo)** \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Brama interfejsu API w skrócie** (seria samouczków bramy interfejsu API platformy ASP.net Core) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Poprzednie](identify-microservice-domain-model-boundaries.md)
>[dalej](communication-in-microservice-architecture.md)
