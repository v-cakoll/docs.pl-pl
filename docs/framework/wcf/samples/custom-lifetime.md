---
title: Niestandardowy okres istnienia
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: be6013d568e3625c5eac7e0c145db7df1c6917e3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410384"
---
# <a name="custom-lifetime"></a><span data-ttu-id="c7809-102">Niestandardowy okres istnienia</span><span class="sxs-lookup"><span data-stu-id="c7809-102">Custom lifetime</span></span>

<span data-ttu-id="c7809-103">Niniejszy przykład pokazuje, jak pisać rozszerzenia programu Windows Communication Foundation (WCF) do dostarczania usług Niestandardowy okres istnienia dla wystąpień udostępnionych usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c7809-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="c7809-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="c7809-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="c7809-105">Udostępnione wystąpień</span><span class="sxs-lookup"><span data-stu-id="c7809-105">Shared instancing</span></span>

<span data-ttu-id="c7809-106">Usługi WCF oferuje kilka wystąpień trybów dla wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="c7809-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="c7809-107">Tryb udostępniania wystąpień omówione w tym artykule zawiera sposobem udostępniania wystąpienia usługi między wiele kanałów.</span><span class="sxs-lookup"><span data-stu-id="c7809-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="c7809-108">Klienci mogą skontaktować się z metodą fabryki w usłudze i Utwórz nowy kanał, aby rozpocząć komunikacji.</span><span class="sxs-lookup"><span data-stu-id="c7809-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="c7809-109">Poniższy fragment kodu przedstawia, jak aplikacja kliencka tworzy nowy kanał do istniejącego wystąpienia usługi:</span><span class="sxs-lookup"><span data-stu-id="c7809-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

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

<span data-ttu-id="c7809-110">W odróżnieniu od innych wystąpień trybów tryb wystąpień udostępniania ma unikatowy sposób przy zwalnianiu wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="c7809-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="c7809-111">Domyślnie po zamknięciu wszystkich kanałów dla <xref:System.ServiceModel.InstanceContext>, środowisko wykonawcze usług WCF sprawdza, czy usługa <xref:System.ServiceModel.InstanceContextMode> jest skonfigurowany do <xref:System.ServiceModel.InstanceContextMode.PerCall> lub <xref:System.ServiceModel.InstanceContextMode.PerSession>i, jeśli więc zwalnia wystąpienie i oświadczeń zasobów.</span><span class="sxs-lookup"><span data-stu-id="c7809-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="c7809-112">Jeśli niestandardowa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest używany, wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda implementacja dostawcy, przed zwolnieniem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c7809-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="c7809-113">Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> zwraca `true` wystąpienie jest zwalniana, w przeciwnym razie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacji odpowiada za powiadamianie `Dispatcher` stanu bezczynności przy użyciu metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c7809-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="c7809-114">Jest to realizowane przez wywołanie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metodę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c7809-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="c7809-115">Niniejszy przykład pokazuje, jak można opóźnić, zwalniając <xref:System.ServiceModel.InstanceContext> z przekroczeniem limitu czasu bezczynności wynoszącego 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="c7809-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="c7809-116">Rozszerzanie obiekt InstanceContext</span><span class="sxs-lookup"><span data-stu-id="c7809-116">Extending the InstanceContext</span></span>

