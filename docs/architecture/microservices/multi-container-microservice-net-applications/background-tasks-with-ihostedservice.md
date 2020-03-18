---
title: Implementowanie zadań w tle w mikrousługach za pomocą usługi IHostedService i klasy BackgroundService
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z nowymi opcjami używania usługi IHostedService i BackgroundService do implementowania zadań w tle w mikrousługach .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fab67c816e90c69a4d593422b4974cb9b8819807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502310"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="23fbd-103">Implementowanie zadań w tle w mikrousługach za pomocą usługi IHostedService i klasy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="23fbd-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="23fbd-104">Zadania w tle i zaplanowane zadania są czymś, co może być konieczne do zaimplementowania, po pewnym czasie, w aplikacji opartej na mikrousługach lub w dowolnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23fbd-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="23fbd-105">Różnica podczas korzystania z architektury mikrousług jest, że można zaimplementować proces/kontener pojedynczej mikrousługi do obsługi tych zadań w tle, dzięki czemu można skalować go w dół/w górę, zgodnie z potrzebami lub można nawet upewnić się, że uruchamia pojedyncze wystąpienie tego procesu mikrousługi/kontenera.</span><span class="sxs-lookup"><span data-stu-id="23fbd-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="23fbd-106">Z ogólnego punktu widzenia w programie .NET Core nazwaliśmy tego typu zadania *hostowane usługi*, ponieważ są one usług/logiki, które hosta w hoście/aplikacji/mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="23fbd-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="23fbd-107">Należy zauważyć, że w tym przypadku usługa hostowana oznacza po prostu klasę z logiką zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="23fbd-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="23fbd-108">Ponieważ .NET Core 2.0, struktura udostępnia <xref:Microsoft.Extensions.Hosting.IHostedService> nowy interfejs o nazwie pomaga łatwo zaimplementować hostowane usługi.</span><span class="sxs-lookup"><span data-stu-id="23fbd-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="23fbd-109">Podstawową ideą jest to, że można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle, gdy host internetowy lub host jest uruchomiony, jak pokazano na obrazie 6-26.</span><span class="sxs-lookup"><span data-stu-id="23fbd-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagram porównujący ASP.NET Core IWebHost i .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="23fbd-111">**Rysunek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="23fbd-111">**Figure 6-26**.</span></span> <span data-ttu-id="23fbd-112">Korzystanie z usługi IHostedService w aplikacji WebHost a host</span><span class="sxs-lookup"><span data-stu-id="23fbd-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="23fbd-113">ASP.NET obsługa `IWebHost` podstawowych 1.x i 2.x procesów w tle w aplikacjach internetowych.</span><span class="sxs-lookup"><span data-stu-id="23fbd-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="23fbd-114">.NET Core 2.1 i `IHost` nowsze wersje obsługują procesy w tle za pomocą zwykłych aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="23fbd-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="23fbd-115">Zwróć uwagę `WebHost` na `Host`różnicę między i .</span><span class="sxs-lookup"><span data-stu-id="23fbd-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="23fbd-116">A `WebHost` (implementacja `IWebHost`klasy podstawowej) w ASP.NET Core 2.0 to artefakt infrastruktury używany do dostarczania funkcji serwera HTTP do procesu, na przykład podczas implementowania aplikacji sieci Web MVC lub usługi interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="23fbd-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="23fbd-117">Zapewnia wszystkie nowe dobroć infrastruktury w ASP.NET Core, umożliwiając użycie iniekcji zależności, wstawione programy pośredniczące w potoku żądania i podobne.</span><span class="sxs-lookup"><span data-stu-id="23fbd-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="23fbd-118">Używa `WebHost` tych samych do `IHostedServices` zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="23fbd-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="23fbd-119">A `Host` (klasa `IHost`podstawowa implementująca) została wprowadzona w .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="23fbd-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="23fbd-120">Zasadniczo, `Host` a pozwala mieć podobną infrastrukturę niż `WebHost` to, co masz z (iniekcji zależności, usługi hostowane, itp.), ale w tym przypadku, po prostu chcesz mieć prosty i lżejszy proces jako host, z niczym związane z MVC, Web API lub funkcje serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="23fbd-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="23fbd-121">W związku z tym można wybrać i `IHost` utworzyć wyspecjalizowany proces hosta z do obsługi usług hostowanych i nic więcej, takie mikrousługi wykonane tylko do hostowania `IHostedServices`, lub można alternatywnie rozszerzyć istniejące ASP.NET Core `WebHost`, takich jak istniejący ASP.NET Core Web API lub MVC aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23fbd-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="23fbd-122">Każde podejście ma zalety i wady w zależności od firmy i potrzeb skalowalności.</span><span class="sxs-lookup"><span data-stu-id="23fbd-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="23fbd-123">Najważniejsze jest to, że jeśli zadania w tle nie`IWebHost`mają nic `IHost`wspólnego z HTTP ( ) należy użyć .</span><span class="sxs-lookup"><span data-stu-id="23fbd-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="23fbd-124">Rejestrowanie hostowanych usług w webhostie lub hoście</span><span class="sxs-lookup"><span data-stu-id="23fbd-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="23fbd-125">Przejdźmy do szczegółów na `IHostedService` interfejsie, ponieważ jego `WebHost` użycie jest `Host`bardzo podobne w lub w .</span><span class="sxs-lookup"><span data-stu-id="23fbd-125">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="23fbd-126">SignalR jest jednym z przykładów artefaktu przy użyciu hostowanych usług, ale można go również używać do znacznie prostszych rzeczy, takich jak:</span><span class="sxs-lookup"><span data-stu-id="23fbd-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="23fbd-127">Zadanie w tle sondowania bazy danych w poszukiwaniu zmian.</span><span class="sxs-lookup"><span data-stu-id="23fbd-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="23fbd-128">Zaplanowane zadanie okresowo aktualizuje niektóre pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="23fbd-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="23fbd-129">Implementacja QueueBackgroundWorkItem, który umożliwia zadanie do wykonania w wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="23fbd-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="23fbd-130">Przetwarzanie wiadomości z kolejki komunikatów w tle aplikacji sieci `ILogger`web podczas udostępniania typowych usług, takich jak .</span><span class="sxs-lookup"><span data-stu-id="23fbd-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="23fbd-131">Zadanie w tle `Task.Run()`rozpoczęte od .</span><span class="sxs-lookup"><span data-stu-id="23fbd-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="23fbd-132">Można w zasadzie odciążyć dowolną z tych `IHostedService`akcji do zadania w tle, które implementuje .</span><span class="sxs-lookup"><span data-stu-id="23fbd-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="23fbd-133">Sposób dodawania jednego `IHostedServices` lub `WebHost` wielu `Host` do ciebie lub jest <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  przez zarejestrowanie `WebHost` ich za `Host` pomocą metody rozszerzenia w ASP.NET Core (lub w .NET Core 2.1 i powyżej).</span><span class="sxs-lookup"><span data-stu-id="23fbd-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="23fbd-134">Zasadniczo musisz zarejestrować hostowane usługi w znanej `ConfigureServices()` metodzie `Startup` klasy, jak w poniższym kodzie z typowego ASP.NET WebHost.</span><span class="sxs-lookup"><span data-stu-id="23fbd-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="23fbd-135">W tym kodzie `GracePeriodManagerService` hostowanej usługi jest prawdziwy kod z mikrousługi biznesowej zamawiania w eShopOnContainers, podczas gdy pozostałe dwa są tylko dwa dodatkowe przykłady.</span><span class="sxs-lookup"><span data-stu-id="23fbd-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="23fbd-136">Wykonywanie `IHostedService` zadania w tle jest koordynowany z okresem istnienia aplikacji (host lub mikrousługi, o to chodzi).</span><span class="sxs-lookup"><span data-stu-id="23fbd-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="23fbd-137">Rejestrujesz zadania podczas uruchamiania aplikacji i masz możliwość wykonania pewnych wdzięku akcji lub oczyszczania podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23fbd-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="23fbd-138">Bez `IHostedService`użycia, zawsze można uruchomić wątek w tle, aby uruchomić dowolne zadanie.</span><span class="sxs-lookup"><span data-stu-id="23fbd-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="23fbd-139">Różnica jest dokładnie w czasie zamykania aplikacji, gdy ten wątek będzie po prostu zabity bez możliwości uruchomienia wdzięku oczyszczania działań.</span><span class="sxs-lookup"><span data-stu-id="23fbd-139">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="23fbd-140">Interfejs IHostedService</span><span class="sxs-lookup"><span data-stu-id="23fbd-140">The IHostedService interface</span></span>

