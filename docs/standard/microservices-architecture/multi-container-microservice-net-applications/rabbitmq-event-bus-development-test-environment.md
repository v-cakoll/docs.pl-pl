---
title: "Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="5f55b-104">Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania</span><span class="sxs-lookup"><span data-stu-id="5f55b-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="5f55b-105">Firma Microsoft należy zacząć od informujący o tym, że po utworzeniu sieci magistrali niestandardowe zdarzenie oparte na RabbitMQ uruchomione w kontenerze, tak jak w przypadku aplikacji eShopOnContainers tej opcji należy używać tylko w przypadku projektowania i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="5f55b-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="5f55b-106">Nie należy używać go do środowiska produkcyjnego, chyba że tworzysz, jako część magistrali usługi gotowe do produkcji.</span><span class="sxs-lookup"><span data-stu-id="5f55b-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="5f55b-107">Magistrali proste niestandardowe zdarzenie może brakować wiele funkcji krytyczne gotowe do produkcji, które ma komercyjnych usługi service bus.</span><span class="sxs-lookup"><span data-stu-id="5f55b-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="5f55b-108">Implementacja niestandardowa eShopOnContainers magistrali zdarzeń jest zasadniczo bibliotekę przy użyciu interfejsu API RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="5f55b-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="5f55b-109">Implementacja umożliwia mikrousług subskrybowanie zdarzeń, publikowanie zdarzeń i odbierania zdarzeń, jak pokazano w rysunek 8-21.</span><span class="sxs-lookup"><span data-stu-id="5f55b-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="5f55b-110">**Rysunek 8-21.**</span><span class="sxs-lookup"><span data-stu-id="5f55b-110">**Figure 8-21.**</span></span> <span data-ttu-id="5f55b-111">Implementacja RabbitMQ magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="5f55b-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="5f55b-112">W kodzie klasa EventBusRabbitMQ implementuje interfejs IEventBus ogólny.</span><span class="sxs-lookup"><span data-stu-id="5f55b-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="5f55b-113">Jest to oparty na iniekcji zależności, dzięki czemu można wymienić z tej wersji i testowania do wersji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="5f55b-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="5f55b-114">Implementacja RabbitMQ magistralą zdarzeń i testowania próbki jest schematyczny kod.</span><span class="sxs-lookup"><span data-stu-id="5f55b-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="5f55b-115">Musi on obsługiwać połączenia z serwerem RabbitMQ i podaj kod do publikowania zdarzeń wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="5f55b-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="5f55b-116">Obejmuje ona również do zaimplementowania słownika kolekcje integracji programów obsługi zdarzeń dla każdego typu zdarzeń; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla każdego mikrousługi odbiornik, jak pokazano w rysunek 8-21.</span><span class="sxs-lookup"><span data-stu-id="5f55b-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="5f55b-117">Implementowanie prostego metody z RabbitMQ publikowania</span><span class="sxs-lookup"><span data-stu-id="5f55b-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="5f55b-118">Następujący kod jest część implementacji magistrali zdarzenia eShopOnContainers dla RabbitMQ, dzięki czemu zwykle nie trzeba kodu go, chyba że wprowadzać ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="5f55b-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="5f55b-119">Kod pobiera połączenia i kanał RabbitMQ, tworzy komunikat i następnie publikuje komunikat do kolejki.</span><span class="sxs-lookup"><span data-stu-id="5f55b-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="5f55b-120">[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikacji zwiększona przy użyciu metody w aplikacji eShopOnContainers [Polly](https://github.com/App-vNext/Polly) ponów zasad, które w przypadku, gdy kontener RabbitMQ będzie ponawiać zadanie wiele razy nie jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="5f55b-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="5f55b-121">Taka sytuacja może wystąpić po rozwiązania docker compose Trwa uruchamianie kontenerów; na przykład kontener RabbitMQ może rozpocząć wolniej niż inne kontenery.</span><span class="sxs-lookup"><span data-stu-id="5f55b-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="5f55b-122">Jak wspomniano wcześniej, istnieje wiele możliwe konfiguracje w RabbitMQ, dlatego ten kod należy używać tylko dla środowisk i testowania.</span><span class="sxs-lookup"><span data-stu-id="5f55b-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="5f55b-123">Wdrażanie kodu subskrypcji przy użyciu interfejsu API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="5f55b-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="5f55b-124">Jako kod publikowania następujący kod jest uproszczenie część implementacji magistrali zdarzeń dla RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="5f55b-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="5f55b-125">Ponownie zwykle nie trzeba go zmienić, chyba że umożliwiają zwiększenie go.</span><span class="sxs-lookup"><span data-stu-id="5f55b-125">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

<span data-ttu-id="5f55b-126">Każdy typ zdarzenia ma powiązanych kanału można pobrać zdarzenia z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="5f55b-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="5f55b-127">Następnie możesz wybrać dowolną liczbę programów obsługi zdarzeń dla typów kanałów i zdarzenia w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5f55b-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="5f55b-128">Metoda Subskrybuj przyjmuje obiekt IIntegrationEventHandler, czyli jak metody wywołania zwrotnego w bieżącym mikrousługi, oraz jego powiązany obiekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="5f55b-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="5f55b-129">Następnie kod dodaje programu obsługi zdarzeń do listy programów obsługi zdarzeń, które poszczególnych typów zdarzeń integracji może mieć na mikrousługi klienta.</span><span class="sxs-lookup"><span data-stu-id="5f55b-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="5f55b-130">Jeśli kod klienta nie ma już subskrybowana w zdarzeniu, kod tworzy kanału typu zdarzenia, może odbierać zdarzenia w stylu wypychania z RabbitMQ po opublikowaniu zdarzenia z innej usługi.</span><span class="sxs-lookup"><span data-stu-id="5f55b-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5f55b-131">[Poprzednie] (integracji — zdarzenie — na podstawie mikrousługi communications.md) [dalej] (subskrypcja events.md)</span><span class="sxs-lookup"><span data-stu-id="5f55b-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
