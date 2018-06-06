---
title: Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: eb6d412ee91ab8d2c97a4917f23ee914e3fb9068
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805571"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Wykonania zadania w tle w mikrousług IHostedService i klasa BackgroundService

Zadania w tle i zaplanowane zadania są coś, co może wystąpić potrzeba wdrożenia, po pewnym czasie w aplikacji na podstawie mikrousługi lub dowolnego rodzaju aplikacji. Różnica podczas korzystania z architektury mikrousług jest zaimplementowanie mikrousługi pojedynczego procesu/kontener dla hostingu te zadania w tle, więc możesz go w dół w górę Skaluj w miarę potrzebne lub można nawet upewnij się, że działa jedno wystąpienie tego proces mikrousługi/kontenera.

Z ogólnym punktu widzenia w .NET Core dzwoniliśmy tego rodzaju zadania usługi hostowanej, ponieważ są one usług/logiki hosta w sieci hosta/aplikacji/mikrousługi. Należy pamiętać, że w takim przypadku usługa hostowana po prostu oznacza, że klasa z logiką zadania tła.

Ponieważ .NET Core 2.0, platformę oferuje nowy interfejs o nazwie <xref:Microsoft.Extensions.Hosting.IHostedService> pomaga łatwo wdrożenie hostowanych usług. Podstawową koncepcją nie można zarejestrować wiele zadania w tle (usług hostowanych), które są wykonywane w tle podczas hosta sieci web lub host działa, jak pokazano na poniższej ilustracji.

![](./media/image26.png)

**Rysunek 8-25.** Przy użyciu IHostedService w WebHost a Host

Różnice między `WebHost` i `Host`. A `WebHost` (podstawowa Implementacja klasy `IWebHost`) w programie ASP.NET 2.0 Core jest artefaktów infrastruktury są używane do udostępniania, serwer HTTP funkcje do procesu, na przykład jeśli wdrażania aplikacji sieci web MVC lub Web API usługi. Zawiera wszystkie nowe zgodność infrastruktury w ASP.NET Core, dzięki któremu można iniekcji zależności, Wstaw middlewares w potoku HTTP, itp. oraz dokładnie poniższe `IHostedServices` dla zadania w tle.

A `Host` (podstawowa Implementacja klasy `IHost`), jednak jest nowa w programie .NET Core 2.1 coś. Zasadniczo `Host` służy do podobnych infrastruktury niż masz z `WebHost` (iniekcji zależności usług hostowanych, itp.), ale w takim przypadku po prostu chcesz mieć procesu proste i jaśniejszy jako hosta, z żadnych danych dotyczących MVC , HTTP lub interfejsu API funkcji serwera w sieci web.

W związku z tym można wybrać i Utwórz specjalne proces hosta z IHost do obsługi usług hostowanych i niczego poza, takie mikrousługi, wykonywane tylko dla hostingu `IHostedServices`, lub też można rozszerzyć istniejące platformy ASP.NET Core `WebHost` , takich jak istniejącej aplikacji interfejsu API platformy ASP.NET Core sieci Web lub MVC. 

Każde podejście jest zalet i wad w zależności od potrzeb biznesowych i skalowalność. Mierzenie jest zasadniczo Jeśli zadania w tle nie mają nic wspólnego z należy używać protokołu HTTP (IWebHost) i IHost, jeśli jest dostępna w programie .NET Core 2.1.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Rejestrowanie hostowanych usług w hosta lub hostem sieci Web

Teraz przejść do szczegółów dalsze na `IHostedService` interfejsu, ponieważ jej użycie jest bardzo podobne w `WebHost` lub `Host`. 

SignalR jest jednym z przykładów artefaktów przy użyciu usług hostowanych, ale można również używać go do łatwiej np.:

