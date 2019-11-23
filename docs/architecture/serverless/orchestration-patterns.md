---
title: Wzorce aranżacji — aplikacje bezserwerowe
description: Usługa Azure trwałe funkcje
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522635"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="887d1-103">Wzorce aranżacji</span><span class="sxs-lookup"><span data-stu-id="887d1-103">Orchestration patterns</span></span>

<span data-ttu-id="887d1-104">Durable Functions ułatwia tworzenie stanowych przepływów pracy, które składają się z dyskretnych, długotrwałych działań w środowisku bezserwerowym.</span><span class="sxs-lookup"><span data-stu-id="887d1-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="887d1-105">Ponieważ Durable Functions może śledzić postęp przepływów pracy i okresowo sprawdzać historię wykonywania, umożliwia zaimplementowanie niektórych interesujących wzorców.</span><span class="sxs-lookup"><span data-stu-id="887d1-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="887d1-106">Łańcuch funkcji</span><span class="sxs-lookup"><span data-stu-id="887d1-106">Function chaining</span></span>

<span data-ttu-id="887d1-107">W typowym procesie sekwencyjnym działania muszą być wykonywane jeden po drugim w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="887d1-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="887d1-108">Opcjonalnie, nadchodzące działanie może wymagać pewnych danych wyjściowych z poprzedniej funkcji.</span><span class="sxs-lookup"><span data-stu-id="887d1-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="887d1-109">Ta zależność od kolejności działań powoduje utworzenie łańcucha funkcji wykonania.</span><span class="sxs-lookup"><span data-stu-id="887d1-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="887d1-110">Korzyści wynikające z używania Durable Functions do implementowania tego wzorca przepływu pracy pochodzą z możliwości tworzenia punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="887d1-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="887d1-111">Jeśli serwer ulegnie awarii, nastąpi przejściu do sieci lub jakiś inny problem, trwałe funkcje mogą wznowić działanie od ostatniego znanego stanu i kontynuować działanie przepływu pracy nawet wtedy, gdy znajduje się on na innym serwerze.</span><span class="sxs-lookup"><span data-stu-id="887d1-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="887d1-112">W poprzednim przykładzie kodu funkcja `CallActivityAsync` jest odpowiedzialna za uruchamianie danego działania na maszynie wirtualnej w centrum danych.</span><span class="sxs-lookup"><span data-stu-id="887d1-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="887d1-113">Po zakończeniu operacji "await" i "bazowego" zadanie zostanie zarejestrowane w tabeli historii.</span><span class="sxs-lookup"><span data-stu-id="887d1-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="887d1-114">Kod w funkcji programu Orchestrator może korzystać z dowolnego znanego konstrukcji biblioteki zadań równoległych i słów kluczowych async/await.</span><span class="sxs-lookup"><span data-stu-id="887d1-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="887d1-115">Poniższy kod stanowi uproszczony przykład sposobu, w jaki Metoda `ProcessPayment` może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="887d1-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="887d1-116">Asynchroniczne interfejsy API protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="887d1-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="887d1-117">W niektórych przypadkach przepływy pracy mogą zawierać działania, które trwają stosunkowo długi czas.</span><span class="sxs-lookup"><span data-stu-id="887d1-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="887d1-118">Wyobraź sobie proces, który umożliwia rozpoczęcie tworzenia kopii zapasowych plików multimedialnych w usłudze BLOB Storage.</span><span class="sxs-lookup"><span data-stu-id="887d1-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="887d1-119">W zależności od rozmiaru i liczby plików multimedialnych proces tworzenia kopii zapasowej może trwać kilka godzin.</span><span class="sxs-lookup"><span data-stu-id="887d1-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="887d1-120">W tym scenariuszu `DurableOrchestrationClient`możliwości sprawdzenia stanu uruchomionego przepływu pracy staną się przydatne.</span><span class="sxs-lookup"><span data-stu-id="887d1-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="887d1-121">Przy użyciu `HttpTrigger` do uruchomienia przepływu pracy, Metoda `CreateCheckStatusResponse` może być używana do zwracania wystąpienia `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="887d1-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="887d1-122">Ta odpowiedź zapewnia klientowi identyfikator URI w ładunku, którego można użyć do sprawdzenia stanu uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="887d1-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="887d1-123">Poniższy przykładowy wynik pokazuje strukturę ładunku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="887d1-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="887d1-124">Korzystając z preferowanego klienta HTTP, można uzyskać żądania GET do identyfikatora URI w statusQueryGetUri, aby sprawdzić stan uruchomionego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="887d1-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="887d1-125">Zwracana odpowiedź stanu powinna wyglądać podobnie do poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="887d1-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="887d1-126">W miarę kontynuowania procesu odpowiedź stanu zmieni się na **Niepowodzenie** lub **zakończenie**.</span><span class="sxs-lookup"><span data-stu-id="887d1-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="887d1-127">Po pomyślnym zakończeniu wartość właściwości **Output** w ładunku będzie zawierać wszystkie zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="887d1-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="887d1-128">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="887d1-128">Monitoring</span></span>

<span data-ttu-id="887d1-129">W przypadku prostych zadań cyklicznych Azure Functions zapewnia `TimerTrigger`, które mogą być zaplanowane w oparciu o wyrażenie firmy cronus.</span><span class="sxs-lookup"><span data-stu-id="887d1-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="887d1-130">Czasomierz działa dobrze w przypadku prostych, krótkoterminowych zadań, ale mogą istnieć scenariusze, w których jest wymagana większa elastyczność planowania.</span><span class="sxs-lookup"><span data-stu-id="887d1-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="887d1-131">Ten scenariusz występuje, gdy wzorzec monitorowania i Durable Functions mogą pomóc.</span><span class="sxs-lookup"><span data-stu-id="887d1-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="887d1-132">Durable Functions umożliwia elastyczne interwały planowania, zarządzanie okresem istnienia oraz tworzenie wielu procesów monitorowania z poziomu pojedynczej funkcji aranżacji.</span><span class="sxs-lookup"><span data-stu-id="887d1-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="887d1-133">Jednym przypadkiem użycia dla tej funkcji może być utworzenie obserwatorów dla zmian cen akcji, które ukończą po spełnieniu określonego progu.</span><span class="sxs-lookup"><span data-stu-id="887d1-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="887d1-134">`DurableOrchestrationContext``CreateTimer` Metoda konfiguruje harmonogram następnego wywołania pętli w celu sprawdzenia, czy zmieniają się ceny giełdowe.</span><span class="sxs-lookup"><span data-stu-id="887d1-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="887d1-135">`DurableOrchestrationContext` ma również właściwość `CurrentUtcDateTime`, aby uzyskać bieżącą wartość DateTime w formacie UTC.</span><span class="sxs-lookup"><span data-stu-id="887d1-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="887d1-136">Lepiej jest używać tej właściwości zamiast `DateTime.UtcNow`, ponieważ jest ona łatwo zastosowana do testowania.</span><span class="sxs-lookup"><span data-stu-id="887d1-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="887d1-137">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="887d1-137">Recommended resources</span></span>

- [<span data-ttu-id="887d1-138">Durable Functions platformy Azure</span><span class="sxs-lookup"><span data-stu-id="887d1-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="887d1-139">Testy jednostkowe w .NET Core i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="887d1-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="887d1-140">[Poprzedni](durable-azure-functions.md)
>[Następny](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="887d1-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
