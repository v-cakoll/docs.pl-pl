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
# <a name="orchestration-patterns"></a>Wzorce aranżacji

Trwałe funkcje ułatwia tworzenie stanowych przepływów pracy, które składają się z dyskretnych, długotrwałych działań w środowisku bezserwerowym. Ponieważ funkcje trwałe można śledzić postęp przepływów pracy i okresowo punktów kontrolnych historii wykonywania, nadaje się do implementowania niektórych ciekawych wzorców.

## <a name="function-chaining"></a>Łączenie funkcji w łańcuchy

W typowym procesie sekwencyjnym działania muszą wykonywać jeden po drugim w określonej kolejności. Opcjonalnie nadchodzące działanie może wymagać pewnych danych wyjściowych z poprzedniej funkcji. Ta zależność od kolejności działań tworzy łańcuch funkcji wykonywania.

Zaletą przy użyciu funkcji trwałych do zaimplementowania tego wzorca przepływu pracy pochodzi z jego zdolność do wykonywania punktów kontrolnych. Jeśli serwer ulegnie awarii, ukończy się unumerem dostępu do sieci lub wystąpi inny problem, trwałe funkcje można wznowić z ostatniego znanego stanu i kontynuować uruchamianie przepływu pracy, nawet jeśli znajduje się na innym serwerze.

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

W poprzednim przykładzie kodu `CallActivityAsync` funkcja jest odpowiedzialna za uruchamianie danego działania na maszynie wirtualnej w centrum danych. Po zakończeniu await zwraca i podstawowe zadanie zakończy wykonanie zostaną zapisane do tabeli historii. Kod w funkcji koordynatora można użyć dowolnej znanej konstrukcji task parallel library i async/await słów kluczowych.

Poniższy kod jest uproszczonym przykładem `ProcessPayment` tego, jak może wyglądać metoda:

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

## <a name="asynchronous-http-apis"></a>Asynchroniczne interfejsy API HTTP

W niektórych przypadkach przepływy pracy mogą zawierać działania, które zajmują stosunkowo długi okres czasu, aby zakończyć. Wyobraź sobie proces, który rozpoczyna tworzenie kopii zapasowych plików multimedialnych do magazynu obiektów blob. W zależności od rozmiaru i ilości plików multimedialnych ten proces tworzenia kopii zapasowej może potrwać wiele godzin.

W tym scenariuszu `DurableOrchestrationClient`'s możliwość sprawdzenia stanu uruchomionego przepływu pracy staje się przydatne. Podczas korzystania `HttpTrigger` z przepływu pracy, `CreateCheckStatusResponse` metoda może służyć do `HttpResponseMessage`zwrócenia wystąpienia . Ta odpowiedź zapewnia klientowi identyfikator URI w ładunku, który może służyć do sprawdzania stanu uruchomionego procesu.

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

Poniższy wynik próbki pokazuje strukturę ładunku odpowiedzi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Przy użyciu preferowanego klienta HTTP żądania GET można wysyłać do identyfikatora URI w stanieQueryGetUri, aby sprawdzić stan uruchomionego przepływu pracy. Zwrócona odpowiedź stanu powinna przypominać następujący kod.

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

W miarę trwania procesu odpowiedź o stanie zmieni się na **Nieudaną** lub **Ukończoną.** Po pomyślnym zakończeniu właściwość **danych wyjściowych** w ładunku będzie zawierać wszystkie zwrócone dane.

## <a name="monitoring"></a>Monitorowanie

W przypadku prostych zadań cyklicznych usługi Azure Functions `TimerTrigger` udostępnia, które można zaplanować na podstawie wyrażenia CRON. Czasowak działa dobrze dla prostych, krótkotrwałych zadań, ale mogą istnieć scenariusze, w których potrzebne jest bardziej elastyczne planowanie. W tym scenariuszu jest, gdy wzorzec monitorowania i trwałe funkcje może pomóc.

Trwałe funkcje umożliwiają elastyczne interwały planowania, zarządzanie okresem istnienia i tworzenie wielu procesów monitorowania z jednej funkcji aranżacji. Jednym z przypadków użycia dla tej funkcji może być tworzenie obserwatorów dla zmian cen akcji, które kończą się po osiągnięciu określonego progu.

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

`DurableOrchestrationContext`'s `CreateTimer` metoda określa harmonogram następnego wywołania pętli, aby sprawdzić zmiany cen akcji. `DurableOrchestrationContext`posiada również `CurrentUtcDateTime` właściwość, aby uzyskać bieżącą wartość DateTime w czasie UTC. Lepiej jest używać tej właściwości, `DateTime.UtcNow` a nie dlatego, że jest łatwo wyśmiewany do testowania.

## <a name="recommended-resources"></a>Zalecane zasoby

- [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Testowanie jednostkowe w .NET Core i .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Poprzedni](durable-azure-functions.md)
>[następny](serverless-business-scenarios.md)
