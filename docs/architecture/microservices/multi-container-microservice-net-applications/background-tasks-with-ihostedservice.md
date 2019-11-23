---
title: Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z nowymi opcjami umożliwiającymi korzystanie z IHostedService i BackgroundService w celu zaimplementowania zadań w tle w mikrousługach .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: d289d8ccc737fa9fc13b95da44e4b617b431f96a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737187"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementowanie zadań w tle w mikrousługach za pomocą IHostedService i klasy BackgroundService

Zadania w tle i zaplanowane zadania to coś, co może wymagać wdrożenia, a ostatecznie, w aplikacji opartej na mikrousługach lub w dowolnym rodzaju aplikacji. Różnica w przypadku korzystania z architektury mikrousług polega na tym, że można zaimplementować pojedynczy proces mikrousług/kontener do obsługi tych zadań w tle, co pozwala na skalowanie w górę lub w górę w miarę potrzeb lub można nawet upewnić się, że uruchamia ono pojedyncze wystąpienie tego procesu mikrousługi/kontenera.

Z ogólnego punktu widzenia w programie .NET Core wywołano te typy zadań *hostowanych usług*, ponieważ są one usługami/logiką hostowaną w ramach hosta/aplikacji/mikrousługi. Należy zauważyć, że w tym przypadku usługa hostowana po prostu oznacza klasę z logiką zadań w tle.

Począwszy od platformy .NET Core 2,0, struktura zawiera nowy interfejs o nazwie <xref:Microsoft.Extensions.Hosting.IHostedService> ułatwiający zaimplementowanie usług hostowanych. Podstawowy pomysł polega na tym, że można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle, podczas gdy host lub host sieci Web jest uruchomiony, jak pokazano na obrazie 6-26.

