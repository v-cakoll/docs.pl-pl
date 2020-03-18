---
title: Wzorce aranżacji — aplikacje bezserwerowe
description: Funkcje trwałe platformy Azure pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522635"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="2ac33-103">Wzorce aranżacji</span><span class="sxs-lookup"><span data-stu-id="2ac33-103">Orchestration patterns</span></span>

<span data-ttu-id="2ac33-104">Trwałe funkcje ułatwia tworzenie stanowych przepływów pracy, które składają się z dyskretnych, długotrwałych działań w środowisku bezserwerowym.</span><span class="sxs-lookup"><span data-stu-id="2ac33-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="2ac33-105">Ponieważ funkcje trwałe można śledzić postęp przepływów pracy i okresowo punktów kontrolnych historii wykonywania, nadaje się do implementowania niektórych ciekawych wzorców.</span><span class="sxs-lookup"><span data-stu-id="2ac33-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="2ac33-106">Łączenie funkcji w łańcuchy</span><span class="sxs-lookup"><span data-stu-id="2ac33-106">Function chaining</span></span>

<span data-ttu-id="2ac33-107">W typowym procesie sekwencyjnym działania muszą wykonywać jeden po drugim w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2ac33-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="2ac33-108">Opcjonalnie nadchodzące działanie może wymagać pewnych danych wyjściowych z poprzedniej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ac33-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="2ac33-109">Ta zależność od kolejności działań tworzy łańcuch funkcji wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2ac33-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="2ac33-110">Zaletą przy użyciu funkcji trwałych do zaimplementowania tego wzorca przepływu pracy pochodzi z jego zdolność do wykonywania punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="2ac33-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="2ac33-111">Jeśli serwer ulegnie awarii, ukończy się unumerem dostępu do sieci lub wystąpi inny problem, trwałe funkcje można wznowić z ostatniego znanego stanu i kontynuować uruchamianie przepływu pracy, nawet jeśli znajduje się na innym serwerze.</span><span class="sxs-lookup"><span data-stu-id="2ac33-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="2ac33-112">W poprzednim przykładzie kodu `CallActivityAsync` funkcja jest odpowiedzialna za uruchamianie danego działania na maszynie wirtualnej w centrum danych.</span><span class="sxs-lookup"><span data-stu-id="2ac33-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="2ac33-113">Po zakończeniu await zwraca i podstawowe zadanie zakończy wykonanie zostaną zapisane do tabeli historii.</span><span class="sxs-lookup"><span data-stu-id="2ac33-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="2ac33-114">Kod w funkcji koordynatora można użyć dowolnej znanej konstrukcji task parallel library i async/await słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="2ac33-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="2ac33-115">Poniższy kod jest uproszczonym przykładem `ProcessPayment` tego, jak może wyglądać metoda:</span><span class="sxs-lookup"><span data-stu-id="2ac33-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="2ac33-116">Asynchroniczne interfejsy API HTTP</span><span class="sxs-lookup"><span data-stu-id="2ac33-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="2ac33-117">W niektórych przypadkach przepływy pracy mogą zawierać działania, które zajmują stosunkowo długi okres czasu, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="2ac33-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="2ac33-118">Wyobraź sobie proces, który rozpoczyna tworzenie kopii zapasowych plików multimedialnych do magazynu obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="2ac33-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="2ac33-119">W zależności od rozmiaru i ilości plików multimedialnych ten proces tworzenia kopii zapasowej może potrwać wiele godzin.</span><span class="sxs-lookup"><span data-stu-id="2ac33-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="2ac33-120">W tym scenariuszu `DurableOrchestrationClient`'s możliwość sprawdzenia stanu uruchomionego przepływu pracy staje się przydatne.</span><span class="sxs-lookup"><span data-stu-id="2ac33-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="2ac33-121">Podczas korzystania `HttpTrigger` z przepływu pracy, `CreateCheckStatusResponse` metoda może służyć do `HttpResponseMessage`zwrócenia wystąpienia .</span><span class="sxs-lookup"><span data-stu-id="2ac33-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="2ac33-122">Ta odpowiedź zapewnia klientowi identyfikator URI w ładunku, który może służyć do sprawdzania stanu uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="2ac33-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="2ac33-123">Poniższy wynik próbki pokazuje strukturę ładunku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2ac33-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="2ac33-124">Przy użyciu preferowanego klienta HTTP żądania GET można wysyłać do identyfikatora URI w stanieQueryGetUri, aby sprawdzić stan uruchomionego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2ac33-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="2ac33-125">Zwrócona odpowiedź stanu powinna przypominać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="2ac33-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="2ac33-126">W miarę trwania procesu odpowiedź o stanie zmieni się na **Nieudaną** lub **Ukończoną.**</span><span class="sxs-lookup"><span data-stu-id="2ac33-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="2ac33-127">Po pomyślnym zakończeniu właściwość **danych wyjściowych** w ładunku będzie zawierać wszystkie zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="2ac33-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="2ac33-128">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="2ac33-128">Monitoring</span></span>

<span data-ttu-id="2ac33-129">W przypadku prostych zadań cyklicznych usługi Azure Functions `TimerTrigger` udostępnia, które można zaplanować na podstawie wyrażenia CRON.</span><span class="sxs-lookup"><span data-stu-id="2ac33-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="2ac33-130">Czasowak działa dobrze dla prostych, krótkotrwałych zadań, ale mogą istnieć scenariusze, w których potrzebne jest bardziej elastyczne planowanie.</span><span class="sxs-lookup"><span data-stu-id="2ac33-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="2ac33-131">W tym scenariuszu jest, gdy wzorzec monitorowania i trwałe funkcje może pomóc.</span><span class="sxs-lookup"><span data-stu-id="2ac33-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="2ac33-132">Trwałe funkcje umożliwiają elastyczne interwały planowania, zarządzanie okresem istnienia i tworzenie wielu procesów monitorowania z jednej funkcji aranżacji.</span><span class="sxs-lookup"><span data-stu-id="2ac33-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="2ac33-133">Jednym z przypadków użycia dla tej funkcji może być tworzenie obserwatorów dla zmian cen akcji, które kończą się po osiągnięciu określonego progu.</span><span class="sxs-lookup"><span data-stu-id="2ac33-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="2ac33-134">`DurableOrchestrationContext`'s `CreateTimer` metoda określa harmonogram następnego wywołania pętli, aby sprawdzić zmiany cen akcji.</span><span class="sxs-lookup"><span data-stu-id="2ac33-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="2ac33-135">`DurableOrchestrationContext`posiada również `CurrentUtcDateTime` właściwość, aby uzyskać bieżącą wartość DateTime w czasie UTC.</span><span class="sxs-lookup"><span data-stu-id="2ac33-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="2ac33-136">Lepiej jest używać tej właściwości, `DateTime.UtcNow` a nie dlatego, że jest łatwo wyśmiewany do testowania.</span><span class="sxs-lookup"><span data-stu-id="2ac33-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="2ac33-137">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="2ac33-137">Recommended resources</span></span>

- [<span data-ttu-id="2ac33-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="2ac33-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="2ac33-139">Testowanie jednostkowe w .NET Core i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="2ac33-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="2ac33-140">[Poprzedni](durable-azure-functions.md)
>[następny](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="2ac33-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
