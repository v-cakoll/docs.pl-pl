---
title: Zapoznaj się z niestandardowych ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania
description: Dowiedz się, jak można zaimplementować, od podstaw, ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania do obsługi możliwych scenariuszy błędu HTTP.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: b7aaad9199bb275f45fd088a6207d707e8e5751c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145101"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="86941-103">Zapoznaj się z niestandardowych ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania</span><span class="sxs-lookup"><span data-stu-id="86941-103">Explore custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="86941-104">Aby utworzyć mikrousługi odporne na błędy, wymagana jest obsługa możliwych scenariuszy błędu HTTP.</span><span class="sxs-lookup"><span data-stu-id="86941-104">To create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="86941-105">Jednym ze sposobów obsługi te błędy, chociaż nie jest to zalecane jest tworzenie własnej implementacji ponownych prób z wykorzystaniem wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="86941-105">One way of handling those failures, although not recommended, is to create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="86941-106">**Ważna Uwaga:** W tej sekcji przedstawiono, jak można utworzyć własny kod niestandardowy w celu zaimplementowania ponownych prób wywołania HTTP.</span><span class="sxs-lookup"><span data-stu-id="86941-106">**Important note:** This section shows you how you could create your own custom code to implement HTTP call retries.</span></span> <span data-ttu-id="86941-107">Jednak nie zaleca się zrobienie tego swoim aplikacjom, ale można użyć bardziej zaawansowana i niezawodna, gdy jest łatwiejszy w obsłudze mechanizmów, takich jak `HttpClientFactory` usłudze Polly dostępne od platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="86941-107">However, it is not recommended to do it by your own but to use more powerful and reliable while simpler to use mechanisms, such as `HttpClientFactory` with Polly, available since .NET Core 2.1.</span></span> <span data-ttu-id="86941-108">Te zalecane metody są szczegółowo opisane w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="86941-108">Those recommended approaches are explained in the next sections.</span></span> 

<span data-ttu-id="86941-109">Jako początkowej eksploracji, można zaimplementować własny kod w klasie narzędzia dla wykładniczego wycofywania, podobnie jak w [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), oraz kod podobnie do następującej (który jest również dostępny w tym [GitHub repozytorium](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span><span class="sxs-lookup"><span data-stu-id="86941-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available at this [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

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

<span data-ttu-id="86941-110">Przy użyciu tego kodu w kliencie C\# aplikacji (inny mikrousług klienta interfejsu API sieci Web, aplikacji ASP.NET MVC lub nawet języku C\# aplikacji Xamarin) jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="86941-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="86941-111">W poniższym przykładzie przedstawiono sposób używania klasy HttpClient.</span><span class="sxs-lookup"><span data-stu-id="86941-111">The following example shows how, using the HttpClient class.</span></span>

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

<span data-ttu-id="86941-112">Należy pamiętać, że ten kod nadaje się tylko jako weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="86941-112">Remember that this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="86941-113">W kolejnych sekcjach wyjaśniono, jak korzystać z bardziej zaawansowanych metod, gdy jest to prostsze, przy użyciu HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="86941-113">The next sections explain how to use more sophisticated approaches while simpler, by using HttpClientFactory.</span></span>
<span data-ttu-id="86941-114">HttpClientFactory jest dostępny od platformy .NET Core 2.1, przy użyciu odporność sprawdzonych bibliotek, takich jak Polly.</span><span class="sxs-lookup"><span data-stu-id="86941-114">HttpClientFactory is available since .NET Core 2.1, with proven resiliency libraries like Polly.</span></span> 

>[!div class="step-by-step"]
><span data-ttu-id="86941-115">[Poprzednie](implement-resilient-entity-framework-core-sql-connections.md)
>[dalej](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="86941-115">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>