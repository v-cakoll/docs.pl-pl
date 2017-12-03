---
title: Niestandardowy okres istnienia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2538a9c483b949dfef1c60bd2225f5daf4e01117
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-lifetime"></a>Niestandardowy okres istnienia
W tym przykładzie pokazano, jak napisać [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] rozszerzeniem w celu zapewnienia usług Niestandardowy okres istnienia współużytkowanych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpień usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="shared-instancing"></a>Udostępnione wystąpień  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferuje kilka wystąpień trybów dla swoich wystąpień usługi. Tryb udostępnionych wystąpień opisanych w tym temacie umożliwia współużytkują wystąpienie usługi, między wiele kanałów. Klientów można rozpoznać adres punktu końcowego wystąpienia lokalnie lub skontaktuj się z metody fabryki w usłudze, aby uzyskać adres punktu końcowego uruchomionego wystąpienia. Po ma adres punktu końcowego, go utworzyć nowy kanał, a następnie uruchomić komunikacji. Poniższy fragment kodu przedstawia, jak aplikacja kliencka tworzy nowy kanał do istniejącego wystąpienia usługi.  
  
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
  
 W przeciwieństwie do innych wystąpień trybów udostępnionego trybu tworzenia ma unikatowy sposób zwolnienia wystąpień usługi. Zamknięcia wszystkich kanałów dla wystąpienia usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego uruchamia czasomierz. Jeśli nikt nie nawiązuje połączenie przed upłynięciem limitu czasu, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zwalnia wystąpienie i oświadczeń zasobów. W ramach procedury usuwania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody wszystkich <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacje przed zwolnieniem wystąpienie. Jeśli wszystkie z nich zwraca `true` wystąpienie zostanie zwolniony. W przeciwnym razie <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacja jest odpowiedzialna za powiadomienie `Dispatcher` stanu bezczynności przy użyciu metody wywołania zwrotnego.  
  
 Domyślnie wartość limitu czasu bezczynności <xref:System.ServiceModel.InstanceContext> jest jedna minuta. Jednak w przykładzie pokazano, jak można rozszerzyć użycie niestandardowego rozszerzenia.  
  
