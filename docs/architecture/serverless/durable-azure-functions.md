---
title: Trwałe funkcje platformy Azure — aplikacje bezserwerowe
description: Trwałe funkcje platformy Azure rozszerzają czas uruchomieniowy funkcji azure, aby włączyć stanowe przepływy pracy w kodzie.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522863"
---
# <a name="durable-azure-functions"></a>Trwałe funkcje platformy Azure

Podczas tworzenia aplikacji bezserwerowych za pomocą funkcji Azure, operacje będą zazwyczaj przeznaczone do uruchamiania w sposób bezstanowy. Powodem tego wyboru projektu jest, ponieważ w miarę skalowania platformy trudno jest wiedzieć, na jakich serwerach jest uruchomiony kod. Trudno jest również wiedzieć, ile wystąpień jest aktywnych w danym momencie. Istnieją jednak klasy aplikacji, które wymagają bieżącego stanu procesu, które mają być znane. Rozważmy proces składania zamówienia do sklepu internetowego. Operacja realizacji transakcji może być przepływem pracy, który składa się z wielu operacji, które muszą znać stan procesu. Takie informacje mogą obejmować spis produktów, jeśli klient ma jakiekolwiek środki na swoim koncie, a także wyniki przetwarzania karty kredytowej. Operacje te mogą być ich własnymi wewnętrznymi przepływami pracy, a nawet usługami z systemów innych firm.

Istnieją dziś różne wzorce, które pomagają w koordynacji stanu aplikacji między systemami wewnętrznymi i zewnętrznymi. Często można natknąć się na rozwiązania, które opierają się na scentralizowanych systemach kolejkowania, rozproszonych magazynach o wartości klucza lub udostępnionych bazach danych w celu zarządzania tym stanem. Są to jednak wszystkie dodatkowe zasoby, które teraz muszą być aprowizowane i zarządzane. W środowisku bezserwerowym kod może stać się kłopotliwe próbuje koordynować z tych zasobów ręcznie. Usługa Azure Functions oferuje alternatywę dla tworzenia funkcji stanowych o nazwie trwałe funkcje.

Funkcje trwałe jest rozszerzeniem do działania funkcji azure, który umożliwia definiowanie stanowych przepływów pracy w kodzie. Poprzez podział przepływów pracy na działania, trwałe funkcje rozszerzenie można zarządzać stanem, tworzenie punktów kontrolnych postępu i obsługiwać dystrybucję wywołań funkcji między serwerami. W tle korzysta z konta usługi Azure Storage, aby utrwalić historię wykonywania, zaplanować funkcje działania i pobrać odpowiedzi. Twój kod bezserwerowy nigdy nie powinien wchodzić w interakcje z utrwaonymi informacjami na tym koncie magazynu i zazwyczaj nie jest czymś, z czym deweloperzy muszą wchodzić w interakcje.

## <a name="triggering-a-stateful-workflow"></a>Wyzwalanie stanowego przepływu pracy

Stateful przepływów pracy w funkcji trwałe można podzielić na dwa składniki wewnętrzne; wyzwalaczy aranżacji i aktywności. Wyzwalacze i powiązania są podstawowymi składnikami używanymi przez usługi Azure Functions, aby umożliwić funkcje bezserwerowe, które mają być powiadamiane o uruchomieniu, odebraniu danych wejściowych i zwrocie wyników.

### <a name="working-with-the-orchestration-client"></a>Praca z klientem Aranżacji

Aranżacje są unikatowe w porównaniu do innych stylów wyzwalanych operacji w usłudze Azure Functions. Trwałe funkcje umożliwia wykonywanie funkcji, które mogą potrwać wiele godzin lub nawet dni, aby zakończyć. Ten typ zachowania pochodzi z konieczności sprawdzania stanu uruchomionej aranżacji, prewencyjnie zakończyć lub wysłać powiadomienia o zdarzeniach zewnętrznych.

W takich przypadkach trwałe funkcje `DurableOrchestrationClient` rozszerzenie zapewnia klasę, która umożliwia interakcję z funkcji zaaranżowanych. Otrzymasz dostęp do klienta aranżacji przy użyciu `OrchestrationClientAttribute` powiązania. Ogólnie rzecz biorąc, należy dołączyć ten atrybut z `HttpTrigger` `ServiceBusTrigger`innym typem wyzwalacza, takich jak lub . Po wyzwoleniu funkcji źródłowej klient aranżacji może służyć do uruchamiania funkcji koordynatora.

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>Funkcja koordynatora

Adnotacje funkcji z OrchestrationTriggerAttribute w funkcji platformy Azure znaków, które działają jako funkcja koordynatora. Jest odpowiedzialny za zarządzanie różnymi działaniami, które składają się na stanowy przepływ pracy.

Funkcje koordynatora nie można używać powiązań innych niż OrchestrationTriggerAttribute. Ten atrybut może służyć tylko z typem parametru DurableOrchestrationContext. Żadne inne dane wejściowe nie mogą być używane, ponieważ deserializacja danych wejściowych w sygnaturze funkcji nie jest obsługiwana. Aby uzyskać dane wejściowe dostarczone przez klienta\<aranżacji, GetInput T\> metoda musi być używany.

Ponadto zwracane typy funkcji aranżacji muszą być nieważne, zadanie lub wartość serializowalną JSON.

> *Kod obsługi błędów został pominięty dla zwięzłości*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

Wiele wystąpień aranżacji można uruchomić i działa w tym samym czasie. Wywołanie `StartNewAsync` metody `DurableOrchestrationClient` na uruchamia nowe wystąpienie aranżacji. Metoda zwraca `Task<string>` a, który kończy się po rozpoczęciu aranżacji. Wyjątek typu `TimeoutException` zostanie wygenerowany, jeśli aranżacja nie została uruchomiona w ciągu 30 sekund.

Ukończone `Task<string>` z `StartNewAsync` powinien zawierać unikatowy identyfikator wystąpienia aranżacji. Ten identyfikator wystąpienia może służyć do wywoływania operacji na tej konkretnej aranżacji. Aranżacja może być wyszukiwane dla stanu lub wysłane powiadomienia o zdarzeniach.

### <a name="the-activity-functions"></a>Działanie działa

Funkcje działania są dyskretne operacje, które są składane razem w ramach funkcji aranżacji, aby utworzyć przepływ pracy. Oto, gdzie większość rzeczywistych prac odbędzie się. Reprezentują one logikę biznesową, długotrwałe procesy i elementy układanki do większego rozwiązania.

Służy `ActivityTriggerAttribute` do adnotatora parametru `DurableActivityContext`funkcji typu . Za pomocą adnotacji informuje program runtime, że funkcja jest przeznaczona do użycia jako funkcja działania. Wartości wejściowe do funkcji działania `GetInput<T>` są pobierane `DurableActivityContext` przy użyciu metody parametru.

Podobnie jak funkcje aranżacji, zwracane typy funkcji działania muszą być nieważne, zadanie lub wartość serializable JSON.

Wszelkie nieobsługiwane wyjątki, które zostaną wygenerowane w ramach funkcji działania zostanie wysłana `TaskFailedException`do funkcji koordynatora wywołującego i przedstawione jako . W tym momencie błąd można przechwycić i zalogować się w koordynatorze, a działanie można ponowić.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Zalecane zasoby

- [Trwałe funkcje](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Wiązania dla trwałych funkcji](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Zarządzanie wystąpieniami w trwałych funkcjach](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Poprzedni](event-grid.md)
>[następny](orchestration-patterns.md)
