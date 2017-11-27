---
title: Buforowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7e893a48e590f2b8a2ada88662cf454dc7881e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pooling"></a><span data-ttu-id="ee450-102">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="ee450-102">Pooling</span></span>
<span data-ttu-id="ee450-103">W tym przykładzie pokazano, jak rozszerzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] do obsługi buforowanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="ee450-103">This sample demonstrates how to extend [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to support object pooling.</span></span> <span data-ttu-id="ee450-104">Przykład przedstawia sposób tworzenia atrybutu składnię i semantycznie podobny do `ObjectPoolingAttribute` atrybutu funkcji usług dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="ee450-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="ee450-105">Buforowanie obiektu może zapewnić znaczne zwiększenie wydajności na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee450-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="ee450-106">Jednak jeśli nie jest prawidłowo używana może mieć odwrotny efekt.</span><span class="sxs-lookup"><span data-stu-id="ee450-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="ee450-107">Buforowanie obiektu pomaga zmniejszyć koszty odtworzenie często używanych obiektów, które wymagają szeroką gamę inicjowania.</span><span class="sxs-lookup"><span data-stu-id="ee450-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="ee450-108">Jednak jeśli wywołanie do metody w obiekcie puli przyjmuje znaczną ilość czasu, buforowanie obiektów kolejek dodatkowych żądań zaraz po osiągnięciu maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="ee450-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="ee450-109">W związku z tym może nie obsługiwać niektórych obiektów żądania tworzenia przez zgłaszanie wyjątków przekroczenia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="ee450-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee450-110">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ee450-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee450-111">Pierwszym krokiem tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzenia jest określenie punkcie rozszerzenia do użycia.</span><span class="sxs-lookup"><span data-stu-id="ee450-111">The first step in creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="ee450-112">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] termin *dyspozytora* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołań metod w usłudze użytkownika i konwertowania wartości zwracanych z tej metody wychodzący Komunikat.</span><span class="sxs-lookup"><span data-stu-id="ee450-112">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="ee450-113">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa tworzy dyspozytora dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-113">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="ee450-114">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, należy użyć dyspozytora kontrakt skojarzony z tego klienta jest kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-114">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="ee450-115">Dystrybucja kanału i punktu końcowego oferują kanału- i rozszerzalność całej kontraktu w przypadku wystawianego różne właściwości, które określają zachowanie Dyspozytor.</span><span class="sxs-lookup"><span data-stu-id="ee450-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="ee450-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Właściwości umożliwia również sprawdzać, zmodyfikować lub dostosowania procesu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="ee450-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="ee450-117">W tym przykładzie koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość, która wskazuje obiekt, który zapewnia wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="ee450-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="ee450-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="ee450-119">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Dyspozytor tworzy wystąpienia przy użyciu klasy usługi <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee450-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="ee450-120">Ten interfejs zawiera trzy metody:</span><span class="sxs-lookup"><span data-stu-id="ee450-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="ee450-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Podczas wywołania dyspozytora nadejścia wiadomości <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę w celu utworzenia wystąpienia klasy usługi, aby przetworzyć komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ee450-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="ee450-122">Częstotliwość połączeń do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee450-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="ee450-123">Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi służy do przetwarzania każdy komunikat przychodzący, dlatego <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana w momencie nadejścia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee450-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="ee450-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest taki sam jak poprzednie metody, z wyjątkiem to wywoływane, gdy istnieje żaden argument komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ee450-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="ee450-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Gdy upłynął okres istnienia wystąpienie usługi, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody.</span><span class="sxs-lookup"><span data-stu-id="ee450-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="ee450-126">Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, częstotliwość wywołania do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee450-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="ee450-127">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="ee450-127">The Object Pool</span></span>  
 <span data-ttu-id="ee450-128">Niestandardowy <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementacja udostępnia wymaganego obiektu buforowanie semantyki dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="ee450-129">Ten przykład ma `ObjectPoolingInstanceProvider` typu, który udostępnia implementację niestandardowych <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do umieszczenia w puli.</span><span class="sxs-lookup"><span data-stu-id="ee450-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="ee450-130">Gdy `Dispatcher` wywołania <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, zamiast tworzyć nowe wystąpienie implementacji niestandardowych szuka istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ee450-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="ee450-131">Jeśli jest dostępny, jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="ee450-131">If one is available, it is returned.</span></span> <span data-ttu-id="ee450-132">W przeciwnym razie jest tworzony nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="ee450-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="ee450-133">Implementację `GetInstance` jest wyświetlany w następujący przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="ee450-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;            
}  
```  
  
 <span data-ttu-id="ee450-134">Niestandardowa `ReleaseInstance` implementacji dodaje Zwolniono wystąpienie puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="ee450-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="ee450-135">`Dispatcher` Można wywołać metody te z różnych wątkach i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolingInstanceProvider` klasa jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="ee450-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests   
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();                       
    }  
}  
```  
  
 <span data-ttu-id="ee450-136">`ReleaseInstance` Metoda zawiera funkcję "oczyszczania inicjowania".</span><span class="sxs-lookup"><span data-stu-id="ee450-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="ee450-137">Zwykle puli obsługuje minimalną liczbę obiektów, dla okresu istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="ee450-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="ee450-138">Jednak może być okresów nadmiernego użycia, które wymaga tworzenia dodatkowe obiekty w puli do osiągnięcia maksymalnego limitu określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee450-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="ee450-139">Po pewnym czasie gdy puli staje się mniej aktywne, te pozostałe obiekty mogą stać się dodatkowego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="ee450-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="ee450-140">W związku z tym, kiedy `activeObjectsCount` osiągnie zero, czasomierza bezczynności została uruchomiona, który wyzwala i wykonuje cyklu czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="ee450-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="ee450-141">Dodawanie zachowania</span><span class="sxs-lookup"><span data-stu-id="ee450-141">Adding the Behavior</span></span>  
 <span data-ttu-id="ee450-142">Rozszerzenia warstwie dyspozytora są podłączonymi przy użyciu następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="ee450-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="ee450-143">Zachowania usług.</span><span class="sxs-lookup"><span data-stu-id="ee450-143">Service Behaviors.</span></span> <span data-ttu-id="ee450-144">Umożliwiają one dostosowywania środowiska uruchomieniowego całej usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="ee450-145">Zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-145">Endpoint Behaviors.</span></span> <span data-ttu-id="ee450-146">Umożliwiają one dostosowywania punktów końcowych usługi, w szczególności kanału i Dyspozytor punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="ee450-147">Zachowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ee450-147">Contract Behaviors.</span></span> <span data-ttu-id="ee450-148">Umożliwiają one dostosowywania, zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy odpowiednio na kliencie i usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="ee450-149">Na potrzeby buforowania rozszerzenie obiektu można utworzyć zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="ee450-150">Zachowania usług są tworzone z zastosowaniem <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee450-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="ee450-151">Istnieje kilka sposobów uświadomić modelu usług niestandardowych zachowania:</span><span class="sxs-lookup"><span data-stu-id="ee450-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="ee450-152">Przy użyciu atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="ee450-153">Imperatively dodanie go do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="ee450-154">Rozszerzenie pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee450-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="ee450-155">W przykładzie użyto atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ee450-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="ee450-156">Gdy <xref:System.ServiceModel.ServiceHost> jest tworzony poszczególne atrybuty, są używane w definicji typu usługi i dodaje zachowania dostępne do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="ee450-157">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody w-- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee450-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="ee450-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda służy do zapewnienia, że zachowanie może odnosić się do usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="ee450-159">W tym przykładzie wdrożenia gwarantuje, że usługa nie jest skonfigurowany z <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="ee450-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="ee450-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania powiązań usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="ee450-161">Nie jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="ee450-161">It is not required in this scenario.</span></span> <span data-ttu-id="ee450-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Służy do konfigurowania usługi dyspozytorów.</span><span class="sxs-lookup"><span data-stu-id="ee450-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="ee450-163">Ta metoda jest wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany.</span><span class="sxs-lookup"><span data-stu-id="ee450-163">This method is called by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="ee450-164">Następujące parametry są przekazywane do tej metody:</span><span class="sxs-lookup"><span data-stu-id="ee450-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="ee450-165">`Description`: Ten argument zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="ee450-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="ee450-166">Może być używany do zbadania opis danych dotyczących punktów końcowych usługi, kontrakty, powiązania i innych danych.</span><span class="sxs-lookup"><span data-stu-id="ee450-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="ee450-167">`ServiceHostBase`: Ten argument zawiera <xref:System.ServiceModel.ServiceHostBase> który jest obecnie inicjowany.</span><span class="sxs-lookup"><span data-stu-id="ee450-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="ee450-168">W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji nowe wystąpienie elementu `ObjectPoolingInstanceProvider` to wystąpienie zostało utworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w obiektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="ee450-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,   
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior   
    // (this.throttlingBehavior==null), it should have initialized   
    // a single ServiceThrottle on all ChannelDispatchers.    
    // As we loop through the ChannelDispatchers, we verify that   
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in   
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all   
            // endpoints. If there were others, we could not enforce   
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&   
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
                if (cd.ServiceThrottle == null)  
                {  
                    throw new   
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =   
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items   
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >   
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="ee450-169">Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka elementów członkowskich, aby dostosować puli obiektów przy użyciu argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee450-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="ee450-170">Elementy te obejmują <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpowiadać obiektowi buforowanie zestaw funkcji udostępniane przez usługi .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="ee450-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="ee450-171">Obiekt, buforowanie zachowanie można teraz dodać do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przez dodawanie adnotacji do implementacji usługi z nowo utworzonych niestandardowych `ObjectPooling` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee450-171">The object pooling behavior can now be added to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="ee450-172">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="ee450-172">Running the Sample</span></span>  
 <span data-ttu-id="ee450-173">W przykładzie pokazano zwiększenia wydajności, które mogą zostać uzyskane przy użyciu buforowanie obiektów w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="ee450-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="ee450-174">Aplikacja usługi implementuje dwóch usług — `WorkService` i `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="ee450-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="ee450-175">Zarówno usługi Udostępnianie tego samego wykonania — one zarówno wymagają inicjalizacji kosztowne i następnie uwidaczniaj `DoWork()` metody względnie niedrogie.</span><span class="sxs-lookup"><span data-stu-id="ee450-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="ee450-176">Jedyną różnicą jest to, że `ObjectPooledWorkService` ma skonfigurowany buforowanie obiektów:</span><span class="sxs-lookup"><span data-stu-id="ee450-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }          
}  
```  
  
 <span data-ttu-id="ee450-177">Po uruchomieniu klienta upłynie wywołania `WorkService` 5 razy.</span><span class="sxs-lookup"><span data-stu-id="ee450-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="ee450-178">Następnie czasu wywołania `ObjectPooledWorkService` 5 razy.</span><span class="sxs-lookup"><span data-stu-id="ee450-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="ee450-179">Różnica czasu są następnie wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="ee450-179">The difference in time is then displayed:</span></span>  
  
```  
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
>  <span data-ttu-id="ee450-180">Klient jest uruchamiany po raz pierwszy obie te usługi są wyświetlane podjęcie o tej samej ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="ee450-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="ee450-181">Jeśli ponownie uruchomić przykład, można stwierdzić, że `ObjectPooledWorkService` zwraca znacznie szybsza, ponieważ istnieje już wystąpienie tego obiektu w puli.</span><span class="sxs-lookup"><span data-stu-id="ee450-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee450-182">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ee450-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee450-183">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee450-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ee450-184">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee450-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ee450-185">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee450-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee450-186">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="ee450-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee450-187">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee450-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee450-188">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ee450-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee450-189">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ee450-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee450-190">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee450-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a><span data-ttu-id="ee450-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee450-191">See Also</span></span>