![Diagram przedstawiający porównanie ASP.NET Core IWebHost i .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Rysunek 6-26**. Używanie IHostedService w elemencie WebHost a Host

ASP.NET Core 1. x i 2. x obsługuje IWebHost dla procesów w tle w usłudze Web Apps. Platforma .NET Core 2,1 obsługuje IHost dla procesów w tle w przypadku zwykłych aplikacji konsolowych. Zwróć uwagę na różnice między `WebHost` i `Host`.

`WebHost` (klasa bazowa implementująca `IWebHost`) w ASP.NET Core 2,0 to artefakt infrastruktury używany do udostępniania funkcji serwera HTTP dla procesu, na przykład w przypadku implementowania aplikacji sieci Web MVC lub usługi Web API. Zapewnia ona wszystkie nowe dobre działania dotyczące infrastruktury w ASP.NET Core, co pozwala na korzystanie z iniekcji zależności, wstawianie middlewares w potoku żądań itd. i precyzyjne korzystanie z tych `IHostedServices` na potrzeby zadań w tle.

`Host` (klasa bazowa implementująca `IHost`) został wprowadzony w programie .NET Core 2,1. W zasadzie `Host` umożliwia korzystanie z podobnej infrastruktury niż w przypadku `WebHost` (iniekcja zależności, usług hostowanych itp.), ale w tym przypadku wystarczy, że chcesz mieć prosty i jaśniejszy proces jako host, bez żadnych informacji związanych z funkcjami MVC, Web API lub HTTP Server.

W związku z tym można wybrać i utworzyć wyspecjalizowany proces hosta z IHost w celu obsługi usług hostowanych, a nic innego nie ma na celu hostowania `IHostedServices`lub można także rozciągnąć istniejące ASP.NET Core `WebHost`, takie jak istniejący ASP.NET Core internetowy interfejs API lub aplikacja MVC.

Każde podejście ma wady i zalety w zależności od potrzeb firmy i skalowalności. Dolna linia jest zasadniczo taka, że jeśli zadania w tle nie mają nic robić z HTTP (IWebHost), należy użyć IHost.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie usług hostowanych w usłudze WebHost lub hoście

Przejdźmy na `IHostedService` interfejsie, ponieważ jego użycie jest dość podobne w `WebHost` lub w `Host`.

Sygnalizujący to jeden przykład artefaktu korzystającego z usług hostowanych, ale można go również użyć do znacznie prostszego działania, takiego jak:

- Zadanie w tle sondowanie bazy danych szukającej zmian.
- Zaplanowane zadanie aktualizuje nieco pamięci podręcznej.
- Implementacja QueueBackgroundWorkItem, która umożliwia wykonywanie zadania w wątku w tle.
- Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacji sieci Web podczas udostępniania wspólnych usług, takich jak `ILogger`.
- Zadanie w tle zostało uruchomione z `Task.Run()`.

Można zasadniczo odciążyć dowolne z tych akcji do zadania w tle w oparciu o IHostedService.

Sposób dodawania jednego lub wielu `IHostedServices` do `WebHost` lub `Host` jest przez zarejestrowanie ich przy użyciu metody rozszerzenia <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> w ASP.NET Core `WebHost` (lub w `Host` w programie .NET Core 2,1 lub nowszym). Zasadniczo należy zarejestrować usługi hostowane w znanej metodzie `ConfigureServices()` klasy `Startup`, jak w poniższym kodzie z typowego elementu WebHost ASP.NET.

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

W tym kodzie usługa hostowana `GracePeriodManagerService` jest prawdziwym kodem z mikrousługi w eShopOnContainers, a pozostałe dwa są tylko dwoma dodatkowymi przykładami.

Wykonywanie zadania w tle `IHostedService` jest koordynowane z okresem istnienia aplikacji (hosta lub mikrousługi). Zadania są rejestrowane, gdy aplikacja zostanie uruchomiona i masz możliwość wykonywania pewnych działań lub czyszczenia danych podczas zamykania aplikacji.

Bez korzystania z `IHostedService`można zawsze uruchomić wątek w tle, aby uruchomić dowolne zadanie. Różnica jest precyzyjna w czasie zamykania aplikacji, gdy ten wątek zostanie po prostu zamknięty, bez możliwości uruchamiania łagodnych akcji oczyszczania.

## <a name="the-ihostedservice-interface"></a>Interfejs IHostedService

Po zarejestrowaniu `IHostedService`.NET Core wywoła metody `StartAsync()` i `StopAsync()` typu `IHostedService` podczas uruchamiania i zatrzymywania aplikacji. Polecenie Start jest wywoływane po uruchomieniu serwera i wyzwoleniu `IApplicationLifetime.ApplicationStarted`.

`IHostedService`, zgodnie z definicją w programie .NET Core, wygląda następująco.

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

Jak można wyobrazić, można utworzyć wiele implementacji IHostedService i zarejestrować je w metodzie `ConfigureService()` w kontenerze DI, jak pokazano wcześniej. Wszystkie te usługi hostowane zostaną uruchomione i zatrzymane wraz z aplikacją/mikrousługą.

Jako programista użytkownik jest odpowiedzialny za obsługę zatrzymania działania usług, gdy `StopAsync()` Metoda jest wyzwalana przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie IHostedService z niestandardową klasą usługi hostowanej pochodną z klasy podstawowej BackgroundService

Można utworzyć niestandardową klasę usług hostowanych od podstaw i zaimplementować `IHostedService`, co należy zrobić w przypadku korzystania z platformy .NET Core 2,0.

Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i innych typowych operacji, istnieje wygodna abstrakcyjna klasa bazowa, o nazwie `BackgroundService` (dostępna od platformy .NET Core 2,1).

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

Podczas wyprowadzania z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej dziedziczonej implementacji, wystarczy zaimplementować metodę `ExecuteAsync()` we własnej niestandardowej klasie usługi hostowanej, jak w poniższym uproszczonym kodzie z eShopOnContainers, który sonduje bazę danych i publikuje zdarzenia integracji w usłudze Event Bus w razie potrzeby.

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

Domyślnie token anulowania jest ustawiany z 5-sekundowym limitem czasu, chociaż można zmienić tę wartość podczas kompilowania `WebHost` przy użyciu rozszerzenia `UseShutdownTimeout` `IWebHostBuilder`. Oznacza to, że nasza usługa powinna zostać anulowana w ciągu 5 sekund, w przeciwnym razie będzie bardziej nieoczekiwanie zabity.

Poniższy kod zmieni ten czas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klas podsumowania

Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów, które są wykorzystywane podczas implementowania IHostedServices.

![Diagram przedstawiający, że IWebHost i IHost mogą obsługiwać wiele usług.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Rysunek 6-27**. Diagram klas przedstawiający wiele klas i interfejsów związanych z IHostedService

Diagram klas: IWebHost i IHost mogą obsługiwać wiele usług, które dziedziczą z BackgroundService, który implementuje IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i wnioski

Należy pamiętać, że sposób wdrażania `WebHost` ASP.NET Core lub .NET Core `Host` może mieć wpływ na ostateczne rozwiązanie. Na przykład w przypadku wdrażania `WebHost` w usługach IIS lub regularnym Azure App Service można wyłączyć hosta z powodu odtwarzania puli aplikacji. Ale w przypadku wdrażania hosta jako kontenera do programu Orchestrator, takiego jak Kubernetes lub Service Fabric, można kontrolować zagwarantowaną liczbę wystąpień na żywo hosta. Ponadto można rozważyć inne podejścia w chmurze szczególnie dla tych scenariuszy, takie jak Azure Functions. Na koniec w przypadku konieczności uruchomienia usługi przez cały czas i wdrożenia na serwerze z systemem Windows można użyć usługi systemu Windows.

Jednak nawet w przypadku `WebHost` wdrożonych w puli aplikacji istnieją scenariusze, takie jak ponowne wypełnianie lub opróżnianie pamięci podręcznej w pamięci aplikacji, które nadal mogą być stosowane.

Interfejs `IHostedService` zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET Core aplikacji sieci Web (w programie .NET Core 2,0) lub w dowolnym procesie/hoście (począwszy od platformy .NET Core 2,1 z `IHost`). Jej główną korzyścią jest możliwość korzystania z bezpiecznego anulowania kodu czyszczenia zadań w tle podczas zamykania samego hosta.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Tworzenie zaplanowanego zadania w ASP.NET Core/Standard 2,0**
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementacja IHostedService w ASP.NET Core 2,0**
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Przykład GenericHost przy użyciu ASP.NET Core 2,1**
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Poprzedni](test-aspnet-core-services-web-apps.md)
>[Następny](implement-api-gateways-with-ocelot.md)
