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
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="f3e0e-103">Zaimplementuj ponowne próby wywołania HTTP przy użyciu wykładniczej wycofywania z zasadami HttpClientFactory i Polly</span><span class="sxs-lookup"><span data-stu-id="f3e0e-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="f3e0e-104">Zalecanym podejściem do ponawiania prób przy użyciu wykładniczej wycofywania jest skorzystanie z bardziej zaawansowanych bibliotek platformy .NET, takich jak [Biblioteka Polly](https://github.com/App-vNext/Polly)typu open source.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="f3e0e-105">Polly to biblioteka platformy .NET, która zapewnia możliwości odporności i obsługi błędów przejściowych.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="f3e0e-106">Można zaimplementować te funkcje, stosując zasady Polly, takie jak ponawianie próby, wyłącznika, izolacja grodziowa, limit czasu i rezerwa.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="f3e0e-107">Polly targets .NET 4. x i Biblioteka .NET Standard 1,0 (która obsługuje platformę .NET Core).</span><span class="sxs-lookup"><span data-stu-id="f3e0e-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="f3e0e-108">Jednak korzystanie z biblioteki Polly z własnym niestandardowym kodem z HttpClient może być znacząco skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="f3e0e-109">W pierwotnej wersji programu eShopOnContainers istniał [blok konstrukcyjny ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) oparty na Polly.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="f3e0e-110">Jednak w wersji [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), odporna komunikacja http została znacznie łatwiejsza do zaimplementowania, dzięki czemu blok konstrukcyjny jest przestarzały z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), resilient HTTP communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="f3e0e-111">W poniższych krokach pokazano, jak można użyć ponownych prób http z Polly zintegrowanym z HttpClientFactory, co zostało wyjaśnione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="f3e0e-112">**Odwoływanie się do pakietów ASP.NET Core 2,2**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="f3e0e-113">`HttpClientFactory`jest dostępny od platformy .NET Core 2,1, ale zalecamy używanie najnowszych pakietów programu ASP.NET Core 2,2 z narzędzia NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="f3e0e-114">Zwykle potrzebny jest pakiet `AspNetCore` z `Microsoft.Extensions.Http.Polly`pakietem.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="f3e0e-115">**Konfigurowanie klienta przy użyciu zasad ponawiania Polly w programie startowym**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="f3e0e-116">Jak pokazano w poprzednich sekcjach, należy zdefiniować nazwaną lub wpisaną HttpClient konfigurację klienta w standardowej metodzie Startup. ConfigureServices (...), ale teraz można dodać przyrostowy kod określający zasady dla ponawiania prób protokołu HTTP przy użyciu wykładniczej wycofywania, jak poniżej</span><span class="sxs-lookup"><span data-stu-id="f3e0e-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="f3e0e-117">Metoda **AddPolicyHandler ()** dodaje zasady do `HttpClient` obiektów, które będą używane.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="f3e0e-118">W takim przypadku dodajemy zasady Polly do ponawiania prób http przy użyciu wykładniczej wycofywania.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="f3e0e-119">Aby zastosować bardziej modularne podejście, zasady ponawiania http można zdefiniować w oddzielnej metodzie w `Startup.cs` pliku, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f3e0e-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="f3e0e-120">Za pomocą Polly można zdefiniować zasady ponawiania z liczbą ponownych prób, wykładniczą konfiguracją wycofywania i akcjami, które należy wykonać w przypadku wystąpienia wyjątku HTTP, takiego jak rejestrowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="f3e0e-121">W takim przypadku zasady są skonfigurowane do wypróbowania sześć razy z ponowieniem wykładniczym, rozpoczynając od dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="f3e0e-122">Dzięki temu będzie można wypróbować sześć razy, a liczba sekund między kolejnymi próbami będzie wykładnicza, rozpoczynając od dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="f3e0e-123">Dodawanie strategii o wahaniu do zasad ponowień</span><span class="sxs-lookup"><span data-stu-id="f3e0e-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="f3e0e-124">Regularne zasady ponawiania mogą mieć wpływ na system w przypadku dużej współbieżności i skalowalności oraz w przypadku dużej rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="f3e0e-125">Aby przezwyciężyć szczyty podobnych ponownych prób pochodzących z wielu klientów w przypadku częściowego przestoju, dobrym rozwiązaniem jest dodanie strategii o wahaniu do algorytmu/zasad ponowień.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="f3e0e-126">Może to poprawić ogólną wydajność systemu kompleksowego, dodając losowość do wykładniczej wycofywania.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="f3e0e-127">Powoduje to rozłożenie skoków w przypadku wystąpienia problemów.</span><span class="sxs-lookup"><span data-stu-id="f3e0e-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="f3e0e-128">W przypadku używania zwykłych zasad Polly kod do implementacji wahania może wyglądać podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="f3e0e-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="f3e0e-129">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f3e0e-129">Additional resources</span></span>

- <span data-ttu-id="f3e0e-130">**Wzorzec ponawiania**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="f3e0e-131">**Polly i HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="f3e0e-132">**Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="f3e0e-133">**Brooker wytłoczyn. Zakłócenia Zwiększanie losowości**</span><span class="sxs-lookup"><span data-stu-id="f3e0e-133">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="f3e0e-134">[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)Następny
>[](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="f3e0e-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
