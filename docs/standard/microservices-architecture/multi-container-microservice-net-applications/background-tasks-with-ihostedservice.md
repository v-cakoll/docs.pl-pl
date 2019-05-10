---
title: Implementowanie zadań w tle w mikrousługach za pomocą interfejsu IHostedService i klasa BackgroundService
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, nowe opcje do użycia pomocą interfejsu IHostedService i BackgroundService implementowania zadań tle w mikrousługach .NET Core.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9203404c0b623570c2b089087b7ce5d676bba376
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062982"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="6bcfa-103">Implementowanie zadań w tle w mikrousługach za pomocą interfejsu IHostedService i klasa BackgroundService</span><span class="sxs-lookup"><span data-stu-id="6bcfa-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="6bcfa-104">Zadania w tle i zaplanowane zadania to coś, co jest potrzebne do zaimplementowania po pewnym czasie w aplikacji mikrousług na podstawie lub w dowolnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="6bcfa-105">Różnica w przypadku korzystania z architektury mikrousług jest zaimplementowanie pojedynczych mikrousług procesu/kontenera do hostowania te zadania w tle, dzięki czemu można skalować ją w górę/w dół zgodnie z potrzebne lub można nawet upewnij się, że działa jedno wystąpienie mikrousługi procesu/kontenera.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="6bcfa-106">Od ogólnego punktu widzenia platformie .NET Core dzwoniliśmy do tego rodzaju zadania *usługi hostowane*, ponieważ są one usług/logikę, która hostować w ramach usługi hosta/aplikacji/mikrousług.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="6bcfa-107">Należy pamiętać, że w tym przypadku usługa hostowana po prostu oznacza, że klasa wraz z logiką zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="6bcfa-108">Od .NET Core 2.0, struktura zapewnia nowy interfejs o nazwie <xref:Microsoft.Extensions.Hosting.IHostedService> pomaga łatwo Implementuj hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="6bcfa-109">Podstawowa Koncepcja polega na można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle podczas hosta sieci web lub hoście jest uruchomiona, jak pokazano na ilustracji 6-26.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1.x i 2.x obsługę IWebHost tła procesów w aplikacji sieci web platformy .NET Core obsługuje 2,1 IHost dla procesów w tle za pomocą aplikacji konsoli zwykły.](./media/image26.png)

