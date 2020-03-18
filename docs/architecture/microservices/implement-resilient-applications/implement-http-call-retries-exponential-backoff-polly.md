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
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="6e5ff-103">Implementowanie ponownych prób wywołań HTTP przy gwałtownym wycofywaniu z zasadami IHttpClientFactory i Polly</span><span class="sxs-lookup"><span data-stu-id="6e5ff-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="6e5ff-104">Zalecane podejście do ponownych prób z wykładniczym wycofywaniem jest wykorzystanie bardziej zaawansowanych bibliotek .NET, takich jak [biblioteka Polly](https://github.com/App-vNext/Polly)typu open source .</span><span class="sxs-lookup"><span data-stu-id="6e5ff-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="6e5ff-105">Polly jest biblioteką .NET, która zapewnia odporność i funkcje obsługi błędów przejściowych.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="6e5ff-106">Te możliwości można zaimplementować, stosując zasady Polly, takie jak Ponów próbę, Wyłącznik, Izolacja grodzi, Ułomek czasu i Rezerwowy.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="6e5ff-107">Obiekty docelowe polly .NET Framework 4.x i .NET Standard 1.0, 1.1 i 2.0 (obsługujące program .NET Core).</span><span class="sxs-lookup"><span data-stu-id="6e5ff-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="6e5ff-108">W poniższych krokach przedstawiono sposób używania ponownych `IHttpClientFactory`prób http z wbudowanym polly , co wyjaśniono w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="6e5ff-109">**Odwołaj się do ASP.NET pakietów Core 3.1**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="6e5ff-110">`IHttpClientFactory`jest dostępna, ponieważ .NET Core 2.1 jednak zalecamy użycie najnowszych pakietów ASP.NET Core 3.1 z NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="6e5ff-111">Zazwyczaj należy również odwołać się `Microsoft.Extensions.Http.Polly`do pakietu rozszerzenia .</span><span class="sxs-lookup"><span data-stu-id="6e5ff-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="6e5ff-112">**Konfigurowanie klienta za pomocą zasad ponów polly w aplikacji Uruchamianie**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="6e5ff-113">Jak pokazano w poprzednich sekcjach, należy zdefiniować nazwanego lub wpisanego klienta httpclient konfiguracji w standardowej Metoda Startup.ConfigureServices(...), ale teraz należy dodać kod przyrostowy określający zasady http ponownych prób z wykładniczego wycofywania, jak Poniżej:</span><span class="sxs-lookup"><span data-stu-id="6e5ff-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="6e5ff-114">**AddPolicyHandler()** Metoda jest co dodaje `HttpClient` zasady do obiektów, które będą używane.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="6e5ff-115">W takim przypadku jest dodanie zasad Polly dla Http Ponownych prób z wykładniczym wycofywania.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="6e5ff-116">Aby mieć bardziej modułowe podejście, zasady ponawiania `Startup.cs` http można zdefiniować w oddzielnej metody w pliku, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="6e5ff-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="6e5ff-117">Za pomocą polly można zdefiniować zasady ponawiania z liczbą ponownych prób, wykładniczą konfiguracją wycofywania i akcjami, które należy wykonać, gdy istnieje wyjątek HTTP, na przykład rejestrowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="6e5ff-118">W takim przypadku zasady jest skonfigurowany do próby sześć razy z wykładnicze ponowienie próby, począwszy od dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="6e5ff-119">Dodawanie strategii jitter do zasad ponawiania</span><span class="sxs-lookup"><span data-stu-id="6e5ff-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="6e5ff-120">Regularne zasady ponawiania może mieć wpływ na system w przypadkach wysokiej współbieżności i skalowalności i w wysokiej rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="6e5ff-121">Aby przezwyciężyć szczyty podobnych ponownych prób pochodzących z wielu klientów w przypadku częściowych awarii, dobrym obejściem jest dodanie strategii jitter do algorytmu/zasad ponawiania prób.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="6e5ff-122">Może to poprawić ogólną wydajność systemu end-to-end, dodając losowość do wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="6e5ff-123">To rozkłada się kolce, gdy pojawiają się problemy.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="6e5ff-124">Zasada ta jest zilustrowana następującym przykładem:</span><span class="sxs-lookup"><span data-stu-id="6e5ff-124">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="6e5ff-125">Polly dostarcza gotowe do produkcji algorytmy jitterza za pośrednictwem strony internetowej projektu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6e5ff-126">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="6e5ff-126">Additional resources</span></span>

- <span data-ttu-id="6e5ff-127">**Ponowij próbę wzorzec**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="6e5ff-128">**Polly i IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="6e5ff-129">**Polly (odporność.NET i biblioteka obsługi błędów przejściowych)**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="6e5ff-130">**Polly: Ponów próbę z jitter**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="6e5ff-131">**Marc Brooker. Jitter: Co lepsze z przypadkowości**</span><span class="sxs-lookup"><span data-stu-id="6e5ff-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="6e5ff-132">[Poprzedni](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[następny](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="6e5ff-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
