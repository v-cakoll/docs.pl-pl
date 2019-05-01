---
title: Zapoznaj się z niestandardowych ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania
description: Dowiedz się, jak można implementować ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania, od początku do obsługi możliwych scenariuszy błędu HTTP.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: fdbc09cddde34cb8897e1d5b105cb15c863b59ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938661"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Zapoznaj się z niestandardowych ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania

Aby utworzyć mikrousługi odporne na błędy, wymagana jest obsługa możliwych scenariuszy błędu HTTP. Jednym ze sposobów obsługi te błędy, chociaż nie jest to zalecane jest tworzenie własnej implementacji ponownych prób z wykorzystaniem wykładniczego wycofywania.

**Ważna Uwaga:** W tej sekcji przedstawiono, jak można utworzyć własny kod niestandardowy w celu zaimplementowania ponownych prób wywołania HTTP. Jednak nie jest zalecane jest, aby to zrobić po własnych ale używać bardziej zaawansowane i niezawodne, gdy jest łatwiejszy w obsłudze mechanizmów, takich jak `HttpClientFactory` usłudze Polly dostępne od platformy .NET Core 2.1. Te zalecane metody są szczegółowo opisane w kolejnych sekcjach.

Jako początkowej eksploracji, można zaimplementować własny kod w klasie narzędzia dla wykładniczego wycofywania, podobnie jak w [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), oraz kod podobnie do poniższego.

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

Przy użyciu tego kodu w kliencie C\# aplikacji (inny mikrousług klienta interfejsu API sieci Web, aplikacji ASP.NET MVC lub nawet języku C\# aplikacji Xamarin) jest bardzo proste. W poniższym przykładzie przedstawiono sposób używania klasy HttpClient.

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

Należy pamiętać, że ten kod nadaje się tylko jako weryfikacji koncepcji. W kolejnych sekcjach wyjaśniono, jak korzystać z bardziej zaawansowanych metod, gdy jest to prostsze, przy użyciu HttpClientFactory. HttpClientFactory jest dostępny od platformy .NET Core 2.1, przy użyciu odporność sprawdzonych bibliotek, takich jak Polly.

>[!div class="step-by-step"]
>[Poprzednie](implement-resilient-entity-framework-core-sql-connections.md)
>[dalej](use-httpclientfactory-to-implement-resilient-http-requests.md)