-   Zadanie w tle sondowania wyszukiwanie zmiany bazy danych.
-   Zaplanowane zadanie okresowo aktualizacja niektórych pamięci podręcznej.
-   Implementacja QueueBackgroundWorkItem, który umożliwia zadania do wykonania wątku w tle.
-   Przetwarzanie komunikatów z kolejki komunikatów w tle aplikacji sieci web podczas udostępniania wspólnych usług takich jak `ILogger`.
-   Wprowadzenie do zadania w tle `Task.Run()`.

Zasadniczo może odciążyć żadnego z tych akcji zadania tła w zależności od IHostedService.

Sposób dodawania jednego lub wielu `IHostedServices` do Twojej `WebHost` lub `Host` jest rejestrując je się za pośrednictwem standardowych Podpisane (iniekcji zależności) w ASP.NET Core `WebHost` (lub `Host` .NET Core 2.1). Zasadniczo, należy zarejestrować usług hostowanych w znanych `ConfigureServices()` metody `Startup` klasy, jak w poniższym kodzie z typowych WebHost ASP.NET. 

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

W tym kodzie `GracePeriodManagerService` usługi hostowanej jest rzeczywisty kod z porządkowanie mikrousługi biznesowych w eShopOnContainers, podczas drugiego dwie usługi są tylko dwie dodatkowe przykłady.

`IHostedService` Wykonywanie zadań w tle jest powiązane z użytkowania aplikacji (host lub mikrousługi istotnego dla badania). Możesz zarejestrować zadania podczas uruchamiania aplikacji i mieć możliwość wykonaj łagodne akcji lub czyszczenia gdy dana aplikacja jest zamykana.

Bez użycia `IHostedService`, zawsze można uruchomić wątku w tle do uruchamiania zadań. Różnica polega na dokładnie na czas zamknięcia aplikacji podczas tego wątku czy po prostu skasowane bez możliwości do uruchamiania działań oczyszczania bezpieczne.


## <a name="the-ihostedservice-interface"></a>Interfejs IHostedService

Po dokonaniu rejestracji `IHostedService`, wywoła .NET Core `StartAsync()` i `StopAsync()` metody z `IHostedService` wpisz podczas uruchamiania aplikacji i Zatrzymaj odpowiednio. W szczególności rozpoczęcia jest wywoływana po uruchomieniu serwera i `IApplicationLifetime.ApplicationStarted` zostanie wywołany.

`IHostedService` Zgodnie z definicją w .NET Core, wygląda podobnie do następującego.

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
Jak można wyobrazić sobie, możesz utworzyć wiele implementacji IHostedService i zarejestruj je w `ConfigureService()` metody w kontenerze Podpisane, jak pokazano wcześniej. Wszystkie te usługi hostowanej będzie można uruchamiania i zatrzymywania wraz z aplikacji/mikrousługi.

Deweloperzy jesteś odpowiedzialny za obsługę Akcja zatrzymania lub usług po `StopAsync()` metody jest wyzwalany przez hosta.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementowanie IHostedService w przypadku tworzenia klasy pochodnej z klasy podstawowej BackgroundService klasy niestandardowe usługi hostowanej

Przejdź dalej i tworzenia klasy niestandardowej usługi hostowanej od początku i implementować `IHostedService`, jak należy wykonać, korzystając z programu .NET Core 2.0. 

Jednak ponieważ większość zadań w tle zostanie mają podobne wymagania w zakresie zarządzania tokeny anulowania i innymi typowymi operacjami, .NET Core 2.1 będzie dostarczać wygodną abstrakcyjna klasa podstawowa, który może pochodzić od o nazwie BackgroundService.

Klasy zawiera głównego pracy niezbędne do skonfigurowania zadania w tle. Należy pamiętać, że ta klasa rozpocznie się w bibliotece programu .NET Core 2.1, więc nie trzeba go zapisać.

