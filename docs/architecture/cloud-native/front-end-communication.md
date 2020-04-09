---
title: Komunikacja z klientem frontonu
description: Dowiedz się, jak klienci front-end komunikują się z systemami natywnymi dla chmury
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989080"
---
# <a name="front-end-client-communication"></a>Komunikacja z klientem frontonu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W systemie natywnym dla chmury klienci front-end (mobilne, internetowe i klasyczne) wymagają kanału komunikacji do interakcji z niezależnymi mikrousługami zaplecza.  

Jakie są opcje?

Aby zachować rzeczy proste, klient front-end może *bezpośrednio komunikować się* z mikrousług zaplecza, pokazano na rysunku 4-2.

![Bezpośrednia komunikacja między klientami a serwisem](./media/direct-client-to-service-communication.png)

**Rysunek 4-2.** Bezpośrednia komunikacja między klientami a serwisem

Dzięki takiemu podejściu każda mikrousługa ma publiczny punkt końcowy, który jest dostępny dla klientów frontonu. W środowisku produkcyjnym należy umieścić moduł równoważenia obciążenia przed mikrousług, routing ruchu proporcjonalnie.

Chociaż jest to proste do zaimplementowania, bezpośrednia komunikacja z klientem byłaby dopuszczalna tylko dla prostych aplikacji mikrousług. Ten wzór szczelnie łączy klientów front-end do podstawowych usług zaplecza, otwierając drzwi dla wielu problemów, w tym:

- Podatność klienta na refaktoryzacji usługi zaplecza.
- Szersza powierzchnia ataku jako podstawowe usługi zaplecza są bezpośrednio narażone.
- Powielanie problemów przekrojowych w każdej mikrousługi.
- Zbyt złożony kod klienta — klienci muszą śledzić wiele punktów końcowych i obsługiwać awarie w sposób odporny.

Zamiast tego powszechnie akceptowany wzorzec projektowania chmury jest zaimplementowanie [usługi bramy interfejsu API](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) między aplikacjami front-end i usługami zaplecza. Wzór jest pokazany na rysunku 4-3.

![Wzorzec bramy interfejsu API](./media/api-gateway-pattern.png)

**Rysunek 4-3.** Wzorzec bramy interfejsu API

Na poprzednim rysunku należy zwrócić uwagę, jak usługa bramy interfejsu API abstrakcje mikrousług rdzenia zaplecza. Zaimplementowany jako internetowy interfejs API działa jako *odwrotny serwer proxy*, routing ruchu przychodzącego do wewnętrznych mikrousług.

Brama izoluje klienta od wewnętrznej partycjonowania usługi i refaktoryzacji. Jeśli zmienisz usługę zaplecza, można pomieścić dla niego w bramie bez przerywania klienta. Jest to również twoja pierwsza linia obrony dla problemów przekrojowych, takich jak tożsamość, buforowanie, odporność, pomiary i ograniczanie przepustowości. Wiele z tych problemów przekrojowych można odciążyć od podstawowych usług zaplecza do bramy, upraszczając usługi zaplecza.

Należy zachować ostrożność, aby brama interfejsu API była prosta i szybka. Zazwyczaj logika biznesowa jest przechowywana poza bramą. Złożona brama może stać się wąskim gardłem, a ostatecznie samym monolitem. Większe systemy często udostępniają wiele bram interfejsu API podzielonych na segmenty według typu klienta (mobilnego, sieci Web, pulpitu) lub funkcji zaplecza. Wewnętrznej [bazy dla frontendów](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) wzorzec zapewnia kierunek implementacji wielu bram. Wzór jest pokazany na rysunku 4-4.

![Wzorzec bramy interfejsu API](./media/backend-for-frontend-pattern.png)

**Rysunek 4-4.** Wewnętrznej bazy dla szyku frontu

