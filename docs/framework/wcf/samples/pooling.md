---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: a6d0ea8705721b707dd4c70673c36c5a122d0f09
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045508"
---
# <a name="pooling"></a><span data-ttu-id="cdc86-102">Buforowanie</span><span class="sxs-lookup"><span data-stu-id="cdc86-102">Pooling</span></span>
<span data-ttu-id="cdc86-103">W tym przykładzie pokazano, jak rozszerzając Windows Communication Foundation (WCF), aby obsługiwał buforowanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="cdc86-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="cdc86-104">W przykładzie pokazano, jak utworzyć atrybut, który jest syntaktycznie i semantycznie podobny do `ObjectPoolingAttribute` funkcji atrybutów usług przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="cdc86-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="cdc86-105">Buforowanie obiektów może stanowić znaczący wzrost wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdc86-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="cdc86-106">Może jednak mieć odwrotny efekt, jeśli nie jest on używany prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="cdc86-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="cdc86-107">Buforowanie obiektów pomaga zmniejszyć obciążenie odtwarzania często używanych obiektów, które wymagają obszernej inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="cdc86-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="cdc86-108">Jeśli jednak wywołanie metody w obiekcie w puli trwa znaczną ilość czasu, w przypadku osiągnięcia limitu maksymalnego rozmiaru puli obiekty będą kolejkować dodatkowe żądania.</span><span class="sxs-lookup"><span data-stu-id="cdc86-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="cdc86-109">W ten sposób może nie obtworzyć niektórych żądań utworzenia obiektów przez wygenerowanie wyjątku limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdc86-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cdc86-111">Pierwszym krokiem tworzenia rozszerzenia WCF jest określenie punktu rozszerzalności, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="cdc86-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="cdc86-112">W programie WCF termin *dyspozytora* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący.</span><span class="sxs-lookup"><span data-stu-id="cdc86-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="cdc86-113">Usługa WCF tworzy dyspozytora dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cdc86-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="cdc86-114">Klient WCF musi użyć dyspozytora, jeśli kontrakt skojarzony z tym klientem jest kontraktem dwukierunkowym.</span><span class="sxs-lookup"><span data-stu-id="cdc86-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="cdc86-115">Dyspozytory kanału i punktu końcowego oferują rozszerzalność obejmującą wiele kanałów i kontraktu przez ujawnienie różnych właściwości, które kontrolują zachowanie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="cdc86-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="cdc86-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Właściwość umożliwia również sprawdzanie, modyfikowanie lub Dostosowywanie procesu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="cdc86-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="cdc86-117">Ten przykład koncentruje się <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> na właściwości, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="cdc86-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="cdc86-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="cdc86-119">W programie WCF Dyspozytor tworzy wystąpienia klasy usługi przy użyciu <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, która <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="cdc86-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="cdc86-120">Ten interfejs ma trzy metody:</span><span class="sxs-lookup"><span data-stu-id="cdc86-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="cdc86-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po nadejściu wiadomości przez dyspozytora wywoływana jest <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metoda tworzenia wystąpienia klasy usługi w celu przetworzenia komunikatu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="cdc86-122">Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="cdc86-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="cdc86-123">Na przykład, jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi jest tworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.</span><span class="sxs-lookup"><span data-stu-id="cdc86-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="cdc86-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest to identyczna z poprzednią metodą, z tą różnicą, że jest wywoływana, gdy nie ma argumentu Message.</span><span class="sxs-lookup"><span data-stu-id="cdc86-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="cdc86-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upływie okresu istnienia wystąpienia usługi Dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodę.</span><span class="sxs-lookup"><span data-stu-id="cdc86-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="cdc86-126">Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody częstotliwość wywołań tej metody jest określana <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="cdc86-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="cdc86-127">Pula obiektów</span><span class="sxs-lookup"><span data-stu-id="cdc86-127">The Object Pool</span></span>  
 <span data-ttu-id="cdc86-128">Implementacja niestandardowa <xref:System.ServiceModel.Dispatcher.IInstanceProvider> zapewnia wymaganą semantykę buforowania obiektów dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="cdc86-129">W związku z tym, ten `ObjectPoolingInstanceProvider` przykład zawiera typ, który zapewnia <xref:System.ServiceModel.Dispatcher.IInstanceProvider> niestandardową implementację do buforowania.</span><span class="sxs-lookup"><span data-stu-id="cdc86-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="cdc86-130">`Dispatcher` Gdy<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> wywołuje metodę, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cdc86-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="cdc86-131">Jeśli jest dostępna, jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="cdc86-131">If one is available, it is returned.</span></span> <span data-ttu-id="cdc86-132">W przeciwnym razie tworzony jest nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="cdc86-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="cdc86-133">Implementacja programu `GetInstance` jest pokazana w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cdc86-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="cdc86-134">Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość.</span><span class="sxs-lookup"><span data-stu-id="cdc86-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="cdc86-135">Może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do elementów członkowskich na poziomie `ObjectPoolingInstanceProvider` klasy w klasie jest wymagana. `Dispatcher`</span><span class="sxs-lookup"><span data-stu-id="cdc86-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="cdc86-136">`ReleaseInstance` Metoda zawiera funkcję "oczyszczanie inicjacji".</span><span class="sxs-lookup"><span data-stu-id="cdc86-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="cdc86-137">Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli.</span><span class="sxs-lookup"><span data-stu-id="cdc86-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="cdc86-138">Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdc86-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="cdc86-139">Ostatecznie, gdy pula stanie się mniej aktywna, te nadwyżkowe obiekty mogą stać się dodatkowymi kosztami.</span><span class="sxs-lookup"><span data-stu-id="cdc86-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="cdc86-140">W związku z `activeObjectsCount` tym, gdy osiągnie zero, uruchamiany jest czasomierz bezczynny, który wyzwala wyzwalacz i wykonuje oczyszczanie.</span><span class="sxs-lookup"><span data-stu-id="cdc86-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="cdc86-141">Dodawanie zachowania</span><span class="sxs-lookup"><span data-stu-id="cdc86-141">Adding the Behavior</span></span>  
 <span data-ttu-id="cdc86-142">Dyspozytor — rozszerzenia warstwy są podłączane przy użyciu następujących zachowań:</span><span class="sxs-lookup"><span data-stu-id="cdc86-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="cdc86-143">Zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-143">Service Behaviors.</span></span> <span data-ttu-id="cdc86-144">Umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="cdc86-145">Zachowania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="cdc86-145">Endpoint Behaviors.</span></span> <span data-ttu-id="cdc86-146">Umożliwiają one dostosowanie punktów końcowych usługi, a w odniesieniu do kanału i dyspozytora punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="cdc86-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="cdc86-147">Zachowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-147">Contract Behaviors.</span></span> <span data-ttu-id="cdc86-148">Umożliwiają one odpowiednio dostosowanie obu klas i <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> zarówno na kliencie, jak i w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cdc86-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="cdc86-149">Na potrzeby rozszerzenia puli obiektów należy utworzyć zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="cdc86-150">Zachowania usługi są tworzone przez implementację <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="cdc86-151">Istnieje kilka sposobów, aby model usług był świadomy niestandardowych zachowań:</span><span class="sxs-lookup"><span data-stu-id="cdc86-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="cdc86-152">Przy użyciu atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cdc86-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="cdc86-153">Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="cdc86-154">Rozszerzanie pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdc86-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="cdc86-155">Ten przykład używa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cdc86-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="cdc86-156">Gdy jest <xref:System.ServiceModel.ServiceHost> konstruowany, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="cdc86-157">Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody w nim <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>—, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdc86-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="cdc86-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda jest używana w celu zapewnienia, że zachowanie można zastosować do usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="cdc86-159">W tym przykładzie implementacja zapewnia, że usługa nie jest skonfigurowana za pomocą <xref:System.ServiceModel.InstanceContextMode.Single>programu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="cdc86-160">Ta <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania powiązań usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="cdc86-161">Nie jest to wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-161">It is not required in this scenario.</span></span> <span data-ttu-id="cdc86-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Służy do konfigurowania nadawców usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="cdc86-163">Ta metoda jest wywoływana przez funkcję WCF, <xref:System.ServiceModel.ServiceHost> gdy jest inicjowana.</span><span class="sxs-lookup"><span data-stu-id="cdc86-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="cdc86-164">Do tej metody są przesyłane następujące parametry:</span><span class="sxs-lookup"><span data-stu-id="cdc86-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="cdc86-165">`Description`: Ten argument zawiera opis usługi dla całej usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="cdc86-166">Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="cdc86-167">`ServiceHostBase`: Ten argument zapewnia <xref:System.ServiceModel.ServiceHostBase> , że jest aktualnie inicjowany.</span><span class="sxs-lookup"><span data-stu-id="cdc86-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="cdc86-168">W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe `ObjectPoolingInstanceProvider` wystąpienie jest tworzone i przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> z obiektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="cdc86-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="cdc86-169"><xref:System.ServiceModel.Description.IServiceBehavior> Oprócz<xref:System.EnterpriseServices.ObjectPoolingAttribute> implementacji Klasa ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="cdc86-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="cdc86-170">Te elementy członkowskie <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>obejmują <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby dopasować zestaw funkcji buforowania obiektów zapewniany przez usługi .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="cdc86-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="cdc86-171">Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF, dodając adnotację do implementacji usługi z nowo utworzonym atrybutem `ObjectPooling` niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="cdc86-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="cdc86-172">Uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="cdc86-172">Running the Sample</span></span>  
 <span data-ttu-id="cdc86-173">W przykładzie przedstawiono korzyści z wydajności, które można uzyskać przy użyciu pul obiektów w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="cdc86-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="cdc86-174">Aplikacja usługi implementuje dwie usługi — `WorkService` i. `ObjectPooledWorkService`</span><span class="sxs-lookup"><span data-stu-id="cdc86-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="cdc86-175">Obie usługi korzystają z tej samej implementacji — obie wymagają kosztownej inicjacji, a następnie `DoWork()` uwidaczniają metodę, która jest stosunkowo tani.</span><span class="sxs-lookup"><span data-stu-id="cdc86-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="cdc86-176">Jedyną różnicą jest to, `ObjectPooledWorkService` że skonfigurowano pulę obiektów:</span><span class="sxs-lookup"><span data-stu-id="cdc86-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="cdc86-177">Po uruchomieniu klienta czas jest wywoływany `WorkService` 5 razy.</span><span class="sxs-lookup"><span data-stu-id="cdc86-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="cdc86-178">Następnie czasy są `ObjectPooledWorkService` wywoływane 5 razy.</span><span class="sxs-lookup"><span data-stu-id="cdc86-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="cdc86-179">Zostanie wyświetlona różnica w czasie:</span><span class="sxs-lookup"><span data-stu-id="cdc86-179">The difference in time is then displayed:</span></span>  
  
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
> <span data-ttu-id="cdc86-180">Gdy klient jest uruchamiany po raz pierwszy, zostanie wyświetlona taka sama ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="cdc86-181">Po ponownym uruchomieniu przykładu można zobaczyć, że `ObjectPooledWorkService` funkcja zwraca dużo szybciej, ponieważ wystąpienie tego obiektu już istnieje w puli.</span><span class="sxs-lookup"><span data-stu-id="cdc86-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cdc86-182">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="cdc86-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cdc86-183">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdc86-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cdc86-184">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdc86-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cdc86-185">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdc86-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdc86-186">Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="cdc86-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cdc86-187">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cdc86-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cdc86-188">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="cdc86-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cdc86-189">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="cdc86-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cdc86-190">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cdc86-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
