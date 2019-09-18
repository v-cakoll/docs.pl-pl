---
title: Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z nowymi opcjami umożliwiającymi korzystanie z IHostedService i BackgroundService w celu zaimplementowania zadań w tle w mikrousługach .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: ff263212536233bef85e9517442b4d7ed9eff115
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039885"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="361c1-103">Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="361c1-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="361c1-104">Zadania w tle i zaplanowane zadania to coś, co może wymagać wdrożenia, a ostatecznie, w aplikacji opartej na mikrousługach lub w dowolnym rodzaju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="361c1-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="361c1-105">Różnica w przypadku korzystania z architektury mikrousług polega na tym, że można zaimplementować pojedynczy proces mikrousług/kontener do obsługi tych zadań w tle, aby można było skalować go w dół lub w górę, a nawet mieć pewność, że uruchamia ono pojedyncze wystąpienie tego typu proces/kontener mikrousług.</span><span class="sxs-lookup"><span data-stu-id="361c1-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="361c1-106">Z ogólnego punktu widzenia w programie .NET Core wywołano te typy zadań *hostowanych usług*, ponieważ są one usługami/logiką hostowaną w ramach hosta/aplikacji/mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="361c1-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="361c1-107">Należy zauważyć, że w tym przypadku usługa hostowana po prostu oznacza klasę z logiką zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="361c1-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="361c1-108">Począwszy od platformy .NET Core 2,0, struktura zawiera nowy interfejs o <xref:Microsoft.Extensions.Hosting.IHostedService> nazwie pomagającej łatwo zaimplementować usługi hostowane.</span><span class="sxs-lookup"><span data-stu-id="361c1-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="361c1-109">Podstawowy pomysł polega na tym, że można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle, gdy host lub host sieci Web jest uruchomiony, jak pokazano na obrazie 6-26.</span><span class="sxs-lookup"><span data-stu-id="361c1-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1. x i 2. x obsługuje IWebHost dla procesów w tle w aplikacjach sieci Web, .NET Core 2, 1 obsługuje IHost dla procesów w tle, w których są proste aplikacje konsolowe.](./media/image26.png)

