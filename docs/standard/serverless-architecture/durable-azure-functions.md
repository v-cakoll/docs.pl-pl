---
title: Trwałe funkcje platformy Azure — aplikacje niekorzystające z serwera
description: Niezawodne usługi Azure functions rozszerza środowisko uruchomieniowe usługi Azure Functions umożliwia stanowych przepływów pracy w kodzie.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147310"
---
# <a name="durable-azure-functions"></a>Trwałe funkcje platformy Azure

Podczas tworzenia aplikacji bez użycia serwera za pomocą usługi Azure Functions, zwykle być zaprojektowane operacje będą uruchamiane w sposób bezstanowe. Przyczyna tego uzasadnienie wyboru tych elementów jest, ponieważ jako skale platformy trudno wiedzieć, jakie serwery, wykonywany jest kod. Również trudno wiedzieć, ile wystąpień są aktywne w dowolnym danym momencie. Istnieją jednak klasy aplikacji, które wymagają bieżący stan procesu, żeby Cię widziano. Należy wziąć pod uwagę proces przesyłania zamówienia do sklepu internetowego. Operacja wyewidencjonowania może być przepływ pracy, który składa się z wielu operacji, które trzeba znać stan procesu. Takie informacje mogą obejmować spis produktów, jeśli odbiorca nie ma żadnych środków na swoje konto, a także wyniki przetwarzania danych karty kredytowej. Te operacje można łatwo własne wewnętrzne przepływy pracy lub nawet usługi z systemami innych firm.

Różnych wzorców istnieje już dziś tego asysta przy użyciu koordynacji stan aplikacji między systemami wewnętrznymi i zewnętrznymi. Są często się spotkać się z rozwiązania, które polegają na tych systemach kolejkowania, rozproszonych klucz wartość magazynów lub udostępnionych baz danych służący do zarządzania nim. Są one jednak wszystkie dodatkowe zasoby, które teraz muszą być udostępniana i zarządzana. W środowisku bezserwerowym Twój kod może stać się skomplikowane, próby ręcznie skontaktować się z tymi zasobami. Usługa Azure Functions oferuje alternatywą dla tworzenia stanowych funkcji o nazwie funkcje trwałe.

Funkcje trwałe to rozszerzenie do środowiska uruchomieniowego usługi Azure Functions, umożliwiająca definicji stanowych przepływów pracy w kodzie. Dzieląc przepływy pracy do działań, rozszerzenia funkcji trwałych można Zarządzanie stanem, tworzyć punkty kontrolne w toku i obsługiwać dystrybucji wywołania funkcji na serwerach. W tle ułatwia korzystanie z konta usługi Azure Storage w celu utrwalanie historii wykonywania, zaplanować działania funkcji i pobrać odpowiedzi. Kod bez użycia serwera nigdy nie powinny korzystać z utrwalonych danych na tym koncie magazynu i zazwyczaj nie jest coś, z którym deweloperzy muszą wchodzić w interakcje.

## <a name="triggering-a-stateful-workflow"></a>Wyzwalanie stanowych przepływu pracy

Stanowe przepływów pracy w programie trwałe funkcje można podzielić na dwa składniki wewnętrzne; Wyzwalacze aranżacji i działania. Wyzwalacze i powiązania są podstawowe składniki używane przez usługi Azure Functions umożliwia swoje funkcje niewymagające użycia serwera otrzymywać powiadomienia, aby rozpocząć odbieranie danych wejściowych, gdy zwrócenia wyników.

### <a name="working-with-the-orchestration-client"></a>Korzystanie z klienckiego aranżacji

Aranżacji są unikatowe, w porównaniu z innymi stylami wyzwolone operacje w usłudze Azure Functions. Funkcje trwałe umożliwia wykonanie funkcji, które może potrwać do godziny, a nawet dni. Tego rodzaju zachowanie jest dostarczany z potrzebami, aby było możliwe sprawdzić stan uruchomionych aranżacji, Zakończ prewencyjnego lub wysyłać powiadomienia o zdarzenia zewnętrzne.

