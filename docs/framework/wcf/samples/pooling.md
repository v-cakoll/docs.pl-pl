---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183404"
---
# <a name="pooling"></a><span data-ttu-id="b37c7-102">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="b37c7-102">Pooling</span></span>
<span data-ttu-id="b37c7-103">W tym przykładzie pokazano, jak rozszerzyć Program Windows Communication Foundation (WCF) do obsługi buforowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="b37c7-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="b37c7-104">W przykładzie pokazano, jak utworzyć atrybut, który jest syntaktycznie `ObjectPoolingAttribute` i semantycznie podobny do funkcji atrybutu enterprise services.</span><span class="sxs-lookup"><span data-stu-id="b37c7-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="b37c7-105">Buforowanie obiektów może zapewnić dramatyczny wzrost wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b37c7-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="b37c7-106">Jednak może mieć odwrotny skutek, jeśli nie jest prawidłowo stosowany.</span><span class="sxs-lookup"><span data-stu-id="b37c7-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="b37c7-107">Buforowanie obiektów pomaga zmniejszyć obciążenie związane z odtwarzaniem często używanych obiektów, które wymagają rozbudowanej inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="b37c7-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="b37c7-108">Jednak jeśli wywołanie metody na obiekcie puli zajmuje dużo czasu, aby zakończyć, buforowanie obiektów kolejkuje dodatkowe żądania, gdy tylko zostanie osiągnięty maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="b37c7-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="b37c7-109">W związku z tym może nie służyć niektóre żądania tworzenia obiektów, zgłaszając wyjątek limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b37c7-110">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b37c7-111">Pierwszym krokiem w tworzeniu rozszerzenia WCF jest podjęcie decyzji o punkt rozszerzalności do użycia.</span><span class="sxs-lookup"><span data-stu-id="b37c7-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="b37c7-112">W WCF termin *dyspozytor* odnosi się do składnika czasu wykonywania odpowiedzialnego za konwertowanie wiadomości przychodzących na wywołania metody w usłudze użytkownika i za konwertowanie wartości zwracanych z tej metody na komunikat wychodzący.</span><span class="sxs-lookup"><span data-stu-id="b37c7-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="b37c7-113">Usługa WCF tworzy dyspozytora dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="b37c7-114">Klient WCF musi używać dyspozytora, jeśli umowa skojarzona z tym klientem jest umową dupleksu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="b37c7-115">Dyspozytorzy kanału i punktu końcowego oferują rozszerzalność całego kanału i umowy, ujawniając różne właściwości, które kontrolują zachowanie dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="b37c7-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="b37c7-116">Właściwość <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> umożliwia również sprawdzanie, modyfikowanie lub dostosowywanie procesu wysyłki.</span><span class="sxs-lookup"><span data-stu-id="b37c7-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="b37c7-117">Ten przykład koncentruje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> się na właściwość, która wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="b37c7-118">The IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="b37c7-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="b37c7-119">W WCF dyspozytor tworzy wystąpienia klasy <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>usługi przy użyciu <xref:System.ServiceModel.Dispatcher.IInstanceProvider> , który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="b37c7-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="b37c7-120">Ten interfejs ma trzy metody:</span><span class="sxs-lookup"><span data-stu-id="b37c7-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="b37c7-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po odebraniu komunikatu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> Dyspozytor wywołuje metodę, aby utworzyć wystąpienie klasy usługi do przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b37c7-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="b37c7-122">Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="b37c7-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="b37c7-123">Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość <xref:System.ServiceModel.InstanceContextMode.PerCall> jest ustawiona na nowe wystąpienie klasy usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest tworzony do przetwarzania każdej wiadomości, która nadejdzie, więc jest wywoływana za każdym razem, gdy pojawia się komunikat.</span><span class="sxs-lookup"><span data-stu-id="b37c7-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="b37c7-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest to identyczne z poprzednią metodą, z tą różnicą, że jest wywoływana, gdy nie ma żadnego argumentu Message.</span><span class="sxs-lookup"><span data-stu-id="b37c7-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="b37c7-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upłynięciu okresu istnienia wystąpienia usługi, Dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodę.</span><span class="sxs-lookup"><span data-stu-id="b37c7-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="b37c7-126">Podobnie jak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> w przypadku metody, częstotliwość wywołań tej <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody jest określana przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="b37c7-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="b37c7-127">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="b37c7-127">The Object Pool</span></span>  
 <span data-ttu-id="b37c7-128">Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceProvider> niestandardowa zapewnia semantyka buforowania wymaganych obiektów dla usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="b37c7-129">W związku z tym `ObjectPoolingInstanceProvider` ten przykład ma <xref:System.ServiceModel.Dispatcher.IInstanceProvider> typ, który zapewnia niestandardową implementację do buforowania.</span><span class="sxs-lookup"><span data-stu-id="b37c7-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="b37c7-130">Gdy `Dispatcher` wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b37c7-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="b37c7-131">Jeśli jeden jest dostępny, jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="b37c7-131">If one is available, it is returned.</span></span> <span data-ttu-id="b37c7-132">W przeciwnym razie tworzony jest nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="b37c7-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="b37c7-133">Implementacja `GetInstance` dla jest pokazana w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b37c7-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b37c7-134">Implementacja `ReleaseInstance` niestandardowa dodaje zwolnione wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="b37c7-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="b37c7-135">Można `Dispatcher` wywołać te metody z różnych wątków, a zatem wymagany `ObjectPoolingInstanceProvider` jest zsynchronizowany dostęp do elementów członkowskich poziomu klasy w klasie.</span><span class="sxs-lookup"><span data-stu-id="b37c7-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b37c7-136">Metoda `ReleaseInstance` zapewnia funkcję "oczyszczania inicjowania".</span><span class="sxs-lookup"><span data-stu-id="b37c7-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="b37c7-137">Zwykle pula utrzymuje minimalną liczbę obiektów przez cały okres istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="b37c7-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="b37c7-138">Jednak mogą istnieć okresy nadmiernego użycia, które wymagają tworzenia dodatkowych obiektów w puli, aby osiągnąć maksymalny limit określony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b37c7-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="b37c7-139">Ostatecznie, gdy pula staje się mniej aktywne, te nadwyżki obiektów może stać się dodatkowym obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="b37c7-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="b37c7-140">W związku z `activeObjectsCount` tym po osiągnięciu zera, czasomierz bezczynny jest uruchamiany, który wyzwala i wykonuje cykl oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="b37c7-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="b37c7-141">Dodawanie zachowania</span><span class="sxs-lookup"><span data-stu-id="b37c7-141">Adding the Behavior</span></span>  
 <span data-ttu-id="b37c7-142">Rozszerzenia warstwy dyspozytora są podłączone przy użyciu następujących zachowań:</span><span class="sxs-lookup"><span data-stu-id="b37c7-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="b37c7-143">Zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-143">Service Behaviors.</span></span> <span data-ttu-id="b37c7-144">Umożliwiają one dostosowanie całego środowiska wykonawczego usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="b37c7-145">Zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-145">Endpoint Behaviors.</span></span> <span data-ttu-id="b37c7-146">Umożliwiają one dostosowanie punktów końcowych usługi, w szczególności dyspozytora kanału i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="b37c7-147">Zachowania kontraktowe.</span><span class="sxs-lookup"><span data-stu-id="b37c7-147">Contract Behaviors.</span></span> <span data-ttu-id="b37c7-148">Umożliwiają one dostosowanie zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas na klienta i usługi odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b37c7-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="b37c7-149">Na potrzeby rozszerzenia buforowania obiektów należy utworzyć zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="b37c7-150">Zachowania usługi są tworzone przez <xref:System.ServiceModel.Description.IServiceBehavior> implementowanie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="b37c7-151">Istnieje kilka sposobów, aby model usługi świadomy zachowań niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="b37c7-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="b37c7-152">Korzystanie z atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="b37c7-153">Konieczne dodanie go do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="b37c7-154">Rozszerzenie pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="b37c7-155">W tym przykładzie użyto atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b37c7-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="b37c7-156"><xref:System.ServiceModel.ServiceHost> Po skonstruowaniu sprawdza atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="b37c7-157">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>-- <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>i .</span><span class="sxs-lookup"><span data-stu-id="b37c7-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="b37c7-158">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> jest używana w celu zapewnienia, że zachowanie może być stosowane do usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="b37c7-159">W tym przykładzie implementacja zapewnia, że usługa <xref:System.ServiceModel.InstanceContextMode.Single>nie jest skonfigurowana z .</span><span class="sxs-lookup"><span data-stu-id="b37c7-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="b37c7-160">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> jest używana do konfigurowania powiązań usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="b37c7-161">Nie jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-161">It is not required in this scenario.</span></span> <span data-ttu-id="b37c7-162">Jest <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> używany do konfigurowania dyspozytorów usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="b37c7-163">Ta metoda jest wywoływana przez <xref:System.ServiceModel.ServiceHost> WCF podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="b37c7-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="b37c7-164">Następujące parametry są przekazywane do tej metody:</span><span class="sxs-lookup"><span data-stu-id="b37c7-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="b37c7-165">`Description`: Ten argument zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="b37c7-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="b37c7-166">Może to służyć do sprawdzania danych opisu dotyczących punktów końcowych usługi, umów, powiązań i innych danych.</span><span class="sxs-lookup"><span data-stu-id="b37c7-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="b37c7-167">`ServiceHostBase`: Ten argument <xref:System.ServiceModel.ServiceHostBase> zapewnia, że jest obecnie inicjowane.</span><span class="sxs-lookup"><span data-stu-id="b37c7-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="b37c7-168">W <xref:System.ServiceModel.Description.IServiceBehavior> niestandardowej implementacji `ObjectPoolingInstanceProvider` nowe wystąpienie jest tworzone <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> i przypisywane do właściwości w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="b37c7-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
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
                throttle ??= cd.ServiceThrottle;
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
  
 <span data-ttu-id="b37c7-169">Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka elementów członkowskich, aby dostosować pulę obiektów przy użyciu argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="b37c7-170">Te elementy <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>członkowskie <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>obejmują , i , aby dopasować zestaw funkcji buforowania obiektów dostarczonych przez usługi .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="b37c7-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="b37c7-171">Zachowanie buforowania obiektów można teraz dodać do usługi WCF, dokonując adnotacji implementacji usługi za pomocą nowo utworzonego atrybutu niestandardowego. `ObjectPooling`</span><span class="sxs-lookup"><span data-stu-id="b37c7-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="b37c7-172">Uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="b37c7-172">Running the Sample</span></span>  
 <span data-ttu-id="b37c7-173">W przykładzie pokazano korzyści wydajności, które można uzyskać przy użyciu buforowania obiektów w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="b37c7-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="b37c7-174">Aplikacja usługi implementuje dwie `WorkService` usługi `ObjectPooledWorkService`- i .</span><span class="sxs-lookup"><span data-stu-id="b37c7-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="b37c7-175">Obie usługi mają tę samą implementację — obie `DoWork()` wymagają kosztownej inicjalizacji, a następnie udostępniają metodę, która jest stosunkowo tania.</span><span class="sxs-lookup"><span data-stu-id="b37c7-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="b37c7-176">Jedyną różnicą `ObjectPooledWorkService` jest to, że ma buforowanie obiektów skonfigurowane:</span><span class="sxs-lookup"><span data-stu-id="b37c7-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b37c7-177">Po uruchomieniu klienta, to razy `WorkService` wywołanie 5 razy.</span><span class="sxs-lookup"><span data-stu-id="b37c7-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="b37c7-178">To wtedy razy `ObjectPooledWorkService` wzywając 5 razy.</span><span class="sxs-lookup"><span data-stu-id="b37c7-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="b37c7-179">Następnie wyświetlana jest różnica czasu:</span><span class="sxs-lookup"><span data-stu-id="b37c7-179">The difference in time is then displayed:</span></span>  
  
```console
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
> <span data-ttu-id="b37c7-180">Po raz pierwszy klient jest uruchamiany obie usługi wydają się zająć mniej więcej tyle samo czasu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="b37c7-181">Jeśli ponownie uruchomić próbki, widać, że `ObjectPooledWorkService` zwraca znacznie szybciej, ponieważ wystąpienie tego obiektu już istnieje w puli.</span><span class="sxs-lookup"><span data-stu-id="b37c7-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b37c7-182">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="b37c7-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b37c7-183">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b37c7-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b37c7-184">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b37c7-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b37c7-185">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b37c7-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b37c7-186">Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="b37c7-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b37c7-187">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b37c7-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b37c7-188">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="b37c7-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b37c7-189">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="b37c7-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b37c7-190">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b37c7-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