<span data-ttu-id="c7809-117">W programie WCF <xref:System.ServiceModel.InstanceContext> stanowi połączenie między wystąpieniem usługi i `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="c7809-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="c7809-118">Usługi WCF umożliwia rozszerzenie tego składnika środowiska uruchomieniowego, dodając nowy stan lub zachowanie za pomocą jego wzorzec extensible object.</span><span class="sxs-lookup"><span data-stu-id="c7809-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="c7809-119">Wzorzec extensible object jest używany w programie WCF, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodać nowe funkcje stan z obiektem.</span><span class="sxs-lookup"><span data-stu-id="c7809-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="c7809-120">Istnieją trzy interfejsy we wzorcu extensible object: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, i <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="c7809-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="c7809-121"><xref:System.ServiceModel.IExtensibleObject%601> Interfejs jest implementowany przez obiekty, aby umożliwić rozszerzeń, które ich funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="c7809-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="c7809-122"><xref:System.ServiceModel.IExtension%601> Interfejs jest implementowany przez obiekty, które mogą być rozszerzenia klas typu `T`.</span><span class="sxs-lookup"><span data-stu-id="c7809-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="c7809-123">I wreszcie <xref:System.ServiceModel.IExtensionCollection%601> interfejsu jest kolekcją <xref:System.ServiceModel.IExtension%601> implementacji, które umożliwia pobieranie implementację <xref:System.ServiceModel.IExtension%601> według ich typu.</span><span class="sxs-lookup"><span data-stu-id="c7809-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="c7809-124">W związku z tym aby rozszerzyć <xref:System.ServiceModel.InstanceContext>, należy zaimplementować <xref:System.ServiceModel.IExtension%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c7809-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="c7809-125">W tym przykładowym projekcie `CustomLeaseExtension` klasa zawiera tę implementację.</span><span class="sxs-lookup"><span data-stu-id="c7809-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="c7809-126"><xref:System.ServiceModel.IExtension%601> Interfejs ma dwie metody <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7809-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="c7809-127">Jak sugerują nazwy te dwie metody są wywoływane, gdy środowisko uruchomieniowe dołącza odłącza rozszerzenia do wystąpienia programu <xref:System.ServiceModel.InstanceContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7809-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="c7809-128">W tym przykładzie `Attach` metoda służy do śledzenia <xref:System.ServiceModel.InstanceContext> obiektu, który należy do bieżącego wystąpienia rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c7809-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="c7809-129">Ponadto należy dodać implementacji konieczne do rozszerzenia, aby zapewnić obsługę rozszerzonych okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="c7809-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="c7809-130">W związku z tym `ICustomLease` interfejs jest zadeklarowana za pomocą metody żądaną i jest zaimplementowana w `CustomLeaseExtension` klasy.</span><span class="sxs-lookup"><span data-stu-id="c7809-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

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

<span data-ttu-id="c7809-131">Kiedy wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in Class metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> wdrożenia, to wywołanie jest kierowane do <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="c7809-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="c7809-132">Następnie `CustomLeaseExtension` umożliwia sprawdzenie stanu prywatny, aby zobaczyć, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="c7809-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="c7809-133">Jeśli jest w stanie bezczynności, zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="c7809-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="c7809-134">W przeciwnym razie uruchamia czasomierz, przez określony przedział rozszerzonego okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="c7809-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

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

<span data-ttu-id="c7809-135">Przez czasomierz `Elapsed` zdarzenie, funkcja wywołania zwrotnego w Dyspozytor jest wywoływane, aby można było uruchomić inny cyklu czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="c7809-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

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

<span data-ttu-id="c7809-136">Nie ma możliwości odnowienia czasomierza uruchomione po nadejściu nowej wiadomości dla tego wystąpienia jest przenoszony do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="c7809-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="c7809-137">Implementuje próbki <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> przechwycenia wywołania <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody i kierować je do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="c7809-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="c7809-138"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Wdrożenia jest zawarty w `CustomLifetimeLease` klasy.</span><span class="sxs-lookup"><span data-stu-id="c7809-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="c7809-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda jest wywoływana, gdy ma wersji wystąpienia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c7809-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="c7809-140">Jednakże, istnieje tylko jedno wystąpienie określonego `ISharedSessionInstance` implementacji ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c7809-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="c7809-141">Oznacza to, nie ma żadnego sposobu, wiedząc, że jeśli <xref:System.ServiceModel.InstanceContext> jest zamknięty w czasie, sprawdza, czy WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7809-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="c7809-142">W związku z tym, w tym przykładzie użyto wątku blokowania, aby serializować żądania <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7809-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7809-143">Za pomocą wątku blokowanie nie jest zalecane podejście ponieważ serializacji poważnie może mieć wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7809-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="c7809-144">Pola prywatnego elementu członkowskiego jest używany w `CustomLifetimeLease` klasy do śledzenia stanu bezczynności i jest zwracany przez <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7809-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="c7809-145">Każdorazowo <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda jest wywoływana, `isIdle` pola został zwrócony, a przywrócenie `false`.</span><span class="sxs-lookup"><span data-stu-id="c7809-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="c7809-146">Istotne jest, aby ustawić tę wartość na `false` aby upewnić się, że wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7809-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

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

<span data-ttu-id="c7809-147">Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> metoda zwraca `false`, Dyspozytor rejestruje funkcję wywołania zwrotnego, za pomocą <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7809-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="c7809-148">Ta metoda otrzymuje odwołanie do <xref:System.ServiceModel.InstanceContext> wydany.</span><span class="sxs-lookup"><span data-stu-id="c7809-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="c7809-149">W związku z tym, można wykonać zapytanie w przykładowym kodzie `ICustomLease` wpisz rozszerzenie i sprawdź `ICustomLease.IsIdle` właściwość rozszerzonego stanu.</span><span class="sxs-lookup"><span data-stu-id="c7809-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

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

<span data-ttu-id="c7809-150">Przed `ICustomLease.IsIdle` właściwość jest zaznaczona, właściwości wywołania zwrotnego musi być ustawiona, ponieważ jest to istotne dla `CustomLeaseExtension` być powiadamiana Dyspozytor staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="c7809-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="c7809-151">Jeśli `ICustomLease.IsIdle` zwraca `true`, `isIdle` prywatnego elementu członkowskiego jest po prostu ustaw `CustomLifetimeLease` do `true` i wywołuje metodę wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c7809-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="c7809-152">Ponieważ kod posiada blokadę, inne wątki nie można zmienić wartość tego elementu członkowskiego prywatne.</span><span class="sxs-lookup"><span data-stu-id="c7809-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="c7809-153">A przy następnym wywołuje dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, zwraca `true` i pozwala zwolnić wystąpienia dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="c7809-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="c7809-154">Skoro przygotowawczych niestandardowego rozszerzenia zostanie zakończona, musi on być podłączony do modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="c7809-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="c7809-155">Aby zaczepić `CustomLeaseExtension` implementacji <xref:System.ServiceModel.InstanceContext>, zapewnia WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interfejsu przeprowadzić inicjowanie <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="c7809-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="c7809-156">W tym przykładzie `CustomLeaseInitializer` klasa implementuje ten interfejs i dodaje instancję `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekcji od inicjowania jedyną metodą.</span><span class="sxs-lookup"><span data-stu-id="c7809-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="c7809-157">Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="c7809-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="c7809-158">Na koniec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest podłączany do modelu usługi za pomocą <xref:System.ServiceModel.Description.IServiceBehavior> implementacji.</span><span class="sxs-lookup"><span data-stu-id="c7809-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="c7809-159">Ta implementacja jest umieszczany w `CustomLeaseTimeAttribute` klasy, a także pochodzi od klasy <xref:System.Attribute> klasy bazowej na udostępnianie tego zachowania jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="c7809-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

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

<span data-ttu-id="c7809-160">To zachowanie można dodać do przykładową klasę usługi przez dodawanie adnotacji do ją za pomocą `CustomLeaseTime` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c7809-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="c7809-161">Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="c7809-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c7809-162">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="c7809-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7809-163">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c7809-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c7809-164">Upewnij się, że zostały wykonane [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7809-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c7809-165">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7809-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="c7809-166">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7809-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7809-167">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c7809-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7809-168">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c7809-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c7809-169">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c7809-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7809-170">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c7809-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