W takich przypadkach udostępnia rozszerzenia funkcji trwałych `DurableOrchestrationClient` klasy, która pozwala na interakcję z zorganizowanych funkcji. Uzyskaj dostęp do aranżacji klienta przy użyciu `OrchestrationClientAttribute` powiązania. Ogólnie rzecz biorąc, należy dołączyć ten atrybut z innym typem wyzwalacza, takich jak `HttpTrigger` lub `ServiceBusTrigger`. Po wyzwoleniu funkcji źródła klient orkiestracji można uruchomić funkcję orkiestratora.

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

### <a name="the-orchestrator-function"></a>Funkcja programu orchestrator

Dodawanie adnotacji do funkcji z OrchestrationTriggerAttribute znakami usługi Azure Functions w tej funkcji jako funkcję orkiestratora. Jest odpowiedzialny za zarządzanie różnych działań, które tworzą stanowych przepływu pracy.

Funkcje programu orchestrator nie są w stanie się korzystanie z powiązania innych niż OrchestrationTriggerAttribute. Ten atrybut można używać tylko z typem parametru DurableOrchestrationContext. Brak danych wejściowych może służyć ponieważ deserializacji danych wejściowych w sygnaturze funkcji nie jest obsługiwana. Można pobrać danych wejściowych dostarczonych przez klienta aranżacji, GetInput\<T\> metoda musi być używana.

Ponadto zwracane typy funkcji aranżacji musi mieć wartość void, zadania lub wartość serializacji JSON.

> *Został pozostawiono kodu obsługi błędów w celu skrócenia programu*

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

Wiele wystąpień aranżacji może być uruchomione w tym samym czasie. Wywoływanie `StartNewAsync` metody `DurableOrchestrationClient` uruchamia nowe wystąpienie klasy aranżacji. Metoda ta zwraca `Task<string>` który zostaje ukończony po aranżacji została uruchomiona. Wystąpił wyjątek typu `TimeoutException` pobiera wygenerowany, jeśli organizacja nie zostało rozpoczęte w ciągu 30 sekund.

Gotowy `Task<string>` z `StartNewAsync` powinien zawierać unikatowy identyfikator wystąpienia aranżacji. Ten identyfikator wystąpienia może służyć do wywołania operacji na tym określonym aranżacji. Orchestration można badane stanu lub wysyłane powiadomienia o zdarzeniach.

### <a name="the-activity-functions"></a>Funkcje działań

Działanie funkcji są osobne operacje, które Pobierz składa się ze sobą w ramach funkcji aranżacji w taki sposób, aby utworzyć przepływ pracy. Poniżej przedstawiono, gdzie większość rzeczywista praca będzie mieć miejsce. Które reprezentują logikę biznesową, długie, uruchomione procesy i części logiczne, aby większe rozwiązania.

`ActivityTriggerAttribute` Służy do dodawania adnotacji typu parametru funkcji `DurableActivityContext`. Przy użyciu adnotacji informuje środowisko uruchomieniowe, funkcja jest przeznaczona do użycia jako funkcja działania. Wartości wejściowe dla funkcji działań są pobierane przy użyciu `GetInput<T>` metody `DurableActivityContext` parametru.

Podobnie jak w funkcji aranżacji, typów zwracanych elementów funkcje działań musi mieć wartość void, zadania lub wartość serializacji JSON.

Nieobsłużone wyjątki, które Pobierz zgłoszone w ramach działania funkcji spowoduje pobieranie przesłane do wywoływania funkcji programu orchestrator i przedstawiane jako `TaskFailedException`. W tym momencie błędu można przechwytywane i rejestrowane w programie orchestrator i mogą być ponawiane działania.

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

* [Trwałe funkcje](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Powiązania trwałe funkcje](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Zarządzanie wystąpieniami w funkcje trwałe](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Poprzednie](event-grid.md)
>[dalej](orchestration-patterns.md)