<span data-ttu-id="23fbd-141">Podczas rejestracji `IHostedService`.NET Core wywoła `StartAsync()` i `StopAsync()` metody typu `IHostedService` podczas uruchamiania i zatrzymywania aplikacji odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="23fbd-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="23fbd-142">W szczególności start jest wywoływany po `IApplicationLifetime.ApplicationStarted` uruchomieniu serwera i jest wyzwalany.</span><span class="sxs-lookup"><span data-stu-id="23fbd-142">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="23fbd-143">Zgodnie `IHostedService` z definicją w .NET Core, wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="23fbd-143">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

<span data-ttu-id="23fbd-144">Jak można sobie wyobrazić, można utworzyć wiele implementacji IHostedService i zarejestrować je w `ConfigureService()` metodzie do kontenera DI, jak pokazano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="23fbd-144">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="23fbd-145">Wszystkie te usługi hostowane zostaną uruchomione i zatrzymane wraz z aplikacją/mikrousługą.</span><span class="sxs-lookup"><span data-stu-id="23fbd-145">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="23fbd-146">Jako deweloper jesteś odpowiedzialny za obsługę akcji zatrzymywania usług, gdy `StopAsync()` metoda jest wyzwalana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="23fbd-146">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="23fbd-147">Implementowanie usługi IHostedService z niestandardową klasą usługi hostowane pochodzącej z klasy podstawowej BackgroundService</span><span class="sxs-lookup"><span data-stu-id="23fbd-147">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="23fbd-148">Można śmiało i utworzyć niestandardowe hostowane klasy usług `IHostedService`od podstaw i zaimplementować , jak trzeba zrobić podczas korzystania z .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="23fbd-148">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="23fbd-149">Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i innych `BackgroundService` typowych operacji, istnieje wygodna abstrakcyjna klasa podstawowa, z której można pochodzić, nazwana (dostępna od .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="23fbd-149">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="23fbd-150">Ta klasa zapewnia główną pracę potrzebną do skonfigurowania zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="23fbd-150">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="23fbd-151">Następny kod jest abstrakcyjną klasą podstawową BackgroundService zaimplementowane w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23fbd-151">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="23fbd-152">Podczas wywodzi się z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej dziedziczonej implementacji, wystarczy zaimplementować `ExecuteAsync()` metodę w własnej niestandardowej klasie hostowanej usługi, jak w poniższym uproszczonym kodzie z eShopOnContainers, który sonduje bazę danych i publikuje zdarzenia integracji w usłudze Event Bus w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="23fbd-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="23fbd-153">W tym konkretnym przypadku dla eShopOnContainers wykonuje metodę aplikacji, która jest wykonywanie kwerendy tabeli bazy danych w poszukiwaniu zamówień o określonym stanie i podczas stosowania zmian, publikuje zdarzenia integracji za pośrednictwem magistrali zdarzeń (pod nim może być przy użyciu rabbitmq lub usługi Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="23fbd-153">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="23fbd-154">Oczywiście, można uruchomić dowolne inne zadanie w tle biznesowym, zamiast.</span><span class="sxs-lookup"><span data-stu-id="23fbd-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="23fbd-155">Domyślnie token anulowania jest ustawiany z 5-sekundowym timeoutm, `WebHost` chociaż `UseShutdownTimeout` można ją `IWebHostBuilder`zmienić podczas tworzenia przy użyciu rozszerzenia pliku .</span><span class="sxs-lookup"><span data-stu-id="23fbd-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="23fbd-156">Oznacza to, że oczekuje się, że nasza usługa anuluje się w ciągu 5 sekund, w przeciwnym razie zostanie ona bardziej gwałtownie zabita.</span><span class="sxs-lookup"><span data-stu-id="23fbd-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="23fbd-157">Poniższy kod będzie zmieniać ten czas na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="23fbd-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="23fbd-158">Diagram klasy podsumowania</span><span class="sxs-lookup"><span data-stu-id="23fbd-158">Summary class diagram</span></span>

<span data-ttu-id="23fbd-159">Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów zaangażowanych podczas implementowania Usług IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="23fbd-159">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagram pokazujący, że IWebHost i IHost mogą obsługiwać wiele usług.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="23fbd-161">**Rysunek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="23fbd-161">**Figure 6-27**.</span></span> <span data-ttu-id="23fbd-162">Diagram klasy przedstawiający wiele klas i interfejsów związanych z usługą IHostedService</span><span class="sxs-lookup"><span data-stu-id="23fbd-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="23fbd-163">Diagram klasy: IWebHost i IHost mogą obsługiwać wiele usług, które dziedziczą z BackgroundService, która implementuje IHostedService.</span><span class="sxs-lookup"><span data-stu-id="23fbd-163">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="23fbd-164">Zagadnienia dotyczące wdrażania i dania na wynos</span><span class="sxs-lookup"><span data-stu-id="23fbd-164">Deployment considerations and takeaways</span></span>

<span data-ttu-id="23fbd-165">Należy pamiętać, że sposób wdrażania ASP.NET `WebHost` Core lub `Host` .NET Core może mieć wpływ na ostateczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="23fbd-165">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="23fbd-166">Na przykład jeśli wdrożysz swoje `WebHost` usługi IIS lub zwykłą usługę Azure App Service, host można zamknąć z powodu recyklingu puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23fbd-166">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="23fbd-167">Ale jeśli wdrażasz hosta jako kontener w koordynatora jak Kubernetes, można kontrolować pewną liczbę wystąpień na żywo hosta.</span><span class="sxs-lookup"><span data-stu-id="23fbd-167">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="23fbd-168">Ponadto można rozważyć inne podejścia w chmurze specjalnie dla tych scenariuszy, takich jak usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="23fbd-168">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="23fbd-169">Na koniec jeśli usługa jest potrzebna do bieżącego uruchomienia i wdrażana na serwerze Windows Server, możesz użyć usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23fbd-169">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="23fbd-170">Ale nawet `WebHost` w przypadku wdrożonych w puli aplikacji istnieją scenariusze, takie jak ponowne wypełnianie lub opróżnianie pamięci podręcznej aplikacji w pamięci, które nadal mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="23fbd-170">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="23fbd-171">Interfejs `IHostedService` zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET core aplikacji sieci web (w .NET Core 2.0 i nowszych wersjach) lub w dowolnym procesie/hoście (począwszy od .NET Core 2.1 z `IHost`).</span><span class="sxs-lookup"><span data-stu-id="23fbd-171">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="23fbd-172">Jego główną zaletą jest możliwość uzyskania z wdzięku anulowania do czyszczenia kodu zadań w tle, gdy sam host jest zamykany.</span><span class="sxs-lookup"><span data-stu-id="23fbd-172">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="23fbd-173">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="23fbd-173">Additional resources</span></span>

- <span data-ttu-id="23fbd-174">**Tworzenie zaplanowanego zadania w ASP.NET Core/Standard 2.0** </span><span class="sxs-lookup"><span data-stu-id="23fbd-174">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="23fbd-175">**Implementowanie usługi IHostedService w ASP.NET Core 2.0** </span><span class="sxs-lookup"><span data-stu-id="23fbd-175">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="23fbd-176">**GenericHost Próbki przy użyciu ASP.NET Core 2.1** </span><span class="sxs-lookup"><span data-stu-id="23fbd-176">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="23fbd-177">[Poprzedni](test-aspnet-core-services-web-apps.md)
>[następny](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="23fbd-177">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
