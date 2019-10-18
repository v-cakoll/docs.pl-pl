---
title: Trwałe funkcje platformy Azure — aplikacje bezserwerowe
description: Trwałe funkcje platformy Azure zwiększają środowisko uruchomieniowe Azure Functions, aby umożliwić stanowe przepływy pracy w kodzie.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522863"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="bbb4c-103">Trwałe funkcje platformy Azure</span><span class="sxs-lookup"><span data-stu-id="bbb4c-103">Durable Azure functions</span></span>

<span data-ttu-id="bbb4c-104">Podczas tworzenia aplikacji bezserwerowych z Azure Functions operacje są zwykle przeznaczone do uruchamiania w sposób bezstanowy.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="bbb4c-105">Przyczyną tego wyboru jest to, że w miarę skalowania platformy trudno jest wiedzieć, na których serwerach jest uruchomiony kod.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="bbb4c-106">Trudno jest również wiedzieć, ile wystąpień jest aktywnych w danym punkcie.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="bbb4c-107">Istnieją jednak klasy aplikacji, które wymagają znanego stanu procesu.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="bbb4c-108">Weź pod uwagę proces przesyłania zamówienia do sklepu online.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="bbb4c-109">Operacja wyewidencjonowywania może być przepływem pracy, który składa się z wielu operacji, które muszą znać stan procesu.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="bbb4c-110">Takie informacje mogą obejmować spis produktów, jeśli klient ma jakiekolwiek środki na swoje konto, a także wyniki przetwarzania karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="bbb4c-111">Te operacje mogą łatwo być własnymi wewnętrznymi przepływami pracy lub nawet usługami z systemów innych firm.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="bbb4c-112">Istnieją różne wzorce, które pomagają w koordynacji stanu aplikacji między systemami wewnętrznymi i zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="bbb4c-113">Często są one dostępne w różnych rozwiązaniach, które polegają na scentralizowanych systemach kolejkowania, rozproszonych magazynach wartości klucza lub udostępnionych bazach danych w celu zarządzania tym stanem.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="bbb4c-114">Są to jednak wszystkie dodatkowe zasoby, które teraz wymagają aprowizacji i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="bbb4c-115">W środowisku bezserwerowym kod może stać się nieskomplikowaną próbą skoordynowania z tymi zasobami ręcznie.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="bbb4c-116">Azure Functions oferuje alternatywę do tworzenia funkcji stanowych o nazwie Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="bbb4c-117">Durable Functions to rozszerzenie środowiska uruchomieniowego Azure Functions, które umożliwia definiowanie stanowych przepływów pracy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="bbb4c-118">Dzieląc przepływy pracy na działania, rozszerzenie Durable Functions może zarządzać stanem, tworzyć punkty kontrolne postępu i obsługiwać dystrybucję wywołań funkcji między serwerami.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="bbb4c-119">W tle korzysta z konta usługi Azure Storage, aby utrzymać historię wykonywania, planować funkcje działania i odbierać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="bbb4c-120">Kod bezserwerowy nigdy nie powinien korzystać z utrwalonych informacji w ramach tego konta magazynu i zazwyczaj nie jest to coś, z którym deweloperzy muszą korzystać.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="bbb4c-121">Wyzwalanie przepływu stanowego</span><span class="sxs-lookup"><span data-stu-id="bbb4c-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="bbb4c-122">Bezstanowe przepływy pracy w Durable Functions można podzielić na dwa składniki wewnętrzne; Wyzwalacze aranżacji i działania.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="bbb4c-123">Wyzwalacze i powiązania są podstawowymi składnikami używanymi przez Azure Functions, aby umożliwić powiadamianie funkcji bezserwerowych w momencie uruchamiania, odbierania danych wejściowych i zwracania wyników.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="bbb4c-124">Praca z klientem aranżacji</span><span class="sxs-lookup"><span data-stu-id="bbb4c-124">Working with the Orchestration client</span></span>

