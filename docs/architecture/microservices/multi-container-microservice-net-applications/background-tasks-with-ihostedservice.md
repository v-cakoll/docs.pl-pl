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
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementowanie zadań w tle w mikrousługach za pomocą usługi IHostedService i klasy BackgroundService

Zadania w tle i zaplanowane zadania są czymś, co może być konieczne do zaimplementowania, po pewnym czasie, w aplikacji opartej na mikrousługach lub w dowolnej aplikacji. Różnica podczas korzystania z architektury mikrousług jest, że można zaimplementować proces/kontener pojedynczej mikrousługi do obsługi tych zadań w tle, dzięki czemu można skalować go w dół/w górę, zgodnie z potrzebami lub można nawet upewnić się, że uruchamia pojedyncze wystąpienie tego procesu mikrousługi/kontenera.

Z ogólnego punktu widzenia w programie .NET Core nazwaliśmy tego typu zadania *hostowane usługi*, ponieważ są one usług/logiki, które hosta w hoście/aplikacji/mikrousługi. Należy zauważyć, że w tym przypadku usługa hostowana oznacza po prostu klasę z logiką zadania w tle.

Ponieważ .NET Core 2.0, struktura udostępnia <xref:Microsoft.Extensions.Hosting.IHostedService> nowy interfejs o nazwie pomaga łatwo zaimplementować hostowane usługi. Podstawową ideą jest to, że można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle, gdy host internetowy lub host jest uruchomiony, jak pokazano na obrazie 6-26.

