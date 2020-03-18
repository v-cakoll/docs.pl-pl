---
title: Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Użyj RabbitMQ do zaimplementowania komunikatów magistrali zdarzeń dla zdarzeń integracji dla środowiska deweloperów lub testów.
ms.date: 10/02/2018
ms.openlocfilehash: ba1cea9384893955ae0743ac8d6a34c350224cd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711195"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich

Należy rozpocząć od mówiąc, że jeśli utworzysz niestandardowej magistrali zdarzeń na podstawie RabbitMQ uruchomiony w kontenerze, jak aplikacja eShopOnContainers nie, powinien być używany tylko dla środowiska rozwoju i testowania. Nie należy go używać w środowisku produkcyjnym, chyba że budujesz go jako część magistrali usług gotowych do produkcji. Prosty niestandardowy magistrali zdarzeń może brakować wielu gotowych do produkcji krytycznych funkcji, które ma komercyjna magistrala usług.

Jedną z implementacji niestandardowej magistrali zdarzeń w eShopOnContainers jest w zasadzie biblioteki przy użyciu interfejsu API RabbitMQ (Istnieje inna implementacja oparta na usłudze Azure Service Bus).

Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousługom subskrybowanie zdarzeń, publikowanie zdarzeń i odbieranie zdarzeń, jak pokazano na rysunku 6-21.

![Diagram przedstawiający RabbitMQ między nadawcą wiadomości a odbiorcą wiadomości.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Rysunek 6-21.** Wykonanie autobusu imprezowego RabbitMQ

RabbitMQ działa jako pośrednik między wydawcą wiadomości a subskrybentami, do obsługi dystrybucji. W kodzie EventBusRabbitMQ klasa implementuje ogólny interfejs IEventBus. Jest to oparte na iniekcji zależności, dzięki czemu można zamienić z tej wersji dev/test do wersji produkcyjnej.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Implementacja RabbitMQ przykładowej magistrali zdarzeń deweloperskich/testowych jest kodem systemowym. Musi obsługiwać połączenie z serwerem RabbitMQ i podać kod do publikowania zdarzenia wiadomości do kolejek. Musi również zaimplementować słownik kolekcji obsługi zdarzeń integracji dla każdego typu zdarzenia; te typy zdarzeń mogą mieć różne wystąpienia i różnych subskrypcji dla każdej mikrousługi odbiornika, jak pokazano na rysunku 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementowanie prostej metody publikowania za pomocą RabbitMQ

Poniższy kod jest ***uproszczoną*** wersją implementacji magistrali zdarzeń dla RabbitMQ, aby zaprezentować cały scenariusz. Tak naprawdę nie obsługujesz połączenia w ten sposób. Aby wyświetlić pełną implementację, zobacz rzeczywisty kod w repozytorium [dotnet-architecture/eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)

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

[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Publish metody w aplikacji eShopOnContainers jest ulepszony przy użyciu zasad ponawiania [Polly,](https://github.com/App-vNext/Polly) który ponawia próbę zadania określoną liczbę razy w przypadku kontenera RabbitMQ nie jest gotowy. Taka sytuacja może wystąpić, gdy docker-compose uruchamia kontenery; na przykład kontener RabbitMQ może rozpoczynać się wolniej niż inne kontenery.

Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, więc ten kod powinien być używany tylko dla środowisk deweloperskich/testowych.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementowanie kodu subskrypcji za pomocą interfejsu API RabbitMQ

Podobnie jak w przypadku kodu publikowania, poniższy kod jest uproszczenie części implementacji magistrali zdarzeń dla RabbitMQ. Ponownie, zwykle nie trzeba go zmieniać, chyba że go poprawiasz.

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

Subscribe Metoda akceptuje IIntegrationEventHandler obiektu, który jest jak metoda wywołania wywołania w bieżącej mikrousługi, a także jego powiązany IntegrEvent obiektu. Następnie kod dodaje, że program obsługi zdarzeń do listy programów obsługi zdarzeń, które każdy typ zdarzenia integracji może mieć na mikrousługi klienta. Jeśli kod klienta nie został jeszcze subskrybowany zdarzenia, kod tworzy kanał dla typu zdarzenia, dzięki czemu może odbierać zdarzenia w stylu wypychania z RabbitMQ, gdy to zdarzenie jest publikowane z innej usługi.

Jak wspomniano powyżej, magistrala zdarzeń zaimplementowana w eShopOnContainers ma tylko i cel edukacyjny, ponieważ obsługuje tylko główne scenariusze, więc nie jest gotowy do produkcji.

W przypadku scenariuszy produkcyjnych sprawdź dodatkowe zasoby poniżej, specyficzne dla RabbitMQ i [implementowanie komunikacji opartej na zdarzeniach między mikrousług](./integration-event-based-microservice-communications.md#additional-resources) sekcji.

## <a name="additional-resources"></a>Zasoby dodatkowe

Gotowe do produkcji rozwiązania ze wsparciem dla RabbitMQ.

- **EasyNetQ** - Klient interfejsu API open source .NET dla RabbitMQ \
  <http://easynetq.com/>

- **Transport masowy** \
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
>[Poprzedni](integration-event-based-microservice-communications.md)
>[następny](subscribe-events.md)
