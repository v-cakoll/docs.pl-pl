---
title: Wzorzec bramy interfejsu API i bezpośrednia komunikacja klient mikrousługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wzorzec bramy interfejsu API i bezpośrednia komunikacja klient mikrousługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 83ec054239814ba20ebeec1f3d50b9f7e6dcdd87
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106281"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Wzorzec bramy interfejsu API i bezpośrednia komunikacja klient mikrousługi

W architekturze mikrousług każdego mikrousługi udostępnia zestaw (zwykle) fine‑grained punktów końcowych. Ten fakt może wpływać na komunikacji client‑to‑microservice, zgodnie z objaśnieniem w tej sekcji.

## <a name="direct-client-to-microservice-communication"></a>Bezpośrednia komunikacja klient mikrousługi

Jest możliwe podejście do użycia z architektury bezpośrednia komunikacja klient mikrousługi. W tym podejście aplikacji klienckiej mogą wysyłać żądania bezpośrednio do niektórych mikrousług, jak pokazano na rysunku 4-12.

![Diagram przedstawiający bezpośrednia komunikacja klient mikrousługi architektury](./media/image12.png)

**Rysunek 4-12**. Przy użyciu architektury bezpośrednia komunikacja klient mikrousługi

W tej metody. Każdy mikrousługi ma publiczny punkt końcowy, niekiedy z różnych portów TCP dla każdego mikrousługi. Przykładowy adres URL dla określonej usługi może być następujący adres URL na platformie Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

W środowisku produkcyjnym, oparty na klastrze, mapującej adres URL do modułu równoważenia obciążenia używanych w klastrze, który z kolei rozdzielaj żądania między mikrousług. W środowiskach produkcyjnych, może mieć aplikacji dostarczania kontrolera (ADC) jak [brama aplikacji w usłudze Azure](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) Twojego mikrousług od Internetu. To dodatkowe przezroczyste warstwy, która nie przeprowadza równoważenia obciążenia tylko zabezpiecza oferując kończenia żądań SSL z usługami. Zwiększa to obciążenia hosty dzięki przeniesieniu kończenia żądań SSL użycie Procesora CPU i inne routingu obowiązków na bramie aplikacji Azure. W każdym przypadku modułu równoważenia obciążenia i ADC są niewidoczne z aplikacji logicznych architektura punktu widzenia.

Architektura bezpośrednia komunikacja klient mikrousługi może to być dobry małych aplikacji opartej na mikrousługi, szczególnie w przypadku aplikacji klienckiej aplikacji sieci web po stronie serwera, takie jak aplikacja ASP.NET MVC. Jednak podczas kompilowania dużych i złożonych aplikacji opartych na mikrousługi (na przykład podczas obsługi wielu rodzajów mikrousługi), a szczególnie w przypadku aplikacji klienta zdalnego aplikacji mobilnych lub aplikacji sieci web SPA tego podejścia skierowany kilka problemów.

Podczas tworzenia dużej aplikacji oparte na mikrousług, należy wziąć pod uwagę następujące kwestie:

- *Jak aplikacje klienckie zminimalizować liczbę żądań do wewnętrznej bazy danych i zmniejszyć chatty komunikacji wielu mikrousług?*

Interakcji z wieloma mikrousług do tworzenia jednym ekranie interfejsu użytkownika powoduje zwiększenie liczby rund w Internecie. Zwiększa to opóźnienie i złożoność po stronie interfejsu użytkownika. W idealnym przypadku odpowiedzi wydajnie agregowania po stronie serwera. Zmniejsza to opóźnienia, ponieważ wiele rodzajów danych wróć równolegle i niektóre interfejsu użytkownika można wyświetlić danych, jak jest gotowy.

- *Jak można obsługiwać kompleksowymi problemów, takich jak autoryzacja, przekształcenia danych i wysyła żądanie dynamiczne?*

Implementacja zabezpieczeń oraz kompleksowymi problemy, np. zabezpieczeń i uwierzytelniania w każdym mikrousługi może wymagać znaczących nakład pracy. Możliwe podejście jest tych usług w ramach Docker host lub klaster wewnętrzny ograniczyć bezpośredni dostęp do nich z zewnątrz i wdrożenie tych problemów kompleksowymi w centralnym miejscu, podobnie jak bramy usługi interfejsu API.

