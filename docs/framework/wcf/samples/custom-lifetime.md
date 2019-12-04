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
# <a name="custom-lifetime"></a>Niestandardowy okres istnienia

Ten przykład pokazuje, jak napisać rozszerzenie Windows Communication Foundation (WCF), aby zapewnić niestandardowe usługi okresu istnienia dla udostępnionych wystąpień usługi WCF.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego artykułu.

## <a name="shared-instancing"></a>Udostępnianie wystąpień

Funkcja WCF oferuje kilka trybów obsługi wystąpień usług. Współużytkowany tryb obsługi wystąpień opisany w tym artykule zapewnia sposób udostępniania wystąpienia usługi między wieloma kanałami. Klienci mogą skontaktować się z metodą fabryki w usłudze i utworzyć nowy kanał w celu rozpoczęcia komunikacji. Poniższy fragment kodu przedstawia sposób tworzenia przez aplikację kliencką nowego kanału z istniejącym wystąpieniem usługi:

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

W przeciwieństwie do innych trybów wystąpienia, współużytkowany tryb wystąpienia ma unikatowy sposób zwalniania wystąpień usługi. Domyślnie, gdy wszystkie kanały są zamknięte dla <xref:System.ServiceModel.InstanceContext>, środowisko uruchomieniowe usługi WCF sprawdza, czy <xref:System.ServiceModel.InstanceContextMode> usługi jest skonfigurowany do <xref:System.ServiceModel.InstanceContextMode.PerCall> lub <xref:System.ServiceModel.InstanceContextMode.PerSession>, a jeśli tak, to zwalnia wystąpienie i przejmuje zasoby. W przypadku użycia niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> WCF wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> implementacji dostawcy przed zwolnieniem wystąpienia. Jeśli <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> zwraca `true` wystąpienie zostanie wydane, w przeciwnym razie implementacja <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest odpowiedzialna za powiadamianie `Dispatcher` stanu bezczynności za pomocą metody wywołania zwrotnego. W tym celu należy wywołać metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> dostawcy.

Ten przykład pokazuje, jak można opóźnić zwolnienie <xref:System.ServiceModel.InstanceContext> z limitem czasu bezczynności wynoszącym 20 sekund.

## <a name="extending-the-instancecontext"></a>Rozszerzanie obiektu InstanceContext

W programie WCF <xref:System.ServiceModel.InstanceContext> jest łączem między wystąpieniem usługi i `Dispatcher`. Funkcja WCF umożliwia rozszerzanie tego składnika środowiska uruchomieniowego przez dodanie nowego stanu lub zachowanie przy użyciu jego wzorca rozszerzalnych obiektów. Rozszerzalny wzór obiektu jest używany w programie WCF do rozszerzania istniejących klas środowiska uruchomieniowego o nowe funkcje lub do dodawania nowych funkcji stanu do obiektu. W wzorcu rozszerzalnych obiektów istnieją trzy interfejsy: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>i <xref:System.ServiceModel.IExtensionCollection%601>.

Interfejs <xref:System.ServiceModel.IExtensibleObject%601> jest implementowany przez obiekty, aby zezwalać na rozszerzenia, które dostosowują ich funkcjonalność.

Interfejs <xref:System.ServiceModel.IExtension%601> jest implementowany przez obiekty, które mogą być rozszerzeniami klas typu `T`.

A wreszcie interfejs <xref:System.ServiceModel.IExtensionCollection%601> jest zbiorem implementacji <xref:System.ServiceModel.IExtension%601>, które umożliwiają pobieranie implementacji <xref:System.ServiceModel.IExtension%601> przez ich typ.

W związku z tym, aby zwiększyć <xref:System.ServiceModel.InstanceContext>, należy zaimplementować interfejs <xref:System.ServiceModel.IExtension%601>. W tym przykładowym projekcie Klasa `CustomLeaseExtension` zawiera tę implementację.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

Interfejs <xref:System.ServiceModel.IExtension%601> ma dwie metody <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>. Jak ich nazwy oznaczają, te dwie metody są wywoływane, gdy środowisko uruchomieniowe dołącza i odłącza rozszerzenie do wystąpienia klasy <xref:System.ServiceModel.InstanceContext>. W tym przykładzie metoda `Attach` służy do śledzenia obiektu <xref:System.ServiceModel.InstanceContext>, który należy do bieżącego wystąpienia rozszerzenia.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Ponadto należy dodać do rozszerzenia niezbędną implementację, aby zapewnić obsługę rozszerzonego okresu istnienia. W związku z tym, interfejs `ICustomLease` jest zadeklarowany z żądanymi metodami i jest zaimplementowany w klasie `CustomLeaseExtension`.

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

