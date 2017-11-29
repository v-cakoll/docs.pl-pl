---
title: "Implementowanie oparty na zdarzeniach komunikacji między mikrousług (zdarzeń integracji)"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie oparty na zdarzeniach komunikacji między mikrousług (zdarzeń integracji)"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementowanie oparty na zdarzeniach komunikacji między mikrousług (zdarzeń integracji)

Jak opisano wcześniej, gdy użytkownik korzysta z komunikacji oparty na zdarzeniach, mikrousługi publikuje zdarzenia zauważalne najważniejsza, takie jak kiedy aktualizuje jednostki biznesowej. Inne mikrousług subskrybować tych zdarzeń. Po mikrousługi odbiera zdarzenia, go zaktualizować własną jednostki biznesowe, które może prowadzić do zdarzeń publikowana. Ten system publikowania/subskrypcji zwykle odbywa się przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń mogą służyć jako interfejs przy użyciu interfejsu API potrzebne umożliwia subskrybowanie i anulowanie subskrypcji zdarzeń i publikowanie zdarzeń. Może mieć także co najmniej jeden implementacje oparte na wszelkie komunikacji między procesami lub obsługi wiadomości, takie jak kolejki wiadomości lub obsługującego komunikacji asynchronicznej i modelu publikowania/subskrypcji usługi service bus.

Służy zdarzenia do zaimplementowania transakcje biznesowe, które obejmują wiele usług zapewniający spójność ostateczna między tymi usługami. Po pewnym czasie spójne transakcji składa się z szeregu rozproszonej akcji. W każdej akcji mikrousługi aktualizuje jednostek biznesowych i publikuje zdarzenie, które wyzwala następnej akcji.

![](./media/image19.PNG)

**Rysunek 8-18**. Sterowane zdarzeniami komunikacji oparte na magistrali zdarzeń

W tej sekcji opisano, jak można wdrożyć ten typ komunikacji z platformą .NET przy użyciu interfejsem magistrali zdarzeń rodzajowych, jak pokazano w rysunek 8-18. Istnieje wiele potencjalnych implementacji, każdy przy użyciu różnych technologii lub infrastruktury, takich jak RabbitMQ, Azure Service Bus lub innych firm typu open source lub komercyjnego usługi service bus.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Za pomocą magistrali usług i brokerzy komunikat dla systemów produkcyjnych.

Jak wspomniano w sekcji architektury, są dostępne z wielu technologii obsługi komunikatów dla implementacji magistrali sieci zdarzenia abstrakcyjnego. Ale technologie te są na różnych poziomach. Na przykład RabbitMQ, transportu brokera obsługi komunikatów, jest na poziomie niższym niż komercyjnych produkty, takie jak usługi Azure Service Bus, NServiceBus, MassTransit lub Brighter. Większość tych produktów może pracować na górze RabbitMQ lub usługi Azure Service Bus. Wybór produktu zależy od tego, jak wiele funkcji i skalowalność ile out-of--box potrzebne dla aplikacji.