Jednak począwszy od chwili pisania tego dokumentu, .NET Core 2.1 nie został zwolniony. W związku z tym w eShopOnContainers, który aktualnie używa .NET Core 2.0, firma Microsoft są po prostu tymczasowo zawierających tej klasy z repozytorium open source .NET Core 2.1 (nie ma potrzeby zastrzeżonych licencji niż licencji open source), ponieważ jest on zgodny z bieżący interfejs IHostedService w programie .NET Core 2.0. Po zwolnieniu .NET Core 2.1, należy po prostu wskaż prawy pakietu NuGet.

Następny kod jest abstrakcyjna klasa podstawowa BackgroundService zaimplementowanego w .NET Core 2.1.

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

Gdy wynikających z poprzednich abstrakcyjna klasa podstawowa, dzięki użyciu tej implementacji dziedziczone, wystarczy do zaimplementowania `ExecuteAsync()` w własne metody klasy usługi hostowanej, w następującej uproszczone kod z eShopOnContainers, który przeprowadza sondowanie bazy danych i publikowania zdarzeń integracji do magistrali zdarzenia w razie potrzeby.

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

W tym przypadku określone dla eShopOnContainers wykonuje metodę aplikacji, która sprawdza tabeli bazy danych wyszukiwania zamówień o określonym stanie i po wprowadzeniu zmian jest publikowanie za pośrednictwem magistrali zdarzeń (na dole mogą zdarzenia integracji za pomocą RabbitMQ lub usługi Azure Service Bus). 

Oczywiście można uruchomić żadnych innych firm zadania w tle, zamiast tego.

Token anulowania jest domyślnie 5 limitu czasu drugiego, mimo że można zmienić tę wartość podczas tworzenia Twojej `WebHost` przy użyciu `UseShutdownTimeout` rozszerzenie `IWebHostBuilder`. Oznacza to, że można anulować w ciągu 5 sekund w przeciwnym razie zostanie ona więcej nagle skasowane oczekuje naszej usługi.

Poniższy kod czy zmiana tego czasu na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram klas podsumowania

Poniższy rysunek 8-26 element wizualny jest widoczne podsumowanie klas i połączony z poruszającą zaangażowany podczas implementowania IHostedServices.
 
![](./media/image27.png)

**Rysunek 8-26.** Klasa diagram przedstawiający wielokrotność klasy i interfejsy powiązane z IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Zagadnienia dotyczące wdrażania i takeaways

Należy zauważyć, że sposób wdrażania programu ASP.NET Core `WebHost` lub .NET Core `Host` może mieć wpływ na ostateczne rozwiązanie. Na przykład w przypadku wdrożenia z `WebHost` na usług IIS lub regularne usługi Azure App Service, host może zostać wyłączony z powodu odtwarzania puli aplikacji. Jeśli na hoście jest wdrażany jako kontener, do programu orchestrator, takich jak Kubernetes lub sieci szkieletowej usług, można jednak sterować bezpieczne liczbę wystąpień na żywo na hoście. Ponadto można rozważyć inne podejścia w chmurze, szczególnie wprowadzone dla tych scenariuszy, takich jak usługi Azure Functions. 

Ale nawet w przypadku `WebHost` wdrożonych w puli aplikacji, istnieją scenariusze, takie jak uważnie lub opróżnianie aplikacji w pamięci podręcznej, które będą nadal stosowane.

`IHostedService` Interfejsu oferują wygodny sposób uruchamiania zadania w tle w ASP.NET Core aplikacji sieci web (w programie .NET Core 2.0) lub w dowolnej procesu/hosta (w programie .NET Core 2.1 z `IHost`). Główne korzyści jest możliwość przypisywany z łagodne anulowania zadania w tle do czyszczenia kodu, gdy sam host jest zamykany.


#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie zaplanowanego zadania w programie ASP.NET 2.0 Core/Standard** 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **Implementowanie IHostedService w platformy ASP.NET Core 2.0** 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **Przykłady Core 2.1 Hosting ASP.NET** 

    [*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
[Poprzednie] (test-aspnet-core-services-web-apps.md) [dalej] (.. /microservice-ddd-cqrs-patterns/index.MD)
