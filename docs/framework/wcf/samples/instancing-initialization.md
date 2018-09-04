---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 651029783f4632fc0b404bea8df8bd3790622bfd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516141"
---
# <a name="instancing-initialization"></a><span data-ttu-id="1394a-102">Tworzenie wystąpienia inicjowania</span><span class="sxs-lookup"><span data-stu-id="1394a-102">Instancing Initialization</span></span>
<span data-ttu-id="1394a-103">Rozszerza w tym przykładzie [Pooling](../../../../docs/framework/wcf/samples/pooling.md) próbki przez definiowanie interfejsu `IObjectControl`, który dostosowuje inicjalizację obiektu za aktywowanie i dezaktywowanie go.</span><span class="sxs-lookup"><span data-stu-id="1394a-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="1394a-104">Klient wywołuje metody, które zwracają obiekt do puli, a które nie zwracają obiekt do puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1394a-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1394a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="1394a-106">Punkty rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="1394a-106">Extensibility Points</span></span>  
 <span data-ttu-id="1394a-107">Pierwszym krokiem tworzenia rozszerzenia programu Windows Communication Foundation (WCF) jest podjęcie decyzji, punkt rozszerzeń do użycia.</span><span class="sxs-lookup"><span data-stu-id="1394a-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="1394a-108">W programie WCF termin *EndpointDispatcher* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołania metody usługi przez użytkownika i konwertowania wartości zwracane z tej metody do wysyłanej wiadomości .</span><span class="sxs-lookup"><span data-stu-id="1394a-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="1394a-109">Usługa WCF tworzy EndpointDispatcher dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1394a-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="1394a-110">EndpointDispatcher oferuje punktu końcowego zakresu (dla wszystkich wiadomości wysłanych i odebranych przez usługę) extensibility za pomocą <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> klasy.</span><span class="sxs-lookup"><span data-stu-id="1394a-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="1394a-111">Ta klasa umożliwia dostosowanie różne właściwości tej kontroli sposobu działania programu.</span><span class="sxs-lookup"><span data-stu-id="1394a-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="1394a-112">Ten przykład koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości, który wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="1394a-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="1394a-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="1394a-113">IInstanceProvider</span></span>  
 <span data-ttu-id="1394a-114">W programie WCF, EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia, która implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1394a-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="1394a-115">Ten interfejs ma tylko dwie metody:</span><span class="sxs-lookup"><span data-stu-id="1394a-115">This interface has only two methods:</span></span>  
  
-   <span data-ttu-id="1394a-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Po umieszczeniu komunikatu, wywołuje dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, aby utworzyć wystąpienie klasy usługi przetworzyć komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1394a-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="1394a-117">Częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1394a-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="1394a-118">Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi zostanie utworzona przetworzenie każdego komunikatu przychodzący, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana w momencie nadejścia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1394a-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="1394a-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Gdy wystąpienie usługi zakończy przetwarzanie komunikatu, wywołuje bibliotekę EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1394a-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="1394a-120">Podobnie jak w <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1394a-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="1394a-121">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="1394a-121">The Object Pool</span></span>  
 <span data-ttu-id="1394a-122">`ObjectPoolInstanceProvider` Klasa zawiera implementację dla puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="1394a-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="1394a-123">Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs do interakcji z warstwy modelu usług.</span><span class="sxs-lookup"><span data-stu-id="1394a-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="1394a-124">Kiedy wywołuje EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa szuka istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1394a-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="1394a-125">Jeśli jest dostępny, jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="1394a-125">If one is available, it is returned.</span></span> <span data-ttu-id="1394a-126">W przeciwnym razie `ObjectPoolInstanceProvider` sprawdza, czy `ActiveObjectsCount` właściwości (liczba obiektów zwróconych z puli), osiągnęła maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="1394a-127">Jeśli nie, nowe wystąpienie jest tworzony i zwracany do wywołującego i `ActiveObjectsCount` następnie rośnie.</span><span class="sxs-lookup"><span data-stu-id="1394a-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="1394a-128">W przeciwnym razie żądanie utworzenia obiektu jest kolejkowana w skonfigurowanym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="1394a-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="1394a-129">Wykonania na `GetObjectFromThePool` przedstawiono w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1394a-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="1394a-130">Niestandardowy `ReleaseInstance` implementacji dodaje wydana wystąpienie do puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="1394a-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="1394a-131">EndpointDispatcher może wywoływać te metody z różnych wątków i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolInstanceProvider` klasy jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="1394a-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="1394a-132">`ReleaseInstance` Metoda zapewnia *oczyszczania inicjowania* funkcji.</span><span class="sxs-lookup"><span data-stu-id="1394a-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="1394a-133">Zwykle puli obsługuje minimalnej liczby obiektów, dla okresu istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="1394a-134">Jednak może być okresy nadmiernego użycia, które wymagają, tworząc dodatkowe obiekty w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1394a-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="1394a-135">Po pewnym czasie po puli staje się mniej aktywne tych pozostałe obiekty mogą stać się dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="1394a-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="1394a-136">W związku z tym gdy `activeObjectsCount` osiągnie zero uruchomieniu czasomierza bezczynności, który wyzwala i wykonuje cyklu czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="1394a-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="1394a-137">Rozszerzenia warstwy modelu ServiceModel są podłączone, wykonując następujące zachowania:</span><span class="sxs-lookup"><span data-stu-id="1394a-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="1394a-138">Zachowania usług: Te umożliwiają dostosowanie środowiska uruchomieniowego całą usługę.</span><span class="sxs-lookup"><span data-stu-id="1394a-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="1394a-139">Zachowań punktu końcowego: Te umożliwiają dostosowanie punktu końcowego określonej usługi, w tym elemencie EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="1394a-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
