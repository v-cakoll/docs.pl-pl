---
title: Implementowanie ponownych prób wywołania HTTP wykonywanych przy użyciu wycofywania wykładniczego usługi Polly
description: Dowiedz się, jak obsługiwać błędy HTTP z Polly i IHttpClientFactory.
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846799"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>Implementowanie ponownych prób wywołań HTTP przy gwałtownym wycofywaniu z zasadami IHttpClientFactory i Polly

Zalecane podejście do ponownych prób z wykładniczym wycofywaniem jest wykorzystanie bardziej zaawansowanych bibliotek .NET, takich jak [biblioteka Polly](https://github.com/App-vNext/Polly)typu open source .

Polly jest biblioteką .NET, która zapewnia odporność i funkcje obsługi błędów przejściowych. Te możliwości można zaimplementować, stosując zasady Polly, takie jak Ponów próbę, Wyłącznik, Izolacja grodzi, Ułomek czasu i Rezerwowy. Obiekty docelowe polly .NET Framework 4.x i .NET Standard 1.0, 1.1 i 2.0 (obsługujące program .NET Core).

W poniższych krokach przedstawiono sposób używania ponownych `IHttpClientFactory`prób http z wbudowanym polly , co wyjaśniono w poprzedniej sekcji.

**Odwołaj się do ASP.NET pakietów Core 3.1**

`IHttpClientFactory`jest dostępna, ponieważ .NET Core 2.1 jednak zalecamy użycie najnowszych pakietów ASP.NET Core 3.1 z NuGet w projekcie. Zazwyczaj należy również odwołać się `Microsoft.Extensions.Http.Polly`do pakietu rozszerzenia .

**Konfigurowanie klienta za pomocą zasad ponów polly w aplikacji Uruchamianie**

Jak pokazano w poprzednich sekcjach, należy zdefiniować nazwanego lub wpisanego klienta httpclient konfiguracji w standardowej Metoda Startup.ConfigureServices(...), ale teraz należy dodać kod przyrostowy określający zasady http ponownych prób z wykładniczego wycofywania, jak Poniżej:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** Metoda jest co dodaje `HttpClient` zasady do obiektów, które będą używane. W takim przypadku jest dodanie zasad Polly dla Http Ponownych prób z wykładniczym wycofywania.

Aby mieć bardziej modułowe podejście, zasady ponawiania `Startup.cs` http można zdefiniować w oddzielnej metody w pliku, jak pokazano w następującym kodzie:

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

Za pomocą polly można zdefiniować zasady ponawiania z liczbą ponownych prób, wykładniczą konfiguracją wycofywania i akcjami, które należy wykonać, gdy istnieje wyjątek HTTP, na przykład rejestrowanie błędu. W takim przypadku zasady jest skonfigurowany do próby sześć razy z wykładnicze ponowienie próby, począwszy od dwóch sekund.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Dodawanie strategii jitter do zasad ponawiania

Regularne zasady ponawiania może mieć wpływ na system w przypadkach wysokiej współbieżności i skalowalności i w wysokiej rywalizacji. Aby przezwyciężyć szczyty podobnych ponownych prób pochodzących z wielu klientów w przypadku częściowych awarii, dobrym obejściem jest dodanie strategii jitter do algorytmu/zasad ponawiania prób. Może to poprawić ogólną wydajność systemu end-to-end, dodając losowość do wykładniczego wycofywania. To rozkłada się kolce, gdy pojawiają się problemy. Zasada ta jest zilustrowana następującym przykładem:

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

Polly dostarcza gotowe do produkcji algorytmy jitterza za pośrednictwem strony internetowej projektu.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Ponowij próbę wzorzec**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly i IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (odporność.NET i biblioteka obsługi błędów przejściowych)**  
  <https://github.com/App-vNext/Polly>

- **Polly: Ponów próbę z jitter**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker. Jitter: Co lepsze z przypadkowości**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Poprzedni](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[następny](implement-circuit-breaker-pattern.md)
