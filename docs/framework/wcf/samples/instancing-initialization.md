---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ee7d470cb80e913707ae6e92039061efde8fcb7f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715804"
---
# <a name="instancing-initialization"></a><span data-ttu-id="b116d-102">Tworzenie wystąpienia inicjowania</span><span class="sxs-lookup"><span data-stu-id="b116d-102">Instancing Initialization</span></span>
<span data-ttu-id="b116d-103">Ten przykład rozszerza przykład [puli](../../../../docs/framework/wcf/samples/pooling.md) przez zdefiniowanie interfejsu, `IObjectControl`, który dostosowuje inicjalizację obiektu przez aktywację i dezaktywowanie go.</span><span class="sxs-lookup"><span data-stu-id="b116d-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="b116d-104">Klient wywołuje metody, które zwracają obiekt do puli i które nie zwracają obiektu do puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b116d-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b116d-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="b116d-106">Punkty rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="b116d-106">Extensibility Points</span></span>  
 <span data-ttu-id="b116d-107">Pierwszym krokiem tworzenia rozszerzenia Windows Communication Foundation (WCF) jest określenie punktu rozszerzalności, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="b116d-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="b116d-108">W programie WCF termin *elemencie EndpointDispatcher* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący.</span><span class="sxs-lookup"><span data-stu-id="b116d-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="b116d-109">Usługa WCF tworzy elemencie EndpointDispatcher dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b116d-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="b116d-110">Elemencie EndpointDispatcher oferuje zakres punktów końcowych (dla wszystkich komunikatów odebranych lub wysłanych przez usługę) przy użyciu klasy <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="b116d-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="b116d-111">Ta klasa pozwala dostosować różne właściwości kontrolujące zachowanie elemencie EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="b116d-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="b116d-112">Ten przykład koncentruje się na właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="b116d-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="b116d-113">IInstanceProvider</span></span>  
 <span data-ttu-id="b116d-114">W programie WCF elemencie EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia implementującego interfejs <xref:System.ServiceModel.Dispatcher.IInstanceProvider>.</span><span class="sxs-lookup"><span data-stu-id="b116d-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="b116d-115">Ten interfejs ma tylko dwie metody:</span><span class="sxs-lookup"><span data-stu-id="b116d-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="b116d-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: po nadejściu komunikatu, Dyspozytor wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, aby utworzyć wystąpienie klasy usługi w celu przetworzenia komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b116d-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="b116d-117">Częstotliwość wywołań tej metody jest określana przez właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="b116d-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="b116d-118">Na przykład jeśli właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi zostanie utworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.</span><span class="sxs-lookup"><span data-stu-id="b116d-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="b116d-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: gdy wystąpienie usługi zakończy przetwarzanie komunikatu, elemencie EndpointDispatcher wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="b116d-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="b116d-120">Podobnie jak w przypadku metody <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> częstotliwość wywołań tej metody jest określana przez właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="b116d-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="b116d-121">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="b116d-121">The Object Pool</span></span>  
 <span data-ttu-id="b116d-122">Klasa `ObjectPoolInstanceProvider` zawiera implementację puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="b116d-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="b116d-123">Ta klasa implementuje interfejs <xref:System.ServiceModel.Dispatcher.IInstanceProvider>, aby można było korzystać z warstwy modelu usług.</span><span class="sxs-lookup"><span data-stu-id="b116d-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="b116d-124">Gdy elemencie EndpointDispatcher wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b116d-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="b116d-125">Jeśli jest dostępna, jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="b116d-125">If one is available, it is returned.</span></span> <span data-ttu-id="b116d-126">W przeciwnym razie `ObjectPoolInstanceProvider` sprawdza, czy właściwość `ActiveObjectsCount` (liczba obiektów zwróconych z puli) osiągnęła maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="b116d-127">Jeśli nie, nowe wystąpienie jest tworzone i zwracane do obiektu wywołującego, a `ActiveObjectsCount` jest następnie zwiększane.</span><span class="sxs-lookup"><span data-stu-id="b116d-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="b116d-128">W przeciwnym razie żądanie utworzenia obiektu jest umieszczane w kolejce przez skonfigurowany okres czasu.</span><span class="sxs-lookup"><span data-stu-id="b116d-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="b116d-129">Implementacja dla `GetObjectFromThePool` jest pokazana w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b116d-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b116d-130">Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza wartość `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="b116d-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="b116d-131">Elemencie EndpointDispatcher może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do elementów członkowskich na poziomie klasy w klasie `ObjectPoolInstanceProvider` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="b116d-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b116d-132">Metoda `ReleaseInstance` zapewnia *oczyszczanie funkcji inicjalizacji* .</span><span class="sxs-lookup"><span data-stu-id="b116d-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="b116d-133">Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="b116d-134">Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b116d-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="b116d-135">Ostatecznie gdy pula stanie się mniej aktywne, te nadmiarowe obiekty mogą stać się dodatkowymi kosztami.</span><span class="sxs-lookup"><span data-stu-id="b116d-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="b116d-136">W związku z tym, gdy `activeObjectsCount` osiągnie zero, uruchamiany jest czasomierz bezczynny, który wyzwala wyzwalacz i wykonuje oczyszczanie.</span><span class="sxs-lookup"><span data-stu-id="b116d-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="b116d-137">Rozszerzenia warstwy ServiceModel są podłączane przy użyciu następujących zachowań:</span><span class="sxs-lookup"><span data-stu-id="b116d-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="b116d-138">Zachowania usługi: umożliwiają dostosowanie całego środowiska uruchomieniowego usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="b116d-139">Zachowania punktów końcowych: umożliwiają one dostosowanie określonego punktu końcowego usługi, w tym elemencie EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="b116d-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="b116d-140">Zachowania kontraktowe: umożliwiają one dostosowanie <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas odpowiednio do klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="b116d-141">Zachowania operacji: umożliwiają one dostosowanie klas <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> na kliencie lub w odpowiedniej usłudze.</span><span class="sxs-lookup"><span data-stu-id="b116d-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="b116d-142">Na potrzeby rozszerzenia puli obiektów można utworzyć zachowanie punktu końcowego lub zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="b116d-143">W tym przykładzie używamy zachowania usługi, która stosuje możliwość buforowania obiektów do każdego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="b116d-144">Zachowania usługi są tworzone przez implementację interfejsu <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b116d-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="b116d-145">Istnieje kilka sposobów, aby dowiedzieć się, jak element ServiceModel ma wpływ na niestandardowe zachowania:</span><span class="sxs-lookup"><span data-stu-id="b116d-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="b116d-146">Przy użyciu atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b116d-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="b116d-147">Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="b116d-148">Rozszerzanie pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b116d-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="b116d-149">Ten przykład używa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b116d-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="b116d-150">Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="b116d-151">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="b116d-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="b116d-152">Te metody są wywoływane przez funkcję WCF, gdy <xref:System.ServiceModel.ServiceHost> jest inicjowana.</span><span class="sxs-lookup"><span data-stu-id="b116d-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="b116d-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> jest wywoływana jako pierwsza; pozwala ona na badanie niespójności usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="b116d-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> jest wywoływana dalej; Ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="b116d-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="b116d-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> jest określany jako ostatni i jest odpowiedzialny za skonfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b116d-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="b116d-156">Następujące parametry są przesyłane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="b116d-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="b116d-157">`Description`: ten parametr zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="b116d-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="b116d-158">Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane skojarzone z usługą.</span><span class="sxs-lookup"><span data-stu-id="b116d-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="b116d-159">`ServiceHostBase`: ten parametr dostarcza <xref:System.ServiceModel.ServiceHostBase>, który jest aktualnie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="b116d-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="b116d-160">W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe wystąpienie `ObjectPoolInstanceProvider` jest tworzone i przypisywane do właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> w każdej <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączonej do <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="b116d-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b116d-161">Oprócz implementacji <xref:System.ServiceModel.Description.IServiceBehavior> Klasa `ObjectPoolingAttribute` ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b116d-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="b116d-162">Te elementy członkowskie obejmują `MaxSize`, `MinSize`, `Enabled` i `CreationTimeout`, aby dopasować zestaw funkcji buforowania obiektów zapewniany przez usługi .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="b116d-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="b116d-163">Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF poprzez dodanie adnotacji do implementacji usługi z nowo utworzonym atrybutem `ObjectPooling` niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b116d-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="b116d-164">Podłączanie aktywacji i dezaktywacji</span><span class="sxs-lookup"><span data-stu-id="b116d-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="b116d-165">Głównym celem tworzenia pul obiektów jest Optymalizowanie długotrwałych obiektów przy stosunkowo kosztownym tworzeniu i inicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="b116d-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="b116d-166">W związku z tym może zapewnić znaczne zwiększenie wydajności aplikacji w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b116d-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="b116d-167">Ponieważ obiekt jest zwracany z puli, Konstruktor jest wywoływany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b116d-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="b116d-168">Niektóre aplikacje wymagają jednak pewnego poziomu kontroli, dzięki czemu mogą inicjować i czyścić zasoby używane w ramach jednego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b116d-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="b116d-169">Na przykład obiekt używany na potrzeby zestawu obliczeń może zresetować swoje pola prywatne przed przetworzeniem kolejnego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="b116d-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="b116d-170">Usługi dla przedsiębiorstw obsługują ten rodzaj inicjalizacji specyficznej dla kontekstu, umożliwiając deweloperowi obiektu zastąpienie metod `Activate` i `Deactivate` z klasy podstawowej <xref:System.EnterpriseServices.ServicedComponent>.</span><span class="sxs-lookup"><span data-stu-id="b116d-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="b116d-171">Pula obiektów wywołuje metodę `Activate` tuż przed zwróceniem obiektu z puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="b116d-172">`Deactivate` jest wywoływana, gdy obiekt zwraca z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="b116d-173">Klasa bazowa <xref:System.EnterpriseServices.ServicedComponent> ma również właściwość `boolean` o nazwie `CanBePooled`, która może być używana do powiadamiania puli o tym, czy obiekt może być dodatkowo puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="b116d-174">Aby naśladować tę funkcję, przykład deklaruje publiczny interfejs (`IObjectControl`), który ma wyżej wspomniane elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="b116d-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="b116d-175">Ten interfejs jest następnie implementowany przez klasy usług przeznaczone do zapewniania inicjalizacji specyficznej dla kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b116d-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="b116d-176">Aby spełnić te wymagania, należy zmodyfikować implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider>.</span><span class="sxs-lookup"><span data-stu-id="b116d-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="b116d-177">Teraz za każdym razem, gdy otrzymujesz obiekt, wywołując metodę `GetInstance`, należy sprawdzić, czy obiekt implementuje `IObjectControl.`, jeśli tak, należy odpowiednio wywołać metodę `Activate`.</span><span class="sxs-lookup"><span data-stu-id="b116d-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="b116d-178">Podczas zwracania obiektu do puli jest wymagane sprawdzenie właściwości `CanBePooled` przed dodaniem obiektu z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="b116d-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b116d-179">Ponieważ deweloper usług może zdecydować, czy obiekt może być w puli, liczba obiektów w puli w danym momencie może przekroczyć minimalny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b116d-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="b116d-180">W związku z tym należy sprawdzić, czy liczba obiektów stała się poniżej minimalnego poziomu i wykonać niezbędne inicjowanie w procedurze oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="b116d-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b116d-181">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b116d-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b116d-182">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="b116d-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b116d-183">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="b116d-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b116d-184">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b116d-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b116d-185">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b116d-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b116d-186">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b116d-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b116d-187">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b116d-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b116d-188">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="b116d-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b116d-189">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b116d-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b116d-190">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b116d-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