## <a name="extending-the-instancecontext"></a>Rozszerzanie obiekt InstanceContext  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> jest łącze między wystąpienie usługi i `Dispatcher`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Umożliwia rozszerzenie tego składnika środowiska wykonawczego przez dodanie nowego stanu lub zachowania przy użyciu jego wzorzec rozszerzonego obiektu. Wzorzec extensible obiekt jest używany w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub dodawania nowych funkcji stanu do obiektu. Istnieją trzy interfejsy we wzorcu obiektu extensible: `IExtensibleObject<T>`, `IExtension<T>`, i `IExtensionCollection<T>`.  
  
 `IExtensibleObject<T>` Interfejs jest implementowany przez obiekty, aby zezwalać na rozszerzenia, które dostosowywanie ich funkcji.  
  
 `IExtension<T>` Interfejs jest implementowany przez obiekty, które mogą być rozszerzenia klasy typu `T`.  
  
 I na koniec `IExtensionCollection<T>` interfejsu jest kolekcją `IExtensions` umożliwiająca pobierania `IExtensions` według typu.  
  
 Dlatego aby rozszerzyć <xref:System.ServiceModel.InstanceContext> musi implementować `IExtension` interfejsu. W tym projekcie próbki `CustomLeaseExtension` klasa zawiera tę implementację.  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 `IExtension` Interfejs ma dwie metody `Attach` i `Detach`. Jak oznaczać ich nazw, te dwie metody są wywołuje się, gdy środowisko uruchomieniowe dołącza i odłącza rozszerzenia na wystąpienie <xref:System.ServiceModel.InstanceContext> klasy. W tym przykładzie `Attach` metoda służy do śledzenia <xref:System.ServiceModel.InstanceContext> obiektu, który należy do bieżącego wystąpienia rozszerzenia.  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 Ponadto należy dodać implementacji niezbędne do rozszerzenia, aby zapewnić obsługę rozszerzonej okres istnienia. W związku z tym `ICustomLease` interfejsu jest zadeklarowany za pomocą metody żądaną i jest zaimplementowana w `CustomLeaseExtension` klasy.  
  
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
  
 Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody w <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementacji tego wywołania jest kierowany do <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody `CustomLeaseExtension`. Następnie przy użyciu `CustomLeaseExtension` umożliwia sprawdzenie stanu prywatne, aby zobaczyć, czy <xref:System.ServiceModel.InstanceContext> jest w stanie bezczynności. Jeśli jest w stanie bezczynności go zwraca `true`. W przeciwnym razie uruchamia czasomierz określoną ilość rozszerzonej okres istnienia.  
  
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
  
 W czasomierza `Elapsed` zdarzenie funkcja wywołania zwrotnego w Dyspozytorze jest wywoływane, aby można było uruchomić inną oczyszczania cyklu.  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 Nie istnieje sposób odnowić czasomierza uruchomione po odebraniu nowego komunikatu dla tego wystąpienia jest przenoszony do stanu bezczynności.  
  
 Implementuje próbki <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> połączeń w celu przechwycenia <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodę i sposób ich do `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Wdrożenia jest zawarty w `CustomLifetimeLease` klasy. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda jest wywoływana po [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma wersji wystąpienia usługi. Istnieje jednak tylko jedno wystąpienie określonego `ISharedSessionInstance` implementacja ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekcji. Oznacza to, nie istnieje sposób wiedzy <xref:System.ServiceModel.InstanceContext> zamknięte w czasie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawdza <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody. Dlatego w tym przykładzie użyto wątku blokowania do serializowania żądań <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.  
  
> [!IMPORTANT]
>  Używanie blokowania wątku nie jest zalecane podejście ponieważ serializacji mogą znacznie wpłynąć na wydajność aplikacji.  
  
 Zmienna prywatnego elementu członkowskiego jest używana `CustomLeaseExtension` klasę, aby śledzić `IsIdle` wartość. Zawsze wartość <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> są pobierane `IsIdle` prywatnego elementu członkowskiego jest zwracana i przywrócenie `false`. Istotne jest ta wartość `false` aby mieć pewność, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.  
  
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
  
 Jeśli `ISharedSessionLifetime.IsIdle` zwraca `false` Dyspozytor rejestruje funkcję wywołania zwrotnego, za pomocą `NotifyIdle` metody. Ta metoda odbiera odwołanie do <xref:System.ServiceModel.InstanceContext> został wydany. W związku z tym przykładowym kodzie można zbadać `ICustomLease` rozszerzenie typu i sprawdź `ICustomLease.IsIdle` właściwości w rozszerzonym stanie.  
  
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
  
 Przed `ICustomLease.IsIdle` właściwość jest zaznaczona właściwość wywołania zwrotnego musi być ustawiona, ponieważ jest to konieczne do `CustomLeaseExtension` powiadomiono dyspozytor, gdy stanie się bezczynności. Jeśli `ICustomLease.IsIdle` zwraca `true`, `isIdle` prywatnego elementu członkowskiego po prostu znajduje się w `CustomLifetimeLease` do `true` i wywołuje metodę wywołania zwrotnego. Ponieważ kod utrzymuje blokadę, innych wątków nie można zmienić wartość tego elementu członkowskiego prywatnych. I przy następnym sprawdza dyspozytora `ISharedSessionLifetime.IsIdle`, zwraca `true` i umożliwia dyspozytora wersji wystąpienia.  
  
 Teraz, przygotowuje niestandardowe rozszerzenie zostało zakończone, musi on być podłączony do modelu usługi. Aby przyłączyć `CustomLeaseExtension` wykonania <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interfejsu przeprowadzić inicjowanie <xref:System.ServiceModel.InstanceContext>. W przykładzie `CustomLeaseInitializer` klasa implementuje ten interfejs i dodaje wystąpienie `CustomLeaseExtension` do <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekcji od zainicjowania jedyną metodą. Ta metoda jest wywoływana przez dyspozytora podczas inicjowania <xref:System.ServiceModel.InstanceContext>.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 Na koniec `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` i <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> są implementacje argumentów podłączono do modelu usługi za pomocą <xref:System.ServiceModel.Description.IServiceBehavior> implementacji. Ta implementacja jest umieszczany w `CustomLeaseTimeAttribute` klasy, a także pochodną `Attribute` klasy podstawowej na udostępnianie tego zachowania jako atrybut. W `IServiceBehavior.ApplyBehavior` metoda, wystąpień <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> i `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementacje są dodawane do `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> kolekcji <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> odpowiednio.  
  
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
  
 To zachowanie można dodać do klasy usługi próbki, adnotacji z `CustomLeaseTime` atrybutu.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>Zobacz też
