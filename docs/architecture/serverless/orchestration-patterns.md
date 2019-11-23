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
# <a name="orchestration-patterns"></a>Wzorce aranżacji

Durable Functions ułatwia tworzenie stanowych przepływów pracy, które składają się z dyskretnych, długotrwałych działań w środowisku bezserwerowym. Ponieważ Durable Functions może śledzić postęp przepływów pracy i okresowo sprawdzać historię wykonywania, umożliwia zaimplementowanie niektórych interesujących wzorców.

## <a name="function-chaining"></a>Łańcuch funkcji

W typowym procesie sekwencyjnym działania muszą być wykonywane jeden po drugim w określonej kolejności. Opcjonalnie, nadchodzące działanie może wymagać pewnych danych wyjściowych z poprzedniej funkcji. Ta zależność od kolejności działań powoduje utworzenie łańcucha funkcji wykonania.

Korzyści wynikające z używania Durable Functions do implementowania tego wzorca przepływu pracy pochodzą z możliwości tworzenia punktów kontrolnych. Jeśli serwer ulegnie awarii, nastąpi przejściu do sieci lub jakiś inny problem, trwałe funkcje mogą wznowić działanie od ostatniego znanego stanu i kontynuować działanie przepływu pracy nawet wtedy, gdy znajduje się on na innym serwerze.

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

W poprzednim przykładzie kodu funkcja `CallActivityAsync` jest odpowiedzialna za uruchamianie danego działania na maszynie wirtualnej w centrum danych. Po zakończeniu operacji "await" i "bazowego" zadanie zostanie zarejestrowane w tabeli historii. Kod w funkcji programu Orchestrator może korzystać z dowolnego znanego konstrukcji biblioteki zadań równoległych i słów kluczowych async/await.

Poniższy kod stanowi uproszczony przykład sposobu, w jaki Metoda `ProcessPayment` może wyglądać następująco:

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

## <a name="asynchronous-http-apis"></a>Asynchroniczne interfejsy API protokołu HTTP

W niektórych przypadkach przepływy pracy mogą zawierać działania, które trwają stosunkowo długi czas. Wyobraź sobie proces, który umożliwia rozpoczęcie tworzenia kopii zapasowych plików multimedialnych w usłudze BLOB Storage. W zależności od rozmiaru i liczby plików multimedialnych proces tworzenia kopii zapasowej może trwać kilka godzin.

W tym scenariuszu `DurableOrchestrationClient`możliwości sprawdzenia stanu uruchomionego przepływu pracy staną się przydatne. Przy użyciu `HttpTrigger` do uruchomienia przepływu pracy, Metoda `CreateCheckStatusResponse` może być używana do zwracania wystąpienia `HttpResponseMessage`. Ta odpowiedź zapewnia klientowi identyfikator URI w ładunku, którego można użyć do sprawdzenia stanu uruchomionego procesu.

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

Poniższy przykładowy wynik pokazuje strukturę ładunku odpowiedzi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Korzystając z preferowanego klienta HTTP, można uzyskać żądania GET do identyfikatora URI w statusQueryGetUri, aby sprawdzić stan uruchomionego przepływu pracy. Zwracana odpowiedź stanu powinna wyglądać podobnie do poniższego kodu.

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

W miarę kontynuowania procesu odpowiedź stanu zmieni się na **Niepowodzenie** lub **zakończenie**. Po pomyślnym zakończeniu wartość właściwości **Output** w ładunku będzie zawierać wszystkie zwrócone dane.

## <a name="monitoring"></a>Monitorowanie

W przypadku prostych zadań cyklicznych Azure Functions zapewnia `TimerTrigger`, które mogą być zaplanowane w oparciu o wyrażenie firmy cronus. Czasomierz działa dobrze w przypadku prostych, krótkoterminowych zadań, ale mogą istnieć scenariusze, w których jest wymagana większa elastyczność planowania. Ten scenariusz występuje, gdy wzorzec monitorowania i Durable Functions mogą pomóc.

Durable Functions umożliwia elastyczne interwały planowania, zarządzanie okresem istnienia oraz tworzenie wielu procesów monitorowania z poziomu pojedynczej funkcji aranżacji. Jednym przypadkiem użycia dla tej funkcji może być utworzenie obserwatorów dla zmian cen akcji, które ukończą po spełnieniu określonego progu.

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

`DurableOrchestrationContext``CreateTimer` Metoda konfiguruje harmonogram następnego wywołania pętli w celu sprawdzenia, czy zmieniają się ceny giełdowe. `DurableOrchestrationContext` ma również właściwość `CurrentUtcDateTime`, aby uzyskać bieżącą wartość DateTime w formacie UTC. Lepiej jest używać tej właściwości zamiast `DateTime.UtcNow`, ponieważ jest ona łatwo zastosowana do testowania.

## <a name="recommended-resources"></a>Zalecane zasoby

- [Durable Functions platformy Azure](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Testy jednostkowe w .NET Core i .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Poprzedni](durable-azure-functions.md)
>[Następny](serverless-business-scenarios.md)
