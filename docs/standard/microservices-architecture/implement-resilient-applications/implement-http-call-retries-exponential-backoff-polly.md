---
title: Implementowanie ponownych prób wywołania HTTP wykonywanych przy użyciu wycofywania wykładniczego usługi Polly
description: Informacje o sposobie obsługi błędów HTTP za pomocą Polly i HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: f9f7c60792527c6bdba9a63b31e3dcbec2963da9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644562"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="d828b-103">Implementowanie ponownych prób wywołania HTTP z wykorzystaniem wykładniczego wycofywania z zasadami dotyczącymi HttpClientFactory i Polly</span><span class="sxs-lookup"><span data-stu-id="d828b-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="d828b-104">Jest zalecane podejście do ponawiają próby z wykorzystaniem wykładniczego wycofywania, aby skorzystać z bardziej zaawansowanych bibliotek .NET, takich jak typu open-source [biblioteki Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="d828b-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="d828b-105">Polly jest bibliotekę .NET, która zapewnia funkcje obsługi przejściowy błędów i odporności na błędy.</span><span class="sxs-lookup"><span data-stu-id="d828b-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="d828b-106">Te funkcje można zaimplementować, stosując zasady Polly, np. Ponów próbę, wyłącznik, grodziowym izolacji, limitu czasu i powrotu.</span><span class="sxs-lookup"><span data-stu-id="d828b-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="d828b-107">Polly jest przeznaczony dla platformy .NET 4.x i .NET Standard biblioteki 1.0 (który obsługuje platformy .NET Core).</span><span class="sxs-lookup"><span data-stu-id="d828b-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="d828b-108">Jednak za pomocą biblioteki Polly firmy przy użyciu własnego kodu niestandardowego za pomocą klasy HttpClient może być znacznie skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="d828b-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="d828b-109">W pierwotnej wersji w ramach aplikacji eShopOnContainers wystąpił [bloków konstrukcyjnych ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) oparte na Polly.</span><span class="sxs-lookup"><span data-stu-id="d828b-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="d828b-110">Jednak wraz z wydaniem [HttpClientFactory](https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests), odporne na błędy komunikacji Http stała się znacznie prostsza do zaimplementowania, tak aby bloków konstrukcyjnych została zakończona w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d828b-110">But with the release of [HttpClientFactory](https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests), resilient Http communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="d828b-111">Poniższe kroki pokazują, jak można użyć protokołu Http ponownych prób w usłudze Polly zintegrowane HttpClientFactory, która została wyjaśniona w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d828b-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="d828b-112">**Odwołania się do pakietów programu ASP.NET Core 2.2**</span><span class="sxs-lookup"><span data-stu-id="d828b-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="d828b-113">`HttpClientFactory` jest dostępny od platformy .NET Core 2.1 jednak zaleca się korzystanie z najnowszych pakietów platformy ASP.NET Core 2.2 z pakietów NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d828b-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="d828b-114">Zazwyczaj należy `AspNetCore` meta Microsoft.aspnetcore.all, a pakiet rozszerzenia `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="d828b-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="d828b-115">**Konfigurowanie klienta zasady ponawiania prób w Polly, uruchamiania**</span><span class="sxs-lookup"><span data-stu-id="d828b-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="d828b-116">Jak pokazano w poprzednich sekcjach, musisz zdefiniować nazwany i typizowany klienta HttpClient konfiguracji w metodzie Startup.ConfigureServices(...) standardowych, ale teraz Dodaj kod przyrostowe, określanie zasad w przypadku ponownych prób Http z wykorzystaniem wykładniczego wycofywania, jako poniżej:</span><span class="sxs-lookup"><span data-stu-id="d828b-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="d828b-117">**AddPolicyHandler()** metoda to, co dodaje zasady do `HttpClient` obiekty użyjesz.</span><span class="sxs-lookup"><span data-stu-id="d828b-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="d828b-118">W tym przypadku go polega na dodaniu zasad Polly dla protokołu Http ponownych prób z wykorzystaniem wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="d828b-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="d828b-119">Aby uzyskać więcej dzięki podejściu, można zdefiniować zasady ponów Http w oddzielnych metodach w ramach `Startup.cs` pliku, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d828b-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="d828b-120">Usłudze Polly można zdefiniować zasady ponawiania z liczbą ponownych prób, konfiguracji wykładniczego wycofywania i jakie działania należy podjąć, gdy występuje wyjątek HTTP, takich jak rejestrowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="d828b-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="d828b-121">W tym przypadku zasad jest skonfigurowany do wypróbowania sześciokrotnie przy użyciu ponawiania wykładniczego, zaczynając od dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="d828b-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="d828b-122">więc spróbuje sześciokrotnie sekund między kolejnymi próbami. zostanie ona wykładniczego, począwszy od dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="d828b-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="d828b-123">Dodaj strategię zakłócenia do zasady ponawiania</span><span class="sxs-lookup"><span data-stu-id="d828b-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="d828b-124">Regularne zasady ponawiania mogą mieć wpływ na systemu w przypadku wysokiej współbieżności i skalowalności i w obszarze rywalizacji o wysokiej.</span><span class="sxs-lookup"><span data-stu-id="d828b-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="d828b-125">Aby wyeliminować szczytowe podobne ponownych prób, pochodzące z wielu klientów w przypadku częściowej awarii, dobre rozwiązanie jest dodanie strategii zakłócenia do algorytmu/zasady ponawiania.</span><span class="sxs-lookup"><span data-stu-id="d828b-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="d828b-126">Może to zwiększyć ogólną wydajność systemu end-to-end, dodając losowości do wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="d828b-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="d828b-127">Rozszerza się skokom o problemach.</span><span class="sxs-lookup"><span data-stu-id="d828b-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="d828b-128">Przy użyciu zwykłego zasad Polly, kod implementujący zakłócenia może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d828b-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="d828b-129">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d828b-129">Additional resources</span></span>

- <span data-ttu-id="d828b-130">**Wzorzec ponawiania**\\</span><span class="sxs-lookup"><span data-stu-id="d828b-130">**Retry pattern**\\</span></span>
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="d828b-131">**Polly i HttpClientFactory**\\</span><span class="sxs-lookup"><span data-stu-id="d828b-131">**Polly and HttpClientFactory**\\</span></span>
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="d828b-132">**Polly (odporności platformy .NET i biblioteki przejściowy błędów obsługi)**\\</span><span class="sxs-lookup"><span data-stu-id="d828b-132">**Polly (.NET resilience and transient-fault-handling library)**\\</span></span>
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="d828b-133">**Marc Brooker. Jitter: Lepiej wprowadzania rzeczy za pomocą losowości**\\</span><span class="sxs-lookup"><span data-stu-id="d828b-133">**Marc Brooker. Jitter: Making Things Better With Randomness**\\</span></span>
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="d828b-134">[Poprzednie](explore-custom-http-call-retries-exponential-backoff.md)
>[dalej](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="d828b-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
