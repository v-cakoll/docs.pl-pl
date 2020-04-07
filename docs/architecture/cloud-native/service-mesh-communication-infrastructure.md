---
title: Infrastruktura komunikacji z siatką usług
description: Dowiedz się, jak technologie siatki usług usprawniają komunikację mikrousług natywną dla chmury
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 8bb57e990dbf1baf8c246fe4aacfbb2904a251e6
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805755"
---
# <a name="service-mesh-communication-infrastructure"></a>Infrastruktura komunikacji z siatką usług

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tym rozdziale zbadaliśmy wyzwania związane z komunikacją mikrousług. Powiedzieliśmy, że zespoły programistyczne muszą być wrażliwe na sposób komunikowania się ze sobą usług zaplecza. Najlepiej, im mniej komunikacji między usługami, tym lepiej. Jednak unikanie nie zawsze jest możliwe, ponieważ usługi zaplecza często polegają na sobie nawzajem, aby zakończyć operacje.

Zbadaliśmy różne podejścia do implementowania synchroniczowej komunikacji HTTP i komunikacji asynchroniiowej. W każdym przypadku deweloper jest obciążony implementacji kodu komunikacji. Kod komunikacji jest złożony i czasochłonne. Nieprawidłowe decyzje mogą prowadzić do istotnych problemów z wydajnością.

Bardziej nowoczesne podejście do centrów komunikacji mikrousług wokół nowej i szybko rozwijającej się technologii *zatytułowanej Service Mesh*. [Siatka usług](https://www.nginx.com/blog/what-is-a-service-mesh/) to konfigurowalna warstwa infrastruktury z wbudowanymi możliwościami obsługi komunikacji między usługami, odpornością i wieloma problemami przekrojowymi. Przenosi odpowiedzialność za te problemy z mikrousług i do warstwy siatki usługi. Komunikacja jest abstrakcja z dala od mikrousług.

Kluczowym składnikiem siatki usług jest serwer proxy. W aplikacji natywnej dla chmury wystąpienie serwera proxy jest zazwyczaj współlokowane z każdej mikrousługi. Podczas wykonywania w oddzielnych procesów, dwa są ściśle połączone i współużytkują ten sam cykl życia. Ten wzór, znany jako [wzór sidecar,](https://docs.microsoft.com/azure/architecture/patterns/sidecar)i jest pokazany na rysunku 4-24.

![Siatka serwisowa z bocznym samochodem](./media/service-mesh-with-side-car.png)

**Rysunek 4-24**. Siatka serwisowa z bocznym samochodem

Uwaga w poprzednim rysunku, jak wiadomości są przechwytywane przez serwer proxy, który działa obok każdej mikrousługi. Każdy serwer proxy można skonfigurować z reguł ruchu specyficzne dla mikrousługi. Rozumie wiadomości i może kierować je przez twoje usługi i świat zewnętrzny.

Wraz z zarządzaniem komunikacją między usługami usługa mesh zapewnia obsługę odnajdowania usług i równoważenia obciążenia.

Po skonfigurowaniu siatka usługi jest bardzo funkcjonalna. Siatka pobiera odpowiednią pulę wystąpień z punktu końcowego odnajdywania usługi. Wysyła żądanie do określonego wystąpienia usługi, rejestrując opóźnienie i typ odpowiedzi wynik. Wybiera wystąpienie najprawdopodobniej do zwrócenia szybkiej odpowiedzi na podstawie różnych czynników, w tym obserwowane opóźnienie dla ostatnich żądań.

Siatka usług zarządza problemami dotyczącymi ruchu, komunikacji i sieci na poziomie aplikacji. Rozumie wiadomości i żądania. Siatka usługi zazwyczaj integruje się z orchestrator kontenera. Kubernetes obsługuje rozszerzalną architekturę, w której można dodać siatkę usług.

W rozdziale 6 zagłębiamy się w technologie usługi Mesh, w tym dyskusję na temat jego architektury i dostępnych implementacji typu open source.

## <a name="summary"></a>Podsumowanie

W tym rozdziale omówiliśmy wzorce komunikacji natywnej dla chmury. Firma Wece rozpoczęła się od zbadania, jak klienci front-end komunikować się z mikrousług zaplecza. Po drodze rozmawialiśmy o platformach bramy INTERFEJSU API i komunikacji w czasie rzeczywistym. Następnie przyjrzeliśmy się, jak mikrousługi komunikują się z innymi usługami zaplecza. Przyjrzeliśmy się zarówno synchroniczowej komunikacji HTTP, jak i asynchronikom w różnych usługach. Omówiliśmy gRPC, nadchodzącą technologię w świecie macierzystym chmury. Na koniec wprowadziliśmy nową i szybko rozwijającą się technologię o prawach usługi Mesh, która może usprawnić komunikację mikrousług.

Szczególny nacisk położono na zarządzane usługi platformy Azure, które mogą pomóc w zaimplementowanie komunikacji w systemach natywnych dla chmury:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Usługa Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Kolejki usługi Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Centrum zdarzeń Azure](https://azure.microsoft.com/services/event-hubs/)

Następnie przechodzimy do rozproszonych danych w systemach natywnych dla chmury oraz korzyści i wyzwań, jakie stwarza.

### <a name="references"></a>Dokumentacja

- [Mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Projektowanie komunikacji międzyusługowej dla mikrousług](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Usługa Azure SignalR — w pełni zarządzana usługa dodawania funkcji w czasie rzeczywistym](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Kontroler transferu danych przychodzących bramy interfejsu API platformy Azure](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Informacje o ruchu przychodzącym w usłudze Azure Kubernetes Service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Dokumentacja gRPC](https://grpc.io/docs/guides/)

- [gRPC dla deweloperów WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Porównywanie usług gRPC z interfejsami API HTTP](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Tworzenie usług gRPC za pomocą wideo .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Poprzedni](grpc.md)
>[następny](database-per-microservice.md)
