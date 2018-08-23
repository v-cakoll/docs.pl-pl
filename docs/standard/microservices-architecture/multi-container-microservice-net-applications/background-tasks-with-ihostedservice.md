---
title: Implementowanie zadań w tle w mikrousługach za pomocą interfejsu IHostedService i klasa BackgroundService
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie zadań w tle w mikrousługach za pomocą interfejsu IHostedService i klasa BackgroundService
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6ce9e40334e80e8bd17ce2f3d2569a1e3c39d09e
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752135"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementowanie zadań w tle w mikrousługach za pomocą interfejsu IHostedService i klasa BackgroundService

Zadania w tle i zaplanowane zadania to coś, co jest potrzebne do zaimplementowania po pewnym czasie w aplikacji mikrousług na podstawie lub w dowolnych aplikacji. Różnica w przypadku korzystania z architektury mikrousług jest zaimplementowanie pojedynczych mikrousług procesu/kontenera do hostowania te zadania w tle, dzięki czemu można skalować ją w górę/w dół zgodnie z potrzebne lub można nawet upewnij się, że działa jedno wystąpienie mikrousługi procesu/kontenera.

Z ogólnych punktu widzenia platformie .NET Core firma Microsoft o nazwie tego rodzaju usługi hostowane zadania, ponieważ są one usług/logikę, która hostować w ramach usługi hosta/aplikacji/mikrousług. Należy pamiętać, że w tym przypadku usługa hostowana po prostu oznacza, że klasa wraz z logiką zadania w tle.

Od .NET Core 2.0, struktura zapewnia nowy interfejs o nazwie <xref:Microsoft.Extensions.Hosting.IHostedService> pomaga łatwo Implementuj hostowanej usługi. Podstawowa Koncepcja polega na można zarejestrować wiele zadań w tle (usługi hostowane), które są uruchamiane w tle podczas hosta sieci web lub hoście jest uruchomiona, jak pokazano na poniższej ilustracji.

![](./media/image26.png)

**Rysunek 8-25.** Korzystanie z pomocą interfejsu IHostedService w WebHost a hostem

Należy zanotować różnicę między `WebHost` i `Host`. A `WebHost` (podstawowa Implementacja klasy `IWebHost`) w programie ASP.NET Core 2.0 jest artefaktów infrastruktury umożliwia Podaj serwer HTTP funkcje do procesu, na przykład w przypadku wdrażania aplikacji sieci web MVC lub interfejsu API sieci Web usługi. Zawiera wszystkie nowe zgodność infrastruktury w programie ASP.NET Core, umożliwiając iniekcji zależności, Wstaw middlewares potok HTTP, itp. i dokładnie służą `IHostedServices` dla zadań w tle.

A `Host` (podstawowa Implementacja klasy `IHost`), jednak jest coś, co nowego w programie .NET Core 2.1. Po prostu `Host` pozwala na korzystanie z podobnych infrastruktury niż posiadane przez Ciebie za pomocą `WebHost` (iniekcji zależności, hostowanych usług, itp.), ale w takim przypadku po prostu chcesz mieć jaśniejszy procesem jako hosta, z żadnych danych dotyczących MVC , HTTP i interfejsów API funkcji serwera w sieci web.

W związku z tym, można wybrać i Utwórz wyspecjalizowane procesu hosta za pomocą IHost do obsługi usług hostowanych i nic, mikrousługi, stworzona dla hostingu `IHostedServices`, lub też można rozszerzyć istniejące platformy ASP.NET Core `WebHost` , takich jak istniejącej aplikacji i interfejsów API platformy ASP.NET Core MVC. 

Każde podejście ma zalety i wady, w zależności od potrzeb biznesowych i skalowalności. Mierzenie jest zasadniczo, jeśli zadania w tle mają one nic wspólnego z protokołu HTTP (IWebHost), należy użyć i IHost, jeśli jest dostępny w programie .NET Core 2.1.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie hostowanych usług w hosta lub hostem sieci Web

Umożliwia przechodzenie do dalsze na `IHostedService` interfejsu, ponieważ jego użycie jest bardzo podobna `WebHost` lub `Host`. 

