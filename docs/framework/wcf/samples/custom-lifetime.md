---
title: Niestandardowy okres istnienia
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715476"
---
# <a name="custom-lifetime"></a><span data-ttu-id="66a00-102">Niestandardowy okres istnienia</span><span class="sxs-lookup"><span data-stu-id="66a00-102">Custom lifetime</span></span>

<span data-ttu-id="66a00-103">Ten przykład pokazuje, jak napisać rozszerzenie Windows Communication Foundation (WCF), aby zapewnić niestandardowe usługi okresu istnienia dla udostępnionych wystąpień usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="66a00-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="66a00-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="66a00-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="66a00-105">Udostępnianie wystąpień</span><span class="sxs-lookup"><span data-stu-id="66a00-105">Shared instancing</span></span>

<span data-ttu-id="66a00-106">Funkcja WCF oferuje kilka trybów obsługi wystąpień usług.</span><span class="sxs-lookup"><span data-stu-id="66a00-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="66a00-107">Współużytkowany tryb obsługi wystąpień opisany w tym artykule zapewnia sposób udostępniania wystąpienia usługi między wieloma kanałami.</span><span class="sxs-lookup"><span data-stu-id="66a00-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="66a00-108">Klienci mogą skontaktować się z metodą fabryki w usłudze i utworzyć nowy kanał w celu rozpoczęcia komunikacji.</span><span class="sxs-lookup"><span data-stu-id="66a00-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="66a00-109">Poniższy fragment kodu przedstawia sposób tworzenia przez aplikację kliencką nowego kanału z istniejącym wystąpieniem usługi:</span><span class="sxs-lookup"><span data-stu-id="66a00-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="66a00-110">W przeciwieństwie do innych trybów wystąpienia, współużytkowany tryb wystąpienia ma unikatowy sposób zwalniania wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="66a00-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="66a00-111">Domyślnie, gdy wszystkie kanały są zamknięte dla <xref:System.ServiceModel.InstanceContext>, środowisko uruchomieniowe usługi WCF sprawdza, czy <xref:System.ServiceModel.InstanceContextMode> usługi jest skonfigurowany do <xref:System.ServiceModel.InstanceContextMode.PerCall> lub <xref:System.ServiceModel.InstanceContextMode.PerSession>, a jeśli tak, to zwalnia wystąpienie i przejmuje zasoby.</span><span class="sxs-lookup"><span data-stu-id="66a00-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="66a00-112">W przypadku użycia niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> WCF wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> implementacji dostawcy przed zwolnieniem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="66a00-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="66a00-113">Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> zwraca `true` wystąpienie zostanie wydane, w przeciwnym razie implementacja <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest odpowiedzialna za powiadamianie `Dispatcher` stanu bezczynności za pomocą metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="66a00-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="66a00-114">W tym celu należy wywołać metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> dostawcy.</span><span class="sxs-lookup"><span data-stu-id="66a00-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="66a00-115">Ten przykład pokazuje, jak można opóźnić zwolnienie <xref:System.ServiceModel.InstanceContext> z limitem czasu bezczynności wynoszącym 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="66a00-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="66a00-116">Rozszerzanie obiektu InstanceContext</span><span class="sxs-lookup"><span data-stu-id="66a00-116">Extending the InstanceContext</span></span>

