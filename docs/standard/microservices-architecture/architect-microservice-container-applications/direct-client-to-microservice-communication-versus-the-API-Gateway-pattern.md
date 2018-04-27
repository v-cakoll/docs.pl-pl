---
title: Bezpośrednia komunikacja klient mikrousługi i wzorzec bramy interfejsu API
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Bezpośrednia komunikacja klient mikrousługi i wzorzec bramy interfejsu API
keywords: Docker, Mikrousług, ASP.NET, kontenera, bramy interfejsu API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa3f4bb97cf942ee7698b1efa1dcd09b3f2ca571
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Bezpośrednia komunikacja klient mikrousługi i wzorzec bramy interfejsu API

W architekturze mikrousług każdego mikrousługi udostępnia zestaw (zwykle) fine‑grained punktów końcowych. Ten fakt może wpływać na komunikacji client‑to‑microservice, zgodnie z objaśnieniem w tej sekcji.

## <a name="direct-client-to-microservice-communication"></a>Bezpośrednia komunikacja klient mikrousługi

Jest możliwe podejście do użycia z architektury bezpośrednia komunikacja klient mikrousługi. W tym podejście aplikacji klienckiej mogą wysyłać żądania bezpośrednio do niektórych mikrousług, jak pokazano na rysunku 4-12.

![](./media/image12.png)

**Rysunek 4-12**. Przy użyciu architektury bezpośrednia komunikacja klient mikrousługi

W tej metody. Każdy mikrousługi ma publiczny punkt końcowy, niekiedy z różnych portów TCP dla każdego mikrousługi. Przykładowy adres URL dla określonej usługi może być następujący adres URL na platformie Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

W środowisku produkcyjnym, oparty na klastrze, mapującej adres URL do modułu równoważenia obciążenia używanych w klastrze, który z kolei rozdzielaj żądania między mikrousług. W środowiskach produkcyjnych, może mieć aplikacji dostarczania kontrolera (ADC) jak [brama aplikacji w usłudze Azure](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) Twojego mikrousług od Internetu. To dodatkowe przezroczyste warstwy, która nie przeprowadza równoważenia obciążenia tylko zabezpiecza oferując kończenia żądań SSL z usługami. Zwiększa to obciążenia hosty dzięki przeniesieniu kończenia żądań SSL użycie Procesora CPU i inne routingu obowiązków na bramie aplikacji Azure. W każdym przypadku modułu równoważenia obciążenia i ADC są niewidoczne z aplikacji logicznych architektura punktu widzenia.

Architektura bezpośrednia komunikacja klient mikrousługi może to być dobry małych aplikacji opartej na mikrousługi, szczególnie w przypadku aplikacji klienckiej aplikacji sieci web po stronie serwera, takie jak aplikacja ASP.NET MVC. Jednak podczas kompilowania dużych i złożonych aplikacji opartych na mikrousługi (na przykład podczas obsługi wielu rodzajów mikrousługi), a szczególnie w przypadku aplikacji klienta zdalnego aplikacji mobilnych lub aplikacji sieci web SPA tego podejścia skierowany kilka problemów.

Podczas tworzenia dużej aplikacji oparte na mikrousług, należy wziąć pod uwagę następujące kwestie:

-   *Jak aplikacje klienckie zminimalizować liczbę żądań do wewnętrznej bazy danych i zmniejszyć chatty komunikacji wielu mikrousług?*

Interakcji z wieloma mikrousług do tworzenia jednym ekranie interfejsu użytkownika zwiększa liczbę dwukierunkowe przesyłanie danych do Internetu. Zwiększa to opóźnienie i złożoność po stronie interfejsu użytkownika. W idealnym przypadku odpowiedzi wydajnie agregowania po stronie serwera — zmniejsza to opóźnienia, ponieważ wiele rodzajów danych wróć równolegle i niektóre interfejsu użytkownika można wyświetlić danych, jak jest gotowy.

-   *Jak można obsługiwać kompleksowymi problemów, takich jak autoryzacja, przekształcenia danych i wysyła żądanie dynamiczne?*

Implementacja zabezpieczeń oraz kompleksowymi problemy, np. zabezpieczeń i uwierzytelniania w każdym mikrousługi może wymagać znaczących nakład pracy. Możliwe rozwiązania jest tych usług w ramach hostów Docker lub wewnątrz klastra, aby ograniczyć bezpośredni dostęp do nich z zewnątrz i do zaimplementowania tych problemów kompleksowymi w centralnym miejscu, podobnie jak bramy usługi interfejsu API.

-   *Jak aplikacje klienckie mogą komunikować się z usług, które używają protokołów innych niż przyjazne Internet?*

Protokoły używane po stronie serwera (na przykład protokołu AMQP lub protokołów binarnych) zwykle nie są obsługiwane w aplikacjach klienckich. W związku z tym żądania musi być wykonywane za pośrednictwem protokołów, takich jak HTTP/HTTPS i później translacji na innych protokołów. A *man-in--middle* może pomóc w takiej sytuacji.

-   *Jak można kształtu fasad, szczególnie wprowadzone dla aplikacji mobilnych*

