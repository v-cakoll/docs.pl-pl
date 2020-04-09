---
title: Implementowanie zadań w tle w mikrousługach za pomocą usługi IHostedService i klasy BackgroundService
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Poznaj nowe opcje do korzystania z IHostedService i BackgroundService do implementowania zadań w tle w mikrousługach .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fd26d0444312d3525ad95b2273f28a6ceaa27911
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988339"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementowanie zadań w tle w mikrousługach za pomocą usługi IHostedService i klasy BackgroundService

Zadania w tle i zaplanowane zadania są czymś, co może być konieczne do zaimplementowania, ostatecznie, w aplikacji opartej na mikrousługach lub w dowolnej aplikacji. Różnica podczas korzystania z architektury mikrousług jest, że można zaimplementować pojedynczy proces mikrousług/kontener do obsługi tych zadań w tle, dzięki czemu można skalować go w dół/w górę, zgodnie z potrzebami lub można nawet upewnić się, że uruchamia jedno wystąpienie tego procesu mikrousług/kontenera.

Z ogólnego punktu widzenia w programie .NET Core nazwaliśmy tego typu zadania *Hostowane usługi,* ponieważ są to usługi/logika hostowane w ramach hosta/aplikacji/mikrousług. Należy zauważyć, że w tym przypadku usługa hostowana oznacza po prostu klasę z logiką zadania w tle.

Ponieważ .NET Core 2.0, struktura zawiera <xref:Microsoft.Extensions.Hosting.IHostedService> nowy interfejs o nazwie pomaga łatwo zaimplementować usługi hostowane. Podstawową ideą jest to, że można zarejestrować wiele zadań w tle (usługi hostowane), które działają w tle, gdy host internetowy lub host jest uruchomiony, jak pokazano na obrazku 6-26.

