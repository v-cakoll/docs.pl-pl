---
title: Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zrozumienie zdarzeń integracji w celu zaimplementowania komunikacji opartej na zdarzeniach między mikrousługami.
ms.date: 10/02/2018
ms.openlocfilehash: 8a5cfa280063da742dc1693905fc44cf870c1fcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296620"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)

Zgodnie z wcześniejszym opisem, gdy używasz komunikacji opartej na zdarzeniach, mikrousługa publikuje zdarzenie w przypadku, gdy coś się stało, na przykład gdy aktualizuje jednostkę biznesową. Inne mikrousługi subskrybują te zdarzenia. Gdy mikrousługa otrzymuje zdarzenie, może aktualizować własne jednostki biznesowe, co może prowadzić do publikowania większej liczby zdarzeń. Jest to istota koncepcji spójności ostatecznej. Ten system publikowania/subskrybowania jest zwykle wykonywany przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń może być zaprojektowana jako interfejs z interfejsem API, który jest wymagany do subskrybowania i anulowania subskrypcji zdarzeń oraz do publikowania zdarzeń. Może również mieć co najmniej jedną implementację opartą na komunikacji między procesami lub obsługą komunikatów, taką jak kolejka komunikatów lub Usługa Service Bus, która obsługuje komunikację asynchroniczną i model publikowania/subskrybowania.

Zdarzenia mogą służyć do implementowania transakcji handlowych obejmujących wiele usług, co zapewnia spójność między tymi usługami. Ostatecznie spójna transakcja składa się z serii działań rozproszonych. W każdej akcji mikrousługa aktualizuje jednostkę biznesową i publikuje zdarzenie, które wyzwala następną akcję.

![Usługa Catalog, która korzysta z komunikacji sterowanej zdarzeniami za pośrednictwem magistrali zdarzeń, w celu zapewnienia spójności ostatecznej dzięki koszykowi i dodatkowym mikrousługom.](./media/image19.png)

**Rysunek 6-18**. Komunikacja sterowana zdarzeniami oparta na magistrali zdarzeń

W tej sekcji opisano, jak można zaimplementować ten typ komunikacji z platformą .NET przy użyciu ogólnego interfejsu magistrali zdarzeń, jak pokazano na rysunku 6-18. Istnieje wiele potencjalnych implementacji, z których każda korzysta z innej technologii lub infrastruktury, takiej jak RabbitMQ, Azure Service Bus lub jakakolwiek inna usługa typu open-source innej firmy lub komercyjnej usługi Service Bus.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Korzystanie z brokerów komunikatów i magistrali usług dla systemów produkcyjnych

Zgodnie z opisem w sekcji architektura można wybrać jedną z wielu technologii obsługi komunikatów w celu zaimplementowania abstrakcyjnej magistrali zdarzeń. Jednak te technologie są na różnych poziomach. Na przykład RabbitMQ, transport brokera komunikatów, znajduje się na niższym poziomie niż produkty komercyjne, takie jak Azure Service Bus, NServiceBus, MassTransit lub jaśniejszy. Większość z tych produktów może korzystać z RabbitMQ lub Azure Service Bus. Wybór produktu zależy od tego, ile funkcji i ile jest potrzebnych skalowalności aplikacji.

W celu zaimplementowania tylko weryfikacji usługi Event Bus dla środowiska deweloperskiego, tak jak w przykładzie eShopOnContainers, prosta implementacja na RabbitMQ działa jako kontener może być wystarczająca. Jednak w przypadku systemów o znaczeniu krytycznym i produkcyjnym wymagających wysokiej skalowalności warto oszacować i użyć Azure Service Bus.

