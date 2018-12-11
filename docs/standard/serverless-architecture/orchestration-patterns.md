---
title: Wzorce aranżacji — aplikacje niekorzystające z serwera
description: Usługa Azure functions trwałe żądania ściągnięcia
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: c3b9dbe473ba9272a8c8c07cec86e11fcd9fc12d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129315"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="9db1a-103">Wzorce aranżacji</span><span class="sxs-lookup"><span data-stu-id="9db1a-103">Orchestration patterns</span></span>

<span data-ttu-id="9db1a-104">Trwałe funkcje ułatwia tworzenie stanowej przepływów pracy, które składają się z działań dyskretnych, długo działające w środowisku bezserwerowym.</span><span class="sxs-lookup"><span data-stu-id="9db1a-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="9db1a-105">Ponieważ funkcje trwałe postęp można śledzić przepływy pracy i okresowo punktów kontrolnych historię wykonywania, pozwalają na implementowanie kilka interesujących wzorców.</span><span class="sxs-lookup"><span data-stu-id="9db1a-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="9db1a-106">Funkcja tworzenia łańcucha</span><span class="sxs-lookup"><span data-stu-id="9db1a-106">Function chaining</span></span>

<span data-ttu-id="9db1a-107">Typowy proces sekwencyjnych działania wymaga wykonywane jedna po drugiej w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9db1a-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="9db1a-108">Opcjonalnie nadchodzących działanie może wymagać pewne dane wyjściowe z poprzednich funkcji.</span><span class="sxs-lookup"><span data-stu-id="9db1a-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="9db1a-109">Tę zależność od kolejności działań tworzy łańcuch funkcji wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9db1a-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="9db1a-110">Zaletą używania funkcje trwałe implementacja tego wzorca przepływu pracy jest dostarczany z jego możliwości tworzenia punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="9db1a-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="9db1a-111">Jeśli serwer ulegnie awarii, upłynie limit czasu sieci lub niektóre problemu, funkcje trwałe można wznowić od ostatniego znanego stanu i kontynuowanie działania przepływu pracy, nawet jeśli jest on na innym serwerze.</span><span class="sxs-lookup"><span data-stu-id="9db1a-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="9db1a-112">W poprzednim przykładzie kodu `CallActivityAsync` funkcja jest odpowiedzialny za działanie danego działania na maszynie wirtualnej w centrum danych.</span><span class="sxs-lookup"><span data-stu-id="9db1a-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="9db1a-113">Po zakończeniu zwraca await i podstawowych zadań wykonywania będą rejestrowane do tabeli historii.</span><span class="sxs-lookup"><span data-stu-id="9db1a-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="9db1a-114">Kod w funkcji programu orchestrator może być użycie dowolnego z dobrze znanych konstrukcje Biblioteka zadań równoległych i słów kluczowych async/await.</span><span class="sxs-lookup"><span data-stu-id="9db1a-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="9db1a-115">Poniższy kod jest uproszczony przykład co `ProcessPayment` metoda może wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="9db1a-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="9db1a-116">Asynchroniczne interfejsy API protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="9db1a-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="9db1a-117">W niektórych przypadkach przepływy pracy mogą zawierać działania, które przyjmują stosunkowo długi okres czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="9db1a-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="9db1a-118">Wyobraź sobie procesu, który dotyczącego utworzenia kopii zapasowej nośnika pliki do magazynu obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="9db1a-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="9db1a-119">W zależności od rozmiaru i liczby plików multimedialnych kopii zapasowej może to potrwać godzin.</span><span class="sxs-lookup"><span data-stu-id="9db1a-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="9db1a-120">W tym scenariuszu `DurableOrchestrationClient`jego możliwości, aby sprawdzić stan uruchomionego przepływu pracy staje się przydatne.</span><span class="sxs-lookup"><span data-stu-id="9db1a-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="9db1a-121">Korzystając z `HttpTrigger` można uruchomić przepływu pracy, `CreateCheckStatusResponse` metoda może służyć do zwrócenia wystąpienia `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="9db1a-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="9db1a-122">Ta odpowiedź zawiera klienta z identyfikatorem URI w ładunku, który może służyć do sprawdzania stanu uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="9db1a-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="9db1a-123">Wynik przykładowe poniżej przedstawia strukturę ładunek odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9db1a-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="9db1a-124">Korzystając z preferowanego klienta HTTP, żądania GET może przyjąć do identyfikatora URI w statusQueryGetUri sprawdzić stan uruchomiony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="9db1a-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="9db1a-125">Odpowiedź zwrócona stan powinien przypominać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="9db1a-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="9db1a-126">Ponieważ proces jest kontynuowany, odpowiedź dotycząca stanu zmieni się na jednej **niepowodzenie** lub **Ukończono**.</span><span class="sxs-lookup"><span data-stu-id="9db1a-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="9db1a-127">Po pomyślnym zakończeniu **dane wyjściowe** właściwość w ładunku będzie zawierać wszystkie zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="9db1a-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="9db1a-128">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="9db1a-128">Monitoring</span></span>

<span data-ttu-id="9db1a-129">Proste zadania cykliczne, usługi Azure Functions zapewnia `TimerTrigger` , można zaplanować określana na podstawie wyrażenia CRON.</span><span class="sxs-lookup"><span data-stu-id="9db1a-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="9db1a-130">Czasomierz sprawdza się w przypadku prostych, krótkotrwałego zadania, ale może być scenariusze, gdy potrzebne są bardziej elastyczne planowanie.</span><span class="sxs-lookup"><span data-stu-id="9db1a-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="9db1a-131">Ten scenariusz jest, gdy wzorzec monitorowania oraz funkcje trwałe może pomóc.</span><span class="sxs-lookup"><span data-stu-id="9db1a-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="9db1a-132">Funkcje trwałe umożliwia elastyczne planowanie odstępach czasu, zarządzanie okresem istnienia i tworzenia wielu procesów monitora z funkcji pojedynczego aranżacji.</span><span class="sxs-lookup"><span data-stu-id="9db1a-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="9db1a-133">Jeden przypadek użycia dla tej funkcji może być do utworzenia obserwatorów zmian cen akcji, kończące się po osiągnięciu określonego progu.</span><span class="sxs-lookup"><span data-stu-id="9db1a-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="9db1a-134">`DurableOrchestrationContext`firmy `CreateTimer` — metoda konfiguruje harmonogram następne wywołanie polecenia pętli w celu wyszukania zmian cen akcji.</span><span class="sxs-lookup"><span data-stu-id="9db1a-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="9db1a-135">`DurableOrchestrationContext` ma również `CurrentUtcDateTime` właściwość, aby uzyskać bieżącą wartość daty/godziny w formacie UTC.</span><span class="sxs-lookup"><span data-stu-id="9db1a-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="9db1a-136">Zaleca się używać tej właściwości zamiast `DateTime.UtcNow` ponieważ ona jest łatwe w postaci makiet do testowania.</span><span class="sxs-lookup"><span data-stu-id="9db1a-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="9db1a-137">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="9db1a-137">Recommended resources</span></span>

* [<span data-ttu-id="9db1a-138">Usługa Azure Functions trwałe</span><span class="sxs-lookup"><span data-stu-id="9db1a-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="9db1a-139">Testowanie jednostek w .NET Core i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9db1a-139">Unit Testing in .NET Core and .NET Standard</span></span>](https://docs.microsoft.com/dotnet/core/testing/)

>[!div class="step-by-step"]
><span data-ttu-id="9db1a-140">[Poprzednie](durable-azure-functions.md)
>[dalej](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="9db1a-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>