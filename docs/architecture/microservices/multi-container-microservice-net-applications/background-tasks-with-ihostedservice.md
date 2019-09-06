---
title: Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z nowymi opcjami umożliwiającymi korzystanie z IHostedService i BackgroundService w celu zaimplementowania zadań w tle w mikrousługach .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: b3dca8db6568e6e8429645d6b433886d1d289b95
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "70296799"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService

Zadania w tle i zaplanowane zadania to coś, co może wymagać wdrożenia, a ostatecznie, w aplikacji opartej na mikrousługach lub w dowolnym rodzaju aplikacji. Różnica w przypadku korzystania z architektury mikrousług polega na tym, że można zaimplementować pojedynczy proces mikrousług/kontener do obsługi tych zadań w tle, aby można było skalować go w dół lub w górę, a nawet mieć pewność, że uruchamia ono pojedyncze wystąpienie tego typu proces/kontener mikrousług.

Z ogólnego punktu widzenia w programie .NET Core wywołano te typy zadań *hostowanych usług*, ponieważ są one usługami/logiką hostowaną w ramach hosta/aplikacji/mikrousługi. Należy zauważyć, że w tym przypadku usługa hostowana po prostu oznacza klasę z logiką zadań w tle.

Począwszy od platformy .NET Core 2,0, struktura zawiera nowy interfejs o <xref:Microsoft.Extensions.Hosting.IHostedService> nazwie pomagającej łatwo zaimplementować usługi hostowane. Podstawowy pomysł polega na tym, że można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle, gdy host lub host sieci Web jest uruchomiony, jak pokazano na obrazie 6-26.

![ASP.NET Core 1. x i 2. x obsługuje IWebHost dla procesów w tle w aplikacjach sieci Web, .NET Core 2, 1 obsługuje IHost dla procesów w tle, w których są proste aplikacje konsolowe.](./media/image26.png)

**Rysunek 6-26**. Używanie IHostedService w elemencie WebHost a Host

Zwróć uwagę na różnice między `WebHost` i `Host`.

(Klasa bazowa implementująca `IWebHost`) w ASP.NET Core 2,0 to artefakt infrastruktury używany do udostępniania funkcji serwera HTTP dla procesu, na przykład w przypadku implementowania aplikacji sieci Web MVC lub usługi Web API. `WebHost` Zapewnia ona wszystkie nowe dobraność infrastruktury w ASP.NET Core, co pozwala na korzystanie z iniekcji zależności, wstawianie middlewares w potoku żądań itd. i precyzyjne korzystanie z `IHostedServices` nich na potrzeby zadań w tle.

A `Host` (implementacja `IHost`klasy bazowej) została wprowadzona w programie .NET Core 2,1. W zasadzie usługa `Host` a pozwala korzystać z podobnej infrastruktury niż to, z `WebHost` jakim korzystasz (iniekcja zależności, usługi hostowane itp.), ale w tym przypadku wystarczy, że chcesz mieć prosty i jaśniejszy proces jako host, bez żadnych elementów związanych z MVC , Interfejs API sieci Web lub funkcje serwera HTTP.

W związku z tym można wybrać i utworzyć wyspecjalizowany proces hosta z IHost, aby obsługiwać usługi hostowane, a nic innego nie miało na celu hostowania `IHostedServices`lub można również zwiększyć istniejące ASP.NET Core `WebHost` , takich jak istniejący ASP.NET Core Web API lub aplikacja MVC.

Każde podejście ma wady i zalety w zależności od potrzeb firmy i skalowalności. Dolna linia jest zasadniczo taka, że jeśli zadania w tle nie mają nic robić z HTTP (IWebHost), należy użyć IHost.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie usług hostowanych w usłudze WebHost lub hoście

Przejdźmy do dalszych etapów interfejsu `IHostedService` , ponieważ jego użycie jest dość podobne `WebHost` w lub w `Host`.

Sygnalizujący to jeden przykład artefaktu korzystającego z usług hostowanych, ale można go również użyć do znacznie prostszego działania, takiego jak:

- Zadanie w tle sondowanie bazy danych szukającej zmian.
- Zaplanowane zadanie aktualizuje nieco pamięci podręcznej.
- Implementacja QueueBackgroundWorkItem, która umożliwia wykonywanie zadania w wątku w tle.
- Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacji sieci Web podczas udostępniania wspólnych usług, takich jak `ILogger`.
- Zadanie w tle zostało uruchomione `Task.Run()`przy użyciu.

Można zasadniczo odciążyć dowolne z tych akcji do zadania w tle w oparciu o IHostedService.

Sposób dodawania jednego `IHostedServices` lub wielu `WebHost` do lub `Host` jest przez zarejestrowanie ich za pomocą standardowego di (iniekcja zależności `Host` ) w ASP.NET Core `WebHost` (lub w środowisku .NET Core 2,1 lub nowszym). Zasadniczo należy zarejestrować usługi hostowane w znanej `ConfigureServices()` metodzie `Startup` klasy, jak w poniższym kodzie z typowego elementu webhost ASP.NET.

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

W tym kodzie `GracePeriodManagerService` usługa hostowana jest realnym kodem z mikrousługi eShopOnContainers w firmie, a pozostałe dwa są tylko dwoma dodatkowymi przykładami.

Wykonywanie `IHostedService` zadania w tle jest koordynowane z okresem istnienia aplikacji (hosta lub mikrousługi). Zadania są rejestrowane, gdy aplikacja zostanie uruchomiona i masz możliwość wykonywania pewnych działań lub czyszczenia danych podczas zamykania aplikacji.

