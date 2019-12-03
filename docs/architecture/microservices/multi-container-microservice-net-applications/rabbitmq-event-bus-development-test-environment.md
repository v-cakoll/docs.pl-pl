---
title: Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Użyj RabbitMQ, aby zaimplementować obsługę komunikatów usługi Event Bus dla zdarzeń integracji dla środowisk programistycznych lub testowych.
ms.date: 10/02/2018
ms.openlocfilehash: ba1cea9384893955ae0743ac8d6a34c350224cd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711195"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich

Należy zacząć od tego, że jeśli utworzysz niestandardową magistralę zdarzeń w oparciu o RabbitMQ uruchomione w kontenerze, jako aplikację eShopOnContainers, powinna ona być używana tylko w środowiskach deweloperskich i testowych. Nie należy używać go w środowisku produkcyjnym, chyba że tworzysz go jako część usługi Service Bus gotowej do produkcji. W przypadku prostej niestandardowej magistrali zdarzeń może brakować wielu funkcji krytycznych gotowych do produkcji dostępnych w komercyjnej usłudze Service Bus.

Jedna z implementacji niestandardowej usługi Event Bus w eShopOnContainers jest zasadniczo biblioteką korzystającą z interfejsu API RabbitMQ (istnieje inna implementacja oparta na Azure Service Bus).

Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousługom subskrybowanie zdarzeń, publikowanie zdarzeń i odbieranie zdarzeń, jak pokazano na rysunku 6-21.

![Diagram przedstawiający RabbitMQ między nadawcą wiadomości i odbiorcą wiadomości.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Rysunek 6-21.** RabbitMQ implementacja magistrali zdarzeń

RabbitMQ działa jako pośrednik między wydawcą komunikatów i subskrybentami, aby obsłużyć dystrybucję. W kodzie Klasa EventBusRabbitMQ implementuje ogólny interfejs IEventBus. Jest to oparte na iniekcji zależności, co pozwala na zamianę z tej wersji deweloperskiej/testowej na wersję produkcyjną.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

RabbitMQ implementacja przykładowej magistrali zdarzeń do tworzenia/testowania to kod standardowy. Musi obsługiwać połączenie z serwerem RabbitMQ i dostarczać kod do publikowania zdarzenia komunikatu w kolejkach. Należy również zaimplementować słownik kolekcji programów obsługi zdarzeń integracji dla każdego typu zdarzenia; te typy zdarzeń mogą mieć różne wystąpienia i różne subskrypcje dla mikrousług odbiornika, jak pokazano na rysunku 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementowanie prostej metody publikacji z RabbitMQ

Poniższy kod jest ***uproszczoną*** wersją implementacji usługi Event Bus dla RabbitMQ, aby zaprezentować cały scenariusz. W ten sposób nie obsługujesz połączenia w ten sposób. Aby wyświetlić pełną implementację, zobacz rzeczywisty kod w repozytorium [dotnet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) .

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

[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) metody Publish w aplikacji eShopOnContainers jest ulepszony za pomocą zasad [Polly](https://github.com/App-vNext/Polly) retry, które ponawiają próbę wykonania zadania przez określoną liczbę razy, gdy kontener RabbitMQ nie jest gotowy. Taka sytuacja może wystąpić, gdy platforma Docker rozpocznie tworzenie kontenerów; na przykład kontener RabbitMQ może zaczynać się wolniej niż inne kontenery.

Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, więc ten kod powinien być używany tylko w środowiskach deweloperskich i testowych.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementowanie kodu subskrypcji za pomocą interfejsu API RabbitMQ

Podobnie jak w przypadku kodu publikacji Poniższy kod jest uproszczeniem części implementacji usługi Event Bus dla RabbitMQ. Zwykle nie trzeba go zmieniać, chyba że jest to ulepszane.

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

Każdy typ zdarzenia ma powiązany kanał, aby uzyskać zdarzenia z RabbitMQ. W razie konieczności można mieć dowolną liczbę programów obsługi zdarzeń dla kanału i typu zdarzenia.

Metoda Subskrybuj akceptuje obiekt IIntegrationEventHandler, który przypomina metodę wywołania zwrotnego w bieżącej mikrousłudze oraz powiązany obiekt IntegrationEvent. Następnie kod dodaje ten program obsługi zdarzeń do listy programów obsługi zdarzeń, które każdy typ zdarzenia integracji może mieć dla mikrousługi klienta. Jeśli kod klienta nie został jeszcze objęty subskrypcją zdarzenia, kod tworzy kanał dla typu zdarzenia, dzięki czemu może odbierać zdarzenia w stylu push z RabbitMQ, gdy to zdarzenie jest publikowane z poziomu innej usługi.

Jak wspomniano powyżej, magistrala zdarzeń zaimplementowana w eShopOnContainers ma tylko cele edukacyjne, ponieważ obsługuje tylko główne scenariusze, więc nie jest gotowa do produkcji.

W przypadku scenariuszy produkcyjnych Sprawdź dodatkowe zasoby poniżej, specyficzne dla RabbitMQ oraz [implementującą komunikację opartą na zdarzeniach między mikrousługami](./integration-event-based-microservice-communications.md#additional-resources) .

## <a name="additional-resources"></a>Dodatkowe zasoby

Gotowe do produkcji rozwiązania z obsługą RabbitMQ.

- **EasyNetQ** — klient interfejsu API .NET Open Source dla RabbitMQ \
  <http://easynetq.com/>

- **MassTransit** \
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
>[Poprzednie](integration-event-based-microservice-communications.md)
>[dalej](subscribe-events.md)