Gdy WCF wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> w implementacji <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, to wywołanie jest kierowane do metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension`. Następnie `CustomLeaseExtension` sprawdza stan prywatny, aby sprawdzić, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności. Jeśli jest bezczynna, zwraca `true`. W przeciwnym razie uruchamia czasomierz dla określonej ilości rozszerzonego okresu istnienia.

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

W zdarzeniu `Elapsed` czasomierza funkcja wywołania zwrotnego w dyspozytorze jest wywoływana w celu uruchomienia kolejnego cyklu oczyszczania.

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

Nie ma możliwości odnowienia uruchomionego czasomierza po nadejściu nowej wiadomości dla wystąpienia przenoszonego do stanu bezczynności.

Przykład implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, aby przechwycić wywołania metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> i skierować je do `CustomLeaseExtension`. Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> jest zawarta w klasie `CustomLifetimeLease`. Metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> jest wywoływana, gdy WCF zostanie zwolnione wystąpienie usługi. Istnieje jednak tylko jedno wystąpienie konkretnej `ISharedSessionInstance` implementacji w kolekcji <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> ServiceBehavior. Oznacza to, że nie ma możliwości znajomości, czy <xref:System.ServiceModel.InstanceContext> jest zamknięte w czasie, gdy WCF sprawdzi metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. W związku z tym, ten przykład używa blokowania wątków do serializacji żądań do metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.

> [!IMPORTANT]
> Używanie blokowania wątków nie jest zalecanym podejściem, ponieważ Serializacja może poważnie wpłynąć na wydajność aplikacji.

Pole prywatnego elementu członkowskiego jest używane w klasie `CustomLifetimeLease` do śledzenia stanu bezczynności i jest zwracane przez metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. Za każdym razem, gdy wywoływana jest metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, pole `isIdle` jest zwracane i resetowane do `false`.  Należy ustawić tę wartość na `false`, aby upewnić się, że Dyspozytor wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.

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

Jeśli metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> zwraca `false`, Dyspozytor rejestruje funkcję wywołania zwrotnego za pomocą metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>. Ta metoda odbiera odwołanie do wydanego <xref:System.ServiceModel.InstanceContext>. W związku z tym przykładowy kod może wysyłać zapytania do rozszerzenia typu `ICustomLease` i sprawdzać właściwość `ICustomLease.IsIdle` w stanie rozszerzonym.

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

Przed zasprawdzaniem właściwości `ICustomLease.IsIdle` należy ustawić właściwość wywołania zwrotnego, ponieważ jest to niezbędne dla `CustomLeaseExtension`, aby powiadomić dyspozytora, gdy przestanie być w stanie bezczynności. Jeśli `ICustomLease.IsIdle` zwraca `true`, prywatny element członkowski `isIdle` jest po prostu ustawiany w `CustomLifetimeLease` do `true` i wywołania metody wywołania zwrotnego. Ponieważ kod przechowuje blokadę, inne wątki nie mogą zmienić wartości tego prywatnego elementu członkowskiego. A następnym wywołaniem wywołującym <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>zwraca `true` i umożliwia dyspozytorowi zwolnienie wystąpienia.

Teraz, gdy podstawę dla niestandardowego rozszerzenia zostało zakończone, należy go podłączyć do modelu usług. Aby podłączyć implementację `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext>, funkcja WCF udostępnia interfejs <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> do wykonania ładowania <xref:System.ServiceModel.InstanceContext>. W przykładzie Klasa `CustomLeaseInitializer` implementuje ten interfejs i dodaje wystąpienie `CustomLeaseExtension` do kolekcji <xref:System.ServiceModel.InstanceContext.Extensions%2A> z jedyną inicjalizacją metody. Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Na koniec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest podłączana do modelu usługi przy użyciu implementacji <xref:System.ServiceModel.Description.IServiceBehavior>. Ta implementacja jest umieszczana w klasie `CustomLeaseTimeAttribute` i dziedziczy również z klasy bazowej <xref:System.Attribute>, aby uwidocznić to zachowanie jako atrybut.

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

To zachowanie można dodać do przykładowej klasy usługi przez adnotację z atrybutem `CustomLeaseTime`.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
