---
title: Wzorce aranżacji — aplikacje niekorzystające z serwera
description: Usługa Azure functions trwałe żądania ściągnięcia
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8be499a24e2c5a94132ce07241e17f675e8a1274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940962"
---
# <a name="orchestration-patterns"></a>Wzorce aranżacji

Trwałe funkcje ułatwia tworzenie stanowej przepływów pracy, które składają się z działań dyskretnych, długo działające w środowisku bezserwerowym. Ponieważ funkcje trwałe postęp można śledzić przepływy pracy i okresowo punktów kontrolnych historię wykonywania, pozwalają na implementowanie kilka interesujących wzorców.

## <a name="function-chaining"></a>Funkcja tworzenia łańcucha

Typowy proces sekwencyjnych działania wymaga wykonywane jedna po drugiej w określonej kolejności. Opcjonalnie nadchodzących działanie może wymagać pewne dane wyjściowe z poprzednich funkcji. Tę zależność od kolejności działań tworzy łańcuch funkcji wykonywania.

Zaletą używania funkcje trwałe implementacja tego wzorca przepływu pracy jest dostarczany z jego możliwości tworzenia punktów kontrolnych. Jeśli serwer ulegnie awarii, upłynie limit czasu sieci lub niektóre problemu, funkcje trwałe można wznowić od ostatniego znanego stanu i kontynuowanie działania przepływu pracy, nawet jeśli jest on na innym serwerze.

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

W poprzednim przykładzie kodu `CallActivityAsync` funkcja jest odpowiedzialny za działanie danego działania na maszynie wirtualnej w centrum danych. Po zakończeniu zwraca await i podstawowych zadań wykonywania będą rejestrowane do tabeli historii. Kod w funkcji programu orchestrator może być użycie dowolnego z dobrze znanych konstrukcje Biblioteka zadań równoległych i słów kluczowych async/await.

Poniższy kod jest uproszczony przykład co `ProcessPayment` metoda może wyglądać tak:

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

W niektórych przypadkach przepływy pracy mogą zawierać działania, które przyjmują stosunkowo długi okres czasu wykonania. Wyobraź sobie procesu, który dotyczącego utworzenia kopii zapasowej nośnika pliki do magazynu obiektów blob. W zależności od rozmiaru i liczby plików multimedialnych kopii zapasowej może to potrwać godzin.

W tym scenariuszu `DurableOrchestrationClient`jego możliwości, aby sprawdzić stan uruchomionego przepływu pracy staje się przydatne. Korzystając z `HttpTrigger` można uruchomić przepływu pracy, `CreateCheckStatusResponse` metoda może służyć do zwrócenia wystąpienia `HttpResponseMessage`. Ta odpowiedź zawiera klienta z identyfikatorem URI w ładunku, który może służyć do sprawdzania stanu uruchomionego procesu.

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

Wynik przykładowe poniżej przedstawia strukturę ładunek odpowiedzi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Korzystając z preferowanego klienta HTTP, żądania GET może przyjąć do identyfikatora URI w statusQueryGetUri sprawdzić stan uruchomiony przepływ pracy. Odpowiedź zwrócona stan powinien przypominać następujący kod.

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

Ponieważ proces jest kontynuowany, odpowiedź dotycząca stanu zmieni się na jednej **niepowodzenie** lub **Ukończono**. Po pomyślnym zakończeniu **dane wyjściowe** właściwość w ładunku będzie zawierać wszystkie zwrócone dane.

## <a name="monitoring"></a>Monitorowanie

Proste zadania cykliczne, usługi Azure Functions zapewnia `TimerTrigger` , można zaplanować określana na podstawie wyrażenia CRON. Czasomierz sprawdza się w przypadku prostych, krótkotrwałego zadania, ale może być scenariusze, gdy potrzebne są bardziej elastyczne planowanie. Ten scenariusz jest, gdy wzorzec monitorowania oraz funkcje trwałe może pomóc.

Funkcje trwałe umożliwia elastyczne planowanie odstępach czasu, zarządzanie okresem istnienia i tworzenia wielu procesów monitora z funkcji pojedynczego aranżacji. Jeden przypadek użycia dla tej funkcji może być do utworzenia obserwatorów zmian cen akcji, kończące się po osiągnięciu określonego progu.

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

`DurableOrchestrationContext`firmy `CreateTimer` — metoda konfiguruje harmonogram następne wywołanie polecenia pętli w celu wyszukania zmian cen akcji. `DurableOrchestrationContext` ma również `CurrentUtcDateTime` właściwość, aby uzyskać bieżącą wartość daty/godziny w formacie UTC. Zaleca się używać tej właściwości zamiast `DateTime.UtcNow` ponieważ ona jest łatwe w postaci makiet do testowania.

## <a name="recommended-resources"></a>Zalecane zasoby

* [Usługa Azure Functions trwałe](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Testowanie jednostek w .NET Core i .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Poprzednie](durable-azure-functions.md)
>[dalej](serverless-business-scenarios.md)