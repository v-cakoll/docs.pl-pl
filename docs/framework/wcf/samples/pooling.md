---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 91fdb34a82446aab1528835132efd31e2858191c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832440"
---
# <a name="pooling"></a><span data-ttu-id="0b80e-102">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="0b80e-102">Pooling</span></span>
<span data-ttu-id="0b80e-103">Niniejszy przykład pokazuje, jak rozszerzyć Windows Communication Foundation (WCF) do obsługi buforowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="0b80e-104">W przykładzie pokazano, jak utworzyć atrybut, który przypomina składniowo i semantycznie `ObjectPoolingAttribute` atrybutu funkcjonalność usług dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="0b80e-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="0b80e-105">Buforowanie obiektu może zapewnić znaczne zwiększenie wydajności na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b80e-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="0b80e-106">Jednak jeśli nie jest poprawnie użyty może mieć odwrotny efekt.</span><span class="sxs-lookup"><span data-stu-id="0b80e-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="0b80e-107">Buforowanie obiektu pomaga zmniejszyć koszty ponowne utworzenie często używanych obiektów, które wymagają rozbudowane inicjowania.</span><span class="sxs-lookup"><span data-stu-id="0b80e-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="0b80e-108">Jednak jeśli wywołanie metody do obiektu puli zajmuje znaczną ilość czasu na ukończenie, buforowanie obiektu kolejki dodatkowych żądań tak szybko, jak Osiągnięto maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="0b80e-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="0b80e-109">Ten sposób może nie obsługiwać żądania tworzenia obiektu zgłaszając wyjątek limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b80e-110">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0b80e-111">Pierwszym krokiem w tworzeniu rozszerzenia WCF jest podjęcie decyzji, punkt rozszerzeń do użycia.</span><span class="sxs-lookup"><span data-stu-id="0b80e-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="0b80e-112">W programie WCF termin *dyspozytora* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołania metody usługi przez użytkownika i konwertowania wartości zwracane z tej metody do wysyłanej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b80e-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="0b80e-113">Usługa WCF tworzy dyspozytora dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="0b80e-114">Klienta programu WCF, należy użyć dyspozytora, jeśli kontrakt skojarzony z tego klienta jest kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="0b80e-115">Dyspozytorów kanału i punktu końcowego oferują kanału — i rozszerzalność całej kontraktu, zapewniając różne właściwości, które kontrolują zachowanie Dyspozytor.</span><span class="sxs-lookup"><span data-stu-id="0b80e-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="0b80e-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Właściwość umożliwia również sprawdzić, zmodyfikować lub dostosować proces wysyłania.</span><span class="sxs-lookup"><span data-stu-id="0b80e-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="0b80e-117">Ten przykład koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości, który wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="0b80e-118">The IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="0b80e-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="0b80e-119">W programie WCF, Dyspozytor tworzy wystąpienia klasy usługi za pomocą <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="0b80e-120">Ten interfejs zawiera trzy metody:</span><span class="sxs-lookup"><span data-stu-id="0b80e-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="0b80e-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po umieszczeniu wywołania funkcji wysyłania komunikatu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę, aby utworzyć wystąpienie klasy usługi przetworzyć komunikatu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="0b80e-122">Częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0b80e-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="0b80e-123">Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi zostanie utworzona przetworzenie każdego komunikatu przychodzący, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana w momencie nadejścia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b80e-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="0b80e-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Może to być taka sama jak Poprzednia metoda, z wyjątkiem wywoływane po żadnego argumentu dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b80e-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="0b80e-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upływie okresu istnienia wystąpienia usługi, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody.</span><span class="sxs-lookup"><span data-stu-id="0b80e-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="0b80e-126">Podobnie jak w przypadku dla <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0b80e-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="0b80e-127">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="0b80e-127">The Object Pool</span></span>  
 <span data-ttu-id="0b80e-128">Niestandardowy <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementacja udostępnia wymaganego obiektu buforowanie semantyki dla usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="0b80e-129">Ten przykład ma `ObjectPoolingInstanceProvider` typ, który zawiera niestandardową implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do umieszczenia w puli.</span><span class="sxs-lookup"><span data-stu-id="0b80e-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="0b80e-130">Gdy `Dispatcher` wywołania <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa szuka istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0b80e-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="0b80e-131">Jeśli jest dostępny, jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="0b80e-131">If one is available, it is returned.</span></span> <span data-ttu-id="0b80e-132">W przeciwnym razie zostanie utworzony nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="0b80e-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="0b80e-133">Wykonania na `GetInstance` przedstawiono w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0b80e-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="0b80e-134">Niestandardowy `ReleaseInstance` implementacji dodaje wydana wystąpienie do puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="0b80e-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="0b80e-135">`Dispatcher` Może wywoływać te metody z różnych wątków i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolingInstanceProvider` klasy jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="0b80e-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="0b80e-136">`ReleaseInstance` Metoda udostępnia funkcję "oczyszczania inicjowania".</span><span class="sxs-lookup"><span data-stu-id="0b80e-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="0b80e-137">Zwykle puli obsługuje minimalnej liczby obiektów, dla okresu istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="0b80e-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="0b80e-138">Jednak może być okresy nadmiernego użycia, które wymagają, tworząc dodatkowe obiekty w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0b80e-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="0b80e-139">Po pewnym czasie gdy pula staje się mniej aktywne, te obiekty nadwyżki może stać się dodatkowego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="0b80e-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="0b80e-140">W związku z tym, kiedy `activeObjectsCount` osiągnie wartość zero, czasomierza bezczynności została uruchomiona, który wyzwala i wykonuje cyklu czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="0b80e-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="0b80e-141">Dodawanie zachowania</span><span class="sxs-lookup"><span data-stu-id="0b80e-141">Adding the Behavior</span></span>  
 <span data-ttu-id="0b80e-142">Rozszerzenia dyspozytorów warstwy są podłączone, wykonując następujące zachowania:</span><span class="sxs-lookup"><span data-stu-id="0b80e-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="0b80e-143">Zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-143">Service Behaviors.</span></span> <span data-ttu-id="0b80e-144">Umożliwiają one do dostosowywania środowiska uruchomieniowego całą usługę.</span><span class="sxs-lookup"><span data-stu-id="0b80e-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="0b80e-145">Zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-145">Endpoint Behaviors.</span></span> <span data-ttu-id="0b80e-146">Umożliwiają one do dostosowywania punktów końcowych usługi, w szczególności kanału i wysyłający punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="0b80e-147">Zachowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-147">Contract Behaviors.</span></span> <span data-ttu-id="0b80e-148">Umożliwiają one do dostosowania obu <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy na kliencie i usługę, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0b80e-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="0b80e-149">Na potrzeby buforowania rozszerzenie obiektu zachowanie usługi, musi zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="0b80e-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="0b80e-150">Zachowania usług są tworzone przez zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="0b80e-151">Istnieje kilka sposobów, aby uświadomić modelu usługi niestandardowe zachowania:</span><span class="sxs-lookup"><span data-stu-id="0b80e-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="0b80e-152">Za pomocą atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="0b80e-153">Obowiązkowo dodanie go do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="0b80e-154">Rozszerzenie pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0b80e-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="0b80e-155">Ta próbka używa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0b80e-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="0b80e-156">Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany poszczególne atrybuty, są używane w definicji typu usługi i zachowania dostępne są dodawane do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="0b80e-157">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> zawiera trzy metody — <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b80e-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="0b80e-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda służy do zapewnienia, że zachowanie może być stosowana w usłudze.</span><span class="sxs-lookup"><span data-stu-id="0b80e-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="0b80e-159">W tym przykładzie wdrożenia gwarantuje, że usługa nie jest skonfigurowana za pomocą <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="0b80e-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="0b80e-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania usługi powiązania.</span><span class="sxs-lookup"><span data-stu-id="0b80e-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="0b80e-161">Nie jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-161">It is not required in this scenario.</span></span> <span data-ttu-id="0b80e-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Służy do konfigurowania dyspozytorów tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="0b80e-163">Ta metoda jest wywoływana przez architekturę WCF podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany.</span><span class="sxs-lookup"><span data-stu-id="0b80e-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="0b80e-164">Następujące parametry są przekazywane do tej metody:</span><span class="sxs-lookup"><span data-stu-id="0b80e-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="0b80e-165">`Description`: Ten argument zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="0b80e-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="0b80e-166">To może służyć do opisu danych dotyczących punktów końcowych usługi, kontrakty, powiązania i inne dane inspekcji.</span><span class="sxs-lookup"><span data-stu-id="0b80e-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="0b80e-167">`ServiceHostBase`: Ten argument zawiera <xref:System.ServiceModel.ServiceHostBase> , jest obecnie inicjowany.</span><span class="sxs-lookup"><span data-stu-id="0b80e-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="0b80e-168">W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji nowe wystąpienie elementu `ObjectPoolingInstanceProvider` jest tworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="0b80e-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="0b80e-169">Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka składowych, aby dostosować puli obiektów przy użyciu argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="0b80e-170">Te elementy Członkowskie zawierają <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpowiadać obiektowi buforowania zestawu funkcji udostępnianego przez usługi Enterprise .NET.</span><span class="sxs-lookup"><span data-stu-id="0b80e-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="0b80e-171">Zachowanie buforowania można teraz można dodać obiektu do usługi WCF przez dodawanie adnotacji do implementacji usługi przy użyciu nowo utworzony niestandardowy `ObjectPooling` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="0b80e-172">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="0b80e-172">Running the Sample</span></span>  
 <span data-ttu-id="0b80e-173">W przykładzie pokazano korzyści w zakresie wydajności, które można uzyskać za pomocą buforowanie obiektów w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="0b80e-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="0b80e-174">Aplikacja usługi implementuje dwóch usług — `WorkService` i `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="0b80e-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="0b80e-175">Zarówno usługi udostępniać tego samego wdrożenia — mogą wymagać kosztownych inicjowania i następnie udostępnić `DoWork()` metoda względnie niedrogie.</span><span class="sxs-lookup"><span data-stu-id="0b80e-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="0b80e-176">Jedyną różnicą jest to, że `ObjectPooledWorkService` ma, skonfigurować buforowanie obiektu:</span><span class="sxs-lookup"><span data-stu-id="0b80e-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="0b80e-177">Po uruchomieniu klienta, czasu jego wywołania `WorkService` 5 razy.</span><span class="sxs-lookup"><span data-stu-id="0b80e-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="0b80e-178">Następnie czasu wywołania `ObjectPooledWorkService` 5 razy.</span><span class="sxs-lookup"><span data-stu-id="0b80e-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="0b80e-179">Różnica w czasie zostanie wyświetlona:</span><span class="sxs-lookup"><span data-stu-id="0b80e-179">The difference in time is then displayed:</span></span>  
  
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
>  <span data-ttu-id="0b80e-180">Podczas pierwszego uruchomienia klienta obie te usługi są wyświetlane potrwać około tyle samo czasu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="0b80e-181">Jeśli ponownie uruchomić przykład, możesz zobaczyć, że `ObjectPooledWorkService` zwraca znacznie szybciej, ponieważ istnieje już wystąpienie tego obiektu w puli.</span><span class="sxs-lookup"><span data-stu-id="0b80e-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b80e-182">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="0b80e-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0b80e-183">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b80e-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0b80e-184">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b80e-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0b80e-185">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b80e-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b80e-186">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="0b80e-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b80e-187">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0b80e-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b80e-188">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0b80e-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b80e-189">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0b80e-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b80e-190">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0b80e-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
