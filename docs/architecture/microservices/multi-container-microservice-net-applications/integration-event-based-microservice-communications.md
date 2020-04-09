---
title: Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zrozumienie zdarzeń integracji w celu zaimplementowania komunikacji opartej na zdarzeniach między mikrousługami.
ms.date: 10/02/2018
ms.openlocfilehash: 8a1d4950247d63e5684c85c029efccf8269e7435
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988326"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)

Jak opisano wcześniej, podczas korzystania z komunikacji opartej na zdarzeniach mikrousługi publikuje zdarzenie, gdy dzieje się coś godnego uwagi, na przykład podczas aktualizacji jednostki biznesowej. Inne mikrousługi subskrybują te zdarzenia. Gdy mikrousługa odbiera zdarzenie, można zaktualizować własne jednostki biznesowe, co może prowadzić do publikowania większej liczby zdarzeń. Jest to istota koncepcji ostatecznej spójności. Ten system publikowania/subskrybowania jest zwykle wykonywane przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń może być zaprojektowana jako interfejs z interfejsem API potrzebny do subskrybowania i anulowania subskrypcji zdarzeń i publikowania zdarzeń. Może również mieć jedną lub więcej implementacji na podstawie komunikacji między procesami lub obsługi wiadomości, takich jak kolejka obsługi wiadomości lub magistrala usługi, która obsługuje komunikację asynchronizacę i model publikowania/subskrybowania.

Zdarzenia można użyć do zaimplementowania transakcji biznesowych, które obejmują wiele usług, co zapewnia spójność ostateczną między tymi usługami. Ostatecznie spójna transakcja składa się z serii akcji rozproszonych. Przy każdej akcji mikrousługi aktualizuje jednostki biznesowej i publikuje zdarzenie, które wyzwala następną akcję. Rysunek 6-18 poniżej, pokazuje PriceUpdated zdarzenie opublikowane za pośrednictwem i magistrali zdarzeń, więc aktualizacja ceny jest propagowane do koszyka i innych mikrousług.

