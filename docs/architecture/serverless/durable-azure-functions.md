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
# <a name="durable-azure-functions"></a><span data-ttu-id="b0dd6-103">Trwałe funkcje platformy Azure</span><span class="sxs-lookup"><span data-stu-id="b0dd6-103">Durable Azure functions</span></span>

<span data-ttu-id="b0dd6-104">Podczas tworzenia aplikacji bezserwerowych za pomocą funkcji Azure, operacje będą zazwyczaj przeznaczone do uruchamiania w sposób bezstanowy.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="b0dd6-105">Powodem tego wyboru projektu jest, ponieważ w miarę skalowania platformy trudno jest wiedzieć, na jakich serwerach jest uruchomiony kod.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="b0dd6-106">Trudno jest również wiedzieć, ile wystąpień jest aktywnych w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="b0dd6-107">Istnieją jednak klasy aplikacji, które wymagają bieżącego stanu procesu, które mają być znane.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="b0dd6-108">Rozważmy proces składania zamówienia do sklepu internetowego.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="b0dd6-109">Operacja realizacji transakcji może być przepływem pracy, który składa się z wielu operacji, które muszą znać stan procesu.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="b0dd6-110">Takie informacje mogą obejmować spis produktów, jeśli klient ma jakiekolwiek środki na swoim koncie, a także wyniki przetwarzania karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="b0dd6-111">Operacje te mogą być ich własnymi wewnętrznymi przepływami pracy, a nawet usługami z systemów innych firm.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="b0dd6-112">Istnieją dziś różne wzorce, które pomagają w koordynacji stanu aplikacji między systemami wewnętrznymi i zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="b0dd6-113">Często można natknąć się na rozwiązania, które opierają się na scentralizowanych systemach kolejkowania, rozproszonych magazynach o wartości klucza lub udostępnionych bazach danych w celu zarządzania tym stanem.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="b0dd6-114">Są to jednak wszystkie dodatkowe zasoby, które teraz muszą być aprowizowane i zarządzane.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="b0dd6-115">W środowisku bezserwerowym kod może stać się kłopotliwe próbuje koordynować z tych zasobów ręcznie.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="b0dd6-116">Usługa Azure Functions oferuje alternatywę dla tworzenia funkcji stanowych o nazwie trwałe funkcje.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="b0dd6-117">Funkcje trwałe jest rozszerzeniem do działania funkcji azure, który umożliwia definiowanie stanowych przepływów pracy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="b0dd6-118">Poprzez podział przepływów pracy na działania, trwałe funkcje rozszerzenie można zarządzać stanem, tworzenie punktów kontrolnych postępu i obsługiwać dystrybucję wywołań funkcji między serwerami.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="b0dd6-119">W tle korzysta z konta usługi Azure Storage, aby utrwalić historię wykonywania, zaplanować funkcje działania i pobrać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="b0dd6-120">Twój kod bezserwerowy nigdy nie powinien wchodzić w interakcje z utrwaonymi informacjami na tym koncie magazynu i zazwyczaj nie jest czymś, z czym deweloperzy muszą wchodzić w interakcje.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="b0dd6-121">Wyzwalanie stanowego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b0dd6-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="b0dd6-122">Stateful przepływów pracy w funkcji trwałe można podzielić na dwa składniki wewnętrzne; wyzwalaczy aranżacji i aktywności.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="b0dd6-123">Wyzwalacze i powiązania są podstawowymi składnikami używanymi przez usługi Azure Functions, aby umożliwić funkcje bezserwerowe, które mają być powiadamiane o uruchomieniu, odebraniu danych wejściowych i zwrocie wyników.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="b0dd6-124">Praca z klientem Aranżacji</span><span class="sxs-lookup"><span data-stu-id="b0dd6-124">Working with the Orchestration client</span></span>

<span data-ttu-id="b0dd6-125">Aranżacje są unikatowe w porównaniu do innych stylów wyzwalanych operacji w usłudze Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="b0dd6-126">Trwałe funkcje umożliwia wykonywanie funkcji, które mogą potrwać wiele godzin lub nawet dni, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="b0dd6-127">Ten typ zachowania pochodzi z konieczności sprawdzania stanu uruchomionej aranżacji, prewencyjnie zakończyć lub wysłać powiadomienia o zdarzeniach zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="b0dd6-128">W takich przypadkach trwałe funkcje `DurableOrchestrationClient` rozszerzenie zapewnia klasę, która umożliwia interakcję z funkcji zaaranżowanych.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="b0dd6-129">Otrzymasz dostęp do klienta aranżacji przy użyciu `OrchestrationClientAttribute` powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="b0dd6-130">Ogólnie rzecz biorąc, należy dołączyć ten atrybut z `HttpTrigger` `ServiceBusTrigger`innym typem wyzwalacza, takich jak lub .</span><span class="sxs-lookup"><span data-stu-id="b0dd6-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="b0dd6-131">Po wyzwoleniu funkcji źródłowej klient aranżacji może służyć do uruchamiania funkcji koordynatora.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="b0dd6-132">Funkcja koordynatora</span><span class="sxs-lookup"><span data-stu-id="b0dd6-132">The orchestrator function</span></span>

