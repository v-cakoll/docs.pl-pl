---
title: Niestandardowy okres istnienia
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809306"
---
# <a name="custom-lifetime"></a><span data-ttu-id="edb6c-102">Niestandardowy okres istnienia</span><span class="sxs-lookup"><span data-stu-id="edb6c-102">Custom Lifetime</span></span>
<span data-ttu-id="edb6c-103">W tym przykładzie pokazano, jak napisać rozszerzenia programu Windows Communication Foundation (WCF) do świadczenia usług Niestandardowy okres istnienia dla udostępnionego wystąpienia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="edb6c-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edb6c-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="edb6c-105">Udostępnione wystąpień</span><span class="sxs-lookup"><span data-stu-id="edb6c-105">Shared Instancing</span></span>  
 <span data-ttu-id="edb6c-106">Usługi WCF oferuje kilka wystąpień trybów dla swoich wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="edb6c-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="edb6c-107">Tryb udostępnionych wystąpień opisanych w tym temacie umożliwia współużytkują wystąpienie usługi, między wiele kanałów.</span><span class="sxs-lookup"><span data-stu-id="edb6c-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="edb6c-108">Klientów można rozpoznać adres punktu końcowego wystąpienia lokalnie lub skontaktuj się z metody fabryki w usłudze, aby uzyskać adres punktu końcowego uruchomionego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="edb6c-109">Po ma adres punktu końcowego, go utworzyć nowy kanał, a następnie uruchomić komunikacji.</span><span class="sxs-lookup"><span data-stu-id="edb6c-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="edb6c-110">Poniższy fragment kodu przedstawia, jak aplikacja kliencka tworzy nowy kanał do istniejącego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="edb6c-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="edb6c-111">W przeciwieństwie do innych wystąpień trybów udostępnionego trybu tworzenia ma unikatowy sposób zwolnienia wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="edb6c-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="edb6c-112">Zamknięcie wszystkich kanałów dla wystąpienia środowiska uruchomieniowego usługi WCF uruchamia czasomierz.</span><span class="sxs-lookup"><span data-stu-id="edb6c-112">When all the channels are closed for an instance, the service WCF runtime starts a timer.</span></span> <span data-ttu-id="edb6c-113">Jeśli nikt nie nawiązuje połączenie przed upłynięciem limitu czasu WCF zwalnia wystąpienie i oświadczeń zasobów.</span><span class="sxs-lookup"><span data-stu-id="edb6c-113">If nobody makes a connection before the timeout expires, WCF releases the instance and claims the resources.</span></span> <span data-ttu-id="edb6c-114">W ramach procedury usuwania wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody wszystkich <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacje przed zwolnieniem wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="edb6c-114">As a part of the teardown procedure WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="edb6c-115">Jeśli wszystkie z nich zwraca `true` wystąpienie zostanie zwolniony.</span><span class="sxs-lookup"><span data-stu-id="edb6c-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="edb6c-116">W przeciwnym razie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest odpowiedzialna za powiadomienie `Dispatcher` stanu bezczynności przy użyciu metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="edb6c-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="edb6c-117">Domyślnie wartość limitu czasu bezczynności <xref:System.ServiceModel.InstanceContext> jest jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="edb6c-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="edb6c-118">Jednak w przykładzie pokazano, jak można rozszerzyć użycie niestandardowego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="edb6c-119">Rozszerzanie obiekt InstanceContext</span><span class="sxs-lookup"><span data-stu-id="edb6c-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="edb6c-120">W programie WCF <xref:System.ServiceModel.InstanceContext> jest łącze między wystąpienie usługi i `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-120">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="edb6c-121">Usługi WCF umożliwia rozszerzenie tego składnika środowiska wykonawczego przez dodanie nowego stanu lub zachowania przy użyciu jego wzorzec rozszerzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-121">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="edb6c-122">Wzorzec extensible obiekt jest używany w programie WCF wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub dodawania nowych funkcji stanu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-122">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="edb6c-123">Istnieją trzy interfejsy we wzorcu obiektu extensible: `IExtensibleObject<T>`, `IExtension<T>`, i `IExtensionCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="edb6c-124">`IExtensibleObject<T>` Interfejs jest implementowany przez obiekty, aby zezwalać na rozszerzenia, które dostosowywanie ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="edb6c-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="edb6c-125">`IExtension<T>` Interfejs jest implementowany przez obiekty, które mogą być rozszerzenia klasy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="edb6c-126">I na koniec `IExtensionCollection<T>` interfejsu jest kolekcją `IExtensions` umożliwiająca pobierania `IExtensions` według typu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="edb6c-127">Dlatego aby rozszerzyć <xref:System.ServiceModel.InstanceContext> musi implementować `IExtension` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="edb6c-128">W tym projekcie próbki `CustomLeaseExtension` klasa zawiera tę implementację.</span><span class="sxs-lookup"><span data-stu-id="edb6c-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="edb6c-129">`IExtension` Interfejs ma dwie metody `Attach` i `Detach`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="edb6c-130">Jak oznaczać ich nazw, te dwie metody są wywołuje się, gdy środowisko uruchomieniowe dołącza i odłącza rozszerzenia na wystąpienie <xref:System.ServiceModel.InstanceContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="edb6c-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="edb6c-131">W tym przykładzie `Attach` metoda służy do śledzenia <xref:System.ServiceModel.InstanceContext> obiektu, który należy do bieżącego wystąpienia rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="edb6c-132">Ponadto należy dodać implementacji niezbędne do rozszerzenia, aby zapewnić obsługę rozszerzonej okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="edb6c-133">W związku z tym `ICustomLease` interfejsu jest zadeklarowany za pomocą metody żądaną i jest zaimplementowana w `CustomLeaseExtension` klasy.</span><span class="sxs-lookup"><span data-stu-id="edb6c-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="edb6c-134">Gdy wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody w <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacji tego wywołania jest kierowany do <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-134">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="edb6c-135">Następnie przy użyciu `CustomLeaseExtension` umożliwia sprawdzenie stanu prywatne, aby zobaczyć, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="edb6c-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="edb6c-136">Jeśli jest w stanie bezczynności go zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="edb6c-137">W przeciwnym razie uruchamia czasomierz określoną ilość rozszerzonej okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
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
  
 <span data-ttu-id="edb6c-138">W czasomierza `Elapsed` zdarzenie funkcja wywołania zwrotnego w Dyspozytorze jest wywoływane, aby można było uruchomić inną oczyszczania cyklu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="edb6c-139">Nie istnieje sposób odnowić czasomierza uruchomione po odebraniu nowego komunikatu dla tego wystąpienia jest przenoszony do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="edb6c-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="edb6c-140">Implementuje próbki <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> połączeń w celu przechwycenia <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodę i sposób ich do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="edb6c-141"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Wdrożenia jest zawarty w `CustomLifetimeLease` klasy.</span><span class="sxs-lookup"><span data-stu-id="edb6c-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="edb6c-142"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda jest wywoływana, gdy funkcja WCF została zwolniona wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="edb6c-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="edb6c-143">Istnieje jednak tylko jedno wystąpienie określonego `ISharedSessionInstance` implementacja ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="edb6c-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="edb6c-144">Oznacza to, nie istnieje sposób wiedzy <xref:System.ServiceModel.InstanceContext> zamknięte w czasie sprawdza WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="edb6c-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="edb6c-145">Dlatego w tym przykładzie użyto wątku blokowania do serializowania żądań <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="edb6c-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="edb6c-146">Używanie blokowania wątku nie jest zalecane podejście ponieważ serializacji mogą znacznie wpłynąć na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edb6c-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="edb6c-147">Zmienna prywatnego elementu członkowskiego jest używana `CustomLeaseExtension` klasę, aby śledzić `IsIdle` wartość.</span><span class="sxs-lookup"><span data-stu-id="edb6c-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="edb6c-148">Zawsze wartość <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> są pobierane `IsIdle` prywatnego elementu członkowskiego jest zwracana i przywrócenie `false`.</span><span class="sxs-lookup"><span data-stu-id="edb6c-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="edb6c-149">Istotne jest ta wartość `false` aby mieć pewność, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="edb6c-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="edb6c-150">Jeśli `ISharedSessionLifetime.IsIdle` zwraca `false` Dyspozytor rejestruje funkcję wywołania zwrotnego, za pomocą `NotifyIdle` metody.</span><span class="sxs-lookup"><span data-stu-id="edb6c-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="edb6c-151">Ta metoda odbiera odwołanie do <xref:System.ServiceModel.InstanceContext> został wydany.</span><span class="sxs-lookup"><span data-stu-id="edb6c-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="edb6c-152">W związku z tym przykładowym kodzie można zbadać `ICustomLease` rozszerzenie typu i sprawdź `ICustomLease.IsIdle` właściwości w rozszerzonym stanie.</span><span class="sxs-lookup"><span data-stu-id="edb6c-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
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
  
 <span data-ttu-id="edb6c-153">Przed `ICustomLease.IsIdle` właściwość jest zaznaczona właściwość wywołania zwrotnego musi być ustawiona, ponieważ jest to konieczne do `CustomLeaseExtension` powiadomiono dyspozytor, gdy stanie się bezczynności.</span><span class="sxs-lookup"><span data-stu-id="edb6c-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="edb6c-154">Jeśli `ICustomLease.IsIdle` zwraca `true`, `isIdle` prywatnego elementu członkowskiego po prostu znajduje się w `CustomLifetimeLease` do `true` i wywołuje metodę wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="edb6c-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="edb6c-155">Ponieważ kod utrzymuje blokadę, innych wątków nie można zmienić wartość tego elementu członkowskiego prywatnych.</span><span class="sxs-lookup"><span data-stu-id="edb6c-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="edb6c-156">I przy następnym sprawdza dyspozytora `ISharedSessionLifetime.IsIdle`, zwraca `true` i umożliwia dyspozytora wersji wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="edb6c-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="edb6c-157">Teraz, przygotowuje niestandardowe rozszerzenie zostało zakończone, musi on być podłączony do modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="edb6c-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="edb6c-158">Aby przyłączyć `CustomLeaseExtension` wykonania <xref:System.ServiceModel.InstanceContext>, zapewnia WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interfejsu przeprowadzić inicjowanie <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="edb6c-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="edb6c-159">W przykładzie `CustomLeaseInitializer` klasa implementuje ten interfejs i dodaje wystąpienie `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekcji od zainicjowania jedyną metodą.</span><span class="sxs-lookup"><span data-stu-id="edb6c-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="edb6c-160">Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="edb6c-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="edb6c-161">Na koniec `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` i <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> są implementacje argumentów podłączono do modelu usługi za pomocą <xref:System.ServiceModel.Description.IServiceBehavior> implementacji.</span><span class="sxs-lookup"><span data-stu-id="edb6c-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="edb6c-162">Ta implementacja jest umieszczany w `CustomLeaseTimeAttribute` klasy, a także pochodną `Attribute` klasy podstawowej na udostępnianie tego zachowania jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="edb6c-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="edb6c-163">W `IServiceBehavior.ApplyBehavior` metoda, wystąpień <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> i `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementacje są dodawane do `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> kolekcji <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="edb6c-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="edb6c-164">To zachowanie można dodać do klasy usługi próbki, adnotacji z `CustomLeaseTime` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="edb6c-165">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="edb6c-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="edb6c-166">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="edb6c-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="edb6c-167">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="edb6c-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="edb6c-168">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edb6c-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="edb6c-169">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edb6c-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="edb6c-170">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edb6c-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="edb6c-171">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="edb6c-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="edb6c-172">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="edb6c-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="edb6c-173">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="edb6c-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="edb6c-174">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="edb6c-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="edb6c-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edb6c-175">See Also</span></span>