Na poprzednim rysunku należy zauważyć, jak ruch przychodzący jest wysyłany do określonej bramy interfejsu API — na podstawie typu klienta: aplikacji sieci Web, urządzeń mobilnych lub aplikacji komputerowej. Takie podejście ma sens, ponieważ możliwości każdego urządzenia różnią się znacznie między współczynnikiem kształtu, wydajnością i ograniczeniami wyświetlania. Zazwyczaj aplikacje mobilne udostępniają mniej funkcji niż przeglądarka lub aplikacje klasyczne. Każdą bramę można zoptymalizować pod kątem zgodności z możliwościami i funkcjonalnościami odpowiedniego urządzenia.

Aby rozpocząć, można utworzyć własną usługę bramy interfejsu API. Szybkie wyszukiwanie GitHub dostarczy wiele przykładów. Istnieje jednak kilka struktur i komercyjnych produktów bramy dostępne.

## <a name="ocelot-gateway"></a>Brama Ocelot

W przypadku prostych aplikacji natywnych dla chmury .NET można rozważyć [bramę Ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot to brama interfejsu API open source utworzona dla mikrousług platformy .NET, które wymagają ujednoliconego punktu wejścia do ich systemu. Jest lekki, szybki i skalowalny.

Podobnie jak każda brama interfejsu API, jego podstawową funkcją jest przekazywanie przychodzących żądań HTTP do dalszych usług. Ponadto obsługuje szeroki zakres możliwości, które można konfigurować w potoku oprogramowania pośredniczącego .NET Core. Jego zestaw funkcji jest przedstawiony w poniższej tabeli.

|Funkcje Ocelot  | |
| :-------- | :-------- |
| Routing | Authentication |
| Agregacja żądań | Autoryzacja |
| Service Discovery (z konsulem i Eureką) | Ograniczanie przepływności |
| Równoważenie obciążenia | Rejestrowanie, śledzenie |
| Buforowanie | Przekształcanie nagłówków/ciągów kwerend |
| Przejście korelacji | Niestandardowe oprogramowanie pośredniczące |
| Jakość usług | Zasady ponawiania prób |

Każda brama Ocelot określa adresy nadrzędne i podrzędne oraz konfigurowalne funkcje w pliku konfiguracyjnym JSON. Klient wysyła żądanie HTTP do bramy Ocelot. Po odebraniu Ocelot przekazuje Obiekt HttpRequest przez jego potok manipulowania go do stanu określonego przez jego konfiguracji. Na końcu potoku Ocelot tworzy nowy HTTPResponseObject i przekazuje go do usługi podrzędnej. W przypadku odpowiedzi Ocelot odwraca potok, wysyłając odpowiedź z powrotem do klienta.

Ocelot jest dostępny jako pakiet NuGet. Jest on przeznaczony dla sieci NET Standard 2.0, dzięki czemu jest kompatybilny zarówno z programami uruchomieniowymi .NET Core 2.0+ i .NET Framework 4.6.1+. Ocelot integruje się ze wszystkim, co mówi HTTP i działa na platformach, które obsługują .NET Core: Linux, macOS i Windows. Ocelot jest rozszerzalny i obsługuje wiele nowoczesnych platform, w tym kontenery platformy Docker, usługi Azure Kubernetes services lub inne chmury publiczne.  Ocelot integruje się z pakietami open source, takimi jak [Konsul,](https://www.consul.io) [GraphQL](https://graphql.org)i [Netflix's Eureka.](https://github.com/Netflix/eureka)

Należy wziąć pod uwagę Ocelot dla prostych aplikacji natywnych dla chmury, które nie wymagają bogatego zestawu funkcji komercyjnej bramy interfejsu API.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Aby uzyskać proste wymagania bramy, można rozważyć [usługi Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview). Usługa Azure [PaaS](https://azure.microsoft.com/overview/what-is-paas/)jest dostępna jako usługa Azure PaaS — zawiera podstawowe funkcje bramy, takie jak routing adresów URL, zakończenie SSL i zapora aplikacji sieci Web. Usługa obsługuje możliwości [równoważenia obciążenia warstwy 7.](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) W warstwie 7 można rozsyłać żądania na podstawie rzeczywistej zawartości wiadomości HTTP, a nie tylko pakietów sieciowych TCP niskiego poziomu.

W całej tej książce ewangelizujemy hosting systemów natywnych dla chmury w [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Koordynator kontenera, Kubernetes automatyzuje wdrażanie, skalowanie i problemy operacyjne konteneryzowanych obciążeń. Brama aplikacji platformy Azure można skonfigurować jako bramę interfejsu API dla klastra [usługi Azure Kubernetes.](https://azure.microsoft.com/services/kubernetes-service/)

[Kontroler transferu danych przychodzących bramy aplikacji](https://azure.github.io/application-gateway-kubernetes-ingress/) umożliwia bramie aplikacji platformy Azure bezpośrednią pracę z [usługą Azure Kubernetes.](https://azure.microsoft.com/services/kubernetes-service/) Rysunek 4.5 przedstawia architekturę.

![Kontroler ruchu przychodzącego usługi Application Gateway](./media/application-gateway-ingress-controller.png)

**Rysunek 4-5.** Kontroler ruchu przychodzącego usługi Application Gateway

Kubernetes zawiera wbudowaną funkcję, która obsługuje równoważenie obciążenia HTTP (Poziom 7), o nazwie [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/). Ingress definiuje zestaw reguł, jak wystąpienia mikrousług wewnątrz usługi AKS mogą być udostępniane na świat zewnętrzny. W poprzednim obrazie kontroler transferu danych przychodzących interpretuje reguły transferu danych przychodzących skonfigurowane dla klastra i automatycznie konfiguruje bramę aplikacji platformy Azure. Na podstawie tych reguł brama aplikacji kieruje ruch do mikrousług działających wewnątrz usługi AKS. Kontroler transferu danych przychodzących nasłuchuje zmian reguł transferu danych przychodzących i wprowadza odpowiednie zmiany w bramie aplikacji platformy Azure.

## <a name="azure-api-management"></a>Usługa Azure API Management

W przypadku systemów natywnych na umiarkowane i duże rozmiary można rozważyć usługę [Azure API Management](https://azure.microsoft.com/services/api-management/). Jest to usługa oparta na chmurze, która nie tylko rozwiązuje potrzeby bramy interfejsu API, ale zapewnia w pełni funkcjonalną obsługę deweloperską i administracyjną. Zarządzanie interfejsami API jest pokazany na rysunku 4-6.

![Usługa Azure API Management](./media/azure-api-management.png)

**Rysunek 4-6.** Usługa Azure API Management

Aby rozpocząć, usługa API Management udostępnia serwer bramy, który umożliwia kontrolowany dostęp do usług zaplecza na podstawie konfigurowalnych reguł i zasad. Te usługi mogą znajdować się w chmurze platformy Azure, centrum danych na przedwczeń lub innych chmurach publicznych. Klucze interfejsu API i tokeny JWT określają, kto może co robić. Cały ruch jest rejestrowany w celach analitycznych.

Dla deweloperów usługi API Management oferuje portal dla deweloperów, który zapewnia dostęp do usług, dokumentacji i przykładowego kodu do ich wywoływania. Deweloperzy mogą używać Swagger/Open API do sprawdzania punktów końcowych usługi i analizowania ich użycia. Usługa działa na głównych platformach programisty bezpieczeństwa: .NET, Java, Golang i innych.

Portal wydawcy udostępnia pulpit nawigacyjny zarządzania, na którym administratorzy udostępniają interfejsy API i zarządzają ich zachowaniem. Dostęp do usługi można przyznać, monitorować kondycję usługi i zbierać dane telemetryczne usługi. Administratorzy stosują *zasady* do każdego punktu końcowego, aby wpłynąć na zachowanie. [Zasady](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) są wstępnie utworzone instrukcje, które są wykonywane sekwencyjnie dla każdego wywołania usługi.  Zasady są konfigurowane dla wywołania przychodzącego, połączenia wychodzącego lub wywoływane po błędzie. Zasady mogą być stosowane w różnych zakresach usług, aby włączyć deterministyczne porządkowanie podczas łączenia zasad. Produkt jest dostarczany z dużą liczbą wstępnie utworzonych [zasad.](https://docs.microsoft.com/azure/api-management/api-management-policies)

Oto przykłady, jak zasady mogą wpływać na zachowanie usług natywnych w chmurze:  

- Ogranicz dostęp do usługi.
- Wymuszanie uwierzytelniania.  
- Przepustnicy wywołania z jednego źródła, jeśli to konieczne.
- Włącz buforowanie.
- Blokuj połączenia z określonych adresów IP.
- Steruj przepływem usługi.
- Konwertuj żądania z protokołu SOAP na REST lub między różnymi formatami danych, takimi jak XML na JSON.

Usługa Azure API Management może udostępniać usługi zaplecza, które są hostowane w dowolnym miejscu — w chmurze lub centrum danych. W przypadku starszych usług, które mogą być uwidaczniane w systemach natywnych dla chmury, obsługuje zarówno interfejsy API REST, jak i SOAP. Nawet inne usługi platformy Azure mogą być udostępniane za pośrednictwem usługi API Management. Możesz umieścić zarządzany interfejs API na usłudze kopii zapasowej platformy Azure, takiej jak [usługa Azure Service Bus](https://azure.microsoft.com/services/service-bus/) lub usługa Azure Logic [Apps.](https://azure.microsoft.com/services/logic-apps/) Usługa Azure API Management nie zawiera wbudowanej obsługi równoważenia obciążenia i powinna być używana w połączeniu z usługą równoważenia obciążenia.

Usługa Azure API Management jest dostępna w [czterech różnych warstwach:](https://azure.microsoft.com/pricing/details/api-management/)

- Developer
- Podstawowy
- Standardowa
- Premium

Warstwa deweloperów jest przeznaczona dla obciążeń nieprodukcyjnych i oceny. Inne warstwy oferują coraz więcej mocy, funkcje i wyższe umowy poziomu usług (SLA). Warstwa Premium zapewnia [obsługę sieci wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) i wielu [regionów.](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region) Wszystkie poziomy mają stałą cenę za godzinę.

Niedawno firma Microsoft ogłosiła [warstwę bezserwerową usługi API Management](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) dla usługi Azure API Management. Nazywana *warstwą cen zużycia*usługa jest wariantem zarządzania interfejsem API zaprojektowanym wokół modelu obliczeniowego bez użycia serwera. W przeciwieństwie do wcześniej pokazanych warstw cenowych "wstępnie przydzielonych", warstwa zużycia zapewnia natychmiastowe inicjowanie obsługi administracyjnej i ustalanie cen płatności za akcję.

Umożliwia funkcje bramy interfejsu API dla następujących przypadków użycia:

- Mikrousługi zaimplementowane przy użyciu technologii bezserwerowych, takich jak [usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) i Azure Logic [Apps.](https://azure.microsoft.com/services/logic-apps/)
- Zasoby usługi azure, takie jak kolejki i tematy usługi Service Bus, magazyn platformy Azure i inne.
- Mikrousługi, w których ruch ma sporadyczne duże skoki, ale pozostaje niski przez większość czasu.

Warstwa zużycia używa tych samych podstawowych składników zarządzania interfejsami API usługi, ale wykorzystuje zupełnie inną architekturę opartą na dynamicznie przydzielonych zasobach. Idealnie pasuje do modelu obliczeniowego bezserwerowego:

- Brak infrastruktury do zarządzania.
- Brak pojemności bezczynności.
- Wysoka dostępność.
- Automatyczne skalowanie.
- Koszt jest oparty na rzeczywistym użyciu.
  
Nowa warstwa zużycia jest doskonałym wyborem dla systemów natywnych dla chmury, które udostępniają zasoby bezserwerowe jako interfejsy API.

> W momencie pisania warstwy zużycie jest w wersji zapoznawczej w chmurze platformy Azure.

## <a name="real-time-communication"></a>Komunikacja w czasie rzeczywistym

Komunikacja w czasie rzeczywistym lub push to kolejna opcja dla aplikacji front-end, które komunikują się z systemami natywnymi dla chmury zaplecza za pośrednictwem protokołu HTTP. Aplikacje, takie jak znaczniki finansowe, edukacja online, gry i aktualizacje postępu pracy, wymagają natychmiastowych odpowiedzi w czasie rzeczywistym z zaplecza. W przypadku normalnej komunikacji HTTP klient nie może wiedzieć, kiedy dostępne są nowe dane. Klient musi stale *sondować* lub wysyłać żądania do serwera. Dzięki komunikacji w *czasie rzeczywistym* serwer może wypychać nowe dane do klienta w dowolnym momencie.

Systemy w czasie rzeczywistym często charakteryzują się przepływem danych o wysokiej częstotliwości i dużą liczbą równoczesnych połączeń klientów. Ręczne wdrażanie łączności w czasie rzeczywistym może szybko stać się skomplikowane, co wymaga nietrywialnej infrastruktury, aby zapewnić skalowalność i niezawodne przesyłanie wiadomości do połączonych klientów. Można znaleźć się zarządzanie wystąpieniem usługi Azure Redis Cache i zestaw modułów równoważenia obciążenia skonfigurowane z sesji przyklejonych dla koligacji klienta.

[Usługa Azure SignalR to](https://azure.microsoft.com/services/signalr-service/) w pełni zarządzana usługa platformy Azure, która upraszcza komunikację w czasie rzeczywistym dla aplikacji natywnych dla chmury. Szczegóły implementacji technicznej, takie jak inicjowanie obsługi administracyjnej pojemności, skalowanie i połączenia trwałe są pobierane. Są one obsługiwane za Ciebie z 99,9% umowy na poziomie usług. Skupić się na funkcjach aplikacji, a nie instalacji wodno-kanalizacyjnych infrastruktury.

Po włączeniu chmurowa usługa HTTP może wypychać aktualizacje zawartości bezpośrednio do połączonych klientów, w tym do aplikacji przeglądarki, aplikacji mobilnych i klasycznych. Klienci są aktualizowani bez konieczności sondowania serwera. Usługa Azure SignalR wyodrębnia technologie transportu, które tworzą łączność w czasie rzeczywistym, w tym websockets, zdarzenia po stronie serwera i długie sondowanie. Deweloperzy koncentrują się na wysyłaniu wiadomości do wszystkich lub określonych podzbiorów połączonych klientów.

Rysunek 4-7 przedstawia zestaw klientów HTTP łączących się z aplikacją natywną chmurą z włączoną obsługą usługi Azure SignalR.

![Azure SignalR](./media/azure-signalr-service.png)

**Rysunek 4-7.** Azure SignalR

Kolejną zaletą usługi Azure SignalR service jest implementowanie usług natywnych dla chmury bez serwerów. Być może kod jest wykonywany na żądanie za pomocą wyzwalaczy usługi Azure Functions. Ten scenariusz może być trudne, ponieważ kod nie utrzymuje długie połączenia z klientami. Usługa Azure SignalR Service może obsłużyć taką sytuację, ponieważ już zarządza połączeniami za Ciebie.

Usługa Azure SignalR Service ściśle integruje się z innymi usługami platformy Azure, takimi jak usługa Azure SQL Database, service bus lub pamięć podręczna Redis, otwierając wiele możliwości dla aplikacji natywnych dla chmury.

>[!div class="step-by-step"]
>[Poprzedni](communication-patterns.md)
>[następny](service-to-service-communication.md)