<span data-ttu-id="361c1-111">**Rysunek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="361c1-111">**Figure 6-26**.</span></span> <span data-ttu-id="361c1-112">Używanie IHostedService w elemencie WebHost a Host</span><span class="sxs-lookup"><span data-stu-id="361c1-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="361c1-113">Zwróć uwagę na różnice między `WebHost` i `Host`.</span><span class="sxs-lookup"><span data-stu-id="361c1-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="361c1-114">(Klasa bazowa implementująca `IWebHost`) w ASP.NET Core 2,0 to artefakt infrastruktury używany do udostępniania funkcji serwera HTTP dla procesu, na przykład w przypadku implementowania aplikacji sieci Web MVC lub usługi Web API. `WebHost`</span><span class="sxs-lookup"><span data-stu-id="361c1-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="361c1-115">Zapewnia ona wszystkie nowe dobraność infrastruktury w ASP.NET Core, co pozwala na korzystanie z iniekcji zależności, wstawianie middlewares w potoku żądań itd. i precyzyjne korzystanie z `IHostedServices` nich na potrzeby zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="361c1-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="361c1-116">A `Host` (implementacja `IHost`klasy bazowej) została wprowadzona w programie .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="361c1-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="361c1-117">W zasadzie usługa `Host` a pozwala korzystać z podobnej infrastruktury niż to, z `WebHost` jakim korzystasz (iniekcja zależności, usługi hostowane itp.), ale w tym przypadku wystarczy, że chcesz mieć prosty i jaśniejszy proces jako host, bez żadnych elementów związanych z MVC , Interfejs API sieci Web lub funkcje serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="361c1-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="361c1-118">W związku z tym można wybrać i utworzyć wyspecjalizowany proces hosta z IHost, aby obsługiwać usługi hostowane, a nic innego nie miało na celu hostowania `IHostedServices`lub można również zwiększyć istniejące ASP.NET Core `WebHost` , takich jak istniejący ASP.NET Core Web API lub aplikacja MVC.</span><span class="sxs-lookup"><span data-stu-id="361c1-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="361c1-119">Każde podejście ma wady i zalety w zależności od potrzeb firmy i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="361c1-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="361c1-120">Dolna linia jest zasadniczo taka, że jeśli zadania w tle nie mają nic robić z HTTP (IWebHost), należy użyć IHost.</span><span class="sxs-lookup"><span data-stu-id="361c1-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="361c1-121">Rejestrowanie usług hostowanych w usłudze WebHost lub hoście</span><span class="sxs-lookup"><span data-stu-id="361c1-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="361c1-122">Przejdźmy do dalszych etapów interfejsu `IHostedService` , ponieważ jego użycie jest dość podobne `WebHost` w lub w `Host`.</span><span class="sxs-lookup"><span data-stu-id="361c1-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="361c1-123">Sygnalizujący to jeden przykład artefaktu korzystającego z usług hostowanych, ale można go również użyć do znacznie prostszego działania, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="361c1-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="361c1-124">Zadanie w tle sondowanie bazy danych szukającej zmian.</span><span class="sxs-lookup"><span data-stu-id="361c1-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="361c1-125">Zaplanowane zadanie aktualizuje nieco pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="361c1-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="361c1-126">Implementacja QueueBackgroundWorkItem, która umożliwia wykonywanie zadania w wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="361c1-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="361c1-127">Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacji sieci Web podczas udostępniania wspólnych usług, takich jak `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="361c1-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="361c1-128">Zadanie w tle zostało uruchomione `Task.Run()`przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="361c1-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="361c1-129">Można zasadniczo odciążyć dowolne z tych akcji do zadania w tle w oparciu o IHostedService.</span><span class="sxs-lookup"><span data-stu-id="361c1-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="361c1-130">Sposób dodawania jednego `IHostedServices` lub wielu `WebHost` do lub `Host` jest przez zarejestrowanie ich za pomocą standardowego di (iniekcja zależności `Host` ) w ASP.NET Core `WebHost` (lub w środowisku .NET Core 2,1 lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="361c1-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="361c1-131">Zasadniczo należy zarejestrować usługi hostowane w znanej `ConfigureServices()` metodzie `Startup` klasy, jak w poniższym kodzie z typowego elementu webhost ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="361c1-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="361c1-132">W tym kodzie `GracePeriodManagerService` usługa hostowana jest realnym kodem z mikrousługi eShopOnContainers w firmie, a pozostałe dwa są tylko dwoma dodatkowymi przykładami.</span><span class="sxs-lookup"><span data-stu-id="361c1-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="361c1-133">Wykonywanie `IHostedService` zadania w tle jest koordynowane z okresem istnienia aplikacji (hosta lub mikrousługi).</span><span class="sxs-lookup"><span data-stu-id="361c1-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="361c1-134">Zadania są rejestrowane, gdy aplikacja zostanie uruchomiona i masz możliwość wykonywania pewnych działań lub czyszczenia danych podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="361c1-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="361c1-135">Bez korzystania `IHostedService`z programu można zawsze uruchomić wątek w tle, aby uruchomić dowolne zadanie.</span><span class="sxs-lookup"><span data-stu-id="361c1-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="361c1-136">Różnica jest precyzyjna w czasie zamykania aplikacji, gdy ten wątek zostanie po prostu zamknięty, bez możliwości uruchamiania łagodnych akcji oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="361c1-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="361c1-137">Interfejs IHostedService</span><span class="sxs-lookup"><span data-stu-id="361c1-137">The IHostedService interface</span></span>

<span data-ttu-id="361c1-138">Po zarejestrowaniu `IHostedService`platforma .NET Core będzie `StartAsync()` wywoływała metody `StopAsync()` `IHostedService` i, podczas uruchamiania i zatrzymywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="361c1-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="361c1-139">Polecenie Start jest wywoływane po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` wyzwoleniu.</span><span class="sxs-lookup"><span data-stu-id="361c1-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="361c1-140">`IHostedService` Zgodnie z definicją w programie .NET Core wygląda to w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="361c1-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="361c1-141">Jak można wyobrazić, można utworzyć wiele implementacji IHostedService i zarejestrować je w `ConfigureService()` metodzie w kontenerze di, jak pokazano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="361c1-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="361c1-142">Wszystkie te usługi hostowane zostaną uruchomione i zatrzymane wraz z aplikacją/mikrousługą.</span><span class="sxs-lookup"><span data-stu-id="361c1-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="361c1-143">Jako programista użytkownik jest odpowiedzialny za obsługę zatrzymania działania usług, gdy `StopAsync()` Metoda jest wyzwalana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="361c1-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="361c1-144">Implementowanie IHostedService z niestandardową klasą usługi hostowanej pochodną z klasy podstawowej BackgroundService</span><span class="sxs-lookup"><span data-stu-id="361c1-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="361c1-145">Można utworzyć niestandardową klasę usług hostowanych od podstaw i zaimplementować ją `IHostedService`, tak jak należy to zrobić w przypadku korzystania z platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="361c1-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="361c1-146">Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i innych typowych operacji, istnieje wygodna abstrakcyjna klasa bazowa, `BackgroundService` z której pochodzi (dostępna od platformy .NET Core 2,1).</span><span class="sxs-lookup"><span data-stu-id="361c1-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="361c1-147">Ta klasa udostępnia główną służbę wymaganą do skonfigurowania zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="361c1-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="361c1-148">Następny kod jest abstrakcyjną klasą bazową BackgroundService zaimplementowaną w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="361c1-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="361c1-149">Podczas wyprowadzania z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej dziedziczonej implementacji, wystarczy zaimplementować `ExecuteAsync()` metodę we własnej niestandardowej klasie usługi hostowanej, jak w poniższym kodzie uproszczonym z eShopOnContainers, który sonduje zdarzenia integracji bazy danych i publikowania w usłudze Event Bus w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="361c1-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

<span data-ttu-id="361c1-150">W tym konkretnym przypadku eShopOnContainers jest wykonywana metoda aplikacji, która jest kwerendą tabeli bazy danych szukającą zamówień o określonym stanie i podczas stosowania zmian, publikuje zdarzenia integracji za pomocą magistrali zdarzeń (poniżej może być Korzystanie z RabbitMQ lub Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="361c1-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="361c1-151">Oczywiście możesz zamiast tego uruchomić dowolne inne zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="361c1-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="361c1-152">Domyślnie token anulowania jest ustawiany z 5-sekundowym limitem czasu, ale można zmienić tę wartość podczas kompilowania `WebHost` `UseShutdownTimeout` przy użyciu rozszerzenia `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="361c1-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="361c1-153">Oznacza to, że nasza usługa powinna zostać anulowana w ciągu 5 sekund, w przeciwnym razie będzie bardziej nieoczekiwanie zabity.</span><span class="sxs-lookup"><span data-stu-id="361c1-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="361c1-154">Poniższy kod zmieni ten czas na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="361c1-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="361c1-155">Diagram klas podsumowania</span><span class="sxs-lookup"><span data-stu-id="361c1-155">Summary class diagram</span></span>

<span data-ttu-id="361c1-156">Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów, które są wykorzystywane podczas implementowania IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="361c1-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>

![Diagram klas: IWebHost i IHost mogą obsługiwać wiele usług, które dziedziczą z BackgroundService, który implementuje IHostedService.](./media/image27.png)

<span data-ttu-id="361c1-158">**Rysunek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="361c1-158">**Figure 6-27**.</span></span> <span data-ttu-id="361c1-159">Diagram klas przedstawiający wiele klas i interfejsów związanych z IHostedService</span><span class="sxs-lookup"><span data-stu-id="361c1-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="361c1-160">Zagadnienia dotyczące wdrażania i wnioski</span><span class="sxs-lookup"><span data-stu-id="361c1-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="361c1-161">Należy pamiętać, że sposób wdrażania ASP.NET Core `WebHost` lub .NET Core `Host` może mieć wpływ na ostateczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="361c1-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="361c1-162">Na przykład w przypadku wdrożenia `WebHost` na serwerze IIS lub w regularnych Azure App Service można wyłączyć hosta z powodu odtwarzania puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="361c1-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="361c1-163">Ale w przypadku wdrażania hosta jako kontenera do programu Orchestrator, takiego jak Kubernetes lub Service Fabric, można kontrolować zagwarantowaną liczbę wystąpień na żywo hosta.</span><span class="sxs-lookup"><span data-stu-id="361c1-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="361c1-164">Ponadto można rozważyć inne podejścia w chmurze szczególnie dla tych scenariuszy, takie jak Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="361c1-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="361c1-165">Na koniec w przypadku konieczności uruchomienia usługi przez cały czas i wdrożenia na serwerze z systemem Windows można użyć usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="361c1-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="361c1-166">Jednak nawet w przypadku `WebHost` wdrożenia w puli aplikacji istnieją scenariusze, takie jak ponowne wypełnianie lub opróżnianie pamięci podręcznej w pamięci, które nadal będą miały zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="361c1-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="361c1-167">Interfejs zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET Core aplikacji sieci Web (w programie .NET Core 2,0) lub w dowolnym procesie/hoście (począwszy od platformy .NET Core 2,1 z `IHost`). `IHostedService`</span><span class="sxs-lookup"><span data-stu-id="361c1-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="361c1-168">Jej główną korzyścią jest możliwość korzystania z bezpiecznego anulowania kodu czyszczenia zadań w tle podczas zamykania samego hosta.</span><span class="sxs-lookup"><span data-stu-id="361c1-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="361c1-169">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="361c1-169">Additional resources</span></span>

- <span data-ttu-id="361c1-170">**Tworzenie zaplanowanego zadania w ASP.NET Core/standardowa 2,0**</span><span class="sxs-lookup"><span data-stu-id="361c1-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span>  
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="361c1-171">**Implementacja IHostedService w ASP.NET Core 2,0**</span><span class="sxs-lookup"><span data-stu-id="361c1-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span>  
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="361c1-172">**Przykład GenericHost za pomocą ASP.NET Core 2,1**</span><span class="sxs-lookup"><span data-stu-id="361c1-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span>  
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="361c1-173">[Poprzedni](test-aspnet-core-services-web-apps.md)Następny
>[](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="361c1-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
