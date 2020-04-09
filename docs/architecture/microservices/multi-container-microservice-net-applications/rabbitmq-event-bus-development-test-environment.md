---
title: Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Użyj RabbitMQ do zaimplementowania komunikatów magistrali zdarzeń dla zdarzeń integracji dla środowisk deweloperskich lub testowych.
ms.date: 10/02/2018
ms.openlocfilehash: 12e37fabfe915b4d2089d27f7852528a9a037d3c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988300"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich

Należy rozpocząć od stwierdzenia, że jeśli utworzysz niestandardowy magistrala zdarzeń na podstawie RabbitMQ uruchomionego w kontenerze, tak jak robi to aplikacja eShopOnContainers, powinna być używana tylko w środowiskach deweloperskich i testowych. Nie należy go używać w środowisku produkcyjnym, chyba że budujesz go jako część magistrali serwisowej gotowej do produkcji. W prostej niestandardowej magistrali zdarzeń może brakować wielu krytycznych funkcji gotowych do produkcji, które ma komercyjna magistrala usług.

Jednym z niestandardowych implementacji magistrali zdarzeń w eShopOnContainers jest w zasadzie biblioteka przy użyciu interfejsu API RabbitMQ. (Istnieje inna implementacja oparta na usłudze Azure Service Bus).

Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousługpodsoby subskrybować zdarzenia, publikować zdarzenia i odbierać zdarzenia, jak pokazano na rysunku 6-21.

![Diagram przedstawiający RabbitMQ między nadawcą wiadomości a odbiorcą wiadomości.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Rysunek 6-21.** RabbitMQ implementacja magistrali zdarzeń

RabbitMQ działa jako pośrednik między wydawcą wiadomości a subskrybentami, do obsługi dystrybucji. W kodzie EventBusRabbitMQ klasa implementuje ogólny interfejs IEventBus. Jest to oparte na iniekcji zależności, dzięki czemu można zamienić z tej wersji deweloperskiej/testowej na wersję produkcyjną.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

RabbitMQ implementacji przykładowej magistrali zdarzeń deweloperskich/testowych jest kodem współpłytowym. Musi obsługiwać połączenie z serwerem RabbitMQ i podać kod do publikowania zdarzenia wiadomości do kolejek. Ma również do zaimplementowania słownika kolekcji programów obsługi zdarzeń integracji dla każdego typu zdarzenia; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla każdego mikrousługi odbiornika, jak pokazano na rysunku 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementowanie prostej metody publikowania za pomocą RabbitMQ

Poniższy kod jest ***uproszczoną*** wersją implementacji magistrali zdarzeń dla RabbitMQ, aby zaprezentować cały scenariusz. Tak naprawdę nie obsługuje połączenia w ten sposób. Aby zobaczyć pełną implementację, zobacz rzeczywisty kod w repozytorium [dotnet-architecture/eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Publish metody w aplikacji eShopOnContainers jest lepsza przy użyciu zasad ponawiania [prób Polly,](https://github.com/App-vNext/Polly) która ponawia zadanie określoną liczbę razy w przypadku, gdy rabbitmq kontenera nie jest gotowy. Może to nastąpić, gdy docker-compose uruchamia kontenery; na przykład RabbitMQ kontenera może rozpocząć się wolniej niż inne kontenery.

Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, więc ten kod powinien być używany tylko dla środowisk deweloperskich/testowych.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementowanie kodu subskrypcji za pomocą interfejsu API RabbitMQ

Podobnie jak w przypadku kodu publikowania, poniższy kod jest uproszczeniem części implementacji magistrali zdarzeń dla RabbitMQ. Ponownie, zwykle nie trzeba go zmieniać, chyba że poprawiasz go.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

Każdy typ zdarzenia ma powiązany kanał, aby uzyskać zdarzenia z RabbitMQ. Następnie można mieć dowolną liczbę programów obsługi zdarzeń na kanał i typ zdarzenia, zgodnie z potrzebami.

Subscribe Metoda akceptuje IIntegrationEventHandler obiektu, który jest jak metoda wywołania zwrotnego w bieżącej mikrousługi, a także jego powiązanych IntegrationEvent obiektu. Kod następnie dodaje, że program obsługi zdarzeń do listy programów obsługi zdarzeń, które każdy typ zdarzenia integracji może mieć na mikrousługi klienta. Jeśli kod klienta nie został jeszcze subskrybowany do zdarzenia, kod tworzy kanał dla typu zdarzenia, dzięki czemu może odbierać zdarzenia w stylu wypychania z RabbitMQ, gdy to zdarzenie jest publikowane z dowolnej innej usługi.

Jak wspomniano powyżej, magistrala zdarzeń zaimplementowana w eShopOnContainers ma tylko cel edukacyjny i edukacyjny, ponieważ obsługuje tylko główne scenariusze, więc nie jest gotowy do produkcji.

W scenariuszach produkcyjnych sprawdź dodatkowe zasoby poniżej, specyficzne dla RabbitMQ i [implementacji komunikacji opartej na zdarzeniach między mikrousługami](./integration-event-based-microservice-communications.md#additional-resources) sekcji.

## <a name="additional-resources"></a>Zasoby dodatkowe

Gotowe do produkcji rozwiązania z obsługą RabbitMQ.

- **EasyNetQ** - Open Source .NET API client for RabbitMQ \ EasyNetQ - Open Source .NET API client for RabbitMQ \ EasyNetQ - Open Source .NET API client for RabbitMQ \ EasyNet
  <http://easynetq.com/>

- **MassTransit (MassTransit)** \
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> [Poprzedni](integration-event-based-microservice-communications.md)
> [następny](subscribe-events.md)
