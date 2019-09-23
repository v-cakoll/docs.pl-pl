---
title: Komunikacja z klientem frontonu
description: Dowiedz się, jak klienci frontonu komunikują się z systemami natywnymi w chmurze
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 67410bf9b5c76acc472018197bb64aa7662dc439
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183127"
---
# <a name="front-end-client-communication"></a>Komunikacja z klientem frontonu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W systemie natywnym w chmurze komputery klienckie frontonu (aplikacje mobilne, sieci Web i komputery stacjonarne) wymagają kanału komunikacyjnego do współpracy z niezależnymi mikrousługami zaplecza.  

Jakie są opcje?

Aby zachować prostotę, klient frontonu może komunikować się *bezpośrednio* z mikrousługami zaplecza, jak pokazano na rysunku 4-2.

![Bezpośredni klient do komunikacji z usługą](./media/direct-client-to-service-communication.png)

**Rysunek 4-2.** Bezpośredni klient do komunikacji z usługą

W tym podejściu każda mikrousługa ma publiczny punkt końcowy, który jest dostępny dla klientów frontonu. W środowisku produkcyjnym należy umieścić moduł równoważenia obciążenia przed mikrousługami, a ruch routingu proporcjonalnie.

Chociaż prosta do zaimplementowania, bezpośrednia Komunikacja klienta byłaby akceptowalna tylko dla prostych aplikacji mikrousług. Ten wzorzec ściśle Couples klientów frontonu do podstawowych usług zaplecza, otwierając drzwi w poszukiwaniu wielu problemów, w tym:

- Podatność klienta na refaktoryzację usługi zaplecza.
- Większa podatna na ataki jako podstawowe usługi zaplecza jest bezpośrednio narażona.
- Duplikowanie zagadnień związanych z wycinaniem z różnych mikrousług.
- Zbyt skomplikowany kod klienta — klienci muszą śledzić wiele punktów końcowych i niepowodzeń obsługi w sposób odporny.

Zamiast tego powszechnie przyjęty Wzorzec projektowy w chmurze polega na implementacji [usługi bramy interfejsu API](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) między aplikacjami frontonu a usługami zaplecza. Wzorzec przedstawiono na rysunku 4-3.

![Wzorzec bramy interfejsu API](./media/api-gateway-pattern.png)

**Rysunek 4-3.** Wzorzec bramy interfejsu API

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak Usługa bramy API jest abstrakcyjna mikrousługi podstawowe zaplecza. Zaimplementowana jako interfejs API sieci Web, działa jako *zwrotny serwer proxy*, kierowanie ruchu przychodzącego do wewnętrznych mikrousług. 

Brama izolowana od klienta od partycjonowania i refaktoryzacji usługi wewnętrznej. W przypadku zmiany usługi zaplecza należy ją uwzględnić w bramie bez przerywania pracy klienta. Jest to również pierwszy wiersz obrony przed rozliczeniem, taki jak tożsamość, buforowanie, odporności, pomiar i ograniczanie. Wiele z tych zagadnień związanych z rozcinaniem można wyłączyć z usług podstawowych zaplecza do bramy, upraszczając usługi zaplecza.

Należy zadbać o to, aby brama interfejsu API była prosta i szybka. Zazwyczaj logika biznesowa jest utrzymywana poza bramą. Złożone ryzyko związane z bramą staje się wąskim gardłem i ostatecznie monolitu. Duże systemy często uwidaczniają wiele bram interfejsu API, które są dzielone przez typ klienta (Mobile, Web, Desktop) lub zaplecza. Wzorzec [zaplecza dla frontonów](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) zapewnia kierunek implementacji wielu bram. Wzorzec przedstawiono na rysunku 4-4.

![Wzorzec bramy interfejsu API](./media/backend-for-frontend-pattern.png)

**Rysunek 4-4.** Wewnętrzna baza danych dla wzorca frontonu

