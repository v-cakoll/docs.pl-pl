---
title: "Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService"
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
ms.openlocfilehash: d60a4590682b79a9f8ac57afee09884b7edd1f98
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="cdf70-104">Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService</span><span class="sxs-lookup"><span data-stu-id="cdf70-104">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="cdf70-105">Zadania w tle i zaplanowane zadania są coś, co może wystąpić potrzeba wdrożenia, po pewnym czasie w aplikacji na podstawie mikrousługi lub dowolnego rodzaju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdf70-105">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="cdf70-106">Różnica podczas korzystania z architektury mikrousług jest zaimplementowanie mikrousługi pojedynczego procesu/kontener dla hostingu te zadania w tle, więc możesz go w dół w górę Skaluj w miarę potrzebne lub można nawet upewnij się, że działa jedno wystąpienie tego proces mikrousługi/kontenera.</span><span class="sxs-lookup"><span data-stu-id="cdf70-106">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="cdf70-107">Z ogólnym punktu widzenia w .NET Core dzwoniliśmy tego rodzaju zadania usługi hostowanej, ponieważ są one usług/logiki hosta w sieci hosta/aplikacji/mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="cdf70-107">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="cdf70-108">Należy pamiętać, że w takim przypadku usługa hostowana po prostu oznacza, że klasa z logiką zadania tła.</span><span class="sxs-lookup"><span data-stu-id="cdf70-108">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="cdf70-109">Ponieważ .NET Core 2.0, platformę oferuje nowy interfejs o nazwie <xref:Microsoft.Extensions.Hosting.IHostedService> pomaga łatwo wdrożenie hostowanych usług.</span><span class="sxs-lookup"><span data-stu-id="cdf70-109">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="cdf70-110">Podstawową koncepcją nie można zarejestrować wiele zadania w tle (usług hostowanych), które są wykonywane w tle podczas hosta sieci web lub host działa, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="cdf70-110">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="cdf70-111">**Rysunek 8-25.**</span><span class="sxs-lookup"><span data-stu-id="cdf70-111">**Figure 8-25.**</span></span> <span data-ttu-id="cdf70-112">Przy użyciu IHostedService w WebHost a Host</span><span class="sxs-lookup"><span data-stu-id="cdf70-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="cdf70-113">Różnice między `WebHost` i `Host`.</span><span class="sxs-lookup"><span data-stu-id="cdf70-113">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="cdf70-114">A `WebHost` (podstawowa Implementacja klasy `IWebHost`) w programie ASP.NET 2.0 Core jest artefaktów infrastruktury są używane do udostępniania, serwer HTTP funkcje do procesu, na przykład jeśli wdrażania aplikacji sieci web MVC lub Web API usługi.</span><span class="sxs-lookup"><span data-stu-id="cdf70-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="cdf70-115">Zawiera wszystkie nowe zgodność infrastruktury w ASP.NET Core, dzięki któremu można iniekcji zależności, Wstaw middlewares w potoku HTTP, itp. oraz dokładnie poniższe `IHostedServices` dla zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="cdf70-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="cdf70-116">A `Host` (podstawowa Implementacja klasy `IHost`), jednak jest nowa w programie .NET Core 2.1 coś.</span><span class="sxs-lookup"><span data-stu-id="cdf70-116">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="cdf70-117">Zasadniczo `Host` służy do podobnych infrastruktury niż masz z `WebHost` (iniekcji zależności usług hostowanych, itp.), ale w takim przypadku po prostu chcesz mieć procesu proste i jaśniejszy jako hosta, z żadnych danych dotyczących MVC , HTTP lub interfejsu API funkcji serwera w sieci web.</span><span class="sxs-lookup"><span data-stu-id="cdf70-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="cdf70-118">W związku z tym można wybrać i Utwórz specjalne proces hosta z IHost do obsługi usług hostowanych i niczego poza, takie mikrousługi, wykonywane tylko dla hostingu `IHostedServices`, lub możesz alternatevely rozszerzyć istniejącą platformy ASP.NET Core `WebHost` , takich jak istniejącej aplikacji interfejsu API platformy ASP.NET Core sieci Web lub MVC.</span><span class="sxs-lookup"><span data-stu-id="cdf70-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatevely extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="cdf70-119">Każde podejście jest zalet i wad w zależności od potrzeb biznesowych i skalowalność.</span><span class="sxs-lookup"><span data-stu-id="cdf70-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="cdf70-120">Mierzenie jest zasadniczo Jeśli zadania w tle nie mają nic wspólnego z należy używać protokołu HTTP (IWebHost) i IHost, jeśli jest dostępna w programie .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="cdf70-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="cdf70-121">Rejestrowanie hostowanych usług w hosta lub hostem sieci Web</span><span class="sxs-lookup"><span data-stu-id="cdf70-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="cdf70-122">Teraz przejść do szczegółów dalsze na `IHostedService` interfejsu, ponieważ jej użycie jest bardzo podobne w `WebHost` lub `Host`.</span><span class="sxs-lookup"><span data-stu-id="cdf70-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="cdf70-123">SignalR jest jednym z przykładów artefaktów przy użyciu usług hostowanych, ale można również używać go do łatwiej np.:</span><span class="sxs-lookup"><span data-stu-id="cdf70-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="cdf70-124">Zadanie w tle sondowania wyszukiwanie zmiany bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cdf70-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="cdf70-125">Zaplanowane zadanie okresowo aktualizacja niektórych pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cdf70-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="cdf70-126">Implementacja QueueBackgroundWorkItem, który umożliwia zadania do wykonania wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="cdf70-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="cdf70-127">Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacji sieci web podczas udostępniania wspólnych usług takich jak `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="cdf70-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="cdf70-128">Wprowadzenie do zadania w tle `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="cdf70-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="cdf70-129">Zasadniczo może odciążyć żadnego z tych akcji zadania tła w zależności od IHostedService.</span><span class="sxs-lookup"><span data-stu-id="cdf70-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="cdf70-130">Sposób dodawania jednego lub wielu `IHostedServices` do Twojej `WebHost` lub `Host` jest rejestrując je się za pośrednictwem standardowych Podpisane (iniekcji zależności) w ASP.NET Core `WebHost` (lub `Host` .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="cdf70-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="cdf70-131">Zasadniczo, należy zarejestrować usług hostowanych w znanych `ConfigureServices()` metody `Startup` klasy, jak w poniższym kodzie z typowych WebHost ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cdf70-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="cdf70-132">W tym kodzie `GracePeriodManagerService` usługi hostowanej jest rzeczywisty kod z porządkowanie mikrousługi biznesowych w eShopOnContainers, podczas drugiego dwie usługi są tylko dwie dodatkowe przykłady.</span><span class="sxs-lookup"><span data-stu-id="cdf70-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="cdf70-133">`IHostedService` Wykonywanie zadań w tle jest powiązane z użytkowania aplikacji (host lub mikrousługi istotnego dla badania).</span><span class="sxs-lookup"><span data-stu-id="cdf70-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="cdf70-134">Możesz zarejestrować zadania podczas uruchamiania aplikacji i mieć możliwość wykonaj łagodne akcji lub czyszczenia gdy dana aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="cdf70-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="cdf70-135">Bez użycia `IHostedService`, zawsze można uruchomić wątku w tle do uruchamiania zadań.</span><span class="sxs-lookup"><span data-stu-id="cdf70-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="cdf70-136">Różnica polega na dokładnie na czas zamknięcia aplikacji podczas tego wątku czy po prostu skasowane bez możliwości do uruchamiania działań oczyszczania bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="cdf70-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="cdf70-137">Interfejs IHostedService</span><span class="sxs-lookup"><span data-stu-id="cdf70-137">The IHostedService interface</span></span>

<span data-ttu-id="cdf70-138">Po dokonaniu rejestracji `IHostedService`, wywoła .NET Core `StartAsync()` i `StopAsync()` metody z `IHostedService` wpisz podczas uruchamiania aplikacji i Zatrzymaj odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="cdf70-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="cdf70-139">W szczególności rozpoczęcia jest wywoływana po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="cdf70-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="cdf70-140">`IHostedService` Zgodnie z definicją w .NET Core, wygląda podobnie do następującego.</span><span class="sxs-lookup"><span data-stu-id="cdf70-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="cdf70-141">Jak można wyobrazić sobie, możesz utworzyć wiele implementacji IHostedService i zarejestruj je w `ConfigureService()` metody w kontenerze Podpisane, jak pokazano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="cdf70-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="cdf70-142">Wszystkie te usługi hostowanej będzie można uruchamiania i zatrzymywania wraz z aplikacji/mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="cdf70-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="cdf70-143">Deweloperzy jesteś odpowiedzialny za obsługę Akcja zatrzymania lub usług po `StopAsync()` metody jest wyzwalany przez hosta.</span><span class="sxs-lookup"><span data-stu-id="cdf70-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="cdf70-144">Implementowanie IHostedService w przypadku tworzenia klasy pochodnej z klasy podstawowej BackgroundService klasy niestandardowe usługi hostowanej</span><span class="sxs-lookup"><span data-stu-id="cdf70-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="cdf70-145">Przejdź dalej i tworzenia klasy niestandardowej usługi hostowanej od początku i implementować `IHostedService`, jak należy wykonać, korzystając z programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdf70-145">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="cdf70-146">Jednak ponieważ większość zadań w tle zostanie mają podobne wymagania w zakresie zarządzania tokeny anulowania i innych operacji tipical, .NET Core 2.1 będzie dostarczać wygodną abstrakcyjna klasa podstawowa, który może pochodzić od o nazwie BackgroundService.</span><span class="sxs-lookup"><span data-stu-id="cdf70-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other tipical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="cdf70-147">Klasy zawiera głównego pracy niezbędne do skonfigurowania zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="cdf70-147">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="cdf70-148">Należy pamiętać, że ta klasa rozpocznie się w bibliotece programu .NET Core 2.1, więc nie trzeba go zapisać.</span><span class="sxs-lookup"><span data-stu-id="cdf70-148">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="cdf70-149">Jednak począwszy od chwili pisania tego dokumentu, .NET Core 2.1 nie został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="cdf70-149">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="cdf70-150">W związku z tym w eShopOnContainers, który aktualnie używa .NET Core 2.0, firma Microsoft są po prostu tymczasowo zawierających tej klasy z repozytorium open source .NET Core 2.1 (nie ma potrzeby zastrzeżonych licencji niż licencji open source), ponieważ jest on zgodny z bieżący interfejs IHostedService w programie .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdf70-150">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="cdf70-151">Po zwolnieniu .NET Core 2.1, należy po prostu wskaż prawy pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="cdf70-151">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="cdf70-152">Następny kod jest abstrakcyjna klasa podstawowa BackgroundService zaimplementowanego w .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="cdf70-152">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

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

<span data-ttu-id="cdf70-153">Gdy wynikających z poprzednich abstrakcyjna klasa podstawowa, dzięki użyciu tej implementacji dziedziczone, wystarczy do zaimplementowania `ExecuteAsync()` w własne metody klasy usługi hostowanej, w następującej uproszczone kod z eShopOnContainers, który przeprowadza sondowanie bazy danych i publikowania zdarzeń integracji do magistrali zdarzenia w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="cdf70-153">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

                // This eShopOnContainers method is quering a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

<span data-ttu-id="cdf70-154">W tym przypadku określone dla eShopOnContainers wykonuje metodę aplikacji, która jest quering tabeli bazy danych wyszukiwania zamówień z określonym stanem oraz podczas stosowania zmian, publikowania za pośrednictwem magistrali zdarzeń (na dole mogą zdarzenia integracji za pomocą RabbitMQ lub usługi Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="cdf70-154">In this specific case for eShopOnContainers, it is executing an application method which is quering a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="cdf70-155">Oczywiście można uruchomić żadnych innych firm zadania w tle, zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cdf70-155">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="cdf70-156">Token anulowania jest domyślnie 5 limitu czasu drugiego, mimo że można zmienić tę wartość podczas tworzenia Twojej `WebHost` przy użyciu `UseShutdownTimeout` rozszerzenie `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="cdf70-156">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="cdf70-157">Oznacza to, że można anulować w ciągu 5 sekund w przeciwnym razie zostanie ona więcej nagle skasowane oczekuje naszej usługi.</span><span class="sxs-lookup"><span data-stu-id="cdf70-157">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="cdf70-158">Poniższy kod czy zmiana tego czasu na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="cdf70-158">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="cdf70-159">Diagram klas podsumowania</span><span class="sxs-lookup"><span data-stu-id="cdf70-159">Summary class diagram</span></span>

<span data-ttu-id="cdf70-160">Poniższy rysunek 8-26 element wizualny jest widoczne podsumowanie klas i połączony z poruszającą zaangażowany podczas implementowania IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="cdf70-160">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="cdf70-161">**Rysunek 8-26.**</span><span class="sxs-lookup"><span data-stu-id="cdf70-161">**Figure 8-26.**</span></span> <span data-ttu-id="cdf70-162">Klasa diagram przedstawiający wielokrotność klasy i interfejsy powiązane z IHostedService</span><span class="sxs-lookup"><span data-stu-id="cdf70-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="cdf70-163">Zagadnienia dotyczące wdrażania i takeaways</span><span class="sxs-lookup"><span data-stu-id="cdf70-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="cdf70-164">Należy zauważyć, że sposób wdrażania programu ASP.NET Core `WebHost` lub .NET Core `Host` może mieć wpływ na ostateczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="cdf70-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="cdf70-165">Na przykład w przypadku wdrożenia z `WebHost` na usług IIS lub regularne usługi Azure App Service, host może zostać wyłączony z powodu odtwarzania puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdf70-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="cdf70-166">Jeśli na hoście jest wdrażany jako kontener, do programu orchestrator, takich jak Kubernetes lub sieci szkieletowej usług, można jednak sterować bezpieczne liczbę wystąpień na żywo na hoście.</span><span class="sxs-lookup"><span data-stu-id="cdf70-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="cdf70-167">Ponadto można rozważyć inne podejścia w chmurze, szczególnie wprowadzone dla tych scenariuszy, takich jak usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="cdf70-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="cdf70-168">Ale nawet w przypadku `WebHost` wdrożonych w puli aplikacji, istnieją scenariusze, takie jak uważnie lub opróżnianie aplikacji w pamięci podręcznej, które będą nadal stosowane.</span><span class="sxs-lookup"><span data-stu-id="cdf70-168">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="cdf70-169">`IHostedService` Interfejsu oferują wygodny sposób uruchamiania zadania w tle w ASP.NET Core aplikacji sieci web (w programie .NET Core 2.0) lub w dowolnej procesu/hosta (w programie .NET Core 2.1 z `IHost`).</span><span class="sxs-lookup"><span data-stu-id="cdf70-169">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="cdf70-170">Główne korzyści jest możliwość przypisywany z łagodne anulowania zadania w tle do czyszczenia kodu, gdy sam host jest zamykany.</span><span class="sxs-lookup"><span data-stu-id="cdf70-170">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="cdf70-171">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="cdf70-171">Additional resources</span></span>

-   <span data-ttu-id="cdf70-172">**Tworzenie zaplanowanego zadania w programie ASP.NET 2.0 Core/Standard**</span><span class="sxs-lookup"><span data-stu-id="cdf70-172">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [<span data-ttu-id="cdf70-173">*https://blog.maartenballiauw.be/POST/2017/08/01/Building-a-scheduled-Cache-Updater-in-ASPNET-Core-2.HTML*</span><span class="sxs-lookup"><span data-stu-id="cdf70-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span></span>](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="cdf70-174">**Implementowanie IHostedService w platformy ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="cdf70-174">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [<span data-ttu-id="cdf70-175">*https://www.stevejgordon.co.uk/ASP-NET-Core-2-ihostedservice*</span><span class="sxs-lookup"><span data-stu-id="cdf70-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span></span>](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="cdf70-176">**Przykłady Core 2.1 Hosting ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="cdf70-176">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [<span data-ttu-id="cdf70-177">*https://github.com/ASPNET/hosting/Tree/dev/Samples/GenericHostSample*</span><span class="sxs-lookup"><span data-stu-id="cdf70-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span></span>](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="cdf70-178">[Poprzednie] (test-aspnet-core-services-web-apps.md) [dalej] (.. /microservice-ddd-cqrs-patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="cdf70-178">[Previous] (test-aspnet-core-services-web-apps.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
