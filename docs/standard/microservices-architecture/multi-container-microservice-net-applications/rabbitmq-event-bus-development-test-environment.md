---
title: "Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3505cb993c736165d4aff4ce8fad38cfa14ed417
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="a4c80-104">Implementowanie magistrali zdarzeń z RabbitMQ dla środowisk deweloperskich lub testowania</span><span class="sxs-lookup"><span data-stu-id="a4c80-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="a4c80-105">Firma Microsoft należy zacząć od informujący o tym, że po utworzeniu sieci magistrali niestandardowe zdarzenie oparte na RabbitMQ uruchomione w kontenerze, tak jak w przypadku aplikacji eShopOnContainers tej opcji należy używać tylko w przypadku projektowania i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="a4c80-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="a4c80-106">Nie należy używać go do środowiska produkcyjnego, chyba że tworzysz, jako część magistrali usługi gotowe do produkcji.</span><span class="sxs-lookup"><span data-stu-id="a4c80-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="a4c80-107">Magistrali proste niestandardowe zdarzenie może brakować wiele funkcji krytyczne gotowe do produkcji, które ma komercyjnych usługi service bus.</span><span class="sxs-lookup"><span data-stu-id="a4c80-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="a4c80-108">Jeden z implementacji niestandardowych magistrali zdarzeń w eShopOnContainers jest zasadniczo bibliotekę przy użyciu interfejsu API RabbitMQ (Brak innego wdrożenia oparte na Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="a4c80-108">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="a4c80-109">Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousług subskrybowanie zdarzeń, publikowanie zdarzeń i odbierania zdarzeń, jak pokazano w rysunek 8-21.</span><span class="sxs-lookup"><span data-stu-id="a4c80-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="a4c80-110">**Rysunek 8-21.**</span><span class="sxs-lookup"><span data-stu-id="a4c80-110">**Figure 8-21.**</span></span> <span data-ttu-id="a4c80-111">Implementacja RabbitMQ magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a4c80-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="a4c80-112">W kodzie klasa EventBusRabbitMQ implementuje interfejs IEventBus ogólny.</span><span class="sxs-lookup"><span data-stu-id="a4c80-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="a4c80-113">Jest to oparty na iniekcji zależności, dzięki czemu można wymienić z tej wersji i testowania do wersji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="a4c80-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="a4c80-114">Implementacja RabbitMQ magistralą zdarzeń i testowania próbki jest schematyczny kod.</span><span class="sxs-lookup"><span data-stu-id="a4c80-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="a4c80-115">Musi on obsługiwać połączenia z serwerem RabbitMQ i podaj kod do publikowania zdarzeń wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a4c80-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="a4c80-116">Obejmuje ona również do zaimplementowania słownika kolekcje integracji programów obsługi zdarzeń dla każdego typu zdarzeń; te typy zdarzeń może mieć różne wystąpienia i różnych subskrypcji dla każdego mikrousługi odbiornik, jak pokazano w rysunek 8-21.</span><span class="sxs-lookup"><span data-stu-id="a4c80-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="a4c80-117">Implementowanie prostego metody z RabbitMQ publikowania</span><span class="sxs-lookup"><span data-stu-id="a4c80-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="a4c80-118">Poniższy kod jest częścią dotyczy implementacji magistrali uproszczony zdarzeń RabbitMQ zwiększona [rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a4c80-118">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="a4c80-119">Zwykle nie trzeba go kodu, chyba że wprowadzać ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="a4c80-119">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="a4c80-120">Kod pobiera połączenia i kanał RabbitMQ, tworzy komunikat i następnie publikuje komunikat do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a4c80-120">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="a4c80-121">[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikacji zwiększona przy użyciu metody w aplikacji eShopOnContainers [Polly](https://github.com/App-vNext/Polly) ponów zasad, które w przypadku, gdy kontener RabbitMQ będzie ponawiać zadanie wiele razy nie jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="a4c80-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="a4c80-122">Taka sytuacja może wystąpić po rozwiązania docker compose Trwa uruchamianie kontenerów; na przykład kontener RabbitMQ może rozpocząć wolniej niż inne kontenery.</span><span class="sxs-lookup"><span data-stu-id="a4c80-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="a4c80-123">Jak wspomniano wcześniej, istnieje wiele możliwe konfiguracje w RabbitMQ, dlatego ten kod należy używać tylko dla środowisk i testowania.</span><span class="sxs-lookup"><span data-stu-id="a4c80-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="a4c80-124">Wdrażanie kodu subskrypcji przy użyciu interfejsu API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="a4c80-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="a4c80-125">Jako kod publikowania następujący kod jest uproszczenie część implementacji magistrali zdarzeń dla RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="a4c80-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="a4c80-126">Ponownie zwykle nie trzeba go zmienić, chyba że umożliwiają zwiększenie go.</span><span class="sxs-lookup"><span data-stu-id="a4c80-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="a4c80-127">Każdy typ zdarzenia ma powiązanych kanału można pobrać zdarzenia z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="a4c80-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="a4c80-128">Następnie możesz wybrać dowolną liczbę programów obsługi zdarzeń dla typów kanałów i zdarzenia w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a4c80-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="a4c80-129">Metoda Subskrybuj przyjmuje obiekt IIntegrationEventHandler, czyli jak metody wywołania zwrotnego w bieżącym mikrousługi, oraz jego powiązany obiekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="a4c80-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="a4c80-130">Następnie kod dodaje programu obsługi zdarzeń do listy programów obsługi zdarzeń, które poszczególnych typów zdarzeń integracji może mieć na mikrousługi klienta.</span><span class="sxs-lookup"><span data-stu-id="a4c80-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="a4c80-131">Jeśli kod klienta nie ma już subskrybowana w zdarzeniu, kod tworzy kanału typu zdarzenia, może odbierać zdarzenia w stylu wypychania z RabbitMQ po opublikowaniu zdarzenia z innej usługi.</span><span class="sxs-lookup"><span data-stu-id="a4c80-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a4c80-132">[Poprzednie] (integracji — zdarzenie — na podstawie mikrousługi communications.md) [dalej] (subskrypcja events.md)</span><span class="sxs-lookup"><span data-stu-id="a4c80-132">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
