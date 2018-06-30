---
title: Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: fb9bf51d947774cddd7b42ade0f05abc8fb3d7e9
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104756"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania

Firma Microsoft należy zacząć od informujący o tym, że po utworzeniu sieci magistrali niestandardowe zdarzenie oparte na RabbitMQ uruchomione w kontenerze, tak jak w przypadku aplikacji eShopOnContainers tej opcji należy używać tylko w przypadku projektowania i środowisk testowych. Nie należy używać go do środowiska produkcyjnego, chyba że tworzysz, jako część magistrali usługi gotowe do produkcji. Magistrali proste niestandardowe zdarzenie może brakować wiele funkcji krytyczne gotowe do produkcji, które ma komercyjnych usługi service bus.

Jeden z implementacji niestandardowych magistrali zdarzeń w eShopOnContainers jest zasadniczo bibliotekę przy użyciu interfejsu API RabbitMQ (Brak innego wdrożenia oparte na Azure Service Bus). 

Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousług subskrybowanie zdarzeń, publikowanie zdarzeń i odbierania zdarzeń, jak pokazano w rysunek 8-21.

![](./media/image22.png)

**Rysunek 8-21.** Implementacja RabbitMQ magistrali zdarzeń

W kodzie klasa EventBusRabbitMQ implementuje interfejs IEventBus ogólny. Jest to oparty na iniekcji zależności, dzięki czemu można wymienić z tej wersji i testowania do wersji produkcyjnej.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

Implementacja RabbitMQ magistralą zdarzeń i testowania próbki jest schematyczny kod. Musi on obsługiwać połączenia z serwerem RabbitMQ i podaj kod do publikowania zdarzeń wiadomości do kolejki. Obejmuje ona również do zaimplementowania słownika kolekcje integracji programów obsługi zdarzeń dla każdego typu zdarzeń; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla każdego mikrousługi odbiornik, jak pokazano w rysunek 8-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementowanie prostego metody z RabbitMQ publikowania

Poniższy kod jest częścią dotyczy implementacji magistrali uproszczony zdarzeń RabbitMQ zwiększona [rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) z eShopOnContainers. Zwykle nie trzeba go kodu, chyba że wprowadzać ulepszenia. Kod pobiera połączenia i kanał RabbitMQ, tworzy komunikat i następnie publikuje komunikat do kolejki.

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

[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikacji zwiększona przy użyciu metody w aplikacji eShopOnContainers [Polly](https://github.com/App-vNext/Polly) ponów zasad, które w przypadku, gdy kontener RabbitMQ będzie ponawiać zadanie wiele razy nie jest gotowy. Taka sytuacja może wystąpić po rozwiązania docker compose Trwa uruchamianie kontenerów; na przykład kontener RabbitMQ może rozpocząć wolniej niż inne kontenery.

Jak wspomniano wcześniej, istnieje wiele możliwe konfiguracje w RabbitMQ, dlatego ten kod należy używać tylko dla środowisk i testowania.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Wdrażanie kodu subskrypcji przy użyciu interfejsu API RabbitMQ

Jako kod publikowania następujący kod jest uproszczenie część implementacji magistrali zdarzeń dla RabbitMQ. Ponownie zwykle nie trzeba go zmienić, chyba że umożliwiają zwiększenie go.

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

Każdy typ zdarzenia ma powiązanych kanału można pobrać zdarzenia z RabbitMQ. Następnie możesz wybrać dowolną liczbę programów obsługi zdarzeń dla typów kanałów i zdarzenia w razie potrzeby.

Metoda Subskrybuj przyjmuje obiekt IIntegrationEventHandler, czyli jak metody wywołania zwrotnego w bieżącym mikrousługi, oraz jego powiązany obiekt IntegrationEvent. Następnie kod dodaje programu obsługi zdarzeń do listy programów obsługi zdarzeń, które poszczególnych typów zdarzeń integracji może mieć na mikrousługi klienta. Jeśli kod klienta nie ma już subskrybowana w zdarzeniu, kod tworzy kanału typu zdarzenia, może odbierać zdarzenia w stylu wypychania z RabbitMQ po opublikowaniu zdarzenia z innej usługi.


>[!div class="step-by-step"]
[Poprzednie](integration-event-based-microservice-communications.md)
[dalej](subscribe-events.md)
