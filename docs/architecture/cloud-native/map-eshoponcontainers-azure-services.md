---
title: Mapowanie eShopOnContainers do usług platformy Azure
description: Mapowanie eShopOnContainers do usług platformy Azure, takich jak usługa Azure Kubernetes, Brama interfejsu API i Azure Service Bus.
ms.date: 06/30/2019
ms.openlocfilehash: 67430da18c0a12c694426214de33e85c2113e454
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275815"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>Mapowanie eShopOnContainers do usług platformy Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Chociaż nie jest to wymagane, platforma Azure dobrze nadaje się do obsługi eShopOnContainers, ponieważ projekt został skompilowany jako aplikacja natywna w chmurze. Aplikacja została skompilowana przy użyciu platformy .NET Core, więc może działać w kontenerach systemu Linux lub Windows w zależności od hosta platformy Docker. Aplikacja składa się z wielu autonomicznych mikrousług, z których każdy ma własne dane. Różne mikrousługi przedstawiają różne podejścia, od prostych operacji CRUD do bardziej złożonych wzorców DDD i CQRS. Mikrousługi komunikują się z klientami za pośrednictwem protokołu HTTP i ze sobą za pośrednictwem komunikacji opartej na komunikatach. Aplikacja obsługuje również wiele platform dla klientów, ponieważ przyjmuje protokołu HTTP jako standardowy protokół komunikacyjny i zawiera ASP.NET Core i aplikacje mobilne Xamarin, które działają na platformach z systemami Android, iOS i Windows.

Architektura aplikacji jest pokazana na rysunku 2-5. Po lewej stronie znajdują się aplikacje klienckie, które zostały podzielone na urządzenia przenośne, tradycyjne sieci Web i aplikacje jednostronicowe (SPA). Po prawej stronie są składniki serwera, które składają się na system, z których każdy może być hostowany w kontenerach platformy Docker i klastrach Kubernetes. Tradycyjna aplikacja sieci Web jest obsługiwana przez aplikację ASP.NET Core MVC poświetloną na żółto. Ta aplikacja oraz aplikacje mobilne i sieci Web SPA komunikują się z indywidualnymi mikrousługami za pomocą co najmniej jednej bramy interfejsu API. Bramy interfejsu API są zgodne ze wzorcem "zaplecze frontonu" (BFF), co oznacza, że każda Brama jest zaprojektowana do obsługi danego klienta frontonu. Poszczególne mikrousługi są wyświetlane z prawej strony bram interfejsu API i obejmują zarówno logikę biznesową, jak i pewien rodzaj magazynu trwałości. Różne usługi wykorzystują SQL Server baz danych, wystąpień pamięci podręcznej Redis i magazynów MongoDB/CosmosDB. Po prawej stronie jest magistrala zdarzeń systemu, która jest używana do komunikacji między mikrousługami.

