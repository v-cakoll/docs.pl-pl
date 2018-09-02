---
title: Niestandardowy okres istnienia
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467749"
---
# <a name="custom-lifetime"></a>Niestandardowy okres istnienia

Niniejszy przykład pokazuje, jak pisać rozszerzenia programu Windows Communication Foundation (WCF) do dostarczania usług Niestandardowy okres istnienia dla wystąpień udostępnionych usługi WCF.

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego artykułu.

## <a name="shared-instancing"></a>Udostępnione wystąpień

Usługi WCF oferuje kilka wystąpień trybów dla wystąpień usługi. Tryb udostępniania wystąpień omówione w tym artykule zawiera sposobem udostępniania wystąpienia usługi między wiele kanałów. Klienci mogą skontaktować się z metodą fabryki w usłudze i Utwórz nowy kanał, aby rozpocząć komunikacji. Poniższy fragment kodu przedstawia, jak aplikacja kliencka tworzy nowy kanał do istniejącego wystąpienia usługi:

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

W odróżnieniu od innych wystąpień trybów tryb wystąpień udostępniania ma unikatowy sposób przy zwalnianiu wystąpień usługi. Domyślnie po zamknięciu wszystkich kanałów dla <xref:System.ServiceModel.InstanceContext>, środowisko wykonawcze usług WCF sprawdza, czy usługa <xref:System.ServiceModel.InstanceContextMode> jest skonfigurowany do <xref:System.ServiceModel.InstanceContextMode.PerCall> lub <xref:System.ServiceModel.InstanceContextMode.PerSession>i, jeśli więc zwalnia wystąpienie i oświadczeń zasobów. Jeśli niestandardowa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest używany, wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda implementacja dostawcy, przed zwolnieniem wystąpienia. Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> zwraca `true` wystąpienie jest zwalniana, w przeciwnym razie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacji odpowiada za powiadamianie `Dispatcher` stanu bezczynności przy użyciu metody wywołania zwrotnego. Jest to realizowane przez wywołanie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metodę dostawcy.

Niniejszy przykład pokazuje, jak można opóźnić, zwalniając <xref:System.ServiceModel.InstanceContext> z przekroczeniem limitu czasu bezczynności wynoszącego 20 sekund.

## <a name="extending-the-instancecontext"></a>Rozszerzanie obiekt InstanceContext

W programie WCF <xref:System.ServiceModel.InstanceContext> stanowi połączenie między wystąpieniem usługi i `Dispatcher`. Usługi WCF umożliwia rozszerzenie tego składnika środowiska uruchomieniowego, dodając nowy stan lub zachowanie za pomocą jego wzorzec extensible object. Wzorzec extensible object jest używany w programie WCF, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodać nowe funkcje stan z obiektem. Istnieją trzy interfejsy we wzorcu extensible object: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, i <xref:System.ServiceModel.IExtensionCollection%601>.

<xref:System.ServiceModel.IExtensibleObject%601> Interfejs jest implementowany przez obiekty, aby umożliwić rozszerzeń, które ich funkcjonalność.

<xref:System.ServiceModel.IExtension%601> Interfejs jest implementowany przez obiekty, które mogą być rozszerzenia klas typu `T`.

I wreszcie <xref:System.ServiceModel.IExtensionCollection%601> interfejsu jest kolekcją <xref:System.ServiceModel.IExtension%601> implementacji, które umożliwia pobieranie implementację <xref:System.ServiceModel.IExtension%601> według ich typu.

W związku z tym aby rozszerzyć <xref:System.ServiceModel.InstanceContext>, należy zaimplementować <xref:System.ServiceModel.IExtension%601> interfejsu. W tym przykładowym projekcie `CustomLeaseExtension` klasa zawiera tę implementację.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> Interfejs ma dwie metody <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>. Jak sugerują nazwy te dwie metody są wywoływane, gdy środowisko uruchomieniowe dołącza odłącza rozszerzenia do wystąpienia programu <xref:System.ServiceModel.InstanceContext> klasy. W tym przykładzie `Attach` metoda służy do śledzenia <xref:System.ServiceModel.InstanceContext> obiektu, który należy do bieżącego wystąpienia rozszerzenia.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Ponadto należy dodać implementacji konieczne do rozszerzenia, aby zapewnić obsługę rozszerzonych okresu istnienia. W związku z tym `ICustomLease` interfejs jest zadeklarowana za pomocą metody żądaną i jest zaimplementowana w `CustomLeaseExtension` klasy.

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

