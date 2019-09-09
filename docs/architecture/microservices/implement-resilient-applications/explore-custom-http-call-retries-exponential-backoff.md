---
title: Eksploruj niestandardowe próby wywołania HTTP przy użyciu wykładniczej wycofywania
description: Dowiedz się, jak można zaimplementować ponawianie prób wywołań HTTP przy użyciu wykładniczej wycofywania, od podstaw, aby obsługiwać możliwe scenariusze błędów HTTP.
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296122"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Eksploruj niestandardowe próby wywołania HTTP przy użyciu wykładniczej wycofywania

Aby utworzyć odporne mikrousługi, musisz obsługiwać możliwe scenariusze błędów HTTP. Jednym ze sposobów obsługi tych niepowodzeń, chociaż nie jest to zalecane, jest utworzenie własnej implementacji ponownych prób przy użyciu wykładniczej wycofywania.

**Ważna Uwaga:** W tej sekcji pokazano, jak utworzyć własny kod niestandardowy w celu zaimplementowania ponownych prób wywołania HTTP. Nie jest to jednak zalecane, ale w celu użycia bardziej wydajnego i niezawodnego korzystania z mechanizmów, takich jak `HttpClientFactory` Polly, dostępnych od platformy .NET Core 2,1. Te zalecane podejścia wyjaśniono w następnych sekcjach.

Jako wstępna Eksploracja można zaimplementować własny kod z klasą narzędzi dla wykładniczej wycofywania, jak w [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), oraz kod podobny do poniższego.

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

Korzystanie z tego kodu w aplikacji klient\# C (inna mikrousługa klienta internetowego interfejsu API, aplikacja ASP.NET MVC lub nawet aplikacja środowiska Xamarin\# w języku C) jest prosta. Poniższy przykład pokazuje, jak za pomocą klasy HttpClient.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

Należy pamiętać, że ten kod jest odpowiedni tylko jako Weryfikacja koncepcji. W następnych sekcjach wyjaśniono, jak używać bardziej złożonych metod, przy użyciu HttpClientFactory. HttpClientFactory jest dostępny od platformy .NET Core 2,1 z sprawdzonymi bibliotekami odporności, takimi jak Polly.

>[!div class="step-by-step"]
>[Poprzedni](implement-resilient-entity-framework-core-sql-connections.md)Następny
>[](use-httpclientfactory-to-implement-resilient-http-requests.md)