![eShopOnContainers Architecture @ no__t-1**rysunek 2-5**. Architektura eShopOnContainers.

Składniki po stronie serwera tej architektury są łatwo mapowane do usług platformy Azure.

## <a name="container-orchestration-and-clustering"></a>Organizowanie i klastrowanie kontenerów

Usługi hostowane w kontenerach aplikacji, z ASP.NET Core aplikacje MVC do poszczególnych katalogów i mikrousług, mogą być hostowane i zarządzane w usłudze Azure Kubernetes Service (AKS). Aplikacja może działać lokalnie na platformie Docker i Kubernetes, a następnie można wdrożyć te same kontenery w środowiskach przejściowych i produkcyjnych hostowanych w AKS. Ten proces może być zautomatyzowany, ponieważ będziemy widzieć w następnej sekcji.

AKS zapewnia usługi zarządzania dla poszczególnych klastrów kontenerów. Aplikacja będzie wdrażać oddzielne klastry AKS dla każdej mikrousługi pokazanej na diagramie architektury powyżej. Takie podejście umożliwia niezależne skalowanie poszczególnych usług zgodnie z wymaganiami zasobów. Każdą mikrousługi można również wdrożyć niezależnie, a w związku z tym takie wdrożenia powinny spowodować zero przestojów systemu.

## <a name="api-gateway"></a>API Gateway

Aplikacja eShopOnContainers ma wielu klientów frontonu i wiele różnych usług zaplecza. Nie istnieje jeden do jednego między aplikacjami klienckimi i mikrousługami, które je obsługują. W takim scenariuszu może wystąpić bardzo duże zmniejszenie złożoności w przypadku pisania oprogramowania klienckiego do interfejsu z różnymi usługami zaplecza w bezpieczny sposób. Każdy klient musi obsłużyć tę złożoność samodzielnie, co spowoduje duplikowanie i wiele miejsc, w których aktualizacje są wprowadzane po zmianie usług lub implementacji nowych zasad.

Usługa Azure API Management (APIM) pomaga organizacjom publikować interfejsy API w spójny, zarządzany sposób. APIM składa się z trzech składników: bramy interfejsu API i portalu administracyjnego (Azure Portal) i portalu dla deweloperów.

Brama interfejsu API akceptuje wywołania interfejsu API i kieruje je do odpowiedniego interfejsu API zaplecza. Może również udostępniać dodatkowe usługi, takie jak weryfikacja kluczy interfejsu API lub tokeny JWT i transformacja interfejsu API na bieżąco bez modyfikacji kodu (na przykład w celu przeprowadzenia obsługi klientów, które oczekują starszego interfejsu).

Azure Portal to miejsce, w którym można zdefiniować schemat interfejsu API i spakować różne interfejsy API do produktów. Możesz również skonfigurować dostęp użytkowników, wyświetlać raporty i konfigurować zasady dla przydziałów lub transformacji.

Portal dla deweloperów służy jako główny zasób dla deweloperów. Udostępnia ona deweloperom dokumentację interfejsu API, interaktywną konsolę testową i raporty dotyczące własnego użycia. Deweloperzy mogą również używać portalu do tworzenia własnych kont i zarządzania nimi, w tym subskrypcji i obsługi kluczy interfejsu API.

Korzystając z APIM, aplikacje mogą uwidaczniać kilka różnych grup usług, z których każda zapewnia zaplecze dla określonego klienta frontonu. APIM jest zalecana w przypadku złożonych scenariuszy. W celu uproszczenia potrzeb można użyć uproszczonej bramy interfejsu API Ocelot. Aplikacja eShopOnContainers używa Ocelot ze względu na prostotę i ponieważ można ją wdrożyć w tym samym środowisku aplikacji co sama aplikacja. [Dowiedz się więcej na temat eShopOnContainers, APIM i Ocelot.](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

Inną opcją, jeśli aplikacja korzysta z programu AKS, jest wdrożenie kontrolera usługi transferu danych w usłudze Azure Gateway w ramach klastra AKS. Dzięki temu klaster może być zintegrowany z usługą Azure Application Gateway, co pozwala bramie równoważyć obciążenie ruchem do AKSch. [Dowiedz się więcej o kontrolerze usługi Azure Gateway Ingress dla AKS](https://github.com/Azure/application-gateway-kubernetes-ingress).

## <a name="data"></a>Dane

Różne usługi zaplecza używane przez eShopOnContainers mają różne wymagania dotyczące magazynu. Kilka mikrousług używa SQL Server baz danych. Mikrousługa koszyka korzysta z pamięci podręcznej Redis w celu jej trwałości. Mikrousługa lokalizacji oczekuje interfejsu API MongoDB dla swoich danych. Platforma Azure obsługuje wszystkie te formaty danych.

Aby uzyskać pomoc techniczną dla SQL Server bazy danych, platforma Azure oferuje produkty dla wszystkiego z pojedynczych baz danych, do wysoce skalowalnych SQL Database elastycznych pul. Poszczególne mikrousługi można skonfigurować tak, aby szybko i łatwo komunikować się ze swoimi indywidualnymi bazami danych SQL Server. Te bazy danych mogą być skalowane w miarę potrzeb w celu obsługi poszczególnych mikrousług zgodnie z potrzebami.

Aplikacja eShopOnContainers przechowuje bieżący koszyk użytkownika między żądaniami. Jest to zarządzane przez mikrousługę koszyka, która przechowuje dane w pamięci podręcznej Redis. W trakcie tworzenia tej pamięci podręcznej można wdrożyć w kontenerze, podczas gdy w środowisku produkcyjnym można korzystać z pamięci podręcznej platformy Azure dla Redis. Pamięć podręczna Azure for Redis to w pełni zarządzana usługa oferująca wysoką wydajność i niezawodność bez konieczności wdrażania i zarządzania wystąpieniami Redis lub kontenerami.

Mikrousługa lokalizacji używa bazy danych MongoDB NoSQL do jej trwałości. Podczas opracowywania baza danych może zostać wdrożona we własnym kontenerze, a w środowisku produkcyjnym usługa może korzystać z [interfejsu API Azure Cosmos DB dla MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). Jedną z zalet Azure Cosmos DB jest możliwość korzystania z wielu różnych protokołów komunikacyjnych, w tym interfejsu API SQL i wspólnych interfejsów API NoSQL, takich jak MongoDB, Cassandra, Gremlin i Azure Table Storage. Azure Cosmos DB oferuje w pełni zarządzaną i globalnie rozproszoną bazę danych jako usługę, którą można skalować w celu spełnienia potrzeb usług, które go używają.

Dane rozproszone w aplikacjach natywnych w chmurze zostały omówione bardziej szczegółowo w [rozdziale 5](distributed-data.md).

## <a name="event-bus"></a>Magistrala zdarzeń

Aplikacja używa zdarzeń do przekazywania zmian między różnymi usługami. Tę funkcję można zaimplementować przy użyciu różnych implementacji, a lokalnie aplikacja eShopOnContainers używa funkcji [RabbitMQ](https://www.rabbitmq.com/). Gdy aplikacja jest hostowana na platformie Azure, będzie ona używać [Azure Service Bus](https://docs.microsoft.com/azure/service-bus/) do obsługi komunikatów. Azure Service Bus to w pełni zarządzany Broker komunikatów integracji, który umożliwia aplikacjom i usługom komunikowanie się ze sobą w niezależny, niezawodny i asynchroniczny sposób. Azure Service Bus obsługuje poszczególne kolejki oraz oddzielne *Tematy* obsługujące scenariusze dla subskrybentów wydawcy. Aplikacja eShopOnContainers będzie używać tematów z Azure Service Bus do obsługi dystrybuowania komunikatów z jednej mikrousługi do dowolnej innej mikrousług, która wymagała reakcji na daną wiadomość.

## <a name="resiliency"></a>Odporność

Po wdrożeniu w środowisku produkcyjnym aplikacja eShopOnContainers może korzystać z kilku dostępnych usług platformy Azure w celu poprawy jej odporności. Aplikacja publikuje kontrolę kondycji, którą można zintegrować z Application Insights w celu zapewnienia raportów i alertów na podstawie dostępności aplikacji. Zasoby platformy Azure dostarczają również dzienników diagnostycznych, które mogą służyć do identyfikowania i poprawiania błędów i problemów z wydajnością. Dzienniki zasobów zawierają szczegółowe informacje o tym, kiedy i w jaki sposób są używane różne zasoby platformy Azure. Dowiesz się więcej na temat funkcji odporności natywnych w chmurze w [rozdziale 6](resiliency.md).

## <a name="references"></a>Informacje

- [Architektura eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Organizowanie mikrousług i aplikacji wielokontenerowych w celu zapewnienia wysokiej skalowalności i dostępności](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Azure API Management](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Przegląd Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [Interfejs API Azure Cosmos DB dla MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Omówienie usługi Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Poprzedni](introduce-eshoponcontainers-reference-app.md)
>[dalej](deploy-eshoponcontainers-azure.md)
