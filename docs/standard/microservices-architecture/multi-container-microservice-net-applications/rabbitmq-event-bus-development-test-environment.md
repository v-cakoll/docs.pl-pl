---
title: Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ środowiska deweloperskie lub testowe
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Używanie oprogramowania RabbitMQ na implementowanie magistrali zdarzeń komunikatów dla zdarzeń integracji dla środowiska deweloperskie lub testowe.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 2bcd3491c58884653cd6c119753696019151bfed
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584372"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ środowiska deweloperskie lub testowe

Firma Microsoft należy zacząć od informujący o tym, że jeśli utworzysz usługi magistrali niestandardowe zdarzenie oparte na RabbitMQ uruchomione w kontenerze, tak jak w ramach aplikacji eShopOnContainers aplikacji, należy jej używać tylko w przypadku Twojego środowiska projektowania i testowania. Nie należy używać go w środowisku produkcyjnym, chyba że tworzysz go jako część gotowe do produkcji usługi Service bus. Magistrali proste zdarzenia niestandardowego może brakować wiele gotowych do produkcji istotnych funkcji, do których ma komercyjnej usługi Service bus.

Jednym z implementacji niestandardowych magistrali zdarzeń w ramach aplikacji eShopOnContainers jest zasadniczo bibliotekę przy użyciu interfejsu API RabbitMQ (ma inny wdrożenia oparte na usłudze Azure Service Bus).

Implementacja magistrali zdarzeń z oprogramowaniem RabbitMQ umożliwia mikrousług subskrybowanie do zdarzeń, publikowanie zdarzeń i odbierania zdarzeń, jak pokazano w rysunek 6-21.

![RabbitMQ działa jako pośrednik pomiędzy komunikat wydawcy i subskrybenci, do obsługi dystrybucji.](./media/image22.png)

**Rysunek 6-21.** Wdrożenia oprogramowania RabbitMQ magistrali zdarzeń

W kodzie klasa EventBusRabbitMQ implementuje interfejs ogólny IEventBus. Tak, aby zamienić na z tej wersji i testowania aplikacji, aby wersja produkcyjna jest oparta na iniekcji zależności.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Implementacja RabbitMQ magistrali zdarzeń i testowania aplikacji przykładowej jest standardowy kod. Musi on obsługiwać połączenia z serwerem RabbitMQ i podać kod do publikowania zdarzeń komunikatów do kolejki. Ma również implementacji słownika kolekcje integracji obsługi zdarzeń dla każdego typu zdarzenia; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla poszczególnych mikrousług odbiornik, jak pokazano w rysunek 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementowanie prostego publikowania metody z oprogramowaniem RabbitMQ

Poniższy kod jest ***uproszczone*** wersję implementacji magistrali zdarzeń RabbitMQ, aby zaprezentować całego scenariusza. Nie naprawdę obsługują połączenia w ten sposób. Aby wyświetlić pełną implementację, zobacz rzeczywisty kod w [dotnet architektura/ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repozytorium. 

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

[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikacji zwiększona przy użyciu metody w aplikacji w ramach aplikacji eShopOnContainers [Polly](https://github.com/App-vNext/Polly) zasady, która ponawia zadanie, ile razy, na wypadek, gdyby kontener RabbitMQ jest ponawiania Brak gotowości. Taka sytuacja może wystąpić po rozwiązania docker compose Trwa uruchamianie kontenerów; na przykład oprogramowania RabbitMQ kontener może uruchomić wolniej niż inne kontenery.

Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, dlatego ten kod należy używać tylko dla środowisk projektowych/testowych.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Wdrażanie kodu subskrypcji przy użyciu interfejsu API RabbitMQ

Jako kodem publikowania, poniższy kod jest uproszczenie część implementacji magistrali zdarzeń dla oprogramowania RabbitMQ. Ponownie zwykle nie trzeba go zmienić, chyba że poprawiamy go.

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

Każdy typ zdarzenia ma powiązane kanału można pobrać zdarzenia z oprogramowania RabbitMQ. Następnie możesz mieć dowolną liczbę programów obsługi zdarzeń dla typu kanału i zdarzenia, zgodnie z potrzebami.

Metoda Subskrybuj akceptuje obiekt IIntegrationEventHandler, czyli jak metody wywołania zwrotnego w bieżącym mikrousług, oraz jego powiązany obiekt IntegrationEvent. Kod następnie dodaje ten program obsługi zdarzeń do listy programów obsługi zdarzeń mających przez każdy typ zdarzenia integracji na mikrousługę klienta. Jeśli kod klienta nie jest już subskrybowana na zdarzenie, kod tworzy kanał dla typu zdarzenia, więc może ona odbierać zdarzenia w stylu wypychane z RabbitMQ, po opublikowaniu tego zdarzenia z dowolnej innej usługi.

>[!div class="step-by-step"]
>[Poprzednie](integration-event-based-microservice-communications.md)
>[dalej](subscribe-events.md)
