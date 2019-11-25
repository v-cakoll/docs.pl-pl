---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 44cd278fb0e48e07562b0b8ad52855b4a3f70761
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975860"
---
# <a name="instancing-initialization"></a>Tworzenie wystąpienia inicjowania
Ten przykład rozszerza przykład [puli](../../../../docs/framework/wcf/samples/pooling.md) przez zdefiniowanie interfejsu, `IObjectControl`, który dostosowuje inicjalizację obiektu przez aktywację i dezaktywowanie go. Klient wywołuje metody, które zwracają obiekt do puli i które nie zwracają obiektu do puli.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="extensibility-points"></a>Punkty rozszerzalności  
 Pierwszym krokiem tworzenia rozszerzenia Windows Communication Foundation (WCF) jest określenie punktu rozszerzalności, który ma być używany. W programie WCF termin *elemencie EndpointDispatcher* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy elemencie EndpointDispatcher dla każdego punktu końcowego.  
  
 Elemencie EndpointDispatcher oferuje zakres punktów końcowych (dla wszystkich komunikatów odebranych lub wysłanych przez usługę) przy użyciu klasy <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. Ta klasa pozwala dostosować różne właściwości kontrolujące zachowanie elemencie EndpointDispatcher. Ten przykład koncentruje się na właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 W programie WCF elemencie EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia implementującego interfejs <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Ten interfejs ma tylko dwie metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: po nadejściu komunikatu, Dyspozytor wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, aby utworzyć wystąpienie klasy usługi w celu przetworzenia komunikatu. Częstotliwość wywołań tej metody jest określana przez właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Na przykład jeśli właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi zostanie utworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: gdy wystąpienie usługi zakończy przetwarzanie komunikatu, elemencie EndpointDispatcher wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>. Podobnie jak w przypadku metody <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> częstotliwość wywołań tej metody jest określana przez właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Klasa `ObjectPoolInstanceProvider` zawiera implementację puli obiektów. Ta klasa implementuje interfejs <xref:System.ServiceModel.Dispatcher.IInstanceProvider>, aby można było korzystać z warstwy modelu usług. Gdy elemencie EndpointDispatcher wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jest dostępna, jest zwracana. W przeciwnym razie `ObjectPoolInstanceProvider` sprawdza, czy właściwość `ActiveObjectsCount` (liczba obiektów zwróconych z puli) osiągnęła maksymalny rozmiar puli. Jeśli nie, nowe wystąpienie jest tworzone i zwracane do obiektu wywołującego, a `ActiveObjectsCount` jest następnie zwiększane. W przeciwnym razie żądanie utworzenia obiektu jest umieszczane w kolejce przez skonfigurowany okres czasu. Implementacja dla `GetObjectFromThePool` jest pokazana w poniższym przykładowym kodzie.  
  
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
  
 Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza wartość `ActiveObjectsCount`. Elemencie EndpointDispatcher może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do elementów członkowskich na poziomie klasy w klasie `ObjectPoolInstanceProvider` jest wymagana.  
  
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
  
 Metoda `ReleaseInstance` zapewnia *oczyszczanie funkcji inicjalizacji* . Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Ostatecznie gdy pula stanie się mniej aktywne, te nadmiarowe obiekty mogą stać się dodatkowymi kosztami. W związku z tym, gdy `activeObjectsCount` osiągnie zero, uruchamiany jest czasomierz bezczynny, który wyzwala wyzwalacz i wykonuje oczyszczanie.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozszerzenia warstwy ServiceModel są podłączane przy użyciu następujących zachowań:  
  
- Zachowania usługi: umożliwiają dostosowanie całego środowiska uruchomieniowego usługi.  
  
- Zachowania punktów końcowych: umożliwiają one dostosowanie określonego punktu końcowego usługi, w tym elemencie EndpointDispatcher.  
  
- Zachowania kontraktowe: umożliwiają one dostosowanie <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas odpowiednio do klienta lub usługi.  
  
- Zachowania operacji: umożliwiają one dostosowanie klas <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> na kliencie lub w odpowiedniej usłudze.  
  
 Na potrzeby rozszerzenia puli obiektów można utworzyć zachowanie punktu końcowego lub zachowanie usługi. W tym przykładzie używamy zachowania usługi, która stosuje możliwość buforowania obiektów do każdego punktu końcowego usługi. Zachowania usługi są tworzone przez implementację interfejsu <xref:System.ServiceModel.Description.IServiceBehavior>. Istnieje kilka sposobów, aby dowiedzieć się, jak element ServiceModel ma wpływ na niestandardowe zachowania:  
  