SignalR jest przykładem artefakt przy użyciu usług hostowanych, ale możesz również używać go do znacznie prostsze elementów, takich jak:

-   Zadanie w tle sondowania szukasz zmiany bazy danych.
-   Zaplanowane zadanie aktualizacji okresowo niektóre pamięci podręcznej.
-   Implementacja QueueBackgroundWorkItem umożliwiająca zadań do wykonania w wątku tła.
-   Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacja sieci web a jednocześnie udostępnianie usług wspólne, takie jak `ILogger`.
-   Rozpoczęcie zadania w tle `Task.Run()`.

W zasadzie można odciążyć dowolne z tych akcji, aby zadanie w tle oparte na pomocą interfejsu IHostedService.

Sposób dodawania jednego lub wielu `IHostedServices` do Twojej `WebHost` lub `Host` polega na rejestrowania ich za pośrednictwem standardowych DI (iniekcji zależności) w programie ASP.NET Core `WebHost` (lub `Host` w programie .NET Core 2.1). Zasadniczo należy zarejestrować usług hostowanych w znanej `ConfigureServices()` metody `Startup` klasy, jak w poniższym kodzie z typowym hostem sieci Web platformy ASP.NET. 

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

W tym kodzie `GracePeriodManagerService` usługi hostowanej jest rzeczywisty kod z mikrousług firm porządkowanie w ramach aplikacji eShopOnContainers, podczas gdy inne dwa są tylko dwa dodatkowe przykłady.

`IHostedService` Wykonywanie zadań w tle są koordynowane za pomocą cyklu życia aplikacji (hosta lub mikrousług istotnego dla badania). Możesz zarejestrować zadania podczas uruchamiania aplikacji i mieć możliwość niektórych czynności łagodne lub czyszczenia po dana aplikacja jest zamykana.

Bez użycia `IHostedService`, zawsze można uruchomić wątku w tle do uruchamiania zadań. Różnica polega na dokładnie na czas zamykania aplikacji, gdy wątek będzie po prostu zabite bez możliwości uruchamiania łagodne akcje czyszczenia.


## <a name="the-ihostedservice-interface"></a>Interfejs pomocą interfejsu IHostedService