![Diagram komunikacji asynchroniiowej sterowanej zdarzeniami z magistralą zdarzeń.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Rysunek 6-18**. Komunikacja oparta na zdarzeniach na podstawie magistrali zdarzeń

W tej sekcji opisano, jak można zaimplementować tego typu komunikacji z .NET przy użyciu ogólnego interfejsu magistrali zdarzeń, jak pokazano na rysunku 6-18. Istnieje wiele potencjalnych implementacji, z których każda korzysta z innej technologii lub infrastruktury, takiej jak RabbitMQ, usługa Azure Service Bus lub inna zewnętrzna magistrala usług typu open source lub komercyjna.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Korzystanie z brokerów komunikatów i magistrali usług dla systemów produkcyjnych

Jak wspomniano w sekcji architektury, można wybrać jedną z wielu technologii obsługi wiadomości do implementowania abstrakcyjnej magistrali zdarzeń. Ale te technologie są na różnych poziomach. Na przykład RabbitMQ, transport brokera obsługi wiadomości, jest na niższym poziomie niż produkty komercyjne, takie jak Azure Service Bus, NServiceBus, MassTransit lub Brighter. Większość z tych produktów może pracować nad rabbitmq lub usługi Azure Service Bus. Wybór produktu zależy od liczby funkcji i ilości skalowalności aplikacji, której potrzebujesz do użycia.

Do implementacji tylko zdarzenia magistrali proof-of-concept dla środowiska programistycznego, jak w przykładzie eShopOnContainers, prosta implementacja na szczycie RabbitMQ działa jako kontener może być wystarczająca. Jednak w przypadku systemów o znaczeniu krytycznym i produkcyjnym, które wymagają wysokiej skalowalności, warto ocenić i używać usługi Azure Service Bus.

Jeśli potrzebujesz abstrakcji wysokiego poziomu i bogatszych funkcji, takich jak Sagas dla [długotrwałych](https://docs.particular.net/nservicebus/sagas/) procesów, które ułatwiają rozwój rozproszony, warto ocenić inne komercyjne i otwarte magistrale usług, takie jak NServiceBus, MassTransit i Brighter. W takim przypadku abstrakcje i API do wykorzystania będą zwykle bezpośrednio te dostarczane przez te autobusy usług wysokiego poziomu zamiast własnych abstrakcji (jak [proste abstrakcje magistrali zdarzeń przewidziane w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). W tym celu można zbadać [rozwidlane eShopOnContainers za pomocą NServiceBus](https://go.particular.net/eShopOnContainers) (dodatkowy przykład pochodny zaimplementowany przez dane oprogramowanie).

Oczywiście zawsze można zbudować własne funkcje magistrali usług na podstawie technologii niższego poziomu, takich jak RabbitMQ i Docker, ale praca potrzebna do "ponownego wynalezienia koła" może być zbyt kosztowna dla niestandardowej aplikacji dla przedsiębiorstwa.

Aby powtórzyć: abstrakcje magistrali zdarzeń przykładowych i implementacji prezentowane w przykładzie eShopOnContainers są przeznaczone do użycia tylko jako dowód koncepcji. Po podjęciu decyzji, że chcesz mieć komunikację asynchronistykę i sterowaną zdarzeniami, jak wyjaśniono w bieżącej sekcji, należy wybrać produkt magistrali usług, który najlepiej odpowiada Twoim potrzebom produkcyjnym.

## <a name="integration-events"></a>Wydarzenia integracyjne

Zdarzenia integracji są używane do przywracania stanu domeny w synchronizacji między wieloma mikrousługami lub systemami zewnętrznymi. Odbywa się to przez publikowanie zdarzeń integracji poza mikrousługą. Gdy zdarzenie jest publikowane do wielu mikrousług odbiornika (do tylu mikrousług, ile są subskrybowane do zdarzenia integracji), odpowiedni program obsługi zdarzeń w każdej mikrousługi odbiornika obsługuje zdarzenie.

Zdarzenie integracji jest zasadniczo klasy przechowywania danych, jak w poniższym przykładzie:

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

Zdarzenia integracji można zdefiniować na poziomie aplikacji każdej mikrousługi, więc są one oddzielone od innych mikrousług, w sposób porównywalny do sposobu, w jaki ViewModels są zdefiniowane na serwerze i kliencie. Co nie jest zalecane jest udostępnianie wspólnej biblioteki zdarzeń integracji w wielu mikrousług; w ten sposób byłoby sprzężenie tych mikrousług z biblioteki danych definicji pojedynczego zdarzenia. Nie chcesz tego robić z tych samych powodów, które nie mają być współużytkować wspólny model domeny w wielu mikrousług: mikrousługi muszą być całkowicie autonomiczne.

Istnieje tylko kilka rodzajów bibliotek, które należy udostępnić w mikrousługach. Jednym z nich są biblioteki, które są ostateczne bloki aplikacji, takich jak [interfejs API klienta usługi Event Bus](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jak w eShopOnContainers. Innym jest biblioteki, które stanowią narzędzia, które mogą być również współużytkowane jako składniki NuGet, takie jak serializatory JSON.

## <a name="the-event-bus"></a>Autobus eventowy

Magistrala zdarzeń umożliwia publikowanie/subskrybowanie komunikacji w stylu między mikrousługami bez konieczności jawnie być świadomi siebie nawzajem, jak pokazano na rysunku 6-19.

![Diagram przedstawiający podstawowy wzorzec publikowania/subskrybowania.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Rysunek 6-19**. Publikowanie/subskrybowanie podstaw za pomocą magistrali zdarzeń

Powyższy diagram pokazuje, że mikrousługa A publikuje do usługi Event Bus, która dystrybuuje do subskrybowania mikrousług B i C, bez wydawcy konieczności poznania subskrybentów. Magistrala zdarzeń jest powiązana ze wzorcem Observer i wzorcem publikowania i subskrybowania.

### <a name="observer-pattern"></a>Wzór obserwatora

W [strukturze Obserwatora](https://en.wikipedia.org/wiki/Observer_pattern)obiekt podstawowy (znany jako Obserwowalny) powiadamia inne zainteresowane obiekty (znane jako obserwatorzy) o odpowiednich informacjach (zdarzeniach).

### <a name="publishsubscribe-pubsub-pattern"></a>Wzór publikowania/subskrybowania (pub/sub)

Cel [wzorca publikowania/subskrybowania](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) jest taki sam jak wzorzec obserwatora: chcesz powiadomić inne usługi, gdy mają miejsce określone zdarzenia. Ale istnieje istotna różnica między obserwatorem i Pub / Sub wzorców. We wzorze obserwatora transmisja jest wykonywana bezpośrednio z obserwowalnych do obserwatorów, więc "znają się" nawzajem. Ale podczas korzystania z pubu/sub wzorzec, istnieje trzeci składnik, o nazwie broker lub broker wiadomości lub magistrali zdarzeń, który jest znany zarówno przez wydawcę i subskrybenta. W związku z tym podczas korzystania z pubu/sub wzorzec wydawcy i subskrybentów są dokładnie oddzielone dzięki wspomnianej magistrali zdarzeń lub brokera wiadomości.

### <a name="the-middleman-or-event-bus"></a>Pośrednik lub autobus zdarzeń

Jak osiągnąć anonimowość między wydawcą a subskrybentem? Łatwym sposobem jest niech pośrednik dbać o całą komunikację. Autobus zdarzeń jest jednym z takich pośredników.

Magistrala zdarzeń składa się zazwyczaj z dwóch części:

- Abstrakcja lub interfejs.

- Co najmniej jedna implementacje.

Na rysunku 6-19 można zobaczyć, jak z punktu widzenia aplikacji magistrala zdarzeń jest niczym więcej niż kanałem Pub/Sub. Sposób implementowania tej komunikacji asynchroniiowej może się różnić. Może mieć wiele implementacji, dzięki czemu można przełączać się między nimi, w zależności od wymagań dotyczących środowiska (na przykład środowiska produkcyjne i rozwojowe).

Na rysunku 6-20 można zobaczyć abstrakcję magistrali zdarzeń z wieloma implementacjami opartymi na technologiach obsługi wiadomości infrastruktury, takich jak RabbitMQ, usługa Azure Service Bus lub inny broker zdarzeń/komunikatów.

![Diagram przedstawiający dodanie warstwy abstrakcji magistrali zdarzeń.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Wykres 6-20.** Wiele implementacji magistrali zdarzeń

Dobrze jest mieć magistrali zdarzeń zdefiniowane za pośrednictwem interfejsu, dzięki czemu można zaimplementować za pomocą kilku technologii, takich jak RabbitMQ azure service bus lub innych. Jednak i jak wspomniano wcześniej, przy użyciu własnych abstrakcji (interfejs magistrali zdarzeń) jest dobry tylko wtedy, gdy potrzebujesz podstawowych funkcji magistrali zdarzeń obsługiwanych przez abstrakcje. Jeśli potrzebujesz bogatszych funkcji magistrali usług, prawdopodobnie należy użyć interfejsu API i abstrakcje dostarczone przez preferowaną komercyjną magistralę usług zamiast własnych abstrakcji.

### <a name="defining-an-event-bus-interface"></a>Definiowanie interfejsu magistrali zdarzeń

Zacznijmy od kodu implementacji interfejsu magistrali zdarzeń i możliwych implementacji do celów eksploracji. Interfejs powinien być ogólny i prosty, jak w poniższym interfejsie.

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

Metoda `Publish` jest prosta. Magistrala zdarzeń będzie emitować zdarzenie integracji przekazane do dowolnego mikrousługi, a nawet aplikacji zewnętrznej, subskrybowanej do tego zdarzenia. Ta metoda jest używana przez mikrousługi, która publikuje zdarzenie.

Metody `Subscribe` (można mieć kilka implementacji w zależności od argumentów) są używane przez mikrousługi, które mają odbierać zdarzenia. Ta metoda ma dwa argumenty. Pierwszym z nich jest wydarzenie integracyjne`IntegrationEvent`do subskrypcji ( ). Drugi argument to program obsługi zdarzeń integracji `IIntegrationEventHandler<T>`(lub metoda wywołania zwrotnego), o nazwie , które mają być wykonywane, gdy mikrousługa odbiorcy pobiera ten komunikat zdarzenia integracji.

## <a name="additional-resources"></a>Zasoby dodatkowe

Niektóre gotowe do produkcji rozwiązania do obsługi wiadomości:

- **Azure Service Bus** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **Autobusy NServiceBus** \
  <https://particular.net/nservicebus>
  
- **MassTransit (MassTransit)** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Poprzedni](database-server-container.md)
> [następny](rabbitmq-event-bus-development-test-environment.md)
