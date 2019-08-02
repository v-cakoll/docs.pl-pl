---
title: Trwałe funkcje platformy Azure — aplikacje bezserwerowe
description: Trwałe funkcje platformy Azure zwiększają środowisko uruchomieniowe Azure Functions, aby umożliwić stanowe przepływy pracy w kodzie.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: f7ee74926d6658042120113b49dc763383881423
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676773"
---
# <a name="durable-azure-functions"></a>Trwałe funkcje platformy Azure

Podczas tworzenia aplikacji bezserwerowych z Azure Functions operacje są zwykle przeznaczone do uruchamiania w sposób bezstanowy. Przyczyną tego wyboru jest to, że w miarę skalowania platformy trudno jest wiedzieć, na których serwerach jest uruchomiony kod. Trudno jest również wiedzieć, ile wystąpień jest aktywnych w danym punkcie. Istnieją jednak klasy aplikacji, które wymagają znanego stanu procesu. Weź pod uwagę proces przesyłania zamówienia do sklepu online. Operacja wyewidencjonowywania może być przepływem pracy, który składa się z wielu operacji, które muszą znać stan procesu. Takie informacje mogą obejmować spis produktów, jeśli klient ma jakiekolwiek środki na swoje konto, a także wyniki przetwarzania karty kredytowej. Te operacje mogą łatwo być własnymi wewnętrznymi przepływami pracy lub nawet usługami z systemów innych firm.

Istnieją różne wzorce, które pomagają w koordynacji stanu aplikacji między systemami wewnętrznymi i zewnętrznymi. Często są one dostępne w różnych rozwiązaniach, które polegają na scentralizowanych systemach kolejkowania, rozproszonych magazynach wartości klucza lub udostępnionych bazach danych w celu zarządzania tym stanem. Są to jednak wszystkie dodatkowe zasoby, które teraz wymagają aprowizacji i zarządzania nimi. W środowisku bezserwerowym kod może stać się nieskomplikowaną próbą skoordynowania z tymi zasobami ręcznie. Azure Functions oferuje alternatywę do tworzenia funkcji stanowych o nazwie Durable Functions.

Durable Functions to rozszerzenie środowiska uruchomieniowego Azure Functions, które umożliwia definiowanie stanowych przepływów pracy w kodzie. Dzieląc przepływy pracy na działania, rozszerzenie Durable Functions może zarządzać stanem, tworzyć punkty kontrolne postępu i obsługiwać dystrybucję wywołań funkcji między serwerami. W tle korzysta z konta usługi Azure Storage, aby utrzymać historię wykonywania, planować funkcje działania i odbierać odpowiedzi. Kod bezserwerowy nigdy nie powinien korzystać z utrwalonych informacji w ramach tego konta magazynu i zazwyczaj nie jest to coś, z którym deweloperzy muszą korzystać.

## <a name="triggering-a-stateful-workflow"></a>Wyzwalanie przepływu stanowego

Bezstanowe przepływy pracy w Durable Functions można podzielić na dwa składniki wewnętrzne; Wyzwalacze aranżacji i działania. Wyzwalacze i powiązania są podstawowymi składnikami używanymi przez Azure Functions, aby umożliwić powiadamianie funkcji bezserwerowych w momencie uruchamiania, odbierania danych wejściowych i zwracania wyników.

### <a name="working-with-the-orchestration-client"></a>Praca z klientem aranżacji

Aranżacje są unikatowe w porównaniu z innymi stylami operacji wyzwalanych w Azure Functions. Durable Functions włącza wykonywanie funkcji, które mogą trwać kilka godzin, a nawet dni. Ten typ zachowania jest konieczny, aby można było sprawdzić stan uruchomionej aranżacji, zapobiegawczo przerwać lub wysyłać powiadomienia o zdarzeniach zewnętrznych.

W takich przypadkach rozszerzenie Durable Functions udostępnia `DurableOrchestrationClient` klasę, która pozwala na współdziałanie z funkcjami zorganizowanymi przez organizację. Dostęp do klienta aranżacji uzyskuje się za pomocą `OrchestrationClientAttribute` powiązania. Ogólnie rzecz biorąc, należy uwzględnić ten atrybut z innym typem wyzwalacza, takim `HttpTrigger` jak `ServiceBusTrigger`lub. Po wyzwoleniu funkcji źródłowej można użyć klienta aranżacji do uruchomienia funkcji programu Orchestrator.

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

### <a name="the-orchestrator-function"></a>Funkcja programu Orchestrator

Dodawanie adnotacji do funkcji z OrchestrationTriggerAttribute w Azure Functions oznacza, że działa jako funkcja programu Orchestrator. Jest on odpowiedzialny za zarządzanie różnymi działaniami, które tworzą swój stanowy przepływ pracy.

Funkcje programu Orchestrator nie mogą używać powiązań innych niż OrchestrationTriggerAttribute. Tego atrybutu można używać tylko z typem parametru DurableOrchestrationContext. Nie można używać innych danych wejściowych, ponieważ deserializacja wejść w sygnaturze funkcji nie jest obsługiwana. Aby uzyskać dane wejściowe dostarczone przez klienta aranżacji, należy użyć metody\<getinput T\> .

Ponadto zwracane typy funkcji aranżacji muszą mieć wartość void, Task lub można serializować wartości JSON.

> *Kod obsługi błędu został pozostawiony dla zwięzłości*

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

Wiele wystąpień aranżacji można uruchomić i uruchomić w tym samym czasie. `StartNewAsync` Wywołanie metody`DurableOrchestrationClient` na uruchamia nowe wystąpienie aranżacji. Metoda zwraca `Task<string>` , która kończy się po rozpoczęciu aranżacji. Wyjątek typu `TimeoutException` jest zgłaszany, jeśli aranżacja nie została uruchomiona w ciągu 30 sekund.

Wykonany `Task<string>` z`StartNewAsync` powinien zawierać unikatowy identyfikator wystąpienia aranżacji. Tego identyfikatora wystąpienia można użyć do wywołania operacji dla danej aranżacji. W ramach aranżacji można wykonywać zapytania dotyczące stanu lub powiadomień o zdarzeniach wysłanych.

### <a name="the-activity-functions"></a>Funkcje działania

Funkcje działania to dyskretne operacje, które są tworzone razem w ramach funkcji aranżacji w celu utworzenia przepływu pracy. Oto miejsce, w którym ma miejsce najwięcej rzeczywistej pracy. Reprezentują one logikę biznesową, długotrwałe procesy i elementy układanki do większych rozwiązań.

Służy do dodawania adnotacji do parametru funkcji typu `DurableActivityContext`. `ActivityTriggerAttribute` Użycie adnotacji informuje środowisko uruchomieniowe, że funkcja jest przeznaczona do użycia jako funkcja działania. Wartości wejściowe do funkcji działania są pobierane przy użyciu `GetInput<T>` metody `DurableActivityContext` parametru.

Podobnie jak w przypadku funkcji aranżacji, zwracane typy funkcji działania muszą być typu void, Task lub wartości możliwy do serializacji JSON.

Wszystkie Nieobsłużone wyjątki, które są zgłaszane w ramach funkcji działania, będą wysyłane do wywoływania funkcji programu Orchestrator i prezentowane `TaskFailedException`jako. W tym momencie błąd może zostać przechwycony i zarejestrowany w programie Orchestrator, a działanie może być ponowione.

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

* [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Powiązania dla Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Zarządzanie wystąpieniami w Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Poprzedni](event-grid.md)Następny
>[](orchestration-patterns.md)