![Diagram porównujący ASP.NET Core IWebHost i .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Rysunek 6-26**. Korzystanie z usługi IHostedService w ugarście internetowym a hostem

ASP.NET obsługa `IWebHost` core 1.x i 2.x dla procesów w tle w aplikacjach internetowych. .NET Core 2.1 i `IHost` nowsze wersje obsługują procesy w tle z prostymi aplikacjami konsoli. Zwróć uwagę na `WebHost` `Host`różnicę między i .

A `WebHost` (implementacja `IWebHost`klasy podstawowej) w ASP.NET Core 2.0 to artefakt infrastruktury używany do dostarczania funkcji serwera HTTP do procesu, na przykład podczas implementowania aplikacji sieci Web MVC lub usługi interfejsu API sieci Web. Zapewnia wszystkie nowe dobroć infrastruktury w ASP.NET Core, umożliwiając użycie iniekcji zależności, wstawianie oprogramowania pośredniczącego w potoku żądania i podobne. Używa `WebHost` tych bardzo `IHostedServices` sam dla zadań w tle.

A `Host` (implementacja `IHost`klasy podstawowej) została wprowadzona w .NET Core 2.1. Zasadniczo, `Host` pozwala mieć podobną infrastrukturę niż `WebHost` to, co masz z (iniekcja zależności, usługi hostowane, itp.), ale w tym przypadku, po prostu chcesz mieć prosty i lżejszy proces jako host, z niczym związanym z MVC, Web API lub funkcje serwera HTTP.

W związku z tym można wybrać i utworzyć `IHost` wyspecjalizowany proces hosta z do obsługi usług hosta `IHostedServices`i nic więcej, takie mikrousługi `WebHost`wykonane tylko dla hostingu , lub alternatywnie można rozszerzyć istniejący ASP.NET Core , takich jak istniejący ASP.NET Core Web API lub aplikacji MVC.

Każde podejście ma plusy i minusy w zależności od potrzeb biznesowych i skalowalności. Najważniejsze jest to, że jeśli zadania w tle nie`IWebHost`mają nic `IHost`wspólnego z HTTP ( ) należy użyć .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie hostowanych usług w witrynie WebHost lub host

Przejdźmy dalej do interfejsu, `IHostedService` ponieważ jego użycie jest `WebHost` bardzo `Host`podobne w lub w .

SignalR jest jednym z przykładów artefaktu przy użyciu usług hostowanych, ale można go również używać do znacznie prostszych rzeczy, takich jak:

- Zadanie w tle sondowania bazy danych w poszukiwaniu zmian.
- Zaplanowane zadanie okresowo aktualizuje niektóre pamięci podręcznej.
- Implementacja QueueBackgroundWorkItem, który umożliwia zadanie do wykonania w wątku w tle.
- Przetwarzanie wiadomości z kolejki komunikatów w tle aplikacji sieci `ILogger`web podczas udostępniania typowych usług, takich jak .
- Zadanie w tle `Task.Run()`rozpoczęte z .

Można zasadniczo odciążyć dowolną z tych akcji `IHostedService`do zadania w tle, które implementuje .

Sposób dodawania jednego `IHostedServices` lub `WebHost` wielu `Host` do lub jest przez <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  zarejestrowanie ich za pomocą `WebHost` metody rozszerzenia `Host` w ASP.NET Core (lub w .NET Core 2.1 i powyżej). Zasadniczo musisz zarejestrować hostowane usługi w `ConfigureServices()` ramach `Startup` znanej metody klasy, jak w poniższym kodzie z typowej ASP.NET WebHost.

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

W tym kodzie usługa `GracePeriodManagerService` hostowana jest prawdziwy kod z mikrousługi biznesowej zamawiania w eShopOnContainers, podczas gdy pozostałe dwa są tylko dwa dodatkowe przykłady.

Wykonanie `IHostedService` zadania w tle jest koordynowane z okresem istnienia aplikacji (host lub mikrousługa, o to chodzi). Rejestrować zadania po uruchomieniu aplikacji i masz możliwość wykonania akcji w sposób pełen wdzięku lub oczyszczania, gdy aplikacja jest zamykanie.

Bez `IHostedService`użycia , zawsze można uruchomić wątek w tle, aby uruchomić dowolne zadanie. Różnica jest właśnie w czasie zamykania aplikacji, gdy ten wątek będzie po prostu zabity bez możliwości uruchamiania wdzięku działań oczyszczania.

## <a name="the-ihostedservice-interface"></a>Interfejs IHostedService

Po zarejestrowaniu `IHostedService`, .NET Core `StartAsync()` `StopAsync()` wywoła i `IHostedService` metody typu podczas uruchamiania i zatrzymywania aplikacji odpowiednio. W szczególności start jest wywoływany po `IApplicationLifetime.ApplicationStarted` uruchomieniu serwera i jest wyzwalany.

Zgodnie `IHostedService` z definicją w .NET Core, wygląda następująco.

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

Jak można sobie wyobrazić, można utworzyć wiele implementacji IHostedService i zarejestrować je w `ConfigureService()` metodzie do kontenera DI, jak pokazano wcześniej. Wszystkie te usługi hostowane zostaną uruchomione i zatrzymane wraz z aplikacją/mikrousługą.

Jako deweloper jesteś odpowiedzialny za obsługę akcji zatrzymania `StopAsync()` usług, gdy metoda jest wyzwalana przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie usługi IHostedService z niestandardową klasą usługi hosta pochodzącą z klasy podstawowej BackgroundService

Możesz iść dalej i utworzyć niestandardową klasę usługi `IHostedService`hostowane od podstaw i zaimplementować , jak trzeba zrobić podczas korzystania z .NET Core 2.0.

Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i `BackgroundService` innych typowych operacji, istnieje wygodna abstrakcyjna klasa podstawowa, z której można czerpać nazwę (dostępna od platformy .NET Core 2.1).

Ta klasa zapewnia główną pracę potrzebną do skonfigurowania zadania w tle.

Następny kod jest abstrakcyjną klasą podstawową BackgroundService zaimplementowana w .NET Core.

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

Podczas wyprowadzania z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej implementacji dziedziczone, wystarczy zaimplementować `ExecuteAsync()` metodę we własnej klasie usługi hostowane niestandardowe, jak w poniższym uproszczonym kodzie z eShopOnContainers, który jest sondowanie bazy danych i publikowania zdarzeń integracji w magistrali zdarzeń w razie potrzeby.

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
        // Constructor's parameters validations...
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

W tym konkretnym przypadku dla eShopOnContainers, jest wykonywanie metody aplikacji, która jest wykonywanie kwerendy tabeli bazy danych szuka zamówień z określonymstanem i podczas stosowania zmian, jest publikowanie zdarzeń integracji za pośrednictwem magistrali zdarzeń (pod nim może być przy użyciu RabbitMQ lub usługi Azure Service Bus).

Oczywiście, można uruchomić inne zadanie w tle firmy, zamiast.

Domyślnie token anulowania jest ustawiany z 5-sekundowym limitem czasu, `UseShutdownTimeout` chociaż można `IWebHostBuilder`zmienić tę wartość podczas tworzenia rozszerzenia `WebHost` . Oznacza to, że nasza usługa ma zostać anulowana w ciągu 5 sekund, w przeciwnym razie zostanie bardziej gwałtownie zabita.

Poniższy kod będzie zmieniać ten czas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klasy podsumowania

Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów zaangażowanych podczas implementowania usługi IHostedServices.

![Diagram pokazujący, że IWebHost i IHost mogą obsługiwać wiele usług.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Rysunek 6-27**. Diagram klas przedstawiający wiele klas i interfejsów związanych z usługą IHostedService

Diagram klas: IWebHost i IHost może obsługiwać wiele usług, które dziedziczą z BackgroundService, który implementuje IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i dania na wynos

Należy pamiętać, że sposób wdrażania ASP.NET Core `WebHost` lub .NET `Host` Core może mieć wpływ na ostateczne rozwiązanie. Na przykład jeśli wdrożysz usługi `WebHost` IIS lub zwykłą usługę Azure App Service, host może zostać zamknięty z powodu odtwarzania puli aplikacji. Ale jeśli wdrażasz hosta jako kontener w koordynatorze, takim jak Kubernetes, możesz kontrolować gwarantowaną liczbę wystąpień na żywo hosta. Ponadto można rozważyć inne podejścia w chmurze specjalnie dla tych scenariuszy, takich jak usługi Azure Functions. Na koniec, jeśli potrzebujesz, aby usługa była uruchomiona przez cały czas i wdrażana w systemie Windows Server, można użyć usługi systemu Windows.

Ale nawet `WebHost` dla wdrożonych w puli aplikacji, istnieją scenariusze, takie jak repopulacji lub opróżniania pamięci podręcznej w pamięci, które będą nadal stosowane.

Interfejs `IHostedService` zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET podstawowej aplikacji sieci web (w .NET Core 2.0 i nowszych wersjach) lub w dowolnym procesie/hoście (począwszy od .NET Core 2.1 z `IHost`). Jego główną zaletą jest możliwość uzyskania z wdzięku anulowania do czyszczenia kodu zadań w tle, gdy sam host jest zamykanie.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie zaplanowanego zadania w ASP.NET Core/Standard 2.0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementacja usługi IHostedService w ASP.NET Core 2.0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **GenericHost Przykład przy użyciu ASP.NET Core 2.1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [Poprzedni](test-aspnet-core-services-web-apps.md)
> [następny](implement-api-gateways-with-ocelot.md)
