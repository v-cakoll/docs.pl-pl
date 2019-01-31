---
title: Implementowanie ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania w usłudze Polly
description: Informacje o sposobie obsługi błędów HTTP za pomocą Polly i HttpClientFactory.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d0c3042f2831e5f256f43e32e70645213054f247
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479649"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementowanie ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania z zasadami dotyczącymi HttpClientFactory i Polly

Jest zalecane podejście do ponawiają próby z wykorzystaniem wykładniczego wycofywania, aby skorzystać z bardziej zaawansowanych bibliotek .NET, takich jak typu open-source [biblioteki Polly](https://github.com/App-vNext/Polly).

Polly jest bibliotekę .NET, która zapewnia funkcje obsługi przejściowy błędów i odporności na błędy. Te funkcje można zaimplementować, stosując zasady Polly, np. Ponów próbę, wyłącznik, grodziowym izolacji, limitu czasu i powrotu. Polly jest przeznaczony dla platformy .NET 4.x i .NET Standard biblioteki 1.0 (który obsługuje platformy .NET Core).

Jednak za pomocą biblioteki Polly firmy przy użyciu własnego kodu niestandardowego za pomocą klasy HttpClient może być znacznie skomplikowane. W pierwotnej wersji w ramach aplikacji eShopOnContainers wystąpił [bloków konstrukcyjnych ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) oparte na Polly. Jednak wraz z wydaniem HttpClientFactory odporne na błędy komunikacji Http stał się znacznie prostsza do zaimplementowania, tak aby bloków konstrukcyjnych została zakończona w ramach aplikacji eShopOnContainers. 

Poniższe kroki pokazują, jak można użyć protokołu Http ponownych prób w usłudze Polly zintegrowane HttpClientFactory, która została wyjaśniona w poprzedniej sekcji.

**Odwołania się do pakietów programu ASP.NET Core 2.2**

`HttpClientFactory` jest dostępny od platformy .NET Core 2.1 jednak zaleca się korzystanie z najnowszych pakietów platformy ASP.NET Core 2.2 z pakietów NuGet w projekcie. Zazwyczaj należy `AspNetCore` meta Microsoft.aspnetcore.all, a pakiet rozszerzenia `Microsoft.Extensions.Http.Polly`.

**Konfigurowanie klienta zasady ponawiania prób w Polly, uruchamiania**

Jak pokazano w poprzednich sekcjach, musisz zdefiniować nazwany i typizowany klienta HttpClient konfiguracji w metodzie Startup.ConfigureServices(...) standardowych, ale teraz Dodaj kod przyrostowe, określanie zasad w przypadku ponownych prób Http z wykorzystaniem wykładniczego wycofywania, jako poniżej:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** metoda to, co dodaje zasady do `HttpClient` obiekty użyjesz. W tym przypadku go polega na dodaniu zasad Polly dla protokołu Http ponownych prób z wykorzystaniem wykładniczego wycofywania.

Aby uzyskać więcej dzięki podejściu, można zdefiniować zasady ponów Http w oddzielnych metodach w ramach `Startup.cs` pliku, jak pokazano w poniższym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Usłudze Polly można zdefiniować zasady ponawiania z liczbą ponownych prób, konfiguracji wykładniczego wycofywania i jakie działania należy podjąć, gdy występuje wyjątek HTTP, takich jak rejestrowanie błędu. W tym przypadku zasad jest skonfigurowany do wypróbowania sześciokrotnie przy użyciu ponawiania wykładniczego, zaczynając od dwóch sekund. 

więc spróbuje sześciokrotnie sekund między kolejnymi próbami. zostanie ona wykładniczego, począwszy od dwóch sekund.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Dodaj strategię zakłócenia do zasady ponawiania

Regularne zasady ponawiania mogą mieć wpływ na systemu w przypadku wysokiej współbieżności i skalowalności i w obszarze rywalizacji o wysokiej. Aby wyeliminować szczytowe podobne ponownych prób, pochodzące z wielu klientów w przypadku częściowej awarii, dobre rozwiązanie jest dodanie strategii zakłócenia do algorytmu/zasady ponawiania. Może to zwiększyć ogólną wydajność systemu end-to-end, dodając losowości do wykładniczego wycofywania. Rozszerza się skokom o problemach. Przy użyciu zwykłego zasad Polly, kod implementujący zakłócenia może wyglądać następująco:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wzorzec ponawiania**\
  [*https://docs.microsoft.com/azure/architecture/patterns/retry*](/azure/architecture/patterns/retry)

- **Polly i HttpClientFactory**\
  [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

- **Polly (odporności platformy .NET i biblioteki przejściowy błędów obsługi)**\
  [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

- **Marc Brooker. Jitter: Lepiej wprowadzania rzeczy za pomocą losowości**\
  [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)

>[!div class="step-by-step"]
>[Poprzednie](explore-custom-http-call-retries-exponential-backoff.md)
>[dalej](implement-circuit-breaker-pattern.md)