Kiedy wywołuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in Class metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> wdrożenia, to wywołanie jest kierowane do <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody `CustomLeaseExtension`. Następnie `CustomLeaseExtension` umożliwia sprawdzenie stanu prywatny, aby zobaczyć, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności. Jeśli jest w stanie bezczynności, zwraca `true`. W przeciwnym razie uruchamia czasomierz, przez określony przedział rozszerzonego okresu istnienia.

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

Przez czasomierz `Elapsed` zdarzenie, funkcja wywołania zwrotnego w Dyspozytor jest wywoływane, aby można było uruchomić inny cyklu czyszczenia.

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

Nie ma możliwości odnowienia czasomierza uruchomione po nadejściu nowej wiadomości dla tego wystąpienia jest przenoszony do stanu bezczynności.

Implementuje próbki <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> przechwycenia wywołania <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody i kierować je do `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Wdrożenia jest zawarty w `CustomLifetimeLease` klasy. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda jest wywoływana, gdy ma wersji wystąpienia usługi WCF. Jednakże, istnieje tylko jedno wystąpienie określonego `ISharedSessionInstance` implementacji ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekcji. Oznacza to, nie ma żadnego sposobu, wiedząc, że jeśli <xref:System.ServiceModel.InstanceContext> jest zamknięty w czasie, sprawdza, czy WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody. W związku z tym, w tym przykładzie użyto wątku blokowania, aby serializować żądania <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.

> [!IMPORTANT]
> Za pomocą wątku blokowanie nie jest zalecane podejście ponieważ serializacji poważnie może mieć wpływ na wydajność aplikacji.

Pola prywatnego elementu członkowskiego jest używany w `CustomLifetimeLease` klasy do śledzenia stanu bezczynności i jest zwracany przez <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody. Każdorazowo <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda jest wywoływana, `isIdle` pola został zwrócony, a przywrócenie `false`.  Istotne jest, aby ustawić tę wartość na `false` aby upewnić się, że wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.

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

Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> metoda zwraca `false`, Dyspozytor rejestruje funkcję wywołania zwrotnego, za pomocą <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody. Ta metoda otrzymuje odwołanie do <xref:System.ServiceModel.InstanceContext> wydany. W związku z tym, można wykonać zapytanie w przykładowym kodzie `ICustomLease` wpisz rozszerzenie i sprawdź `ICustomLease.IsIdle` właściwość rozszerzonego stanu.

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

Przed `ICustomLease.IsIdle` właściwość jest zaznaczona, właściwości wywołania zwrotnego musi być ustawiona, ponieważ jest to istotne dla `CustomLeaseExtension` być powiadamiana Dyspozytor staje się nieaktywna. Jeśli `ICustomLease.IsIdle` zwraca `true`, `isIdle` prywatnego elementu członkowskiego jest po prostu ustaw `CustomLifetimeLease` do `true` i wywołuje metodę wywołania zwrotnego. Ponieważ kod posiada blokadę, inne wątki nie można zmienić wartość tego elementu członkowskiego prywatne. A przy następnym wywołuje dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, zwraca `true` i pozwala zwolnić wystąpienia dyspozytora.

Skoro przygotowawczych niestandardowego rozszerzenia zostanie zakończona, musi on być podłączony do modelu usługi. Aby zaczepić `CustomLeaseExtension` implementacji <xref:System.ServiceModel.InstanceContext>, zapewnia WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interfejsu przeprowadzić inicjowanie <xref:System.ServiceModel.InstanceContext>. W tym przykładzie `CustomLeaseInitializer` klasa implementuje ten interfejs i dodaje instancję `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekcji od inicjowania jedyną metodą. Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Na koniec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest podłączany do modelu usługi za pomocą <xref:System.ServiceModel.Description.IServiceBehavior> implementacji. Ta implementacja jest umieszczany w `CustomLeaseTimeAttribute` klasy, a także pochodzi od klasy `Attribute` klasy bazowej na udostępnianie tego zachowania jako atrybut.

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

To zachowanie można dodać do przykładową klasę usługi przez dodawanie adnotacji do ją za pomocą `CustomLeaseTime` atrybutu.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że zostały wykonane [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).

3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
