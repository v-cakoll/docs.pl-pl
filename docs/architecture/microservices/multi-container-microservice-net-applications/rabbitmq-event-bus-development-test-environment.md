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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="6a660-103">Implementowanie magistrali zdarzeń z oprogramowaniem RabbitMQ na potrzeby środowisk testowych lub deweloperskich</span><span class="sxs-lookup"><span data-stu-id="6a660-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="6a660-104">Należy rozpocząć od mówiąc, że jeśli utworzysz niestandardowej magistrali zdarzeń na podstawie RabbitMQ uruchomiony w kontenerze, jak aplikacja eShopOnContainers nie, powinien być używany tylko dla środowiska rozwoju i testowania.</span><span class="sxs-lookup"><span data-stu-id="6a660-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="6a660-105">Nie należy go używać w środowisku produkcyjnym, chyba że budujesz go jako część magistrali usług gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="6a660-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="6a660-106">Prosty niestandardowy magistrali zdarzeń może brakować wielu gotowych do produkcji krytycznych funkcji, które ma komercyjna magistrala usług.</span><span class="sxs-lookup"><span data-stu-id="6a660-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="6a660-107">Jedną z implementacji niestandardowej magistrali zdarzeń w eShopOnContainers jest w zasadzie biblioteki przy użyciu interfejsu API RabbitMQ (Istnieje inna implementacja oparta na usłudze Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="6a660-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="6a660-108">Implementacja magistrali zdarzeń z RabbitMQ umożliwia mikrousługom subskrybowanie zdarzeń, publikowanie zdarzeń i odbieranie zdarzeń, jak pokazano na rysunku 6-21.</span><span class="sxs-lookup"><span data-stu-id="6a660-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Diagram przedstawiający RabbitMQ między nadawcą wiadomości a odbiorcą wiadomości.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="6a660-110">**Rysunek 6-21.**</span><span class="sxs-lookup"><span data-stu-id="6a660-110">**Figure 6-21.**</span></span> <span data-ttu-id="6a660-111">Wykonanie autobusu imprezowego RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="6a660-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="6a660-112">RabbitMQ działa jako pośrednik między wydawcą wiadomości a subskrybentami, do obsługi dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="6a660-112">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="6a660-113">W kodzie EventBusRabbitMQ klasa implementuje ogólny interfejs IEventBus.</span><span class="sxs-lookup"><span data-stu-id="6a660-113">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="6a660-114">Jest to oparte na iniekcji zależności, dzięki czemu można zamienić z tej wersji dev/test do wersji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="6a660-114">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="6a660-115">Implementacja RabbitMQ przykładowej magistrali zdarzeń deweloperskich/testowych jest kodem systemowym.</span><span class="sxs-lookup"><span data-stu-id="6a660-115">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="6a660-116">Musi obsługiwać połączenie z serwerem RabbitMQ i podać kod do publikowania zdarzenia wiadomości do kolejek.</span><span class="sxs-lookup"><span data-stu-id="6a660-116">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="6a660-117">Musi również zaimplementować słownik kolekcji obsługi zdarzeń integracji dla każdego typu zdarzenia; te typy zdarzeń mogą mieć różne wystąpienia i różnych subskrypcji dla każdej mikrousługi odbiornika, jak pokazano na rysunku 6-21.</span><span class="sxs-lookup"><span data-stu-id="6a660-117">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="6a660-118">Implementowanie prostej metody publikowania za pomocą RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="6a660-118">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="6a660-119">Poniższy kod jest ***uproszczoną*** wersją implementacji magistrali zdarzeń dla RabbitMQ, aby zaprezentować cały scenariusz.</span><span class="sxs-lookup"><span data-stu-id="6a660-119">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="6a660-120">Tak naprawdę nie obsługujesz połączenia w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="6a660-120">You don't really handle the connection this way.</span></span> <span data-ttu-id="6a660-121">Aby wyświetlić pełną implementację, zobacz rzeczywisty kod w repozytorium [dotnet-architecture/eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)</span><span class="sxs-lookup"><span data-stu-id="6a660-121">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="6a660-122">[Rzeczywisty kod](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Publish metody w aplikacji eShopOnContainers jest ulepszony przy użyciu zasad ponawiania [Polly,](https://github.com/App-vNext/Polly) który ponawia próbę zadania określoną liczbę razy w przypadku kontenera RabbitMQ nie jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="6a660-122">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="6a660-123">Taka sytuacja może wystąpić, gdy docker-compose uruchamia kontenery; na przykład kontener RabbitMQ może rozpoczynać się wolniej niż inne kontenery.</span><span class="sxs-lookup"><span data-stu-id="6a660-123">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="6a660-124">Jak wspomniano wcześniej, istnieje wiele możliwych konfiguracji w RabbitMQ, więc ten kod powinien być używany tylko dla środowisk deweloperskich/testowych.</span><span class="sxs-lookup"><span data-stu-id="6a660-124">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="6a660-125">Implementowanie kodu subskrypcji za pomocą interfejsu API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="6a660-125">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="6a660-126">Podobnie jak w przypadku kodu publikowania, poniższy kod jest uproszczenie części implementacji magistrali zdarzeń dla RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="6a660-126">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="6a660-127">Ponownie, zwykle nie trzeba go zmieniać, chyba że go poprawiasz.</span><span class="sxs-lookup"><span data-stu-id="6a660-127">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="6a660-128">Każdy typ zdarzenia ma powiązany kanał, aby uzyskać zdarzenia z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="6a660-128">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="6a660-129">Następnie można mieć dowolną liczbę programów obsługi zdarzeń na kanał i typ zdarzenia, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="6a660-129">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="6a660-130">Subscribe Metoda akceptuje IIntegrationEventHandler obiektu, który jest jak metoda wywołania wywołania w bieżącej mikrousługi, a także jego powiązany IntegrEvent obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a660-130">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="6a660-131">Następnie kod dodaje, że program obsługi zdarzeń do listy programów obsługi zdarzeń, które każdy typ zdarzenia integracji może mieć na mikrousługi klienta.</span><span class="sxs-lookup"><span data-stu-id="6a660-131">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="6a660-132">Jeśli kod klienta nie został jeszcze subskrybowany zdarzenia, kod tworzy kanał dla typu zdarzenia, dzięki czemu może odbierać zdarzenia w stylu wypychania z RabbitMQ, gdy to zdarzenie jest publikowane z innej usługi.</span><span class="sxs-lookup"><span data-stu-id="6a660-132">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="6a660-133">Jak wspomniano powyżej, magistrala zdarzeń zaimplementowana w eShopOnContainers ma tylko i cel edukacyjny, ponieważ obsługuje tylko główne scenariusze, więc nie jest gotowy do produkcji.</span><span class="sxs-lookup"><span data-stu-id="6a660-133">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="6a660-134">W przypadku scenariuszy produkcyjnych sprawdź dodatkowe zasoby poniżej, specyficzne dla RabbitMQ i [implementowanie komunikacji opartej na zdarzeniach między mikrousług](./integration-event-based-microservice-communications.md#additional-resources) sekcji.</span><span class="sxs-lookup"><span data-stu-id="6a660-134">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6a660-135">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="6a660-135">Additional resources</span></span>

<span data-ttu-id="6a660-136">Gotowe do produkcji rozwiązania ze wsparciem dla RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="6a660-136">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="6a660-137">**EasyNetQ** - Klient interfejsu API open source .NET dla RabbitMQ </span><span class="sxs-lookup"><span data-stu-id="6a660-137">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <http://easynetq.com/>

- <span data-ttu-id="6a660-138">**Transport masowy** </span><span class="sxs-lookup"><span data-stu-id="6a660-138">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
><span data-ttu-id="6a660-139">[Poprzedni](integration-event-based-microservice-communications.md)
>[następny](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="6a660-139">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
