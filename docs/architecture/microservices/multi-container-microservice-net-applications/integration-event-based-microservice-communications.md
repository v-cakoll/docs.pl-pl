---
title: Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumienie zdarzeń integracji w celu zaimplementowania komunikacji opartej na zdarzeniach między mikrousługami.
ms.date: 10/02/2018
ms.openlocfilehash: 6d4e324a05def91935a82df41c971a75cb75c3f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712406"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)

Jak opisano wcześniej, podczas korzystania z komunikacji opartej na zdarzeniach mikrousługi publikuje zdarzenie, gdy coś godnego uwagi dzieje się, na przykład, gdy aktualizuje jednostkę biznesową. Inne mikrousługi subskrybują te zdarzenia. Gdy mikrousługa odbiera zdarzenie, można zaktualizować własne jednostki biznesowe, co może prowadzić do więcej zdarzeń są publikowane. Jest to istota koncepcji spójności ostatecznej. Ten system publikowania/subskrybowania jest zwykle wykonywane przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń może być zaprojektowana jako interfejs z interfejsem API potrzebnym do subskrybowania i anulowania subskrypcji zdarzeń oraz publikowania zdarzeń. Może również mieć co najmniej jedną implementacje na podstawie dowolnej komunikacji między procesami lub wiadomościami, takiej jak kolejka obsługi wiadomości lub magistrala usług, która obsługuje komunikację asynchroniczną i model publikowania/subskrybowania.

Zdarzenia można użyć do zaimplementowania transakcji biznesowych, które obejmują wiele usług, co zapewnia spójność ostateczną między tymi usługami. Ostatecznie spójna transakcja składa się z serii akcji rozproszonych. Przy każdej akcji mikrousługi aktualizuje jednostkę biznesową i publikuje zdarzenie, które wyzwala następną akcję. Rysunek 6-18 poniżej pokazuje PriceUpdated zdarzenie opublikowane za pośrednictwem i magistrali zdarzeń, więc aktualizacja cen jest propagowane do koszyka i innych mikrousług.