Interfejs API z wielu mikrousług może nie dobrze zaprojektowanej na potrzeby aplikacji innego klienta. Na przykład na potrzeby aplikacji mobilnej może różnić się od potrzeb aplikacji sieci web. Dla aplikacji mobilnych konieczne może być jeszcze bardziej zoptymalizować tak, aby dane odpowiedzi może być skuteczniejsza. Może to zrobić przez agregowanie danych z wielu mikrousług i zwracanie jednego zestawu danych, a czasami wyeliminowanie żadnych danych w odpowiedzi, które nie są wymagane przez aplikację mobilną. I oczywiście można kompresować dane. Ponownie fasad lub interfejsu API Between aplikacji mobilnej i mikrousług mogą być użyteczne dla tego scenariusza.

## <a name="using-an-api-gateway"></a>Przy użyciu bramy interfejsu API

Podczas projektowania i tworzenie dużych lub złożonych mikrousługi aplikacji z wielu klientów aplikacji może być dobrym sposobem należy wziąć pod uwagę [bramy interfejsu API](https://microservices.io/patterns/apigateway.html). Jest to usługa, która zapewnia jeden punkt wejścia dla niektórych grup mikrousług. Jest on podobny do [wzorzec fasady](https://en.wikipedia.org/wiki/Facade_pattern) od object‑oriented projektu, ale w takim przypadku jest częścią systemu rozproszonego. Wzorzec bramy interfejsu API jest również nazywany "wewnętrzna frontonu" [(BFF)](https://samnewman.io/patterns/architectural/bff/) ponieważ skompiluj go podczas planowania na potrzeby aplikacji klienckiej.

Rysunek 4-13 przedstawiono, jak brama niestandardowego interfejsu API można umieścić w architektura mikrousługi.
Ważne jest, aby wyróżnić który na tym diagramie, jak można przy użyciu jednej usługi interfejsu API bramy niestandardowych skierowane w wielu i aplikacjach innego klienta. Fakt można poważne zagrożenie, ponieważ usługi bramy interfejsu API zostanie powiększania i zmieniających się na podstawie wielu różne wymagania z aplikacji klienta. Po pewnym czasie będzie przeglądarek z powodu tych różnych potrzeb i efektywnie może być bardzo podobna do wbudowanymi aplikacji lub usługi wbudowanymi. To jest znacznie zalecane jest podzielenie bramy interfejsu API w wielu usługach lub wielu mniejszych interfejsu API bram, po jednym dla każdego typu obudowie dla wystąpienia.

![](./media/image13.png)

**Rysunek 4-13**. Przy użyciu bramy interfejsu API zaimplementowano ją jako niestandardowe usługi interfejsu API sieci Web

W tym przykładzie brama interfejsu API będzie można zaimplementować jako niestandardowego interfejsu API sieci Web usługi uruchomione jako kontener.

Jak wspomniano, należy zaimplementować kilka bram interfejsu API, dzięki czemu mają różne fasad na potrzeby każdej aplikacji klienta. Każdej bramy interfejsu API zapewniają innego interfejsu API dostosowane do każdej aplikacji klienta, prawdopodobnie nawet na podstawie współczynnika formularza klienta przez wdrażania kodu określonych kart, które na dole wywołuje wiele wewnętrznych mikrousług.

Ponieważ brama niestandardowego interfejsu API jest zazwyczaj agregatora danych, musisz należy zachować ostrożność z nim. Zwykle nie jest dobrym pomysłem jest mieć pojedynczy bramy interfejsu API agregowanie wszystkich mikrousług wewnętrznych aplikacji. Jeśli tak, działa jako wbudowanymi agregator lub orchestrator i narusza Autonomia mikrousługi przez wszystkie mikrousług sprzężenia. W związku z tym bram interfejsu API powinno rozdzielony na podstawie granice biznesowych i nie act jako agregatora dla całej aplikacji.

Czasami szczegółowego bramy interfejsu API można również mieć mikrousługi samodzielnie, a nawet mieć domeny lub nazwy firmy i powiązane dane. O granice bramy interfejsu API ustawieniem firmy lub domeny pomogą uzyskać lepsze projektu.

Może być szczególnie przydatna w przypadku bardziej zaawansowanych aplikacji złożonych interfejsu użytkownika oparte na mikrousług, szczegółowości w warstwie bramy interfejsu API, ponieważ pojęcie szczegółowych bramy interfejsu API jest podobny do interfejsu użytkownika usługi kompozycji. Omówiono to później w [Tworzenie złożonego interfejsu użytkownika oparte na mikrousług](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

W związku z tym dla wielu aplikacji i dużych średniego, przy użyciu niestandardowej bramy interfejsu API jest zwykle dobry podejście, ale nie jako pojedynczy agregatora wbudowanymi lub unikatowy centralnej bramy niestandardowego interfejsu API.

Innym rozwiązaniem jest użycie produktu, takich jak [Azure API Management](https://azure.microsoft.com/services/api-management/) jak pokazano w rysunek 4-14. Takie podejście, nie tylko rozwiązuje potrzeb bramy interfejsu API, ale zawiera funkcje, takie jak zbieranie szczegółowych informacji z swoje interfejsy API. Jeśli korzystasz z interfejsu API rozwiązania do zarządzania, bramę interfejsu API jest tylko składnik w tym pełnego rozwiązania do zarządzania interfejsu API.

![](./media/image14.png)

**Rysunek 4-14**. Za pomocą usługi Azure API Management bramy interfejsu API

W takim przypadku przy użyciu produktu, takich jak Azure API Management, fakt, że może być pojedyncza brama interfejsu API nie jest więc ryzykowne ponieważ tego rodzaju bram interfejsu API są "grubsza", co oznacza, że nie implementują niestandardowego kodu C#, który można przekształcenia wbudowanymi składnik. 

Ten typ produktu więcej działa jak zwrotny serwer proxy dla komunikacji wejściowych, można gdzie także filtrować interfejsy API z wewnętrznego mikrousług oraz dotyczą autoryzacji opublikowanych interfejsów API w tej warstwie pojedynczego.

Dostępne z pomocy systemu zarządzanie interfejsami API szczegółowych danych zawierają opis sposobu używania swoje interfejsy API i jak są wykonywane. Robią to, co pozwala wyświetlać niemal analiz w czasie rzeczywistym raporty oraz identyfikowanie trendów, które mogą mieć wpływ na firmy. Ponadto można mieć dzienniki o działaniu żądania i odpowiedzi w celu dalszej analizy online i offline.

Z usługą Azure API Management można zabezpieczyć swoje interfejsy API przy użyciu klucza, token i filtrowanie IP. Te funkcje umożliwiają wymuszanie przydziały elastyczne i szczegółowych i limity szybkości, zmodyfikować kształt i zachowanie swoje interfejsy API przy użyciu zasad i poprawić wydajność z buforowania odpowiedzi.

W tym przewodniku i odwołanie przykładowej aplikacji (eShopOnContainers) aby skupić się na zwykły kontenery bez użycia PaaS produktów, takich jak zarządzanie interfejsami API Azure możemy są ograniczanie architektury konteneryzowanych architektura prostszy i utworzone przez użytkownika. Jednak duża mikrousługi aplikacji wdrażanych w Microsoft Azure, firma Microsoft zachęca do przeglądu i wdrożyć usługę Azure API Management jako podstawa dla bram sieci interfejsu API.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Wady wzorca bramy interfejsu API

-   Najważniejsze wadą jest to, że podczas implementowania interfejsu API bramy są sprzężenia warstwa z wewnętrznego mikrousług. Sprzężenia w następujący sposób może powodować poważne problemy dla aplikacji. Vaster Clemens architektów w zespół usługi Azure Service Bus odwołuje się do tego potencjalne problemy jako "nowe ESB" w jego "[obsługi wiadomości i Mikrousług](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" sesji na GOTO 2016.

-   Przy użyciu mikrousług interfejsu API bramy tworzy dodatkowe możliwości pojedynczego punktu awarii.

-   Brama usługi interfejsu API można wprowadzać czas odpowiedzi zwiększona z powodu wywołania dodatkowe sieci. To wywołanie dodatkowe ma zazwyczaj mniej wpływ niż o kliencie interfejs, który jest zbyt chatty bezpośrednio wywołać wewnętrzny mikrousług.

-   Brama interfejsu API nie skalować w poziomie prawidłowo, może być wąskiego gardła.

-   Bramy usługi interfejsu API wymaga programowanie dodatkowych kosztów i konserwacji w przyszłości, jeśli zawiera on niestandardowej logiki i agregacja danych. Deweloperzy muszą aktualizuje bramy interfejsu API w celu ekspozycji punktów końcowych każdego mikrousługi. Ponadto zmiany implementacji w wewnętrznej mikrousług może spowodować zmiany kodu na poziomie interfejsu API bramy. Jednak jeśli bramy interfejsu API jest po prostu stosowania zabezpieczeń, rejestrowanie i przechowywanie wersji (w przypadku korzystania z usługi Azure API Management), ten koszt dodatkowe programowanie może nie mieć zastosowania.

-   Jeśli brama interfejsu API opracowanego przez jeden zespół, może być wąskie gardło rozwoju. Jest to kolejny powód, dlaczego lepszym rozwiązaniem jest kilka dopasowanymi grzywną interfejsu API bram, które odpowiadają na potrzeby innego klienta. Brama interfejsu API można również segregowanie wewnętrznie do wielu obszarów i warstwy, które należą do różnych zespołów pracuje wewnętrzny mikrousług.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Lesiak Charlesa. Wzorzec: Interfejs API bramy / wewnętrznej bazy danych dla frontonu**
    [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

-   **Zarządzanie interfejsami API Azure**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan. Kompozycja zorientowane na usługę**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Wiadomości i Mikrousług na GOTO 2016** (klip wideo) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Poprzednie] (zidentyfikować mikrousługi domeny — model-boundaries.md) [dalej] (komunikacji w — mikrousługi architecture.md)