<span data-ttu-id="bbb4c-125">Aranżacje są unikatowe w porównaniu z innymi stylami operacji wyzwalanych w Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="bbb4c-126">Durable Functions włącza wykonywanie funkcji, które mogą trwać kilka godzin, a nawet dni.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="bbb4c-127">Ten typ zachowania jest konieczny, aby można było sprawdzić stan uruchomionej aranżacji, zapobiegawczo przerwać lub wysyłać powiadomienia o zdarzeniach zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="bbb4c-128">W takich przypadkach rozszerzenie Durable Functions udostępnia klasę `DurableOrchestrationClient`, która pozwala na współdziałanie z funkcjami zorganizowanymi przez organizację.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="bbb4c-129">Dostęp do klienta aranżacji uzyskuje się za pomocą powiązania `OrchestrationClientAttribute`.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="bbb4c-130">Ogólnie rzecz biorąc, należy uwzględnić ten atrybut z innym typem wyzwalacza, takim jak `HttpTrigger` lub `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="bbb4c-131">Po wyzwoleniu funkcji źródłowej można użyć klienta aranżacji do uruchomienia funkcji programu Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="bbb4c-132">Funkcja programu Orchestrator</span><span class="sxs-lookup"><span data-stu-id="bbb4c-132">The orchestrator function</span></span>

<span data-ttu-id="bbb4c-133">Dodawanie adnotacji do funkcji z OrchestrationTriggerAttribute w Azure Functions oznacza, że działa jako funkcja programu Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="bbb4c-134">Jest on odpowiedzialny za zarządzanie różnymi działaniami, które tworzą swój stanowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="bbb4c-135">Funkcje programu Orchestrator nie mogą używać powiązań innych niż OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="bbb4c-136">Tego atrybutu można używać tylko z typem parametru DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="bbb4c-137">Nie można używać innych danych wejściowych, ponieważ deserializacja wejść w sygnaturze funkcji nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="bbb4c-138">Aby uzyskać dane wejściowe dostarczone przez klienta aranżacji, należy użyć metody getinput \<T \>.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="bbb4c-139">Ponadto zwracane typy funkcji aranżacji muszą mieć wartość void, Task lub można serializować wartości JSON.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="bbb4c-140">*Kod obsługi błędu został pozostawiony dla zwięzłości*</span><span class="sxs-lookup"><span data-stu-id="bbb4c-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="bbb4c-141">Wiele wystąpień aranżacji można uruchomić i uruchomić w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="bbb4c-142">Wywołanie metody `StartNewAsync` na `DurableOrchestrationClient` uruchamia nowe wystąpienie aranżacji.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="bbb4c-143">Metoda zwraca `Task<string>`, która kończy się po rozpoczęciu aranżacji.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="bbb4c-144">Wyjątek typu `TimeoutException` jest zgłaszany, jeśli aranżacja nie została uruchomiona w ciągu 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="bbb4c-145">Ukończony `Task<string>` od `StartNewAsync` powinien zawierać unikatowy identyfikator wystąpienia aranżacji.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="bbb4c-146">Tego identyfikatora wystąpienia można użyć do wywołania operacji dla danej aranżacji.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="bbb4c-147">W ramach aranżacji można wykonywać zapytania dotyczące stanu lub powiadomień o zdarzeniach wysłanych.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="bbb4c-148">Funkcje działania</span><span class="sxs-lookup"><span data-stu-id="bbb4c-148">The activity functions</span></span>

<span data-ttu-id="bbb4c-149">Funkcje działania to dyskretne operacje, które są tworzone razem w ramach funkcji aranżacji w celu utworzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="bbb4c-150">Oto miejsce, w którym ma miejsce najwięcej rzeczywistej pracy.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="bbb4c-151">Reprezentują one logikę biznesową, długotrwałe procesy i elementy układanki do większych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="bbb4c-152">@No__t_0 jest używany do dodawania adnotacji do parametru funkcji typu `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="bbb4c-153">Użycie adnotacji informuje środowisko uruchomieniowe, że funkcja jest przeznaczona do użycia jako funkcja działania.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="bbb4c-154">Wartości wejściowe do funkcji działania są pobierane przy użyciu metody `GetInput<T>` parametru `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="bbb4c-155">Podobnie jak w przypadku funkcji aranżacji, zwracane typy funkcji działania muszą być typu void, Task lub wartości możliwy do serializacji JSON.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="bbb4c-156">Wszystkie Nieobsłużone wyjątki, które są zgłaszane w ramach funkcji działania, będą wysyłane do wywoływania funkcji programu Orchestrator i prezentowane jako `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="bbb4c-157">W tym momencie błąd może zostać przechwycony i zarejestrowany w programie Orchestrator, a działanie może być ponowione.</span><span class="sxs-lookup"><span data-stu-id="bbb4c-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="bbb4c-158">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="bbb4c-158">Recommended resources</span></span>

- [<span data-ttu-id="bbb4c-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="bbb4c-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="bbb4c-160">Powiązania dla Durable Functions</span><span class="sxs-lookup"><span data-stu-id="bbb4c-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="bbb4c-161">Zarządzanie wystąpieniami w Durable Functions</span><span class="sxs-lookup"><span data-stu-id="bbb4c-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="bbb4c-162">[Poprzedni](event-grid.md)
>[Następny](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4c-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