-   <span data-ttu-id="1394a-140">Zachowania kontraktu: Te umożliwiają dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy po stronie klienta lub usługę, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1394a-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
-   <span data-ttu-id="1394a-141">Zachowania operacji: Te umożliwiają dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy po stronie klienta lub usługę, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1394a-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="1394a-142">Na potrzeby buforowania rozszerzenie obiektu zachowanie punktu końcowego lub zachowanie usługi mogą być tworzone.</span><span class="sxs-lookup"><span data-stu-id="1394a-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="1394a-143">W tym przykładzie używamy zachowanie usługi, które stosuje obiekt buforowanie zdolność do każdego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="1394a-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="1394a-144">Zachowania usług są tworzone przez zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1394a-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="1394a-145">Istnieje kilka sposobów, aby uświadomić ServiceModel niestandardowe zachowania:</span><span class="sxs-lookup"><span data-stu-id="1394a-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="1394a-146">Za pomocą atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1394a-146">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="1394a-147">Obowiązkowo dodanie go do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="1394a-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="1394a-148">Rozszerzenie pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1394a-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="1394a-149">Ta próbka używa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1394a-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="1394a-150">Gdy <xref:System.ServiceModel.ServiceHost> jest skonstruowany, jej poszczególne atrybuty, są używane w definicji typu usługi, jak i zachowania dostępne są dodawane do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="1394a-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="1394a-151"><xref:System.ServiceModel.Description.IServiceBehavior> Interfejs ma trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="1394a-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="1394a-152">Te metody są wywoływane przez architekturę WCF podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany.</span><span class="sxs-lookup"><span data-stu-id="1394a-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="1394a-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> nazywa się najpierw; Umożliwia usłudze poddanych niespójności.</span><span class="sxs-lookup"><span data-stu-id="1394a-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="1394a-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> nazywa się obok; Ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="1394a-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="1394a-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> nazywa się ostatnio i jest odpowiedzialny za konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1394a-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="1394a-156">Następujące parametry są przekazywane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="1394a-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
-   <span data-ttu-id="1394a-157">`Description`: Ten parametr zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="1394a-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="1394a-158">To może służyć do wglądu opis danych dotyczących punktów końcowych usługi, kontrakty, powiązania i inne dane związane z usługą.</span><span class="sxs-lookup"><span data-stu-id="1394a-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
-   <span data-ttu-id="1394a-159">`ServiceHostBase`: Ten parametr zawiera <xref:System.ServiceModel.ServiceHostBase> , jest obecnie inicjowany.</span><span class="sxs-lookup"><span data-stu-id="1394a-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="1394a-160">W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji, nowe wystąpienie klasy `ObjectPoolInstanceProvider` jest tworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość w każdym <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączona do <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="1394a-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 <span data-ttu-id="1394a-161">Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji `ObjectPoolingAttribute` klasa ma kilka składowych, aby dostosować puli obiektów przy użyciu argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1394a-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="1394a-162">Te elementy Członkowskie zawierają `MaxSize`, `MinSize`, `Enabled` i `CreationTimeout`, aby odpowiadać obiektowi buforowania zestawu funkcji udostępnianego przez usługi Enterprise .NET.</span><span class="sxs-lookup"><span data-stu-id="1394a-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="1394a-163">Zachowanie buforowania można teraz można dodać obiektu do usługi WCF przez dodawanie adnotacji do implementacji usługi przy użyciu nowo utworzony niestandardowy `ObjectPooling` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1394a-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="1394a-164">Przechwytywanie, aktywacja i dezaktywacja</span><span class="sxs-lookup"><span data-stu-id="1394a-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="1394a-165">Podstawowym celem buforowanie obiektu jest zoptymalizować obiekty krótkotrwałe relatywnie kosztowne tworzenia i inicjowania.</span><span class="sxs-lookup"><span data-stu-id="1394a-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="1394a-166">W związku z tym zwiększeniu wydajności znaczne go można udostępnić aplikację, czy poprawnie zastosowane.</span><span class="sxs-lookup"><span data-stu-id="1394a-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="1394a-167">Ponieważ obiekt jest zwracany z puli, Konstruktor jest wywoływany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1394a-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="1394a-168">Jednak niektóre aplikacje wymagają pewien stopień kontroli, tak aby mogli inicjowanie i oczyszczanie zasoby używane podczas pojedynczego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1394a-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="1394a-169">Na przykład obiekt używany zbiór obliczenia można zresetować jego pola prywatne przed przetworzeniem dalej obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1394a-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="1394a-170">Usługi Enterprise włączone tento typ inicializace zależne od kontekstu, umożliwiając developer obiektu zastępują `Activate` i `Deactivate` metody z <xref:System.EnterpriseServices.ServicedComponent> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="1394a-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="1394a-171">Wywołań puli obiektów `Activate` metoda tuż przed zwróceniem obiektu z puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="1394a-172">`Deactivate` jest wywoływana, gdy obiekt zwraca z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="1394a-173"><xref:System.EnterpriseServices.ServicedComponent> Ma również klasę bazową `boolean` właściwość o nazwie `CanBePooled`, który może służyć do powiadamiania w puli, czy obiekt może dodatkowo puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="1394a-174">Aby naśladował tę funkcję, przykład deklaruje interfejsu publicznego (`IObjectControl`) zawierający wyżej wymienionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1394a-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="1394a-175">Ten interfejs, następnie jest implementowany przez usługę klasy mają na celu dostarczenie Inicjalizacja określonego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1394a-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="1394a-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementacji muszą zostać zmodyfikowane w celu spełnienia tych wymagań.</span><span class="sxs-lookup"><span data-stu-id="1394a-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="1394a-177">Teraz zawsze możesz uzyskać obiektu przez wywołanie metody `GetInstance` metody, musisz sprawdzić, czy obiekt implementuje `IObjectControl.` Jeśli tak jest, należy wywołać `Activate` metoda odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1394a-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="1394a-178">Gdy zwracany obiekt do puli, kontrola jest wymagany dla `CanBePooled` właściwości przed dodaniem obiektu z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="1394a-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="1394a-179">Ponieważ Deweloper usługi może zdecydować, czy obiekt może być gromadzone, liczba obiektów w puli w danym momencie może zejść poniżej minimalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="1394a-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="1394a-180">W związku z tym musisz sprawdzić, czy liczba obiektów poniżej minimalnego poziomu i wykonywać niezbędne inicjowania procedury oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="1394a-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="1394a-181">Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="1394a-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1394a-182">Naciśnij klawisz Enter każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="1394a-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1394a-183">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="1394a-183">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1394a-184">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1394a-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1394a-185">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1394a-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1394a-186">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1394a-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1394a-187">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1394a-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1394a-188">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1394a-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1394a-189">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="1394a-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1394a-190">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1394a-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a><span data-ttu-id="1394a-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1394a-191">See Also</span></span>
