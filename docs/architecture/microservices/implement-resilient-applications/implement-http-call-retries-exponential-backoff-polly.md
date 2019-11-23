---
title: Implementowanie ponownych prób wywołania HTTP wykonywanych przy użyciu wycofywania wykładniczego usługi Polly
description: Dowiedz się, jak obsługiwać błędy HTTP za pomocą Polly i HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: 551cd1230c565b30c81090c984747e726680b9ed
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089957"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Zaimplementuj ponowne próby wywołania HTTP przy użyciu wykładniczej wycofywania z zasadami HttpClientFactory i Polly

Zalecanym podejściem do ponawiania prób przy użyciu wykładniczej wycofywania jest skorzystanie z bardziej zaawansowanych bibliotek platformy .NET, takich jak [Biblioteka Polly](https://github.com/App-vNext/Polly)typu open source.

Polly to biblioteka platformy .NET, która zapewnia możliwości odporności i obsługi błędów przejściowych. Można zaimplementować te funkcje, stosując zasady Polly, takie jak ponawianie próby, wyłącznika, izolacja grodziowa, limit czasu i rezerwa. Polly targets .NET Framework 4. x i .NET Standard 1,0, 1,1 i 2,0 (które obsługują platformę .NET Core).

Jednak zapisanie własnego niestandardowego kodu do używania biblioteki Polly z HttpClient może być znacząco skomplikowane. W pierwotnej wersji programu eShopOnContainers istniał [blok konstrukcyjny ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) oparty na Polly. Jednak w przypadku wersji [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md)implementacja odpornej komunikacji http z Pollyem została znacznie prostsza, tak że blok konstrukcyjny został uznany za przestarzały z eShopOnContainers.

W poniższych krokach pokazano, jak można użyć ponownych prób http z Polly zintegrowanym z HttpClientFactory, co zostało wyjaśnione w poprzedniej sekcji.

**Odwoływanie się do pakietów ASP.NET Core 2,2**

`HttpClientFactory` jest dostępna od platformy .NET Core 2,1, ale zalecamy korzystanie z najnowszych pakietów ASP.NET Core 2,2 z narzędzia NuGet w projekcie. Zwykle potrzebny jest pakiet `AspNetCore`, a pakiet rozszerzenia `Microsoft.Extensions.Http.Polly`.

**Konfigurowanie klienta przy użyciu zasad ponawiania Polly w programie startowym**

Jak pokazano w poprzednich sekcjach, należy zdefiniować nazwaną lub wpisaną HttpClient konfigurację klienta w standardowej metodzie Startup. ConfigureServices (...), ale teraz można dodać przyrostowy kod określający zasady dla ponawiania prób protokołu HTTP przy użyciu wykładniczej wycofywania, jak poniżej

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Metoda **AddPolicyHandler ()** dodaje zasady do obiektów `HttpClient`, które będą używane. W takim przypadku dodajemy zasady Polly do ponawiania prób http przy użyciu wykładniczej wycofywania.

Aby zastosować bardziej modularne podejście, zasady ponawiania http można zdefiniować w oddzielnej metodzie w pliku `Startup.cs`, jak pokazano w poniższym kodzie:

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

Za pomocą Polly można zdefiniować zasady ponawiania z liczbą ponownych prób, wykładniczą konfiguracją wycofywania i akcjami, które należy wykonać w przypadku wystąpienia wyjątku HTTP, takiego jak rejestrowanie błędu. W takim przypadku zasady są skonfigurowane do wypróbowania sześć razy z ponowieniem wykładniczym, rozpoczynając od dwóch sekund.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Dodawanie strategii o wahaniu do zasad ponowień

Regularne zasady ponawiania mogą mieć wpływ na system w przypadku dużej współbieżności i skalowalności oraz w przypadku dużej rywalizacji. Aby przezwyciężyć szczyty podobnych ponownych prób pochodzących z wielu klientów w przypadku częściowego przestoju, dobrym rozwiązaniem jest dodanie strategii o wahaniu do algorytmu/zasad ponowień. Może to poprawić ogólną wydajność systemu kompleksowego, dodając losowość do wykładniczej wycofywania. Powoduje to rozłożenie skoków w przypadku wystąpienia problemów. Zasada jest zilustrowana przy użyciu poniższego przykładu:

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

Polly zapewnia algorytmy wahania produkcji w środowisku produkcyjnym za pośrednictwem witryny sieci Web projektu.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wzorzec ponawiania**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly i HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**  
  <https://github.com/App-vNext/Polly>

- **Polly: ponów próbę z wahaniem**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Brooker wytłoczyn. Wahanie: zwiększanie losowości**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)
>[Następny](implement-circuit-breaker-pattern.md)