<span data-ttu-id="b0dd6-133">Adnotacje funkcji z OrchestrationTriggerAttribute w funkcji platformy Azure znaków, które działają jako funkcja koordynatora.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="b0dd6-134">Jest odpowiedzialny za zarządzanie różnymi działaniami, które składają się na stanowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="b0dd6-135">Funkcje koordynatora nie można używać powiązań innych niż OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="b0dd6-136">Ten atrybut może służyć tylko z typem parametru DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="b0dd6-137">Żadne inne dane wejściowe nie mogą być używane, ponieważ deserializacja danych wejściowych w sygnaturze funkcji nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="b0dd6-138">Aby uzyskać dane wejściowe dostarczone przez klienta\<aranżacji, GetInput T\> metoda musi być używany.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="b0dd6-139">Ponadto zwracane typy funkcji aranżacji muszą być nieważne, zadanie lub wartość serializowalną JSON.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="b0dd6-140">*Kod obsługi błędów został pominięty dla zwięzłości*</span><span class="sxs-lookup"><span data-stu-id="b0dd6-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="b0dd6-141">Wiele wystąpień aranżacji można uruchomić i działa w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="b0dd6-142">Wywołanie `StartNewAsync` metody `DurableOrchestrationClient` na uruchamia nowe wystąpienie aranżacji.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="b0dd6-143">Metoda zwraca `Task<string>` a, który kończy się po rozpoczęciu aranżacji.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="b0dd6-144">Wyjątek typu `TimeoutException` zostanie wygenerowany, jeśli aranżacja nie została uruchomiona w ciągu 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="b0dd6-145">Ukończone `Task<string>` z `StartNewAsync` powinien zawierać unikatowy identyfikator wystąpienia aranżacji.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="b0dd6-146">Ten identyfikator wystąpienia może służyć do wywoływania operacji na tej konkretnej aranżacji.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="b0dd6-147">Aranżacja może być wyszukiwane dla stanu lub wysłane powiadomienia o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="b0dd6-148">Działanie działa</span><span class="sxs-lookup"><span data-stu-id="b0dd6-148">The activity functions</span></span>

<span data-ttu-id="b0dd6-149">Funkcje działania są dyskretne operacje, które są składane razem w ramach funkcji aranżacji, aby utworzyć przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="b0dd6-150">Oto, gdzie większość rzeczywistych prac odbędzie się.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="b0dd6-151">Reprezentują one logikę biznesową, długotrwałe procesy i elementy układanki do większego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="b0dd6-152">Służy `ActivityTriggerAttribute` do adnotatora parametru `DurableActivityContext`funkcji typu .</span><span class="sxs-lookup"><span data-stu-id="b0dd6-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="b0dd6-153">Za pomocą adnotacji informuje program runtime, że funkcja jest przeznaczona do użycia jako funkcja działania.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="b0dd6-154">Wartości wejściowe do funkcji działania `GetInput<T>` są pobierane `DurableActivityContext` przy użyciu metody parametru.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="b0dd6-155">Podobnie jak funkcje aranżacji, zwracane typy funkcji działania muszą być nieważne, zadanie lub wartość serializable JSON.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="b0dd6-156">Wszelkie nieobsługiwane wyjątki, które zostaną wygenerowane w ramach funkcji działania zostanie wysłana `TaskFailedException`do funkcji koordynatora wywołującego i przedstawione jako .</span><span class="sxs-lookup"><span data-stu-id="b0dd6-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="b0dd6-157">W tym momencie błąd można przechwycić i zalogować się w koordynatorze, a działanie można ponowić.</span><span class="sxs-lookup"><span data-stu-id="b0dd6-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="b0dd6-158">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="b0dd6-158">Recommended resources</span></span>

- [<span data-ttu-id="b0dd6-159">Trwałe funkcje</span><span class="sxs-lookup"><span data-stu-id="b0dd6-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="b0dd6-160">Wiązania dla trwałych funkcji</span><span class="sxs-lookup"><span data-stu-id="b0dd6-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="b0dd6-161">Zarządzanie wystąpieniami w trwałych funkcjach</span><span class="sxs-lookup"><span data-stu-id="b0dd6-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="b0dd6-162">[Poprzedni](event-grid.md)
>[następny](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="b0dd6-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
