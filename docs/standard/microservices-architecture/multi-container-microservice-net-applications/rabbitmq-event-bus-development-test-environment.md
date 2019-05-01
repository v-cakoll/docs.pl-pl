---
title: Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Używanie oprogramowania RabbitMQ na implementowanie magistrali zdarzeń komunikatów dla zdarzeń integracji dla środowiska deweloperskie lub testowe.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 2bcd3491c58884653cd6c119753696019151bfed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864273"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="45fa6-103">Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich</span><span class="sxs-lookup"><span data-stu-id="45fa6-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="45fa6-104">Firma Microsoft należy zacząć od informujący o tym, że jeśli utworzysz usługi magistrali niestandardowe zdarzenie oparte na RabbitMQ uruchomione w kontenerze, tak jak w ramach aplikacji eShopOnContainers aplikacji, należy jej używać tylko w przypadku Twojego środowiska projektowania i testowania.</span><span class="sxs-lookup"><span data-stu-id="45fa6-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="45fa6-105">Nie należy używać go w środowisku produkcyjnym, chyba że tworzysz go jako część gotowe do produkcji usługi Service bus.</span><span class="sxs-lookup"><span data-stu-id="45fa6-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="45fa6-106">Magistrali proste zdarzenia niestandardowego może brakować wiele gotowych do produkcji istotnych funkcji, do których ma komercyjnej usługi Service bus.</span><span class="sxs-lookup"><span data-stu-id="45fa6-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="45fa6-107">Jednym z implementacji niestandardowych magistrali zdarzeń w ramach aplikacji eShopOnContainers jest zasadniczo bibliotekę przy użyciu interfejsu API RabbitMQ (ma inny wdrożenia oparte na usłudze Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="45fa6-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="45fa6-108">Implementacja magistrali zdarzeń z oprogramowaniem RabbitMQ umożliwia mikrousług subskrybowanie do zdarzeń, publikowanie zdarzeń i odbierania zdarzeń, jak pokazano w rysunek 6-21.</span><span class="sxs-lookup"><span data-stu-id="45fa6-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![RabbitMQ działa jako pośrednik pomiędzy komunikat wydawcy i subskrybenci, do obsługi dystrybucji.](./media/image22.png)

<span data-ttu-id="45fa6-110">**Rysunek 6-21.**</span><span class="sxs-lookup"><span data-stu-id="45fa6-110">**Figure 6-21.**</span></span> <span data-ttu-id="45fa6-111">Wdrożenia oprogramowania RabbitMQ magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="45fa6-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="45fa6-112">W kodzie klasa EventBusRabbitMQ implementuje interfejs ogólny IEventBus.</span><span class="sxs-lookup"><span data-stu-id="45fa6-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="45fa6-113">Tak, aby zamienić na z tej wersji i testowania aplikacji, aby wersja produkcyjna jest oparta na iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="45fa6-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="45fa6-114">Implementacja RabbitMQ magistrali zdarzeń i testowania aplikacji przykładowej jest standardowy kod.</span><span class="sxs-lookup"><span data-stu-id="45fa6-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="45fa6-115">Musi on obsługiwać połączenia z serwerem RabbitMQ i podać kod do publikowania zdarzeń komunikatów do kolejki.</span><span class="sxs-lookup"><span data-stu-id="45fa6-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="45fa6-116">Ma również implementacji słownika kolekcje integracji obsługi zdarzeń dla każdego typu zdarzenia; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla poszczególnych mikrousług odbiornik, jak pokazano w rysunek 6-21.</span><span class="sxs-lookup"><span data-stu-id="45fa6-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="45fa6-117">Implementowanie prostego publikowania metody z oprogramowaniem RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="45fa6-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="45fa6-118">Poniższy kod jest ***uproszczone*** wersję implementacji magistrali zdarzeń RabbitMQ, aby zaprezentować całego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="45fa6-118">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="45fa6-119">Nie naprawdę obsługują połączenia w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="45fa6-119">You don't really handle the connection this way.</span></span> <span data-ttu-id="45fa6-120">Aby wyświetlić pełną implementację, zobacz rzeczywisty kod w [dotnet architektura/ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="45fa6-120">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span> 

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

<span data-ttu-id="45fa6-121">[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikacji zwiększona przy użyciu metody w aplikacji w ramach aplikacji eShopOnContainers [Polly](https://github.com/App-vNext/Polly) zasady, która ponawia zadanie, ile razy, na wypadek, gdyby kontener RabbitMQ jest ponawiania Brak gotowości.</span><span class="sxs-lookup"><span data-stu-id="45fa6-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="45fa6-122">Taka sytuacja może wystąpić po rozwiązania docker compose Trwa uruchamianie kontenerów; na przykład oprogramowania RabbitMQ kontener może uruchomić wolniej niż inne kontenery.</span><span class="sxs-lookup"><span data-stu-id="45fa6-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="45fa6-123">Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, dlatego ten kod należy używać tylko dla środowisk projektowych/testowych.</span><span class="sxs-lookup"><span data-stu-id="45fa6-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="45fa6-124">Wdrażanie kodu subskrypcji przy użyciu interfejsu API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="45fa6-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="45fa6-125">Jako kodem publikowania, poniższy kod jest uproszczenie część implementacji magistrali zdarzeń dla oprogramowania RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="45fa6-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="45fa6-126">Ponownie zwykle nie trzeba go zmienić, chyba że poprawiamy go.</span><span class="sxs-lookup"><span data-stu-id="45fa6-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="45fa6-127">Każdy typ zdarzenia ma powiązane kanału można pobrać zdarzenia z oprogramowania RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="45fa6-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="45fa6-128">Następnie możesz mieć dowolną liczbę programów obsługi zdarzeń dla typu kanału i zdarzenia, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="45fa6-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="45fa6-129">Metoda Subskrybuj akceptuje obiekt IIntegrationEventHandler, czyli jak metody wywołania zwrotnego w bieżącym mikrousług, oraz jego powiązany obiekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="45fa6-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="45fa6-130">Kod następnie dodaje ten program obsługi zdarzeń do listy programów obsługi zdarzeń mających przez każdy typ zdarzenia integracji na mikrousługę klienta.</span><span class="sxs-lookup"><span data-stu-id="45fa6-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="45fa6-131">Jeśli kod klienta nie jest już subskrybowana na zdarzenie, kod tworzy kanał dla typu zdarzenia, więc może ona odbierać zdarzenia w stylu wypychane z RabbitMQ, po opublikowaniu tego zdarzenia z dowolnej innej usługi.</span><span class="sxs-lookup"><span data-stu-id="45fa6-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="45fa6-132">[Poprzednie](integration-event-based-microservice-communications.md)
>[dalej](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="45fa6-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