Po dokonaniu rejestracji `IHostedService`, .NET Core będzie wywoływać `StartAsync()` i `StopAsync()` metody usługi `IHostedService` wpisz podczas uruchamiania aplikacji i Zatrzymaj odpowiednio. W szczególności start jest wywoływana po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` zostanie wywołany.

`IHostedService` Zgodnie z definicją w programie .NET Core, wygląda podobnie do następującego.

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
Jak możesz sobie wyobrazić, możesz utworzyć wiele implementacji pomocą interfejsu IHostedService i zarejestruj je w `ConfigureService()` metody do kontenera DI, jak pokazano wcześniej. Wszystkie te usługi hostowanej będzie można uruchamiać i zatrzymywać wraz z aplikacji/mikrousług.

Jako deweloper jest odpowiedzialny za obsługę Akcja zatrzymania lub usługi w przypadku `StopAsync()` metoda jest wywoływana przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie pomocą interfejsu IHostedService za pomocą klasy niestandardowej usługi hostowanej pochodząca z klasy bazowej BackgroundService

Przejdź dalej i tworzenia klasy niestandardowej usługi hostowanej od podstaw i zaimplementować `IHostedService`, jak należy wykonać w przypadku korzystania z platformy .NET Core 2.0. 

Jednakże ponieważ większość zadań w tle będzie miał podobnych potrzebach w zakresie zarządzania tokenów anulowania i innymi typowymi operacjami, platformy .NET Core 2.1 będzie udostępniać wygodna abstrakcyjna klasa bazowa, użytkownik może pochodzić od, o nazwie BackgroundService.

Ta klasa zawiera główna Praca niezbędne do skonfigurowania zadanie w tle. Należy pamiętać, że ta klasa pojawią się w bibliotece platformy .NET Core 2.1, dzięki czemu nie trzeba go zapisać.

Jednak począwszy od chwili pisania tego dokumentu, platformy .NET Core 2.1 nie został wydany. W związku z tym, w ramach aplikacji eShopOnContainers, który jest obecnie przy użyciu platformy .NET Core 2.0, firma Microsoft są po prostu czasowo dołączanie tej klasy z repozytorium typu open source platformy .NET Core 2.1 (nie ma potrzeby licencji zastrzeżonych niż licencji open source), ponieważ jest on zgodny z bieżący interfejs pomocą interfejsu IHostedService w programie .NET Core 2.0. Po udostępnieniu platformy .NET Core 2.1, należy po prostu wskaż odpowiedni pakiet NuGet.

Następny kod jest abstrakcyjna klasa bazowa BackgroundService zaimplementowanego w programie .NET Core 2.1.

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

Podczas wyprowadzania z poprzednim abstrakcyjna klasa bazowa, dzięki tym dziedziczona implementacja wystarczy do zaimplementowania `ExecuteAsync()` metody w Twoje własne, niestandardowe klasy usługi hostowanej, w następującej uproszczony kod w ramach aplikacji eShopOnContainers, którego sondowanie bazę danych i publikowania zdarzeń integracji do magistrali zdarzeń, gdy potrzebne.

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

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

W tym konkretnym przypadku dla ramach aplikacji eShopOnContainers wykonuje metodę aplikacji, która sprawdza tabelę bazy danych, wyszukiwanie zamówienia z określonym stanem, i po wprowadzeniu zmian publikowania zdarzeń integracji za pomocą magistrali zdarzeń (na dole przyczyną może być Korzystanie z oprogramowania RabbitMQ lub Azure Service Bus). 

Oczywiście można uruchomić żadnych innych firm zadanie w tle, zamiast tego.

Token anulowania jest domyślnie z 5 drugi przekroczenie limitu czasu, mimo że można zmienić tę wartość podczas tworzenia usługi `WebHost` przy użyciu `UseShutdownTimeout` rozszerzenie `IWebHostBuilder`. Oznacza to, że usługa oczekuje się, można anulować w ciągu 5 sekund w przeciwnym razie zostanie więcej nagle zabita.

Poniższy kod będzie zmiana czasu na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klas podsumowania

Poniższa ilustracja 8 26 przedstawia podsumowanie klasy wizualizacji i połączony z poruszającą zaangażowane podczas implementowania IHostedServices.
 
![](./media/image27.png)

**Rysunek 8-26.** Diagram klas przedstawiający wielokrotność klasy i interfejsy powiązane z pomocą interfejsu IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i wnioski

Ważne jest, aby należy pamiętać, że sposób wdrażania ASP.NET Core `WebHost` lub .NET Core `Host` mogą mieć wpływ na ostateczne rozwiązanie. Na przykład w przypadku wdrożenia usługi `WebHost` w usługach IIS lub regularnych usługi Azure App Service hosta może zostać wyłączony z powodu odtwarzanie puli aplikacji. Jeżeli wdrażasz hosta jako kontener, do programu orchestrator, takich jak Kubernetes lub usługi Service Fabric można jednak sterować bezpieczne liczbę wystąpień na żywo hosta. Ponadto można rozważyć inne podejścia w chmurze, szczególnie wprowadzone dla tych scenariuszy, takich jak Azure Functions. 

Ale nawet w przypadku `WebHost` wdrożone do puli aplikacji, istnieją scenariusze, takie jak uważnie lub opróżniania pamięci podręcznej w pamięci aplikacji, które będą nadal stosowane.

`IHostedService` Interfejs zapewnia wygodny sposób uruchamiania zadania w tle w platformy ASP.NET Core w aplikacji sieci web (w programie .NET Core 2.0) lub w dowolnym host/procesu (począwszy od platformy .NET Core 2.1 przy użyciu `IHost`). Jego największą korzyścią jest możliwość pobranego z łagodne anulowanie zadania w tle na kod czyszczenia, gdy sam host jest zamykany.


#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie zaplanowanego zadania w programie ASP.NET 2.0 Core/Standard** 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **Implementowanie pomocą interfejsu IHostedService w programie ASP.NET Core 2.0** 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **Przykłady Core 2.1 hostingu platformy ASP.NET** 

    [*https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
[Poprzednie](test-aspnet-core-services-web-apps.md)
[dalej](../microservice-ddd-cqrs-patterns/index.md)