- *Jak aplikacje klienckie mogą komunikować się z usług, które używają protokołów innych niż przyjazne Internet?*

Protokoły używane po stronie serwera (na przykład protokołu AMQP lub protokołów binarnych) zwykle nie są obsługiwane w aplikacjach klienckich. W związku z tym żądania musi być wykonywane za pośrednictwem protokołów, takich jak HTTP/HTTPS i później translacji na innych protokołów. A *man-in--middle* może pomóc w takiej sytuacji.

- *Jak można kształtu fasad, szczególnie wprowadzone dla aplikacji mobilnych*

Interfejs API z wielu mikrousług może nie dobrze zaprojektowanej na potrzeby aplikacji innego klienta. Na przykład na potrzeby aplikacji mobilnej może różnić się od potrzeb aplikacji sieci web. Dla aplikacji mobilnych konieczne może być jeszcze bardziej zoptymalizować tak, aby dane odpowiedzi może być skuteczniejsza. Może to zrobić przez agregowanie danych z wielu mikrousług i zwracanie jednego zestawu danych, a czasami wyeliminowanie żadnych danych w odpowiedzi, które nie są wymagane przez aplikację mobilną. I oczywiście można kompresować dane. Ponownie fasad lub interfejsu API Between aplikacji mobilnej i mikrousług mogą być użyteczne dla tego scenariusza.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Dlaczego należy wziąć pod uwagę bram interfejsu API zamiast bezpośredniej komunikacji klient mikrousługi

W architekturze mikrousług aplikacje klienckie zwykle muszą korzystać z funkcji z więcej niż jeden mikrousługi. Jeśli użycie tego jest wykonywana bezpośrednio, klient musi obsługiwać wielu wywołań do punktów końcowych mikrousługi. Co się dzieje podczas rozwoju aplikacji i wprowadzane są nowe mikrousług lub aktualizacji istniejącego mikrousług? Jeśli aplikacja ma wiele mikrousług, obsługi tak wielu punktów końcowych z aplikacji klienta może być nightmare. Ponieważ aplikacja kliencka może zostać dołączone do tych wewnętrznych punktów końcowych, rozwijającymi mikrousług w przyszłości może spowodować duże znaczenie dla aplikacji klienckich.

W związku z tym poziomie pośrednim lub warstwy pośredni (bramy) może być bardzo wygodny dla aplikacji opartych na mikrousługi. Jeśli nie masz bram interfejsu API aplikacji klienta musi wysyłać żądania bezpośrednio do mikrousług i który stwarza problemy, takie jak następujące problemy:

- **Sprzężenia**: bez wzorca bramy interfejsu API aplikacji klienta są powiązane do wewnętrznego mikrousług. Aplikacje klient musi wiedzieć, jak wiele obszarów aplikacji są rozłożone w mikrousług. Gdy zmieniające się i refaktoryzacji mikrousług wewnętrznego, wpływ tych czynności konserwacji pretty nieprawidłowo ponieważ spowodują one najważniejszych zmian w aplikacjach klienta z powodu bezpośrednie odwołanie do wewnętrznego mikrousług z klienta aplikacji. Aplikacje klienta muszą zostać zaktualizowane często, co przeszkodę podlegać ewolucji rozwiązania.

- **Zbyt wiele rund**: jednej strony/ekranu w aplikacji klienta może wymagać wielu wywołań wielu usług. Czy można doprowadzi do wielu sieci przekazywanych między klientem i serwerem, dodawanie znaczne opóźnienia. Obsługiwane w poziomie pośrednim agregacji może poprawić wydajność i środowisko użytkownika dla aplikacji klienckich.

- **Problemy z zabezpieczeniami**: bez bramy, muszą być widoczne wszystkie mikrousług "zewnętrzne World", co obszar narażony na ataki większych niż ukryć wewnętrzny mikrousług bezpośrednio używane przez aplikacje klienckie. Jest mniejszy obszar narażony na ataki, bezpieczniejsze może być aplikacji.

- **Dotyczy kompleksowymi**: każdego publicznie opublikowanych mikrousługi musi obsługiwać dotyczy takich jak autoryzacja, SSL, itp. W wielu sytuacjach te problemy można obsługiwane w pojedynczej warstwie, więc wewnętrzny mikrousług są uproszczone.