Jeśli wymagane są abstrakcje wysokiego poziomu i bogatsze funkcje, takie jak [sagach](https://docs.particular.net/nservicebus/sagas/) dla długotrwałych procesów, które ułatwiają opracowywanie rozproszonego, inne komercyjne i typu "open source", takie jak NServiceBus, MassTransit i jaśniejszy oceny. W takim przypadku abstrakcje i interfejsy API, które mają być używane, zwykle są bezpośrednio podane przez te magistrale usług wyższego poziomu zamiast własnych streszczeń (takich jak [proste abstrakcje magistrali zdarzeń dostępne w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). W takim przypadku można zbadać [eShopOnContainers rozwidlenia przy użyciu NServiceBus](https://go.particular.net/eShopOnContainers) (dodatkowe pochodne próbki zaimplementowane przez określone oprogramowanie)

Oczywiście można zawsze tworzyć własne funkcje usługi Service Bus na podstawie technologii niższego poziomu, takich jak RabbitMQ i Docker, ale pracy wymaganej do "odtworzenia kółka" może być zbyt kosztowne dla niestandardowej aplikacji przedsiębiorstwa.

Aby wykonać ponownie iterację: abstrakcje i implementacje magistrali zdarzeń opisane w próbce eShopOnContainers są przeznaczone do użycia tylko jako Weryfikacja koncepcji. Po ustaleniu, że chcesz mieć komunikację asynchroniczną i opartą na zdarzeniach, jak wyjaśniono w bieżącej sekcji, należy wybrać produkt usługi Service Bus, który najlepiej odpowiada Twoim potrzebom produkcyjnym.

## <a name="integration-events"></a>Zdarzenia integracji

Zdarzenia integracji służą do przełączania stanu domeny w ramach wielu mikrousług lub systemów zewnętrznych. Jest to realizowane przez opublikowanie zdarzeń integracji poza mikrousługą. W przypadku opublikowania zdarzenia w wielu mikrousługach odbiornika (do jak wielu mikrousług jako subskrybowanych przez zdarzenie integracji) odpowiednia procedura obsługi zdarzeń w każdej mikrousłudze odbiornika obsługuje zdarzenie.

Zdarzenie integracji jest zasadniczo klasą holdingu danych, jak w poniższym przykładzie:

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

Zdarzenia integracji można definiować na poziomie aplikacji każdej mikrousług, dzięki czemu są one oddzielone od innych mikrousług, podobnie jak modele widoków są zdefiniowane na serwerze i kliencie. Nie zaleca się udostępniania wspólnej biblioteki zdarzeń integracji w wielu mikrousługach; Dzięki temu można sprzęgać te mikrousługi za pomocą pojedynczej biblioteki danych definicji zdarzenia. Nie chcesz tego robić z tego samego powodu, w którym nie chcesz udostępniać wspólnego modelu domeny w wielu mikrousługach: mikrousługi muszą być całkowicie autonomiczne.

Istnieje tylko kilka rodzajów bibliotek, które powinny być współużytkowane przez mikrousługi. Jedną z nich są biblioteki, które są końcowymi blokami aplikacji, na przykład [interfejs API klienta usługi Event Bus](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jak w eShopOnContainers. Inne to biblioteki, które stanowią narzędzia, które mogą być również udostępniane jako składniki NuGet, takie jak serializatory JSON.

## <a name="the-event-bus"></a>Magistrala zdarzeń

Magistrala zdarzeń umożliwia komunikację w stylu publikacji/subskrypcji między mikrousługami bez konieczności jawnego informowania składników, jak pokazano na rysunku 6-19.

![Podstawowa Patter pub/sub, mikrousługa A publikuje w usłudze Event Bus, która dystrybuuje w celu subskrybowania mikrousług B i C, bez konieczności poznania subskrybentów przez wydawcę.](./media/image20.png)

**Rysunek 6-19**. Podstawowe informacje dotyczące publikowania/subskrybowania za pomocą usługi Event Bus

Magistrala zdarzeń jest powiązana ze wzorcem obserwatora i wzorcem publikowania/subskrybowania.

### <a name="observer-pattern"></a>Wzorzec obserwatora

We [wzorcu obserwatora](https://en.wikipedia.org/wiki/Observer_pattern)obiekt podstawowy (znany jako widoczny) powiadamia inne zainteresowane obiekty (zwane obserwatorami) z odpowiednimi informacjami (zdarzenia).

### <a name="publishsubscribe-pubsub-pattern"></a>Wzorzec publikowania/subskrybowania (pub/Sub)

Celem [wzorca publikowania/subskrybowania](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) jest taka sama jak wzorzec obserwatora: chcesz powiadomić inne usługi o wystąpieniu pewnych zdarzeń. Ale istnieje istotna różnica między wzorcem obserwatora a publikowaniem/podrzędnym. We wzorcu obserwatora emisja jest wykonywana bezpośrednio od zauważalnych obserwatorów, więc "wiedzą". Jednak w przypadku korzystania ze wzorca publikowania/sub, istnieje trzeci składnik, nazywany brokerem lub brokerem komunikatów lub magistralą zdarzeń, który jest znany przez wydawcę i abonenta. W związku z tym w przypadku używania wzorca publikowania/podłączania Wydawca i Subskrybenci są precyzyjnie oddzielone przez wymienioną magistralę zdarzeń lub brokera komunikatów.

### <a name="the-middleman-or-event-bus"></a>Centrum oprogramowania lub magistrali zdarzeń

Jak uzyskać anonimowość między wydawcą a subskrybentem? Prostym sposobem jest poinformowanie o całej komunikacji przez centrum. Magistrala zdarzeń to ten środek pośredniczący.

Magistrala zdarzeń zwykle składa się z dwóch części:

- Streszczenie lub interfejs.

- Co najmniej jedna implementacja.

Na rysunku 6-19 można zobaczyć, jak, z punktu widzenia aplikacji, magistrala zdarzeń nie ma więcej niż w oddzielnym kanale pub/sub. Sposób implementacji komunikacji asynchronicznej może się różnić. Może być wiele implementacji, aby można było zamienić między nimi, w zależności od wymagań środowiska (na przykład środowiska produkcyjnego i środowisk deweloperskich).

Na rysunku 6-20 można zobaczyć abstrakcję magistrali zdarzeń z wieloma implementacjami na podstawie technologii obsługi komunikatów infrastruktury, takich jak RabbitMQ, Azure Service Bus lub innego brokera zdarzeń/komunikatów.

![Dobrym sposobem jest użycie magistrali zdarzeń zdefiniowanej za pomocą interfejsu, aby można ją było zaimplementować przy użyciu kilku technologii, takich jak RabbitMQ usługi Azure Service Bus lub innych.](./media/image21.png)

**Rysunek 6-20.** Wiele implementacji magistrali zdarzeń

Jednak jak wspomniano wcześniej, użycie własnych streszczeń (interfejsu magistrali zdarzeń) jest dobre tylko wtedy, gdy potrzebne są podstawowe funkcje magistrali zdarzeń obsługiwane przez abstrakcyjne. Jeśli potrzebujesz bogatszych funkcji usługi Service Bus, prawdopodobnie Użyj interfejsu API i abstrakcji udostępnianych przez preferowaną komercyjną usługę Service Bus zamiast własnych streszczeń.

### <a name="defining-an-event-bus-interface"></a>Definiowanie interfejsu magistrali zdarzeń

Zacznijmy od pewnego kodu implementacji dla interfejsu usługi Event Bus i możliwych implementacji dla celów eksploracji. Interfejs powinien być ogólny i prosty, tak jak w poniższym interfejsie.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

`Publish` Metoda jest prosta. Magistrala zdarzeń będzie emitować przesłane do niej zdarzenie integracji z dowolną mikrousługą, a nawet z aplikacją zewnętrzną, która subskrybuje to zdarzenie. Ta metoda jest używana przez mikrousługę, która publikuje zdarzenie.

`Subscribe` Metody (mogą być dostępne różne implementacje zależne od argumentów) są używane przez mikrousługi, które chcą odbierać zdarzenia. Ta metoda ma dwa argumenty. Pierwsze jest zdarzeniem integracji subskrybowanym przez usługę (`IntegrationEvent`). Drugim argumentem jest program obsługi zdarzeń integracji (lub metoda wywołania zwrotnego) `IIntegrationEventHandler<T>`o nazwie, który ma być wykonywany, gdy mikrousługa odbiornika pobiera ten komunikat o zdarzeniu integracji.

> [!div class="step-by-step"]
> [Poprzedni](database-server-container.md)Następny
> [](rabbitmq-event-bus-development-test-environment.md)