<span data-ttu-id="6bcfa-111">**Rysunek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-111">**Figure 6-26**.</span></span> <span data-ttu-id="6bcfa-112">Korzystanie z pomocą interfejsu IHostedService w WebHost a hostem</span><span class="sxs-lookup"><span data-stu-id="6bcfa-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="6bcfa-113">Należy zanotować różnicę między `WebHost` i `Host`.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="6bcfa-114">A `WebHost` (podstawowa Implementacja klasy `IWebHost`) w programie ASP.NET Core 2.0 jest artefaktów infrastruktury umożliwia Podaj serwer HTTP funkcje do procesu, na przykład w przypadku wdrażania aplikacji sieci web MVC lub interfejsu API sieci Web usługi.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="6bcfa-115">Zawiera wszystkie nowe zgodność infrastruktury w programie ASP.NET Core, umożliwiając iniekcji zależności, Wstaw middlewares Potok żądań, itp. i dokładnie służą `IHostedServices` dla zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="6bcfa-116">A `Host` (podstawowa Implementacja klasy `IHost`) wprowadzono w programie .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="6bcfa-117">Po prostu `Host` pozwala na korzystanie z podobnych infrastruktury niż posiadane przez Ciebie za pomocą `WebHost` (iniekcji zależności, hostowanych usług, itp.), ale w takim przypadku po prostu chcesz mieć jaśniejszy procesem jako hosta, z żadnych danych dotyczących MVC , HTTP i interfejsów API funkcji serwera w sieci web.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="6bcfa-118">W związku z tym, można wybrać i Utwórz wyspecjalizowane procesu hosta za pomocą IHost do obsługi usług hostowanych i nic, mikrousługi, stworzona dla hostingu `IHostedServices`, lub też można rozszerzyć istniejące platformy ASP.NET Core `WebHost` , takich jak istniejącej aplikacji i interfejsów API platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="6bcfa-119">Każde podejście ma zalety i wady, w zależności od potrzeb biznesowych i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="6bcfa-120">Mierzenie jest zasadniczo Jeśli zadania w tle nie ma nic do zrobienia za pośrednictwem protokołu HTTP (IWebHost), należy użyć IHost.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="6bcfa-121">Rejestrowanie hostowanych usług w hosta lub hostem sieci Web</span><span class="sxs-lookup"><span data-stu-id="6bcfa-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="6bcfa-122">Umożliwia przechodzenie do dalsze na `IHostedService` interfejsu, ponieważ jego użycie jest bardzo podobna `WebHost` lub `Host`.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="6bcfa-123">SignalR jest przykładem artefakt przy użyciu usług hostowanych, ale możesz również używać go do znacznie prostsze elementów, takich jak:</span><span class="sxs-lookup"><span data-stu-id="6bcfa-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="6bcfa-124">Zadanie w tle sondowania szukasz zmiany bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="6bcfa-125">Zaplanowane zadanie aktualizacji okresowo niektóre pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="6bcfa-126">Implementacja QueueBackgroundWorkItem umożliwiająca zadań do wykonania w wątku tła.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="6bcfa-127">Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacja sieci web a jednocześnie udostępnianie usług wspólne, takie jak `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="6bcfa-128">Rozpoczęcie zadania w tle `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="6bcfa-129">W zasadzie można odciążyć dowolne z tych akcji, aby zadanie w tle oparte na pomocą interfejsu IHostedService.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="6bcfa-130">Sposób dodawania jednego lub wielu `IHostedServices` do Twojej `WebHost` lub `Host` polega na rejestrowania ich za pośrednictwem standardowych DI (iniekcji zależności) w programie ASP.NET Core `WebHost` (lub `Host` platformy .NET Core 2.1 lub więcej).</span><span class="sxs-lookup"><span data-stu-id="6bcfa-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="6bcfa-131">Zasadniczo należy zarejestrować usług hostowanych w znanej `ConfigureServices()` metody `Startup` klasy, jak w poniższym kodzie z typowym hostem sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="6bcfa-132">W tym kodzie `GracePeriodManagerService` usługi hostowanej jest rzeczywisty kod z mikrousług firm porządkowanie w ramach aplikacji eShopOnContainers, podczas gdy inne dwa są tylko dwa dodatkowe przykłady.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="6bcfa-133">`IHostedService` Wykonywanie zadań w tle są koordynowane za pomocą cyklu życia aplikacji (hosta lub mikrousług istotnego dla badania).</span><span class="sxs-lookup"><span data-stu-id="6bcfa-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="6bcfa-134">Możesz zarejestrować zadania podczas uruchamiania aplikacji i mieć możliwość niektórych czynności łagodne lub czyszczenia po dana aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="6bcfa-135">Bez użycia `IHostedService`, zawsze można uruchomić wątku w tle do uruchamiania zadań.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="6bcfa-136">Różnica polega na dokładnie na czas zamykania aplikacji, gdy wątek będzie po prostu zabite bez możliwości uruchamiania łagodne akcje czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="6bcfa-137">Interfejs pomocą interfejsu IHostedService</span><span class="sxs-lookup"><span data-stu-id="6bcfa-137">The IHostedService interface</span></span>

<span data-ttu-id="6bcfa-138">Po dokonaniu rejestracji `IHostedService`, .NET Core będzie wywoływać `StartAsync()` i `StopAsync()` metody usługi `IHostedService` wpisz podczas uruchamiania aplikacji i Zatrzymaj odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="6bcfa-139">W szczególności start jest wywoływana po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="6bcfa-140">`IHostedService` Zgodnie z definicją w programie .NET Core, wygląda podobnie do następującego.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="6bcfa-141">Jak możesz sobie wyobrazić, możesz utworzyć wiele implementacji pomocą interfejsu IHostedService i zarejestruj je w `ConfigureService()` metody do kontenera DI, jak pokazano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="6bcfa-142">Wszystkie te usługi hostowanej będzie można uruchamiać i zatrzymywać wraz z aplikacji/mikrousług.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="6bcfa-143">Jako deweloper jest odpowiedzialny za obsługę Akcja zatrzymania usług podczas `StopAsync()` metoda jest wywoływana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="6bcfa-144">Implementowanie pomocą interfejsu IHostedService za pomocą klasy niestandardowej usługi hostowanej pochodząca z klasy bazowej BackgroundService</span><span class="sxs-lookup"><span data-stu-id="6bcfa-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="6bcfa-145">Przejdź dalej i tworzenia klasy niestandardowej usługi hostowanej od podstaw i zaimplementować `IHostedService`, jak należy wykonać w przypadku korzystania z platformy .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="6bcfa-146">Ponieważ większość zadań w tle będzie miał podobnych potrzebach w zakresie zarządzania tokenów anulowania i innymi typowymi operacjami, ma jednak wygodne abstrakcyjna klasa bazowa może pochodzić od o nazwie `BackgroundService` (dostępny od platformy .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="6bcfa-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="6bcfa-147">Ta klasa zawiera główna Praca niezbędne do skonfigurowania zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="6bcfa-148">Następny kod jest abstrakcyjna klasa bazowa BackgroundService zaimplementowanego w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="6bcfa-149">Podczas wyprowadzania z poprzednim abstrakcyjna klasa bazowa, dzięki tym dziedziczona implementacja wystarczy do zaimplementowania `ExecuteAsync()` metody w Twoje własne, niestandardowe klasy usługi hostowanej, w następującej uproszczony kod w ramach aplikacji eShopOnContainers, którego sondowanie bazę danych i publikowania zdarzeń integracji do magistrali zdarzeń, gdy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
            // and publishing events into the Event Bus (RabbitMS / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="6bcfa-150">W tym konkretnym przypadku dla ramach aplikacji eShopOnContainers wykonuje metodę aplikacji, która sprawdza tabelę bazy danych, wyszukiwanie zamówienia z określonym stanem, i po wprowadzeniu zmian publikowania zdarzeń integracji za pomocą magistrali zdarzeń (na dole przyczyną może być Korzystanie z oprogramowania RabbitMQ lub Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="6bcfa-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="6bcfa-151">Oczywiście można uruchomić żadnych innych firm zadanie w tle, zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="6bcfa-152">Token anulowania jest domyślnie z 5 drugi przekroczenie limitu czasu, mimo że można zmienić tę wartość podczas tworzenia usługi `WebHost` przy użyciu `UseShutdownTimeout` rozszerzenie `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="6bcfa-153">Oznacza to, że usługa oczekuje się, można anulować w ciągu 5 sekund w przeciwnym razie zostanie więcej nagle zabita.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="6bcfa-154">Poniższy kod będzie zmiana czasu na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="6bcfa-155">Diagram klas podsumowania</span><span class="sxs-lookup"><span data-stu-id="6bcfa-155">Summary class diagram</span></span>

