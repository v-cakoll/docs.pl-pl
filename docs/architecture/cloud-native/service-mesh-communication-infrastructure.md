---
title: Infrastruktura komunikacji z siatką usług
description: Dowiedz się więcej na temat sposobu, w jaki technologie sieci w chmurze upraszczają natywną komunikację mikrousług
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 89bc4d307d725e7e31e020ef156c4c5967dd2a1c
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199953"
---
# <a name="service-mesh-communication-infrastructure"></a>Infrastruktura komunikacji z siatką usług

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tym rozdziale zbadamy wyzwania komunikacji mikrousług. Firma Microsoft stwierdziła, że zespoły programistyczne muszą być wrażliwe na to, jak usługi zaplecza komunikują się ze sobą. W idealnym przypadku mniejsza komunikacja między usługami jest lepsza. Jednak unikanie nie zawsze jest możliwe, ponieważ usługi zaplecza często korzystają ze sobą, aby zakończyć operacje.

Zbadamy różne podejścia do implementacji synchronicznej komunikacji HTTP i asynchronicznej obsługi komunikatów. W każdym z tych przypadków deweloper jest w trakcie implementowania kodu komunikacji. Kod komunikacji jest skomplikowany i intensywnie korzystający z czasu. Nieprawidłowe decyzje mogą prowadzić do znaczących problemów z wydajnością.

Bardziej nowoczesne podejście do centrów komunikacji mikrousług obejmujące nową i szybko rozwijający się *technologię.* [Siatka usługi](https://www.nginx.com/blog/what-is-a-service-mesh/) jest konfigurowalną warstwą infrastruktury z wbudowanymi funkcjami do obsługi komunikacji między usługami, odporności i wielu zagadnień związanych z wycinaniem. Przenosi odpowiedzialność za te kwestie dotyczące mikrousług i warstwy sieci usługi. Komunikacja jest wyodrębniana z mikrousług.

Kluczowym elementem siatki usługi jest serwer proxy. W aplikacji natywnej w chmurze wystąpienie serwera proxy jest zazwyczaj współpracujące z każdą mikrousługą. Gdy są one wykonywane w oddzielnych procesach, te dwa są ściśle powiązane i mają ten sam cykl życia. Ten wzorzec, znany jako [wzorzec przyczepki](https://docs.microsoft.com/azure/architecture/patterns/sidecar), jest przedstawiony na rysunku 4-24.

![Siatka usług z samochodem bocznym](./media/service-mesh-with-side-car.png)

**Rysunek 4-24**. Siatka usług z samochodem bocznym

Zwróć uwagę na powyższym rysunku, w jaki sposób komunikaty są przechwytywane przez serwer proxy, który jest uruchamiany razem z każdą mikrousługą. Każdy serwer proxy można skonfigurować przy użyciu reguł ruchu specyficznych dla mikrousługi. Umożliwia ona zrozumienie komunikatów i pozwala na ich kierowanie w ramach usług i na zewnątrz.

Wraz z zarządzaniem komunikacją między usługami usługa ta umożliwia obsługę odnajdywania usług i równoważenia obciążenia.

Po skonfigurowaniu usługi siatka jest wysoce funkcjonalna. Siatka pobiera odpowiednią pulę wystąpień z punktu końcowego odnajdowania usług. Wysyła żądanie do określonego wystąpienia usługi, rejestrując czas oczekiwania i typ odpowiedzi wyniku. Wybiera wystąpienie najlepiej zwracające szybką odpowiedź na podstawie różnych czynników, w tym zaobserwowanych opóźnień dla ostatnich żądań.

Siatka usług zarządza problemami dotyczącymi ruchu, komunikacji i sieci na poziomie aplikacji. Rozpoznaje komunikaty i żądania. Siatka usługi zazwyczaj integruje się z koordynatorem kontenerów. Kubernetes obsługuje rozszerzalną architekturę, w której można dodać siatkę usług.

W rozdziale 6 szczegółowe się z technologiami siatki usług, w tym w dyskusjach dotyczących architektury i dostępnych implementacjach typu "open source".

## <a name="summary"></a>Podsumowanie

W tym rozdziale omówiono wzorce komunikacji natywnej w chmurze. Rozpoczęto badanie, jak klienci frontonu komunikują się z mikrousługami zaplecza. Dzięki temu będziemy mówić o platformach usługi API Gateway i komunikacji w czasie rzeczywistym. Następnie przeglądamy, jak mikrousługi komunikują się z innymi usługami zaplecza. Oglądamy synchroniczną komunikację HTTP i asynchroniczną obsługę komunikatów między usługami. Firma Microsoft pogRPCa, nadchodząca technologia w świecie macierzystym w chmurze. Wreszcie wprowadziliśmy nową i błyskawicznie rozwijający się technologię, która może usprawnić komunikację mikrousług.

Szczególny nacisk na zarządzane usługi platformy Azure, które mogą pomóc w zaimplementowaniu komunikacji w systemach natywnych w chmurze:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Usługa Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Kolejki usługi Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Centrum zdarzeń Azure](https://azure.microsoft.com/services/event-hubs/)

Następnie następnym przejdziemy do danych rozproszonych w systemach natywnych w chmurze oraz korzyści i wyzwania.

### <a name="references"></a>Dokumentacja

- [Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Projektowanie komunikacji międzyusługowej dla mikrousług](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Usługa Azure Signal Service — w pełni zarządzana usługa umożliwiająca dodawanie funkcji w czasie rzeczywistym](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Kontroler usługi transferu danych w usłudze Azure API Gateway](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Informacje o ruchu przychodzącego w usłudze Azure Kubernetes Service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Dokumentacja gRPC](https://grpc.io/docs/guides/)

- [gRPC dla deweloperów WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Porównanie usług gRPC z interfejsami API protokołu HTTP](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Tworzenie usług gRPC z użyciem wideo .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Poprzedni](grpc.md)
>[Następny](distributed-data.md)
