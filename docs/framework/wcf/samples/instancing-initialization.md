---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183593"
---
# <a name="instancing-initialization"></a><span data-ttu-id="ce3a0-102">Tworzenie wystąpienia inicjowania</span><span class="sxs-lookup"><span data-stu-id="ce3a0-102">Instancing Initialization</span></span>
<span data-ttu-id="ce3a0-103">Ten przykład rozszerza [próbkę buforowania,](../../../../docs/framework/wcf/samples/pooling.md) definiując interfejs, `IObjectControl`który dostosowuje inicjowanie obiektu przez aktywowanie i dezaktywację.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="ce3a0-104">Klient wywołuje metody, które zwracają obiekt do puli i które nie zwracają obiektu do puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce3a0-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="ce3a0-106">Punkty rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ce3a0-106">Extensibility Points</span></span>  
 <span data-ttu-id="ce3a0-107">Pierwszym krokiem w tworzeniu rozszerzenia Windows Communication Foundation (WCF) jest podjęcie decyzji o punkt rozszerzalności do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="ce3a0-108">W WCF termin *EndpointDispatcher* odnosi się do składnika czasu wykonywania odpowiedzialnego za konwertowanie wiadomości przychodzących na wywołania metody w usłudze użytkownika i za konwertowanie wartości zwracanych z tej metody na komunikat wychodzący.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="ce3a0-109">Usługa WCF tworzy EndpointDispatcher dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="ce3a0-110">EndpointDispatcher oferuje zakres punktu końcowego (dla wszystkich wiadomości odebranych lub <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> wysłanych przez usługę) rozszerzalność przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="ce3a0-111">Ta klasa umożliwia dostosowanie różnych właściwości, które kontrolują zachowanie EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="ce3a0-112">Ten przykład koncentruje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> się na właściwość, która wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="ce3a0-113">Iinstanceprovider</span><span class="sxs-lookup"><span data-stu-id="ce3a0-113">IInstanceProvider</span></span>  
 <span data-ttu-id="ce3a0-114">W WCF EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="ce3a0-115">Ten interfejs ma tylko dwie metody:</span><span class="sxs-lookup"><span data-stu-id="ce3a0-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="ce3a0-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Po odebraniu wiadomości dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, aby utworzyć wystąpienie klasy usługi do przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="ce3a0-117">Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="ce3a0-118">Na przykład, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> jeśli właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> usługi jest tworzony do przetwarzania każdej wiadomości, która nadejdzie, więc jest wywoływana, gdy pojawia się komunikat.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="ce3a0-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Po zakończeniu przetwarzania komunikatu wystąpienie usługi, EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="ce3a0-120">Podobnie jak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> w metodzie, częstotliwość wywołań tej <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody jest określana przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="ce3a0-121">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="ce3a0-121">The Object Pool</span></span>  
 <span data-ttu-id="ce3a0-122">Klasa `ObjectPoolInstanceProvider` zawiera implementację puli obiektów.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="ce3a0-123">Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs do interakcji z warstwą modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="ce3a0-124">Gdy EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="ce3a0-125">Jeśli jeden jest dostępny, jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-125">If one is available, it is returned.</span></span> <span data-ttu-id="ce3a0-126">W `ObjectPoolInstanceProvider` przeciwnym razie `ActiveObjectsCount` sprawdza, czy właściwość (liczba obiektów zwróconych z puli) osiągnęła maksymalny rozmiar puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="ce3a0-127">Jeśli nie, nowe wystąpienie jest tworzony i `ActiveObjectsCount` zwracany do wywołującego, a następnie zwiększa.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="ce3a0-128">W przeciwnym razie żądanie utworzenia obiektu jest umieszczane w kolejce przez skonfigurowany okres czasu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="ce3a0-129">Implementacja `GetObjectFromThePool` dla jest pokazana w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ce3a0-130">Implementacja `ReleaseInstance` niestandardowa dodaje zwolnione wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="ce3a0-131">EndpointDispatcher można wywołać te metody z różnych wątków i dlatego zsynchronizowanego dostępu do elementów członkowskich poziomu klasy w `ObjectPoolInstanceProvider` klasie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="ce3a0-132">Metoda `ReleaseInstance` zapewnia funkcję *oczyszczania inicjowania.*</span><span class="sxs-lookup"><span data-stu-id="ce3a0-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="ce3a0-133">Zwykle pula utrzymuje minimalną liczbę obiektów przez cały okres istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="ce3a0-134">Jednak mogą istnieć okresy nadmiernego użycia, które wymagają tworzenia dodatkowych obiektów w puli, aby osiągnąć maksymalny limit określony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="ce3a0-135">Po pewnym czasie, gdy pula staje się mniej aktywna, te nadwyżki obiektów może stać się dodatkowym obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="ce3a0-136">W związku `activeObjectsCount` z tym po osiągnięciu zera jest uruchamiany czasomierz bezczynny, który wyzwala i wykonuje cykl oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="ce3a0-137">Rozszerzenia warstwy ServiceModel są podłączone przy użyciu następujących zachowań:</span><span class="sxs-lookup"><span data-stu-id="ce3a0-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="ce3a0-138">Zachowania usługi: umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="ce3a0-139">Zachowania punktu końcowego: umożliwiają one dostosowanie określonego punktu końcowego usługi, w tym EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="ce3a0-140">Zachowania kontraktów: umożliwiają one dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas na klienta lub usługi odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="ce3a0-141">Zachowania operacji: Umożliwiają one dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> klas na kliencie lub usługi odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="ce3a0-142">Na potrzeby rozszerzenia buforowania obiektów można utworzyć zachowanie punktu końcowego lub zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="ce3a0-143">W tym przykładzie używamy zachowania usługi, która stosuje zdolność buforowania obiektów do każdego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="ce3a0-144">Zachowania usługi są tworzone przez <xref:System.ServiceModel.Description.IServiceBehavior> implementowanie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="ce3a0-145">Istnieje kilka sposobów, aby ServiceModel świadomość zachowań niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="ce3a0-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="ce3a0-146">Korzystanie z atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="ce3a0-147">Konieczne dodanie go do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="ce3a0-148">Rozszerzenie pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="ce3a0-149">W tym przykładzie użyto atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="ce3a0-150">Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, sprawdza atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="ce3a0-151">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` metody: i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="ce3a0-152">Metody te są wywoływane przez <xref:System.ServiceModel.ServiceHost> WCF podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="ce3a0-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>nazywa się pierwszy; pozwala na sprawdzenie usługi pod kątem niespójności.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="ce3a0-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>nazywa się dalej; ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="ce3a0-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>jest nazywany ostatni i jest odpowiedzialny za konfigurowanie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="ce3a0-156">Następujące parametry są <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>przekazywane do:</span><span class="sxs-lookup"><span data-stu-id="ce3a0-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="ce3a0-157">`Description`: Ten parametr zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="ce3a0-158">Może to służyć do sprawdzania danych opisu dotyczących punktów końcowych usługi, umów, powiązań i innych danych skojarzonych z usługą.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="ce3a0-159">`ServiceHostBase`: Ten parametr <xref:System.ServiceModel.ServiceHostBase> zapewnia, że jest obecnie inicjowany.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="ce3a0-160">W <xref:System.ServiceModel.Description.IServiceBehavior> implementacji niestandardowej nowe `ObjectPoolInstanceProvider` wystąpienie jest tworzone i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> przypisywane <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> do właściwości w <xref:System.ServiceModel.ServiceHostBase>każdym, który jest dołączony do .</span><span class="sxs-lookup"><span data-stu-id="ce3a0-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="ce3a0-161">Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji `ObjectPoolingAttribute` klasa ma kilka elementów członkowskich, aby dostosować pulę obiektów przy użyciu argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="ce3a0-162">Te elementy `MaxSize` `MinSize`członkowskie `Enabled` `CreationTimeout`obejmują , i , aby dopasować zestaw funkcji buforowania obiektów dostarczonych przez usługi .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="ce3a0-163">Zachowanie buforowania obiektów można teraz dodać do usługi WCF, dokonując adnotacji implementacji usługi za pomocą nowo utworzonego atrybutu niestandardowego. `ObjectPooling`</span><span class="sxs-lookup"><span data-stu-id="ce3a0-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="ce3a0-164">Aktywacja i dezaktywacja hakowania</span><span class="sxs-lookup"><span data-stu-id="ce3a0-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="ce3a0-165">Głównym celem buforowania obiektów jest optymalizacja obiektów krótkotrwałych przy stosunkowo kosztownym tworzeniu i inicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="ce3a0-166">W związku z tym może dać dramatyczny wzrost wydajności aplikacji, jeśli jest prawidłowo używany.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="ce3a0-167">Ponieważ obiekt jest zwracany z puli, konstruktor jest wywoływany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="ce3a0-168">Jednak niektóre aplikacje wymagają pewnego poziomu kontroli, dzięki czemu można zainicjować i oczyścić zasoby używane w jednym kontekście.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="ce3a0-169">Na przykład obiekt używany do zestawu obliczeń może zresetować swoje pola prywatne przed przetworzeniem następnego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="ce3a0-170">Usługi dla przedsiębiorstw włączyły tego rodzaju inicjalizację specyficzne `Activate` `Deactivate` dla kontekstu, zezwalając deweloperowi na zastępowanie obiektów i metody z klasy podstawowej. <xref:System.EnterpriseServices.ServicedComponent></span><span class="sxs-lookup"><span data-stu-id="ce3a0-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="ce3a0-171">Pula obiektów `Activate` wywołuje metodę tuż przed zwróceniem obiektu z puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="ce3a0-172">`Deactivate`jest wywoływana, gdy obiekt powraca do puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="ce3a0-173">Klasa <xref:System.EnterpriseServices.ServicedComponent> podstawowa ma `boolean` również `CanBePooled`właściwość o nazwie , która może służyć do powiadamiania puli, czy obiekt może być dalej łączony.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="ce3a0-174">Aby naśladować tę funkcję, w próbce`IObjectControl`deklaruje interfejs publiczny ( ), który ma wyżej wymienionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="ce3a0-175">Ten interfejs jest następnie implementowane przez klasy usług przeznaczone do zapewnienia inicjowania specyficzne dla kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="ce3a0-176">Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceProvider> musi zostać zmodyfikowana, aby spełnić te wymagania.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="ce3a0-177">Teraz za każdym razem, gdy `GetInstance` otrzymasz obiekt, wywołując metodę, `IObjectControl.` należy sprawdzić, czy `Activate` obiekt implementuje Jeśli tak, należy wywołać metodę odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="ce3a0-178">Podczas zwracania obiektu do puli, sprawdzanie jest `CanBePooled` wymagane dla właściwości przed dodaniem obiektu z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="ce3a0-179">Ponieważ deweloper usługi może zdecydować, czy obiekt może być łączony, liczba obiektów w puli w danym czasie może zejść poniżej minimalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="ce3a0-180">W związku z tym należy sprawdzić, czy liczba obiektów spadła poniżej minimalnego poziomu i wykonać niezbędne inicjowanie w procedurze oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="ce3a0-181">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ce3a0-182">Naciśnij klawisz Enter w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce3a0-183">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="ce3a0-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ce3a0-184">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3a0-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce3a0-185">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3a0-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ce3a0-186">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce3a0-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce3a0-187">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce3a0-188">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ce3a0-189">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce3a0-190">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce3a0-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