<span data-ttu-id="66a00-117">W programie WCF <xref:System.ServiceModel.InstanceContext> jest łączem między wystąpieniem usługi i `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="66a00-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="66a00-118">Funkcja WCF umożliwia rozszerzanie tego składnika środowiska uruchomieniowego przez dodanie nowego stanu lub zachowanie przy użyciu jego wzorca rozszerzalnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="66a00-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="66a00-119">Rozszerzalny wzór obiektu jest używany w programie WCF do rozszerzania istniejących klas środowiska uruchomieniowego o nowe funkcje lub do dodawania nowych funkcji stanu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="66a00-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="66a00-120">W wzorcu rozszerzalnych obiektów istnieją trzy interfejsy: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>i <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="66a00-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="66a00-121">Interfejs <xref:System.ServiceModel.IExtensibleObject%601> jest implementowany przez obiekty, aby zezwalać na rozszerzenia, które dostosowują ich funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="66a00-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="66a00-122">Interfejs <xref:System.ServiceModel.IExtension%601> jest implementowany przez obiekty, które mogą być rozszerzeniami klas typu `T`.</span><span class="sxs-lookup"><span data-stu-id="66a00-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="66a00-123">A wreszcie interfejs <xref:System.ServiceModel.IExtensionCollection%601> jest zbiorem implementacji <xref:System.ServiceModel.IExtension%601>, które umożliwiają pobieranie implementacji <xref:System.ServiceModel.IExtension%601> przez ich typ.</span><span class="sxs-lookup"><span data-stu-id="66a00-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="66a00-124">W związku z tym, aby zwiększyć <xref:System.ServiceModel.InstanceContext>, należy zaimplementować interfejs <xref:System.ServiceModel.IExtension%601>.</span><span class="sxs-lookup"><span data-stu-id="66a00-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="66a00-125">W tym przykładowym projekcie Klasa `CustomLeaseExtension` zawiera tę implementację.</span><span class="sxs-lookup"><span data-stu-id="66a00-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="66a00-126">Interfejs <xref:System.ServiceModel.IExtension%601> ma dwie metody <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="66a00-127">Jak ich nazwy oznaczają, te dwie metody są wywoływane, gdy środowisko uruchomieniowe dołącza i odłącza rozszerzenie do wystąpienia klasy <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="66a00-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="66a00-128">W tym przykładzie metoda `Attach` służy do śledzenia obiektu <xref:System.ServiceModel.InstanceContext>, który należy do bieżącego wystąpienia rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="66a00-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="66a00-129">Ponadto należy dodać do rozszerzenia niezbędną implementację, aby zapewnić obsługę rozszerzonego okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="66a00-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="66a00-130">W związku z tym, interfejs `ICustomLease` jest zadeklarowany z żądanymi metodami i jest zaimplementowany w klasie `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="66a00-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="66a00-131">Gdy WCF wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> w implementacji <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, to wywołanie jest kierowane do metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="66a00-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="66a00-132">Następnie `CustomLeaseExtension` sprawdza stan prywatny, aby sprawdzić, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="66a00-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="66a00-133">Jeśli jest bezczynna, zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="66a00-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="66a00-134">W przeciwnym razie uruchamia czasomierz dla określonej ilości rozszerzonego okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="66a00-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="66a00-135">W zdarzeniu `Elapsed` czasomierza funkcja wywołania zwrotnego w dyspozytorze jest wywoływana w celu uruchomienia kolejnego cyklu oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="66a00-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="66a00-136">Nie ma możliwości odnowienia uruchomionego czasomierza po nadejściu nowej wiadomości dla wystąpienia przenoszonego do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="66a00-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="66a00-137">Przykład implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, aby przechwycić wywołania metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> i skierować je do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="66a00-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="66a00-138">Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest zawarta w klasie `CustomLifetimeLease`.</span><span class="sxs-lookup"><span data-stu-id="66a00-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="66a00-139">Metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> jest wywoływana, gdy WCF zostanie zwolnione wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="66a00-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="66a00-140">Istnieje jednak tylko jedno wystąpienie konkretnej `ISharedSessionInstance` implementacji w kolekcji <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> ServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="66a00-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="66a00-141">Oznacza to, że nie ma możliwości znajomości, czy <xref:System.ServiceModel.InstanceContext> jest zamknięte w czasie, gdy WCF sprawdzi metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="66a00-142">W związku z tym, ten przykład używa blokowania wątków do serializacji żądań do metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66a00-143">Używanie blokowania wątków nie jest zalecanym podejściem, ponieważ Serializacja może poważnie wpłynąć na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66a00-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="66a00-144">Pole prywatnego elementu członkowskiego jest używane w klasie `CustomLifetimeLease` do śledzenia stanu bezczynności i jest zwracane przez metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="66a00-145">Za każdym razem, gdy wywoływana jest metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, pole `isIdle` jest zwracane i resetowane do `false`.</span><span class="sxs-lookup"><span data-stu-id="66a00-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="66a00-146">Należy ustawić tę wartość na `false`, aby upewnić się, że Dyspozytor wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="66a00-147">Jeśli metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> zwraca `false`, Dyspozytor rejestruje funkcję wywołania zwrotnego za pomocą metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="66a00-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="66a00-148">Ta metoda odbiera odwołanie do wydanego <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="66a00-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="66a00-149">W związku z tym przykładowy kod może wysyłać zapytania do rozszerzenia typu `ICustomLease` i sprawdzać właściwość `ICustomLease.IsIdle` w stanie rozszerzonym.</span><span class="sxs-lookup"><span data-stu-id="66a00-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="66a00-150">Przed zasprawdzaniem właściwości `ICustomLease.IsIdle` należy ustawić właściwość wywołania zwrotnego, ponieważ jest to niezbędne dla `CustomLeaseExtension`, aby powiadomić dyspozytora, gdy przestanie być w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="66a00-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="66a00-151">Jeśli `ICustomLease.IsIdle` zwraca `true`, prywatny element członkowski `isIdle` jest po prostu ustawiany w `CustomLifetimeLease` do `true` i wywołania metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="66a00-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="66a00-152">Ponieważ kod przechowuje blokadę, inne wątki nie mogą zmienić wartości tego prywatnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="66a00-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="66a00-153">A następnym wywołaniem wywołującym <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>zwraca `true` i umożliwia dyspozytorowi zwolnienie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="66a00-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="66a00-154">Teraz, gdy podstawę dla niestandardowego rozszerzenia zostało zakończone, należy go podłączyć do modelu usług.</span><span class="sxs-lookup"><span data-stu-id="66a00-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="66a00-155">Aby podłączyć implementację `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext>, funkcja WCF udostępnia interfejs <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> do wykonania ładowania <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="66a00-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="66a00-156">W przykładzie Klasa `CustomLeaseInitializer` implementuje ten interfejs i dodaje wystąpienie `CustomLeaseExtension` do kolekcji <xref:System.ServiceModel.InstanceContext.Extensions%2A> z jedyną inicjalizacją metody.</span><span class="sxs-lookup"><span data-stu-id="66a00-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="66a00-157">Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="66a00-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="66a00-158">Na koniec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest podłączana do modelu usługi przy użyciu implementacji <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="66a00-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="66a00-159">Ta implementacja jest umieszczana w klasie `CustomLeaseTimeAttribute` i dziedziczy również z klasy bazowej <xref:System.Attribute>, aby uwidocznić to zachowanie jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="66a00-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="66a00-160">To zachowanie można dodać do przykładowej klasy usługi przez adnotację z atrybutem `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="66a00-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="66a00-161">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="66a00-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="66a00-162">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="66a00-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="66a00-163">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="66a00-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="66a00-164">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66a00-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="66a00-165">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66a00-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="66a00-166">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66a00-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66a00-167">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="66a00-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66a00-168">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="66a00-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="66a00-169">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66a00-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66a00-170">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="66a00-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