## <a name="what-is-the-api-gateway-pattern"></a>Co to jest wzorzec bramy interfejsu API?

Podczas projektowania i tworzenie dużych lub złożonych mikrousługi aplikacji z wielu klientów aplikacji może być dobrym sposobem należy wziąć pod uwagę [bramy interfejsu API](https://microservices.io/patterns/apigateway.html). Jest to usługa, która zapewnia jeden punkt wejścia dla niektórych grup mikrousług. Jest on podobny do [wzorzec fasady](https://en.wikipedia.org/wiki/Facade_pattern) od object‑oriented projektu, ale w takim przypadku tego część rozproszonego systemu.
Wzorzec bramy interfejsu API jest również nazywany "wewnętrzna frontonu" [(BFF)](https://samnewman.io/patterns/architectural/bff/) ponieważ skompiluj go podczas planowania na potrzeby aplikacji klienckiej.

W związku z tym API bramy znajduje się między aplikacjami klienta i mikrousług. Działa ona jako zwrotny serwer proxy, routingu żądań od klientów do usług. Można też podać dodatkowe funkcje kompleksowymi, takich jak uwierzytelnianie, kończenia żądań SSL i pamięci podręcznej.

Rysunek 4-13 przedstawiono, jak brama niestandardowego interfejsu API można umieścić w uproszczenia architektury mikrousługi na podstawie z kilku mikrousług.

![Diagram pokazujący, że bramy usługi interfejsu API zaimplementowano ją jako niestandardowe usługi](./media/image13.png)

**Rysunek 4-13**. Przy użyciu bramy interfejsu API zaimplementowano ją jako niestandardowe usługi

W tym przykładzie brama interfejsu API będzie można zaimplementować jako niestandardowe usługi hosta sieci Web platformy ASP.NET Core uruchomionej jako kontener.

Ważne jest, aby wyróżnić który na tym diagramie, jak można przy użyciu jednej usługi interfejsu API bramy niestandardowych skierowane w wielu i aplikacjach innego klienta. Fakt można poważne zagrożenie, ponieważ usługi bramy interfejsu API zostanie powiększania i zmieniających się na podstawie wielu różne wymagania z aplikacji klienta. Po pewnym czasie będzie przeglądarek z powodu tych różnych potrzeb i efektywnie może być bardzo podobna do wbudowanymi aplikacji lub usługi wbudowanymi. To jest znacznie zalecane jest podzielenie bramy interfejsu API w wielu usługach lub wielu mniejszych interfejsu API bram, po jednym dla każdego typu obudowie aplikacji klienta, na przykład.

Należy zachować ostrożność podczas implementowania wzorzec bramy interfejsu API. Zwykle nie jest dobrym pomysłem jest mieć pojedynczy bramy interfejsu API agregowanie wszystkich mikrousług wewnętrznych aplikacji. Jeśli tak, działa jako wbudowanymi agregator lub orchestrator i narusza Autonomia mikrousługi przez wszystkie mikrousług sprzężenia.

W związku z tym bram interfejsu API powinno rozdzielony na podstawie granice firm i aplikacji klienckich i nie act jako pojedynczy agregatora dla wszystkich wewnętrzny mikrousług.

W przypadku dzielenia warstwy interfejsu API bramy do wielu bram interfejsu API, jeśli aplikacja ma wiele aplikacji klienta, które mogą być podstawowy pivot podczas identyfikowania wiele typów bram interfejsu API, dzięki czemu mają różne fasad na potrzeby każdej aplikacji klienta. Ten przypadek to wzorzec o nazwie "Wewnętrznej bazy danych dla serwera sieci Web" ([BFF](http://samnewman.io/patterns/architectural/bff/)) w przypadku, gdy każdej bramy interfejsu API zapewniają interfejs API różnych dostosowane do każdego typu aplikacji klienta, prawdopodobnie nawet na podstawie współczynnika formularza klienta zaimplementowanie określonej karty kod który na dole wywołuje wielu mikrousług wewnętrznych, jak pokazano na poniższej ilustracji:

![Diagram przedstawiający wielu bram niestandardowego interfejsu API](./media/image13.1.png)

**Rysunek 4-13.1**. Korzystanie z wielu bram niestandardowego interfejsu API

Na poprzedniej ilustracji przedstawiono uproszczenia architektury z wielu bram szczegółowych interfejsu API. W takim przypadku granice dla każdej bramy interfejsu API są oparte wyłącznie na "wewnętrznej bazy danych dla serwera sieci Web" ([BFF](http://samnewman.io/patterns/architectural/bff/)) wzorzec, dlatego oparte tylko na potrzeby każdej aplikacji klienta interfejsu API. Jednak w dużych aplikacji należy również Przejdź dalej i utworzyć dodatkowe bram interfejsu API w oparciu firm granice jako drugi pivot projektu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Główne funkcje we wzorcu interfejsu API bramy

Brama usługi interfejsu API można oferują wiele funkcji. W zależności od produktu może oferować bardziej zaawansowane funkcje lub prostsze funkcje jednak najważniejsze i podstawowych funkcji wszystkie bramy interfejsu API są następujące wzorce projektowe:

**Wycofaj serwera proxy lub bramy routingu**. Brama interfejsu API oferuje zwrotny serwer proxy do przekierowywania lub kierować żądania (warstwy 7 routingu, zazwyczaj w żądaniach Http) do punktów końcowych mikrousług wewnętrzny. Brama zapewnia jeden punkt końcowy lub adres URL dla klienta aplikacji, a następnie wewnętrznie mapuje żądania do grupy mikrousług wewnętrznego. Rozdzielenie aplikacji klienta z mikrousług pomaga routingu, ale jest również bardzo wygodny podczas modernizacji wbudowanymi interfejsu API przez działo bramy interfejsu API Between wbudowanymi interfejsu API i aplikacje klienckie, a następnie można dodać nowych interfejsów API jako mikrousług nowy Podczas nadal przy użyciu starszej wersji interfejsu API z wbudowanymi do momentu jej jest podzielony na wiele mikrousług w przyszłości. Ze względu na bramie interfejsu API aplikacji klienta nie będzie Zwróć uwagę, jeśli interfejsy API używane są zaimplementowane jako mikrousług wewnętrzny lub wbudowanymi interfejsu API i co ważniejsze, gdy zmieniające się i refaktoryzacji wbudowanymi interfejsu API w mikrousług, Dziękujemy bramy Interfejs API routingu , nie będzie mieć wpływ na aplikacje klienckie przy każdej zmianie identyfikatora URI.

Aby uzyskać więcej informacji, zobacz [wzorzec routingu bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Żąda agregacji**. W ramach wzorzec bramy może agregować wiele żądań klientów (zazwyczaj żądań Http) przeznaczonych dla wielu mikrousług wewnętrznego na pojedyncze żądanie klienta. Ten wzorzec jest zwłaszcza wtedy, gdy ekran/strony klienta wymaga informacji z kilku mikrousług. Z tej metody aplikacja kliencka wysyła pojedyncze żądanie do bramy interfejsu API, która wywołuje kilka żądań do wewnętrznego mikrousług, a następnie agreguje wyniki i wysyła wszystkie elementy z powrotem do aplikacji klienckiej. Celem tego wzorca projektowego i główne korzyści jest zmniejszenie chattiness między aplikacjami klienta i zaplecza interfejsu API, który jest szczególnie ważne dla aplikacji zdalnych poza centrum danych, gdzie mikrousług na żywo, takich jak aplikacje mobilne lub żądania pochodzące z aplikacji JEDNOSTRONICOWEJ który pochodzą z języka Javascript w przeglądarkach zdalnego klienta. Dla aplikacji web regularne wykonywanie żądania w środowisku serwera (np. aplikacji sieci web platformy ASP.NET Core MVC) ten wzorzec nie jest tak ważne, jak opóźnienie jest znacznie mniejszy niż w przypadku aplikacji klienta zdalnego.

W zależności od używanego produktu do bramy interfejsu API może być możliwe do wykonania tej agregacji. Jednak w wielu przypadkach jest bardziej elastyczne, aby utworzyć mikrousług agregacji w zakresie bramy interfejsu API, zdefiniuj agregacji w kodzie (to znaczy kodu C#).

Aby uzyskać więcej informacji, zobacz [wzorzec agregacji bramy](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Problemy kompleksowymi lub Odciążanie bramy**. W zależności od funkcji oferowanych przez każdy z produktów bramy interfejsu API można odciążenia funkcjonalności z poszczególnych mikrousług do bramy, która ułatwia implementację każdego mikrousługi dzięki konsolidacji kompleksowymi problemy w jedną warstwę. Jest to szczególnie wygodne specjalne funkcje, które mogą być skomplikowane, aby prawidłowo zaimplementować w każdym mikrousługi wewnętrzne, takie jak następujące funkcje:

- Uwierzytelnianie i autoryzacja
- Usługi integracji odnajdywania
- Buforowanie odpowiedzi
- Ponów próbę wykonania zasady, wyłącznika i QoS
- Limitów szybkości i ograniczania przepustowości
- Równoważenie obciążenia
- Rejestrowanie śledzenia korelacji
- Nagłówki, ciągów zapytania i przekształcania oświadczeń
- Listę dozwolonych podobnej IP

Aby uzyskać więcej informacji, zobacz [bramy Odciążanie wzorzec](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Funkcje interfejsu API bramy przy użyciu produktów

Może istnieć wiele więcej dotyczy kompleksowymi oferowane przez produkty bram interfejsu API w zależności od każdego wdrożenia. Na przykład [Azure API Management](https://azure.microsoft.com/services/api-management/) (jak pokazano w rysunek 4-14) nie tylko rozwiązuje potrzeb bramy interfejsu API, ale zawiera funkcje, takie jak zbieranie szczegółowych informacji z swoje interfejsy API. Jeśli korzystasz z interfejsu API rozwiązania do zarządzania, bramę interfejsu API jest tylko składnik w tym pełnego rozwiązania do zarządzania interfejsu API.

![Diagram przedstawiający bramy interfejsu API z interfejsu API Azure Architektura zarządzania](./media/image14.png)

**Rysunek 4-14**. Za pomocą usługi Azure API Management bramy interfejsu API

W takim przypadku przy użyciu produktu, takich jak Azure API Management, fakt, że może być pojedyncza brama interfejsu API nie jest więc ryzykowne ponieważ tego rodzaju bram interfejsu API są "grubsza", co oznacza, że nie implementują niestandardowego kodu C#, który można przekształcenia wbudowanymi składnik.

Produkty bramy interfejsu API zwykle działać tak jak zwrotny serwer proxy dla komunikacji wejściowych, można gdzie także filtrować interfejsy API z wewnętrznego mikrousług oraz dotyczą autoryzacji opublikowanych interfejsów API w tej warstwie pojedynczego.

Dostępne z pomocy systemu zarządzanie interfejsami API szczegółowych danych zawierają opis sposobu używania swoje interfejsy API i jak są wykonywane. Robią to, co pozwala wyświetlać niemal analiz w czasie rzeczywistym raporty oraz identyfikowanie trendów, które mogą mieć wpływ na firmy. Ponadto można mieć dzienniki o działaniu żądania i odpowiedzi w celu dalszej analizy online i offline.

Z usługą Azure API Management można zabezpieczyć swoje interfejsy API przy użyciu klucza, token i filtrowanie IP. Te funkcje umożliwiają wymuszanie przydziały elastyczne i szczegółowych i limity szybkości, zmodyfikować kształt i zachowanie swoje interfejsy API przy użyciu zasad i poprawić wydajność z buforowania odpowiedzi.

W tym przewodniku i odwołanie przykładowej aplikacji (eShopOnContainers) architektura jest ograniczona do prostszy i utworzone przez użytkownika architektura konteneryzowanych aby skupić się na zwykły kontenery bez użycia PaaS produktów, takich jak zarządzanie interfejsami API Azure. Jednak duża mikrousługi aplikacji wdrażanych w Microsoft Azure, firma Microsoft zachęca do oceny usługi Azure API Management jako podstawa dla bram sieci interfejsu API w środowisku produkcyjnym.

**Ocelot.** Dla metod prostszy lekkie bramy interfejsu API, takich jak Ocelot jest zalecane. [Ocelot](https://github.com/ThreeMammals/Ocelot) open source bramy oparte na .NET Core API szczególnie staje się dla architektury mikrousług, wymagającym ujednoliconego punktów wejścia w systemie. Jest lekki, szybkie i skalowalne i udostępnia routingu i uwierzytelniania między wiele innych funkcji.

Głównym celem Dlaczego Ocelot został użyty w [eShopOnContainers odwołania aplikacji](https://github.com/dotnet-architecture/eShopOnContainers) ponieważ .NET Core lekkie interfejsu API bramy można wdrożyć na tym samym środowisku wdrażania aplikacji, którym jest wdrażany jest Ocelot mikrousług/kontenerów, takich jak Docker Host, Kubernetes, Service Fabric, itp. Ponieważ jest on oparty na .NET Core, jest wieloplatformowych, co umożliwia wdrażanie w systemie Linux lub Windows i.

Poprzednich diagramach przedstawiający niestandardowych bramy interfejsu API w kontenerach są dokładnie sposób można także uruchomić Ocelot w aplikacji opartej na mikrousługi i kontenera.

Ponadto istnieje wiele innych produktów na rynku, oferujący funkcje interfejsu API bram, takie jak Apigee, Kong, MuleSoft, WSO2, i innych produktów, takich jak Linkerd i Istio usługi siatki funkcje kontrolera wejściowych.

Po początkowej architektury i wzorce wyjaśnienie sekcje, w kolejnych sekcjach wyjaśniono sposób implementacji interfejsu API bramy przy użyciu [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Wady wzorca bramy interfejsu API

- Najważniejsze wadą jest to, że podczas implementowania interfejsu API bramy w przypadku sprzężenia warstwa z wewnętrznego mikrousług. Sprzężenia w następujący sposób może powodować poważne problemy dla aplikacji. Vaster Clemens architektów w zespół usługi Azure Service Bus odwołuje się do tego potencjalne problemy jako "nowe ESB" w "[obsługi wiadomości i Mikrousług](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" sesji na GOTO 2016.

- Przy użyciu mikrousług interfejsu API bramy tworzy dodatkowe możliwości pojedynczego punktu awarii.

- Brama usługi interfejsu API można wprowadzać czas odpowiedzi zwiększona z powodu wywołania dodatkowe sieci. To wywołanie dodatkowe ma zazwyczaj mniej wpływ niż o kliencie interfejs, który jest zbyt chatty bezpośrednio wywołać wewnętrzny mikrousług.

- Brama interfejsu API nie skalować w poziomie prawidłowo, może być wąskiego gardła.

- Bramy usługi interfejsu API wymaga programowanie dodatkowych kosztów i konserwacji w przyszłości, jeśli zawiera on niestandardowej logiki i agregacja danych. Deweloperzy muszą aktualizuje bramy interfejsu API w celu ekspozycji punktów końcowych każdego mikrousługi. Ponadto zmiany implementacji w wewnętrznej mikrousług może spowodować zmiany kodu na poziomie interfejsu API bramy. Jednak jeśli bramy interfejsu API jest po prostu stosowania zabezpieczeń, rejestrowanie i przechowywanie wersji (w przypadku korzystania z usługi Azure API Management), ten koszt dodatkowe programowanie może nie mieć zastosowania.

- Jeśli brama interfejsu API opracowanego przez jeden zespół, może być wąskie gardło rozwoju. Jest to kolejny powód, dlaczego lepszym rozwiązaniem jest kilka dopasowanymi grzywną interfejsu API bram, które odpowiadają na potrzeby innego klienta. Brama interfejsu API można również segregowanie wewnętrznie do wielu obszarów i warstwy, które należą do różnych zespołów pracuje wewnętrzny mikrousług.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Lesiak Charlesa. Wzorzec: Interfejs API bramy / wewnętrznej bazy danych dla frontonu** [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **Wzorzec bramy interfejsu API** [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Wzorzec agregacji i kompozycji** [*http://microservices.io/patterns/data/api-composition.html*](http://microservices.io/patterns/data/api-composition.html)

- **Zarządzanie interfejsami API Azure** [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **Udi Dahan. Kompozycja zorientowane na usługę**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Clemens Vasters. Wiadomości i Mikrousług na GOTO 2016** (klip wideo)   [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

>[!div class="step-by-step"]
[Poprzednie](identify-microservice-domain-model-boundaries.md)
[dalej](communication-in-microservice-architecture.md)