Wykonywania tylko zdarzenia magistrali z koncepcji dla swojego środowiska programowania, jak próbki eShopOnContainers prostych implementacji u góry RabbitMQ uruchomione jako kontener może być wystarczającej ilości. Nawet w przypadku krytycznym i systemów produkcyjnych, które wymagają wysokiej skalowalności, można ocenić i użycie sieci szkieletowej usług Azure. Jeśli wymagają wysokiego poziomu obiektów abstrakcyjnych i bardziej rozbudowane funkcje, takie jak [sagas](https://docs.particular.net/nservicebus/sagas/) dla procesów długotrwałe, które należy rozproszonej programowanie magistrali łatwiejsze, inne usługi handlowych i open source, takie jak NServiceBus, MassTransit, i Brighter są warto oceny. Oczywiście zawsze można zbudować własnych funkcji magistrali usług na niższym poziomie technologii, takich jak RabbitMQ i Docker, ale pracy wymaganej do reinvent koła może być zbyt kosztowne stosowania niestandardowego.

Aby przywołują: przykładowe zdarzenie magistrali abstrakcje i implementacja pokazywane w przykładowym eShopOnContainers mają na celu można użyć tylko jako Weryfikacja koncepcji. Po określeniu, czy mają komunikacji asynchronicznej i sterowane zdarzeniami, zgodnie z objaśnieniem w bieżącej sekcji, należy wybrać produktu magistrali usług, która najlepiej odpowiada Twoim potrzebom.

## <a name="integration-events"></a>Zdarzenia integracji

Integracja zdarzenia są używane do pobierania stanu domeny synchronizację wielu mikrousług lub systemami zewnętrznymi. Jest to realizowane przez publikowanie zdarzeń integracji poza mikrousługi. Gdy zdarzenie zostanie opublikowany do wielu mikrousług odbiornika (na tyle mikrousług jako subskrybuje zdarzenia integracji), program obsługi zdarzeń odpowiednie w każdym mikrousługi odbiornika obsługuje zdarzenie.

Zdarzenie integracji jest zasadniczo klasy używane do przechowywania danych, jak w poniższym przykładzie:

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

Klasa zdarzeń integracji może być prosty; na przykład może zawierać identyfikator GUID dla jej identyfikatora.

Zdarzenia integracji można zdefiniować na poziomie aplikacji z każdym mikrousługi, są one całkowicie niezależna od innych mikrousług w sposób można porównywać jak ViewModels są definiowane w serwera i klienta. Co nie jest zalecane jest udostępnianie wspólnej biblioteki zdarzeń integracji między wieloma mikrousług; operacją może być sprzężenia tych mikrousług z biblioteki pojedyncze zdarzenie definicji danych. Czy chcesz to zrobić na takie same powodów, dla których nie chcesz udostępniać wspólnego modelu domeny między wieloma mikrousług: mikrousług musi być całkowicie autonomicznego.

Istnieje tylko kilka rodzajów bibliotek, które powinny współużytkować między mikrousług. Jeden z nich jest bibliotek, które są blokami końcowego aplikacji, takie jak [interfejs API klienta magistrali zdarzeń](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)w eShopOnContainers. Inny jest bibliotek wchodzących w skład narzędzi, które również zostaną udostępnione jako części NuGet, takich jak serializatorów JSON.

## <a name="the-event-bus"></a>Magistrala zdarzeń

Magistrala zdarzeń umożliwia publikowania/subskrybowania — styl komunikacji między mikrousług bez konieczności składniki jawnie mieć świadomość, jak pokazano w rysunek 8-19.

![](./media/image20.png)

**Rysunek 8-19**. Podstawy z magistralą zdarzeń publikowania/subskrypcji

Magistrala zdarzenia jest powiązany z wzorzec obserwatora i opublikuj-subskrypcji wzorzec.

### <a name="observer-pattern"></a>Wzorzec obserwatora

W [wzorzec obserwatora](https://en.wikipedia.org/wiki/Observer_pattern), obiektu podstawowego (nazywane według) powiadamia innych zainteresowanych obiektów (znany jako obserwatorzy) istotnych informacji (zdarzeń).

### <a name="publish-subscribe-pubsub-pattern"></a>Wzorzec publikowania / subskrypcji (Pub/Sub) 

Celem [wzorzec Pub/Sub](https://msdn.microsoft.com/en-us/library/ff649664.aspx) jest taka sama jak wzorzec obserwatora: chcesz powiadomić inne usługi, gdy określone zdarzenia została wykonana. Występuje semantycznego istotną różnicą między wzorce obserwatora i Pub/Sub. We wzorcu Pub/Sub koncentruje się na wiadomości emisji. Z kolei we wzorcu obserwatora według nie może określić kto zdarzenia mają być, właśnie tę zrealizowane limit. Innymi słowy według (wydawcy) nie może określić kto są obserwatorzy (subskrybentów).

### <a name="the-middleman-or-event-bus"></a>Magistrala pośredników lub zdarzenia 

Jak uzyskać anonimowość między wydawcy i subskrybenta? Łatwo jest let pośredników zajmie się całej komunikacji. Magistrali zdarzeń jest jedną z takich pośredników.

Magistrala zdarzeń zazwyczaj składa się z dwóch części:

-   Abstrakcja lub interfejs.

-   Co najmniej jeden implementacji.

W rysunek 8-19 widać sposób, z punktu widzenia aplikacji, magistrali zdarzeń ma więcej niż kanał Pub/Sub. Sposób wykonania tej komunikacji asynchronicznej może się różnić. Dzięki czemu można wymienić między nimi, w zależności od wymagań środowiska (na przykład produkcyjnym i środowisk deweloperskich) może mieć wiele implementacji.

W rysunek 8-20 wyświetlane abstrakcję magistrali zdarzenia o wiele implementacji oparte na infrastrukturze obsługi wiadomości technologii, takich jak RabbitMQ, usługi Azure Service Bus lub innych magistrali usługi NServiceBus, MassTransit itd.

![](./media/image21.png)

**Rysunek 8 - 20.** Wiele implementacji magistrali zdarzeń

Jednak jak wyróżniono wcześniej przy użyciu obiektów abstrakcyjnych (interfejsu zdarzenia magistrali) jest możliwe tylko wtedy, gdy potrzebujesz funkcji magistrali podstawowego zdarzenia obsługiwane przez użytkownika obiekty abstrakcyjne. Jeśli potrzebujesz bardziej rozbudowane funkcje magistrali usług, prawdopodobnie należy używać pochodzącymi z preferowanych usługi service bus zamiast własnych abstrakcje interfejsu API.

### <a name="defining-an-event-bus-interface"></a>Definiowanie interfejsu magistrali zdarzeń

Zacznijmy możliwe implementacji dla celów eksploracji i niektóre kod implementacji interfejsu zdarzenia magistrali. Interfejs powinna być rodzajowa i proste, jak interfejsu.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

Metoda publikowania jest prosta. Magistrala zdarzeń będzie emisji zdarzeń integracji przekazanego do dowolnego mikrousługi subskrybowane dla tego zdarzenia. Ta metoda jest używana przez mikrousługi, która publikuje zdarzenia.

Metoda Subskrybuj jest używana przez mikrousług, który chcesz otrzymywać zdarzeń. Ta metoda ma dwie części. Pierwsza to zdarzenie integracji subskrybować (IntegrationEvent). Druga część to integracji programu obsługi zdarzeń (lub metoda wywołania zwrotnego) ma być wywoływana (IIntegrationEventHandler&lt;T&gt;) po mikrousługi odbiera ten komunikat zdarzeń integracji.


>[!div class="step-by-step"]
[Poprzednie] (bazy danych server-container.md) [dalej] (rabbitmq-event-bus-development-test-environment.md)