Bez korzystania `IHostedService`z programu można zawsze uruchomić wątek w tle, aby uruchomić dowolne zadanie. Różnica jest precyzyjna w czasie zamykania aplikacji, gdy ten wątek zostanie po prostu zamknięty, bez możliwości uruchamiania łagodnych akcji oczyszczania.

## <a name="the-ihostedservice-interface"></a>Interfejs IHostedService

Po zarejestrowaniu `IHostedService`platforma .NET Core będzie `StartAsync()` wywoływała metody `StopAsync()` `IHostedService` i, podczas uruchamiania i zatrzymywania aplikacji. Polecenie Start jest wywoływane po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` wyzwoleniu.

`IHostedService` Zgodnie z definicją w programie .NET Core wygląda to w następujący sposób.

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

Jak można wyobrazić, można utworzyć wiele implementacji IHostedService i zarejestrować je w `ConfigureService()` metodzie w kontenerze di, jak pokazano wcześniej. Wszystkie te usługi hostowane zostaną uruchomione i zatrzymane wraz z aplikacją/mikrousługą.

Jako programista użytkownik jest odpowiedzialny za obsługę zatrzymania działania usług, gdy `StopAsync()` Metoda jest wyzwalana przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie IHostedService z niestandardową klasą usługi hostowanej pochodną z klasy podstawowej BackgroundService

Można utworzyć niestandardową klasę usług hostowanych od podstaw i zaimplementować ją `IHostedService`, tak jak należy to zrobić w przypadku korzystania z platformy .NET Core 2,0.

Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i innych typowych operacji, istnieje wygodna abstrakcyjna klasa bazowa, `BackgroundService` z której pochodzi (dostępna od platformy .NET Core 2,1).

Ta klasa udostępnia główną służbę wymaganą do skonfigurowania zadania w tle.

Następny kod jest abstrakcyjną klasą bazową BackgroundService zaimplementowaną w środowisku .NET Core.

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

Podczas wyprowadzania z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej dziedziczonej implementacji, wystarczy zaimplementować `ExecuteAsync()` metodę we własnej niestandardowej klasie usługi hostowanej, jak w poniższym kodzie uproszczonym z eShopOnContainers, który sonduje zdarzenia integracji bazy danych i publikowania w usłudze Event Bus w razie konieczności.

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

W tym konkretnym przypadku eShopOnContainers jest wykonywana metoda aplikacji, która jest kwerendą tabeli bazy danych szukającą zamówień o określonym stanie i podczas stosowania zmian, publikuje zdarzenia integracji za pomocą magistrali zdarzeń (poniżej może być Korzystanie z RabbitMQ lub Azure Service Bus).

Oczywiście możesz zamiast tego uruchomić dowolne inne zadanie w tle.

Domyślnie token anulowania jest ustawiany z 5-sekundowym limitem czasu, ale można zmienić tę wartość podczas kompilowania `WebHost` `UseShutdownTimeout` przy użyciu rozszerzenia `IWebHostBuilder`. Oznacza to, że nasza usługa powinna zostać anulowana w ciągu 5 sekund, w przeciwnym razie będzie bardziej nieoczekiwanie zabity.

Poniższy kod zmieni ten czas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klas podsumowania

Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów, które są wykorzystywane podczas implementowania IHostedServices.

![Diagram klas: IWebHost i IHost mogą obsługiwać wiele usług, które dziedziczą z BackgroundService, który implementuje IHostedService.](./media/image27.png)

**Rysunek 6-27**. Diagram klas przedstawiający wiele klas i interfejsów związanych z IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i wnioski

Należy pamiętać, że sposób wdrażania ASP.NET Core `WebHost` lub .NET Core `Host` może mieć wpływ na ostateczne rozwiązanie. Na przykład w przypadku wdrożenia `WebHost` na serwerze IIS lub w regularnych Azure App Service można wyłączyć hosta z powodu odtwarzania puli aplikacji. Ale w przypadku wdrażania hosta jako kontenera do programu Orchestrator, takiego jak Kubernetes lub Service Fabric, można kontrolować zagwarantowaną liczbę wystąpień na żywo hosta. Ponadto można rozważyć inne podejścia w chmurze szczególnie dla tych scenariuszy, takie jak Azure Functions. Na koniec w przypadku konieczności uruchomienia usługi przez cały czas i wdrożenia na serwerze z systemem Windows można użyć usługi systemu Windows.

Jednak nawet w przypadku `WebHost` wdrożenia w puli aplikacji istnieją scenariusze, takie jak ponowne wypełnianie lub opróżnianie pamięci podręcznej w pamięci, które nadal będą miały zastosowanie.

Interfejs zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET Core aplikacji sieci Web (w programie .NET Core 2,0) lub w dowolnym procesie/hoście (począwszy od platformy .NET Core 2,1 z `IHost`). `IHostedService` Jej główną korzyścią jest możliwość korzystania z bezpiecznego anulowania kodu czyszczenia zadań w tle podczas zamykania samego hosta.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Tworzenie zaplanowanego zadania w ASP.NET Core/standardowa 2,0** <br/>
    <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementacja IHostedService w ASP.NET Core 2,0** <br/>
    <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Przykład GenericHost za pomocą ASP.NET Core 2,1** <br/>
    <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Poprzedni](test-aspnet-core-services-web-apps.md)Następny
>[](implement-api-gateways-with-ocelot.md)