Zwróć uwagę na powyższym rysunku, w jaki sposób ruch przychodzący jest wysyłany do określonej bramy interfejsu API na podstawie typu klienta: Web, Mobile lub aplikacja klasyczna. Takie podejście sprawia, że możliwości poszczególnych urządzeń różnią się znacznie w zależności od współczynnika, wydajności i ograniczeń wyświetlania. Zazwyczaj aplikacje mobilne uwidaczniają mniej funkcji niż przeglądarki lub aplikacje klasyczne. Każdą bramę można zoptymalizować w taki sposób, aby odpowiadała funkcjom i funkcjom odpowiedniego urządzenia.

Aby rozpocząć, można utworzyć własną usługę bramy API. Szybkie wyszukiwanie w serwisie GitHub zapewni wiele przykładów. Istnieje jednak kilka platform i dostępnych produktów bramy komercyjnej.

## <a name="ocelot-gateway"></a>Brama Ocelot

W przypadku prostych aplikacji natywnych platformy .NET można rozważyć użycie [bramy Ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot to brama interfejsu API typu open source utworzona dla mikrousług platformy .NET, która wymaga ujednoliconego punktu wejścia w System. Jest to lekkie, szybkie i skalowalne. 

Podobnie jak w przypadku dowolnej bramy interfejsu API, jej podstawową funkcją jest przekazanie przychodzących żądań HTTP do usług podrzędnych. Ponadto obsługuje szeroką gamę możliwości, które można skonfigurować w potoku oprogramowania pośredniczącego platformy .NET Core. Jego zestaw funkcji jest przedstawiony w poniższej tabeli.

|Funkcje Ocelot  | |
| :-------- | :-------- |
| Routing | Uwierzytelnianie |
| Agregacja żądań | Autoryzacja |
| Odnajdowanie usług (z Consul i Eureka) | Dławienie |
| Równoważenie obciążenia | Rejestrowanie, śledzenie |
| Buforowanie | Przekształcenie nagłówka/ciągu zapytania |
| Przekazywanie korelacji | Niestandardowe oprogramowanie pośredniczące |
| Jakość usług | Zasady ponawiania |

Każda Brama Ocelot określa adresy nadrzędne i podrzędne oraz konfigurowalne funkcje w pliku konfiguracji JSON. Klient wysyła żądanie HTTP do bramy Ocelot. Po odebraniu Ocelot przekazuje obiekt HttpRequest przez jego potok manipulowanie nim do stanu określonego przez jego konfigurację. Na końcu potoku Ocelot tworzy nowy HTTPResponseObject i przekazuje go do usługi podrzędnej. Na potrzeby odpowiedzi Ocelot odwraca potok, wysyłając odpowiedź z powrotem do klienta.

Ocelot jest dostępny jako pakiet NuGet. Jest ona przeznaczona dla standardu NET 2,0, dzięki czemu jest zgodna z programem .NET Core 2.0 + i .NET Framework 4.6.1 + środowiska uruchomieniowe. Ocelot integruje się ze wszystkimi elementami, które mówią HTTP i są uruchamiane na platformach obsługiwanych przez platformę .NET Core: Linux, macOS i Windows. Ocelot jest rozszerzalny i obsługuje wiele nowoczesnych platform, w tym kontenerów platformy Docker, usługi Azure Kubernetes Services lub innych chmur publicznych.  Ocelot integruje się z pakietami typu open source, takimi jak [Consul](https://www.consul.io), [GraphQL](https://graphql.org)i Netflix [Eureka](https://github.com/Netflix/eureka). 

Rozważ Ocelot dla prostych aplikacji natywnych w chmurze, które nie wymagają bogatego zestawu funkcji dla komercyjnej bramy interfejsu API.

## <a name="azure-application-gateway"></a>Application Gateway platformy Azure

Aby uzyskać proste wymagania dotyczące bramy, możesz rozważyć [Application Gateway platformy Azure](https://docs.microsoft.com/azure/application-gateway/overview). Dostępna jako usługa Azure [PaaS](https://azure.microsoft.com/overview/what-is-paas/)obejmuje podstawowe funkcje bramy, takie jak routing adresów URL, zakończenie protokołu SSL i Zapora aplikacji sieci Web. Usługa obsługuje funkcje [równoważenia obciążenia warstwy 7](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) . Za pomocą warstwy 7 można kierować żądania na podstawie rzeczywistej zawartości komunikatu HTTP, a nie tylko pakietów sieciowych TCP niskiego poziomu. 

W tej książce nauczanie hosting natywnych systemów w chmurze w [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Koordynator kontenerów, Kubernetes automatyzuje wdrażanie, skalowanie i problemy operacyjne obciążeń kontenerów. Usługę Azure Application Gateway można skonfigurować jako bramę interfejsu API dla klastra [usługi Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) .

[Application Gateway kontroler](https://azure.github.io/application-gateway-kubernetes-ingress/) transferu danych przychodzących umożliwia usłudze Azure Application Gateway bezpośrednią współpracę z [usługą Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). Na rysunku 4,5 przedstawiono architekturę.

![Application Gateway kontroler transferu danych przychodzących](./media/application-gateway-ingress-controller.png)

**Rysunek 4-5.** Application Gateway kontroler transferu danych przychodzących

Kubernetes zawiera wbudowaną funkcję, która obsługuje Równoważenie obciążenia HTTP (Level 7) [, nazywane](https://kubernetes.io/docs/concepts/services-networking/ingress/)ruchem przychodzącym. Ruch przychodzący definiuje zestaw reguł dotyczących sposobu, w jaki wystąpienia mikrousług wewnątrz AKS można uwidocznić na świecie zewnętrznym. Na powyższym obrazie kontroler transferu danych przychodzących interpretuje reguły transferu danych przychodzących skonfigurowane dla klastra i automatycznie skonfiguruje Application Gateway platformy Azure. Na podstawie tych reguł Application Gateway kieruje ruch do mikrousług działających w AKS. Kontroler transferu danych przychodzących nasłuchuje zmian w regułach związanych z transferem danych wejściowych i wprowadza odpowiednie zmiany w usłudze Azure Application Gateway.

## <a name="azure-api-management"></a>API Management platformy Azure

W przypadku komputerów z średnim i dużą skalą w chmurze możesz rozważyć [API Management platformy Azure](https://azure.microsoft.com/services/api-management/). Jest to usługa oparta na chmurze, która nie tylko rozwiązuje potrzeby związane z bramą interfejsu API, ale udostępnia w pełni funkcjonalne środowisko programistyczne i administracyjne. API Management przedstawiono na rysunku 4-6. 

![API Management platformy Azure](./media/azure-api-management.png)

**Rysunek 4-6.** API Management platformy Azure

Aby rozpocząć, API Management uwidacznia serwer bramy, który umożliwia kontrolowany dostęp do usług zaplecza na podstawie konfigurowalnych zasad i zasad. Te usługi mogą znajdować się w chmurze platformy Azure, w Premium centrum danych lub w innych chmurach publicznych. Klucze interfejsu API i tokeny JWT określają, kto może wykonywać te czynności. Cały ruch jest rejestrowany do celów analitycznych. 

W przypadku deweloperów API Management oferuje portal dla deweloperów, który zapewnia dostęp do usług, dokumentacji i przykładowego kodu do wywoływania ich. Deweloperzy mogą używać platformy Swagger/Open API do sprawdzenia punktów końcowych usługi i przeanalizowania ich użycia. Usługa działa na głównych platformach deweloperskich: .NET, Java, golang i innych. 

Portal wydawców udostępnia pulpit nawigacyjny zarządzania, w którym Administratorzy ujawniają interfejsy API i zarządzają ich zachowaniem. Można udzielić dostępu do usługi, monitorować kondycję usługi i zbierać dane telemetryczne usługi. Administratorzy stosują *zasady* do każdego punktu końcowego, aby mieć wpływ na zachowanie. [Zasady](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) są wstępnie skompilowanymi instrukcjami wykonywanymi sekwencyjnie dla każdego wywołania usługi.  Zasady są konfigurowane dla wywołania przychodzącego, wywołania wychodzącego lub wywoływanego po błędzie. Zasady mogą być stosowane w różnych zakresach usług, co umożliwia jednoznaczne porządkowanie podczas łączenia zasad. Produkt jest dostarczany z dużą liczbą wstępnie utworzonych [zasad](https://docs.microsoft.com/azure/api-management/api-management-policies). 

Poniżej przedstawiono przykłady zastosowania zasad, które mogą mieć wpływ na zachowanie usług natywnych w chmurze:  

- Ogranicz dostęp do usługi.
- Wymuś uwierzytelnianie.  
- Dławienia wywołań z jednego źródła, jeśli jest to konieczne.
- Włącz buforowanie.
- Blokuj wywołania z określonych adresów IP.
- Sterowanie przepływem usługi.
- Przekonwertuj żądania z protokołu SOAP na Interfejs REST lub między różnymi formatami danych, takimi jak z XML do JSON.

Usługa Azure API Management może uwidaczniać usługi zaplecza hostowane w dowolnym miejscu — w chmurze lub centrum danych. W przypadku starszych usług, które mogą zostać ujawnione w systemach natywnych w chmurze, obsługiwane są interfejsy API REST i SOAP. Nawet inne usługi platformy Azure mogą być udostępniane za pomocą API Management. Zarządzany interfejs API można umieścić na bazie usługi Azure resite, takiej jak [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) lub [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/). Usługa Azure API Management nie obejmuje wbudowanej obsługi równoważenia obciążenia i powinna być używana w połączeniu z usługą równoważenia obciążenia.

Usługa Azure API Management jest dostępna w [czterech różnych warstwach](https://azure.microsoft.com/pricing/details/api-management/):

- Deweloper
- Podstawowy
- Standardowa (Standard)
- Premium

Warstwa Deweloper jest przeznaczona dla obciążeń nieprodukcyjnych i oceny. Inne warstwy oferują coraz więcej mocy, funkcji i wyższych umów dotyczących poziomu usług (umowy SLA). Warstwa Premium zapewnia [platformę Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) i [obsługę wieloregionową](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region). Wszystkie warstwy mają stałą cenę za godzinę. 

Niedawno firma Microsoft ogłosiła [API Managementą warstwę bezserwerową](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) dla API Management platformy Azure. W odniesieniu do *warstwy cenowej zużycie*usługa jest odmianą API Management zaprojektowaną wokół modelu obliczeniowego bezserwerowego. W przeciwieństwie do wcześniej podanych warstw cenowych "wstępnie przydzielona" warstwa zużycia zapewnia szybkie Inicjowanie obsługi i Cennik płatnych akcji.

Umożliwia ona korzystanie z funkcji bramy interfejsu API dla następujących przypadków użycia:

- Mikrousługi zaimplementowane przy użyciu technologii bezserwerowych, takich jak [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) i [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/).
- Zasoby usługi Azure Site Recovery, takie jak kolejki i tematy Service Bus, Azure Storage i inne.
- Mikrousługi, w przypadku których ruch ma sporadyczne duże wartości, ale pozostaje niski przez większość czasu. 

Warstwa zużycia wykorzystuje te same podstawowe składniki API Management usługi, ale wykorzystuje całkowicie inną architekturę na podstawie dynamicznie przyznanych zasobów. Idealnie narównuje się z modelem obliczeniowym bez serwera:

- Brak infrastruktury do zarządzania.
- Brak możliwości bezczynności.
- Wysoka dostępność.
- Automatyczne skalowanie.
- Koszt jest określany na podstawie rzeczywistego użycia. 
  
Nowa warstwa zużycia to doskonały wybór dla systemów natywnych w chmurze, które uwidaczniają zasoby bezserwerowe jako interfejsy API. 

> W momencie pisania warstwa zużycia jest w wersji zapoznawczej w chmurze platformy Azure.

## <a name="real-time-communication"></a>Komunikacja w czasie rzeczywistym

Komunikacja w czasie rzeczywistym i wypychanie jest kolejną opcją dla aplikacji frontonu, które komunikują się z natywnymi systemami macierzystymi w chmurze za pośrednictwem protokołu HTTP. Aplikacje, takie jak finansowe znaczniki, Edukacja online, gry i aktualizacje postępu zadania, wymagają natychmiastowego, w czasie rzeczywistym odpowiedzi z zaplecza. W przypadku normalnej komunikacji HTTP nie ma możliwości, aby Klient wiedział, kiedy nowe dane są dostępne. Klient musi stale *sondować* lub wysyłać żądania do serwera. W przypadku komunikacji w czasie *rzeczywistym* serwer może w dowolnym momencie wysyłać do klienta nowe dane. 

Systemy czasu rzeczywistego często charakteryzują się przepływami danych o wysokiej częstotliwości i dużą liczbą jednoczesnych połączeń klientów. Ręczne implementowanie łączności w czasie rzeczywistym może szybko stać się złożonym, wymagającem nieuproszczonej infrastruktury w celu zapewnienia skalowalności i niezawodnej obsługi komunikatów dla podłączonych klientów. Możesz znaleźć samodzielnie Zarządzanie wystąpieniem Azure Redis Cache i zestawem modułów równoważenia obciążenia skonfigurowanych z sesjami programu Sticky Client dla koligacji klientów. 

[Usługa Azure Signal Service](https://azure.microsoft.com/services/signalr-service/) to w pełni zarządzana usługa platformy Azure, która upraszcza komunikację w czasie rzeczywistym dla aplikacji natywnych w chmurze. Szczegóły implementacji technicznej, takie jak inicjowanie obsługi wydajności, skalowanie i połączenia trwałe, są wyodrębniane. Są one obsługiwane w ramach umowy dotyczącej poziomu usług 99,9%. Skupiasz się na funkcjach aplikacji, a nie w infrastrukturze. 

Po włączeniu usługa HTTP oparta na chmurze może wysyłać aktualizacje zawartości bezpośrednio do podłączonych klientów, w tym aplikacji w przeglądarce, mobilnych i klasycznych. Klienci są aktualizacją bez konieczności sondowania serwera. Usługa Azure sygnalizująca dzieli Technologie transportowe, które tworzą łączność w czasie rzeczywistym, w tym obiekty WebSockets, zdarzenia po stronie serwera i długotrwałe sondowanie. Deweloperzy koncentrują się na wysyłaniu komunikatów do wszystkich lub określonych podzestawów połączonych klientów.

Rysunek 4-7 przedstawia zestaw klientów HTTP łączących się z aplikacją natywną w chmurze z włączonym usługą Azure Signal.

![Usługa Azure Signal](./media/azure-signalr-service.png)

**Rysunek 4-7.** Usługa Azure Signal

Kolejną zaletą usługi Azure sygnalizującej jest wdrożenie nienatywnych usług w chmurze. Być może Twój kod jest wykonywany na żądanie z wyzwalaczami Azure Functions. Ten scenariusz może być kłopotliwy, ponieważ kod nie zachowuje długich połączeń z klientami. Usługa Azure Signal Service może obsłużyć tę sytuację, ponieważ usługa już zarządza połączeniami.

Usługa Azure sygnalizująca ściśle integruje się z innymi usługami platformy Azure, takimi jak Azure SQL Database, Service Bus lub Redis Cache, otwierając wiele możliwości aplikacji natywnych w chmurze.

>[!div class="step-by-step"]
>[Poprzedni](communication-patterns.md)
>[Następny](service-to-service-communication.md)
