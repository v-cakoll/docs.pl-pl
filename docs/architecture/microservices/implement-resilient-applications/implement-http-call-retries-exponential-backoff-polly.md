---
title: Implementowanie ponownych prób wywołania HTTP wykonywanych przy użyciu wycofywania wykładniczego usługi Polly
description: Dowiedz się, jak obsługiwać błędy HTTP za pomocą Polly i HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296073"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Zaimplementuj ponowne próby wywołania HTTP przy użyciu wykładniczej wycofywania z zasadami HttpClientFactory i Polly

Zalecanym podejściem do ponawiania prób przy użyciu wykładniczej wycofywania jest skorzystanie z bardziej zaawansowanych bibliotek platformy .NET, takich jak [Biblioteka Polly](https://github.com/App-vNext/Polly)typu open source.

Polly to biblioteka platformy .NET, która zapewnia możliwości odporności i obsługi błędów przejściowych. Można zaimplementować te funkcje, stosując zasady Polly, takie jak ponawianie próby, wyłącznika, izolacja grodziowa, limit czasu i rezerwa. Polly targets .NET 4. x i Biblioteka .NET Standard 1,0 (która obsługuje platformę .NET Core).

Jednak korzystanie z biblioteki Polly z własnym niestandardowym kodem z HttpClient może być znacząco skomplikowane. W pierwotnej wersji programu eShopOnContainers istniał [blok konstrukcyjny ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) oparty na Polly. Jednak w wersji [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), odporna komunikacja http została znacznie łatwiejsza do zaimplementowania, dzięki czemu blok konstrukcyjny jest przestarzały z eShopOnContainers. 

W poniższych krokach pokazano, jak można użyć ponownych prób http z Polly zintegrowanym z HttpClientFactory, co zostało wyjaśnione w poprzedniej sekcji.

**Odwoływanie się do pakietów ASP.NET Core 2,2**

`HttpClientFactory`jest dostępny od platformy .NET Core 2,1, ale zalecamy używanie najnowszych pakietów programu ASP.NET Core 2,2 z narzędzia NuGet w projekcie. Zwykle potrzebny jest pakiet `AspNetCore` z `Microsoft.Extensions.Http.Polly`pakietem.

**Konfigurowanie klienta przy użyciu zasad ponawiania Polly w programie startowym**

Jak pokazano w poprzednich sekcjach, należy zdefiniować nazwaną lub wpisaną HttpClient konfigurację klienta w standardowej metodzie Startup. ConfigureServices (...), ale teraz można dodać przyrostowy kod określający zasady dla ponawiania prób protokołu HTTP przy użyciu wykładniczej wycofywania, jak poniżej

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Metoda **AddPolicyHandler ()** dodaje zasady do `HttpClient` obiektów, które będą używane. W takim przypadku dodajemy zasady Polly do ponawiania prób http przy użyciu wykładniczej wycofywania.

Aby zastosować bardziej modularne podejście, zasady ponawiania http można zdefiniować w oddzielnej metodzie w `Startup.cs` pliku, jak pokazano w poniższym kodzie:

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

Dzięki temu będzie można wypróbować sześć razy, a liczba sekund między kolejnymi próbami będzie wykładnicza, rozpoczynając od dwóch sekund.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Dodawanie strategii o wahaniu do zasad ponowień

Regularne zasady ponawiania mogą mieć wpływ na system w przypadku dużej współbieżności i skalowalności oraz w przypadku dużej rywalizacji. Aby przezwyciężyć szczyty podobnych ponownych prób pochodzących z wielu klientów w przypadku częściowego przestoju, dobrym rozwiązaniem jest dodanie strategii o wahaniu do algorytmu/zasad ponowień. Może to poprawić ogólną wydajność systemu kompleksowego, dodając losowość do wykładniczej wycofywania. Powoduje to rozłożenie skoków w przypadku wystąpienia problemów. W przypadku używania zwykłych zasad Polly kod do implementacji wahania może wyglądać podobnie do poniższego przykładu:

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

- **Wzorzec ponawiania**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly i HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**  
  <https://github.com/App-vNext/Polly>

- **Brooker wytłoczyn. Zakłócenia Zwiększanie losowości**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)Następny
>[](implement-circuit-breaker-pattern.md)