<span data-ttu-id="6bcfa-156">Na poniższej ilustracji przedstawiono wizualizację podsumowanie klas i podłączony zaangażowane podczas implementowania IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>

![Diagram klasy: IWebHost i IHost może obsługiwać wiele usług, które dziedziczą z BackgroundService, która implementuje pomocą interfejsu IHostedService.](./media/image27.png)

<span data-ttu-id="6bcfa-158">**Rysunek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-158">**Figure 6-27**.</span></span> <span data-ttu-id="6bcfa-159">Diagram klas przedstawiający wielokrotność klasy i interfejsy powiązane z pomocą interfejsu IHostedService</span><span class="sxs-lookup"><span data-stu-id="6bcfa-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="6bcfa-160">Zagadnienia dotyczące wdrażania i wnioski</span><span class="sxs-lookup"><span data-stu-id="6bcfa-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="6bcfa-161">Ważne jest, aby należy pamiętać, że sposób wdrażania ASP.NET Core `WebHost` lub .NET Core `Host` mogą mieć wpływ na ostateczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="6bcfa-162">Na przykład w przypadku wdrożenia usługi `WebHost` w usługach IIS lub regularnych usługi Azure App Service hosta może zostać wyłączony z powodu odtwarzanie puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="6bcfa-163">Jeżeli wdrażasz hosta jako kontener, do programu orchestrator, takich jak Kubernetes lub usługi Service Fabric można jednak sterować bezpieczne liczbę wystąpień na żywo hosta.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="6bcfa-164">Ponadto można rozważyć inne podejścia w chmurze, szczególnie wprowadzone dla tych scenariuszy, takich jak Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="6bcfa-165">Ponadto jeśli niezbędna jest usługa działa przez cały czas i są wdrażane na systemie Windows Server można użyć usługa Windows.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="6bcfa-166">Ale nawet w przypadku `WebHost` wdrożone do puli aplikacji, istnieją scenariusze, takie jak uważnie lub opróżniania pamięci podręcznej w pamięci aplikacji, które będą nadal stosowane.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="6bcfa-167">`IHostedService` Interfejs zapewnia wygodny sposób uruchamiania zadania w tle w platformy ASP.NET Core w aplikacji sieci web (w programie .NET Core 2.0) lub w dowolnym host/procesu (począwszy od platformy .NET Core 2.1 przy użyciu `IHost`).</span><span class="sxs-lookup"><span data-stu-id="6bcfa-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="6bcfa-168">Jego największą korzyścią jest możliwość pobranego z łagodne anulowanie zadania w tle na kod czyszczenia, gdy sam host jest zamykany.</span><span class="sxs-lookup"><span data-stu-id="6bcfa-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6bcfa-169">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="6bcfa-169">Additional resources</span></span>

- <span data-ttu-id="6bcfa-170">**Tworzenie zaplanowanego zadania w programie ASP.NET 2.0 Core/Standard**</span><span class="sxs-lookup"><span data-stu-id="6bcfa-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> <br/>
    <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="6bcfa-171">**Implementowanie pomocą interfejsu IHostedService w programie ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="6bcfa-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> <br/>
    <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="6bcfa-172">**Przykład GenericHost za pomocą platformy ASP.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="6bcfa-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span> <br/>
    <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="6bcfa-173">[Poprzednie](test-aspnet-core-services-web-apps.md)
>[dalej](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="6bcfa-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