![Diagram komunikacji asynchronicznej opartej na zdarzeniach z magistralą zdarzeń.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Rysunek 6-18**. Komunikacja oparta na zdarzeniach oparta na magistrali zdarzeń

W tej sekcji opisano, jak można zaimplementować tego typu komunikacji z .NET przy użyciu interfejsu ogólnej magistrali zdarzeń, jak pokazano na rysunku 6-18. Istnieje wiele potencjalnych implementacji, z których każda korzysta z innej technologii lub infrastruktury, takiej jak RabbitMQ, Azure Service Bus lub innej innej firmy typu open source lub komercyjnej magistrali usług.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Korzystanie z brokerów komunikatów i autobusów usługowych dla systemów produkcyjnych

Jak wspomniano w sekcji architektury, można wybrać jedną z wielu technologii obsługi wiadomości do implementowania magistrali zdarzeń abstrakcyjnych. Ale te technologie są na różnych poziomach. Na przykład RabbitMQ, transport brokera obsługi wiadomości, jest na niższym poziomie niż produkty komercyjne, takie jak usługa Azure Service Bus, NServiceBus, MassTransit lub Brighter. Większość z tych produktów może działać na górze RabbitMQ lub Usługi Azure Service Bus. Wybór produktu zależy od liczby funkcji i ilości niedostępnej skalowalności potrzebnej do zastosowania.

Do implementowania tylko system weryfikacji magistrali zdarzeń dla środowiska programistycznego, jak w przykładzie eShopOnContainers, wystarczy prosta implementacja na górze RabbitMQ uruchomiony jako kontener. Jednak w przypadku systemów o znaczeniu krytycznym i produkcyjnych, które wymagają wysokiej skalowalności, można ocenić usługę Azure Service Bus i korzystać z niej.

Jeśli potrzebujesz abstrakcji wysokiego poziomu i bogatszych funkcji, takich jak Sagas dla [długotrwałych](https://docs.particular.net/nservicebus/sagas/) procesów, które ułatwiają rozwój rozproszony, warto ocenić inne komercyjne i open source magistrale, takie jak NServiceBus, MassTransit i Brighter. W takim przypadku abstrakcje i interfejs API do użycia będzie zwykle bezpośrednio te dostarczane przez te magistrale usług wysokiego poziomu zamiast własnych abstrakcji (jak [abstrakcje prostej magistrali zdarzeń dostarczonych w eShopOnContainers).](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs) O to chodzi, można zbadać [rozwidliwe eShopOnContainers przy użyciu NServiceBus](https://go.particular.net/eShopOnContainers) (dodatkowe próbki pochodne zaimplementowane przez oprogramowanie particular).

Oczywiście zawsze możesz zbudować własne funkcje magistrali usług na technologiach niższego poziomu, takich jak RabbitMQ i Docker, ale praca potrzebna do "ponownego wynalezienia koła" może być zbyt kosztowna dla niestandardowej aplikacji dla przedsiębiorstw.

Aby powtórzyć: abstrakcje magistrali zdarzeń przykładowych i implementacji prezentowane w przykładzie eShopOnContainers są przeznaczone tylko jako dowód koncepcji. Po podjęciu decyzji, że chcesz mieć komunikację asynchroniczną i opartą na zdarzeniach, jak wyjaśniono w bieżącej sekcji, należy wybrać produkt magistrali usług, który najlepiej odpowiada Twoim potrzebom w środowisku produkcyjnym.

## <a name="integration-events"></a>Wydarzenia integracyjne

Zdarzenia integracji są używane do synchronizacji stanu domeny w wielu mikrousługach lub systemach zewnętrznych. Odbywa się to przez publikowanie zdarzeń integracji poza mikrousług. Gdy zdarzenie jest publikowane do wielu mikrousług odbiornika (do tylu mikrousług, jak są subskrybowane do zdarzenia integracji), odpowiedni program obsługi zdarzeń w każdym mikrousługi odbiornika obsługuje zdarzenie.

Zdarzenie integracji jest w zasadzie klasy przechowywania danych, jak w poniższym przykładzie:

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

Zdarzenia integracji można zdefiniować na poziomie aplikacji każdej mikrousługi, więc są one oddzielone od innych mikrousług, w sposób porównywalny do sposobu ViewModels są zdefiniowane na serwerze i kliencie. Co nie jest zalecane jest udostępnianie biblioteki typowych zdarzeń integracji w wielu mikrousług; w ten sposób będzie sprzężenie tych mikrousług z biblioteki danych definicji pojedynczego zdarzenia. Nie chcesz to zrobić z tych samych powodów, które nie chcesz współużytkować wspólny model domeny w wielu mikrousług: mikrousług musi być całkowicie autonomiczne.

Istnieje tylko kilka rodzajów bibliotek, które należy udostępnić w mikrousługach. Jednym z nich są biblioteki, które są blokami aplikacji końcowych, takich jak [interfejs API klienta magistrali zdarzeń](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jak w eShopOnContainers. Innym jest biblioteki, które stanowią narzędzia, które mogą być również współużytkowane jako składniki NuGet, takie jak serializatory JSON.

## <a name="the-event-bus"></a>Autobus imprezowy

Magistrala zdarzeń umożliwia komunikację w stylu publikowania/subskrybowania między mikrousługami bez konieczności używania składników jawnie świadomych siebie nawzajem, jak pokazano na rysunku 6-19.

![Diagram przedstawiający podstawowy wzorzec publikowania/subskrybowania.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Rysunek 6-19**. Publikowanie/subskrybowanie podstawowych za pomocą magistrali zdarzeń

Powyższy diagram pokazuje, że mikrousługi A publikuje do usługi Event Bus, która dystrybuuje do subskrypcji mikrousług B i C, bez wydawcy konieczności poznania subskrybentów. Magistrala zdarzeń jest powiązana ze wzorcem Obserwatora i wzorcem publikowania i subskrybowania.

### <a name="observer-pattern"></a>Wzór obserwatora

We [wzorcu obserwatora](https://en.wikipedia.org/wiki/Observer_pattern)obiekt podstawowy (znany jako Obserwowalny) powiadamia inne zainteresowane obiekty (znane jako obserwatorzy) odpowiednimi informacjami (zdarzeniami).

### <a name="publishsubscribe-pubsub-pattern"></a>Wzorzec publikowania/subskrybowania (Pub/Sub)

Celem [publikowania/subskrybowania wzorzec](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) jest taki sam jak wzorca obserwatora: chcesz powiadomić inne usługi, gdy pewne zdarzenia mają miejsce. Istnieje jednak istotna różnica między wzorcami Obserwatora i Pub/Sub. We wzorcu obserwatora transmisja jest wykonywana bezpośrednio z obserwowalnych obserwatorów, więc "znają się" na siebie. Ale podczas korzystania z wzorca Pub/Sub istnieje trzeci składnik, nazywany brokerem lub brokerem komunikatów lub magistralią zdarzeń, który jest znany zarówno wydawcy, jak i subskrybentowi. W związku z tym podczas korzystania z wzorca Pub/Sub wydawcy i subskrybentów są dokładnie oddzielone dzięki wspomnianej magistrali zdarzeń lub brokera komunikatów.

### <a name="the-middleman-or-event-bus"></a>Pośrednik lub autobus imprezowy

Jak uzyskać anonimowość między wydawcą a subskrybentem? Łatwym sposobem jest niech pośrednik zajmie się całą komunikacją. Autobus zdarzeń jest jednym z takich pośredników.

Magistrala zdarzeń składa się zazwyczaj z dwóch części:

- Abstrakcja lub interfejs.

- Co najmniej jedna implementacja.

Na rysunku 6-19 można zobaczyć, jak z punktu widzenia aplikacji magistrala zdarzeń jest niczym więcej niż kanałem Pub/Sub. Sposób implementowania tej komunikacji asynchronicznej może się różnić. Może mieć wiele implementacji, dzięki czemu można wymieniać między nimi, w zależności od wymagań środowiskowych (na przykład środowiska produkcyjne go i programistyczne).

Na rysunku 6-20 można zobaczyć abstrakcję magistrali zdarzeń z wieloma implementacjami opartymi na technologiach obsługi wiadomości infrastruktury, takich jak RabbitMQ, Usługa Azure Service Bus lub inny broker zdarzeń/komunikatów.

![Diagram przedstawiający dodanie warstwy abstrakcji magistrali zdarzeń.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Rysunek 6- 20.** Wiele implementacji magistrali zdarzeń

Dobrze jest mieć magistrali zdarzeń zdefiniowane za pośrednictwem interfejsu, dzięki czemu można zaimplementować za pomocą kilku technologii, takich jak rabbitMQ azure service bus lub innych. Jednak i jak wspomniano wcześniej, przy użyciu własnych abstrakcji (interfejs magistrali zdarzeń) jest dobre tylko wtedy, gdy potrzebne są podstawowe funkcje magistrali zdarzeń obsługiwane przez abstrakcje. Jeśli potrzebujesz bogatszych funkcji magistrali usług, prawdopodobnie należy użyć interfejsu API i abstrakcji dostarczonych przez preferowaną komercyjną magistralię usług zamiast własnych abstrakcji.

### <a name="defining-an-event-bus-interface"></a>Definiowanie interfejsu magistrali zdarzeń

Zacznijmy od kodu implementacji dla interfejsu magistrali zdarzeń i możliwych implementacji do celów eksploracji. Interfejs powinien być ogólny i prosty, jak w poniższym interfejsie.

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

Metoda `Publish` jest prosta. Magistrala zdarzeń będzie emitować zdarzenie integracji przekazywane do dowolnego mikrousługi lub nawet aplikacji zewnętrznej, subskrybowane do tego zdarzenia. Ta metoda jest używana przez mikrousługę, która publikuje zdarzenie.

`Subscribe` Metody (może mieć kilka implementacji w zależności od argumentów) są używane przez mikrousług, które mają odbierać zdarzenia. Ta metoda ma dwa argumenty. Pierwszym z nich jest zdarzenie`IntegrationEvent`integracji do subskrybowania ( ). Drugi argument jest obsługi zdarzeń integracji (lub `IIntegrationEventHandler<T>`metody wywołania wywołania wywołania), o nazwie , które mają być wykonywane, gdy mikrousługi odbiornika pobiera ten komunikat zdarzenia integracji.

## <a name="additional-resources"></a>Zasoby dodatkowe

Niektóre rozwiązania do obsługi wiadomości gotowe do produkcji:

- **Usługa usługi Azure** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **Usługa NServiceBus** \
  <https://particular.net/nservicebus>
  
- **Transport masowy** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Poprzedni](database-server-container.md)
> [następny](rabbitmq-event-bus-development-test-environment.md)