![Diagram porównujący ASP.NET Core IWebHost i .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Rysunek 6-26**. Korzystanie z usługi IHostedService w aplikacji WebHost a host

ASP.NET obsługa `IWebHost` podstawowych 1.x i 2.x procesów w tle w aplikacjach internetowych. .NET Core 2.1 i `IHost` nowsze wersje obsługują procesy w tle za pomocą zwykłych aplikacji konsoli. Zwróć uwagę `WebHost` na `Host`różnicę między i .

A `WebHost` (implementacja `IWebHost`klasy podstawowej) w ASP.NET Core 2.0 to artefakt infrastruktury używany do dostarczania funkcji serwera HTTP do procesu, na przykład podczas implementowania aplikacji sieci Web MVC lub usługi interfejsu API sieci Web. Zapewnia wszystkie nowe dobroć infrastruktury w ASP.NET Core, umożliwiając użycie iniekcji zależności, wstawione programy pośredniczące w potoku żądania i podobne. Używa `WebHost` tych samych do `IHostedServices` zadań w tle.

A `Host` (klasa `IHost`podstawowa implementująca) została wprowadzona w .NET Core 2.1. Zasadniczo, `Host` a pozwala mieć podobną infrastrukturę niż `WebHost` to, co masz z (iniekcji zależności, usługi hostowane, itp.), ale w tym przypadku, po prostu chcesz mieć prosty i lżejszy proces jako host, z niczym związane z MVC, Web API lub funkcje serwera HTTP.

W związku z tym można wybrać i `IHost` utworzyć wyspecjalizowany proces hosta z do obsługi usług hostowanych i nic więcej, takie mikrousługi wykonane tylko do hostowania `IHostedServices`, lub można alternatywnie rozszerzyć istniejące ASP.NET Core `WebHost`, takich jak istniejący ASP.NET Core Web API lub MVC aplikacji.

Każde podejście ma zalety i wady w zależności od firmy i potrzeb skalowalności. Najważniejsze jest to, że jeśli zadania w tle nie`IWebHost`mają nic `IHost`wspólnego z HTTP ( ) należy użyć .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie hostowanych usług w webhostie lub hoście

Przejdźmy do szczegółów na `IHostedService` interfejsie, ponieważ jego `WebHost` użycie jest `Host`bardzo podobne w lub w .

SignalR jest jednym z przykładów artefaktu przy użyciu hostowanych usług, ale można go również używać do znacznie prostszych rzeczy, takich jak:

- Zadanie w tle sondowania bazy danych w poszukiwaniu zmian.
- Zaplanowane zadanie okresowo aktualizuje niektóre pamięci podręcznej.
- Implementacja QueueBackgroundWorkItem, który umożliwia zadanie do wykonania w wątku w tle.
- Przetwarzanie wiadomości z kolejki komunikatów w tle aplikacji sieci `ILogger`web podczas udostępniania typowych usług, takich jak .
- Zadanie w tle `Task.Run()`rozpoczęte od .

Można w zasadzie odciążyć dowolną z tych `IHostedService`akcji do zadania w tle, które implementuje .

Sposób dodawania jednego `IHostedServices` lub `WebHost` wielu `Host` do ciebie lub jest <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  przez zarejestrowanie `WebHost` ich za `Host` pomocą metody rozszerzenia w ASP.NET Core (lub w .NET Core 2.1 i powyżej). Zasadniczo musisz zarejestrować hostowane usługi w znanej `ConfigureServices()` metodzie `Startup` klasy, jak w poniższym kodzie z typowego ASP.NET WebHost.

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

W tym kodzie `GracePeriodManagerService` hostowanej usługi jest prawdziwy kod z mikrousługi biznesowej zamawiania w eShopOnContainers, podczas gdy pozostałe dwa są tylko dwa dodatkowe przykłady.

Wykonywanie `IHostedService` zadania w tle jest koordynowany z okresem istnienia aplikacji (host lub mikrousługi, o to chodzi). Rejestrujesz zadania podczas uruchamiania aplikacji i masz możliwość wykonania pewnych wdzięku akcji lub oczyszczania podczas zamykania aplikacji.

Bez `IHostedService`użycia, zawsze można uruchomić wątek w tle, aby uruchomić dowolne zadanie. Różnica jest dokładnie w czasie zamykania aplikacji, gdy ten wątek będzie po prostu zabity bez możliwości uruchomienia wdzięku oczyszczania działań.

## <a name="the-ihostedservice-interface"></a>Interfejs IHostedService

Podczas rejestracji `IHostedService`.NET Core wywoła `StartAsync()` i `StopAsync()` metody typu `IHostedService` podczas uruchamiania i zatrzymywania aplikacji odpowiednio. W szczególności start jest wywoływany po `IApplicationLifetime.ApplicationStarted` uruchomieniu serwera i jest wyzwalany.

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

Jako deweloper jesteś odpowiedzialny za obsługę akcji zatrzymywania usług, gdy `StopAsync()` metoda jest wyzwalana przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie usługi IHostedService z niestandardową klasą usługi hostowane pochodzącej z klasy podstawowej BackgroundService

Można śmiało i utworzyć niestandardowe hostowane klasy usług `IHostedService`od podstaw i zaimplementować , jak trzeba zrobić podczas korzystania z .NET Core 2.0.

Jednak ponieważ większość zadań w tle będzie miała podobne potrzeby w odniesieniu do zarządzania tokenami anulowania i innych `BackgroundService` typowych operacji, istnieje wygodna abstrakcyjna klasa podstawowa, z której można pochodzić, nazwana (dostępna od .NET Core 2.1).

Ta klasa zapewnia główną pracę potrzebną do skonfigurowania zadania w tle.

Następny kod jest abstrakcyjną klasą podstawową BackgroundService zaimplementowane w .NET Core.

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

Podczas wywodzi się z poprzedniej abstrakcyjnej klasy podstawowej, dzięki tej dziedziczonej implementacji, wystarczy zaimplementować `ExecuteAsync()` metodę w własnej niestandardowej klasie hostowanej usługi, jak w poniższym uproszczonym kodzie z eShopOnContainers, który sonduje bazę danych i publikuje zdarzenia integracji w usłudze Event Bus w razie potrzeby.

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

W tym konkretnym przypadku dla eShopOnContainers wykonuje metodę aplikacji, która jest wykonywanie kwerendy tabeli bazy danych w poszukiwaniu zamówień o określonym stanie i podczas stosowania zmian, publikuje zdarzenia integracji za pośrednictwem magistrali zdarzeń (pod nim może być przy użyciu rabbitmq lub usługi Azure Service Bus).

Oczywiście, można uruchomić dowolne inne zadanie w tle biznesowym, zamiast.

Domyślnie token anulowania jest ustawiany z 5-sekundowym timeoutm, `WebHost` chociaż `UseShutdownTimeout` można ją `IWebHostBuilder`zmienić podczas tworzenia przy użyciu rozszerzenia pliku . Oznacza to, że oczekuje się, że nasza usługa anuluje się w ciągu 5 sekund, w przeciwnym razie zostanie ona bardziej gwałtownie zabita.

Poniższy kod będzie zmieniać ten czas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klasy podsumowania

Na poniższej ilustracji przedstawiono wizualne podsumowanie klas i interfejsów zaangażowanych podczas implementowania Usług IHostedServices.

![Diagram pokazujący, że IWebHost i IHost mogą obsługiwać wiele usług.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Rysunek 6-27**. Diagram klasy przedstawiający wiele klas i interfejsów związanych z usługą IHostedService

Diagram klasy: IWebHost i IHost mogą obsługiwać wiele usług, które dziedziczą z BackgroundService, która implementuje IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i dania na wynos

Należy pamiętać, że sposób wdrażania ASP.NET `WebHost` Core lub `Host` .NET Core może mieć wpływ na ostateczne rozwiązanie. Na przykład jeśli wdrożysz swoje `WebHost` usługi IIS lub zwykłą usługę Azure App Service, host można zamknąć z powodu recyklingu puli aplikacji. Ale jeśli wdrażasz hosta jako kontener w koordynatora jak Kubernetes, można kontrolować pewną liczbę wystąpień na żywo hosta. Ponadto można rozważyć inne podejścia w chmurze specjalnie dla tych scenariuszy, takich jak usługi Azure Functions. Na koniec jeśli usługa jest potrzebna do bieżącego uruchomienia i wdrażana na serwerze Windows Server, możesz użyć usługi systemu Windows.

Ale nawet `WebHost` w przypadku wdrożonych w puli aplikacji istnieją scenariusze, takie jak ponowne wypełnianie lub opróżnianie pamięci podręcznej aplikacji w pamięci, które nadal mają zastosowanie.

Interfejs `IHostedService` zapewnia wygodny sposób uruchamiania zadań w tle w ASP.NET core aplikacji sieci web (w .NET Core 2.0 i nowszych wersjach) lub w dowolnym procesie/hoście (począwszy od .NET Core 2.1 z `IHost`). Jego główną zaletą jest możliwość uzyskania z wdzięku anulowania do czyszczenia kodu zadań w tle, gdy sam host jest zamykany.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie zaplanowanego zadania w ASP.NET Core/Standard 2.0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementowanie usługi IHostedService w ASP.NET Core 2.0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **GenericHost Próbki przy użyciu ASP.NET Core 2.1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Poprzedni](test-aspnet-core-services-web-apps.md)
>[następny](implement-api-gateways-with-ocelot.md)