- Przy użyciu atrybutu niestandardowego.  
  
- Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.  
  
- Rozszerzanie pliku konfiguracji.  
  
 Ten przykład używa atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Te metody są wywoływane przez funkcję WCF, gdy <xref:System.ServiceModel.ServiceHost> jest inicjowana. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> jest wywoływana jako pierwsza; pozwala ona na badanie niespójności usługi. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> jest wywoływana dalej; Ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> jest określany jako ostatni i jest odpowiedzialny za skonfigurowanie środowiska uruchomieniowego. Następujące parametry są przesyłane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
- `Description`: ten parametr zawiera opis usługi dla całej usługi. Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane skojarzone z usługą.  
  
- `ServiceHostBase`: ten parametr dostarcza <xref:System.ServiceModel.ServiceHostBase>, który jest aktualnie zainicjowany.  
  
 W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe wystąpienie `ObjectPoolInstanceProvider` jest tworzone i przypisywane do właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> w każdej <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączonej do <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Oprócz implementacji <xref:System.ServiceModel.Description.IServiceBehavior> Klasa `ObjectPoolingAttribute` ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów. Te elementy członkowskie obejmują `MaxSize`, `MinSize`, `Enabled` i `CreationTimeout`, aby dopasować zestaw funkcji buforowania obiektów zapewniany przez usługi .NET Enterprise.  
  
 Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF poprzez dodanie adnotacji do implementacji usługi z nowo utworzonym atrybutem `ObjectPooling` niestandardowego.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Podłączanie aktywacji i dezaktywacji  
 Głównym celem tworzenia pul obiektów jest Optymalizowanie długotrwałych obiektów przy stosunkowo kosztownym tworzeniu i inicjowaniu. W związku z tym może zapewnić znaczne zwiększenie wydajności aplikacji w razie potrzeby. Ponieważ obiekt jest zwracany z puli, Konstruktor jest wywoływany tylko raz. Niektóre aplikacje wymagają jednak pewnego poziomu kontroli, dzięki czemu mogą inicjować i czyścić zasoby używane w ramach jednego kontekstu. Na przykład obiekt używany na potrzeby zestawu obliczeń może zresetować swoje pola prywatne przed przetworzeniem kolejnego obliczenia. Usługi dla przedsiębiorstw obsługują ten rodzaj inicjalizacji specyficznej dla kontekstu, umożliwiając deweloperowi obiektu zastąpienie metod `Activate` i `Deactivate` z klasy podstawowej <xref:System.EnterpriseServices.ServicedComponent>.  
  
 Pula obiektów wywołuje metodę `Activate` tuż przed zwróceniem obiektu z puli. `Deactivate` jest wywoływana, gdy obiekt zwraca z powrotem do puli. Klasa bazowa <xref:System.EnterpriseServices.ServicedComponent> ma również właściwość `boolean` o nazwie `CanBePooled`, która może być używana do powiadamiania puli o tym, czy obiekt może być dodatkowo puli.  
  
 Aby naśladować tę funkcję, przykład deklaruje publiczny interfejs (`IObjectControl`), który ma wyżej wspomniane elementy członkowskie. Ten interfejs jest następnie implementowany przez klasy usług przeznaczone do zapewniania inicjalizacji specyficznej dla kontekstu. Aby spełnić te wymagania, należy zmodyfikować implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Teraz za każdym razem, gdy otrzymujesz obiekt, wywołując metodę `GetInstance`, należy sprawdzić, czy obiekt implementuje `IObjectControl.`, jeśli tak, należy odpowiednio wywołać metodę `Activate`.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Podczas zwracania obiektu do puli jest wymagane sprawdzenie właściwości `CanBePooled` przed dodaniem obiektu z powrotem do puli.  
  
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
  
 Ponieważ deweloper usług może zdecydować, czy obiekt może być w puli, liczba obiektów w puli w danym momencie może przekroczyć minimalny rozmiar. W związku z tym należy sprawdzić, czy liczba obiektów stała się poniżej minimalnego poziomu i wykonać niezbędne inicjowanie w procedurze oczyszczania.  
  
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
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
