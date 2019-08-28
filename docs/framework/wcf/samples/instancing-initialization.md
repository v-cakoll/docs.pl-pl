---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 4d6fdfedad9d522230a35014c0ee164e8b24fcfb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039610"
---
# <a name="instancing-initialization"></a>Tworzenie wystąpienia inicjowania
Ten przykład rozszerza przykład [puli](../../../../docs/framework/wcf/samples/pooling.md) przez zdefiniowanie interfejsu, `IObjectControl`, który dostosowuje inicjalizację obiektu przez aktywację i dezaktywowanie go. Klient wywołuje metody, które zwracają obiekt do puli i które nie zwracają obiektu do puli.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="extensibility-points"></a>Punkty rozszerzalności  
 Pierwszym krokiem tworzenia rozszerzenia Windows Communication Foundation (WCF) jest określenie punktu rozszerzalności, który ma być używany. W programie WCF termin *elemencie EndpointDispatcher* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy elemencie EndpointDispatcher dla każdego punktu końcowego.  
  
 Elemencie EndpointDispatcher oferuje zakres punktów końcowych (dla wszystkich komunikatów odebranych lub wysłanych przez usługę) przy <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> użyciu klasy. Ta klasa pozwala dostosować różne właściwości kontrolujące zachowanie elemencie EndpointDispatcher. Ten przykład koncentruje się <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> na właściwości, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 W programie WCF elemencie EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpień, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs. Ten interfejs ma tylko dwie metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Po nadejściu wiadomości Dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, aby utworzyć wystąpienie klasy usługi w celu przetworzenia komunikatu. Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi jest tworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Gdy wystąpienie usługi zakończy przetwarzanie komunikatu, elemencie EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metodę. Podobnie jak w <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodzie częstotliwość wywołań tej metody jest określana <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> przez właściwość.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 `ObjectPoolInstanceProvider` Klasa zawiera implementację dla puli obiektów. Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs do współpracy z warstwą modelu usług. Gdy elemencie EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jest dostępna, jest zwracana. W przeciwnym `ObjectPoolInstanceProvider` razie sprawdza, `ActiveObjectsCount` czy właściwość (liczba obiektów zwróconych z puli) osiągnęła maksymalny rozmiar puli. Jeśli nie, nowe wystąpienie jest tworzone i zwracane do obiektu wywołującego, `ActiveObjectsCount` a następnie zwiększa się. W przeciwnym razie żądanie utworzenia obiektu jest umieszczane w kolejce przez skonfigurowany okres czasu. Implementacja programu `GetObjectFromThePool` jest pokazana w poniższym przykładowym kodzie.  
  
```  
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
  
 Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość. Elemencie EndpointDispatcher może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do składowych na poziomie `ObjectPoolInstanceProvider` klasy w klasie jest wymagana.  
  
```  
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
  
 Metoda zapewnia funkcję *inicjowania oczyszczania.* `ReleaseInstance` Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Ostatecznie gdy pula stanie się mniej aktywne, te nadmiarowe obiekty mogą stać się dodatkowymi kosztami. W związku z `activeObjectsCount` tym, gdy osiągnie zero, uruchomiony jest czasomierz bezczynny, który wyzwala wyzwalacz i wykonuje czyszczenie.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozszerzenia warstwy ServiceModel są podłączane przy użyciu następujących zachowań:  
  
- Zachowania usługi: Umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.  
  
- Zachowania punktów końcowych: Umożliwiają one dostosowanie określonego punktu końcowego usługi, w tym elemencie EndpointDispatcher.  
  
- Zachowania kontraktowe: Umożliwiają one dostosowanie obu <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> tych klas odpowiednio do klienta lub usługi.  
  
- Zachowania operacji: Umożliwiają one dostosowanie obu <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> tych klas odpowiednio do klienta lub usługi.  
  
 Na potrzeby rozszerzenia puli obiektów można utworzyć zachowanie punktu końcowego lub zachowanie usługi. W tym przykładzie używamy zachowania usługi, która stosuje możliwość buforowania obiektów do każdego punktu końcowego usługi. Zachowania usługi są tworzone przez implementację <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów, aby dowiedzieć się, jak element ServiceModel ma wpływ na niestandardowe zachowania:  
  
- Przy użyciu atrybutu niestandardowego.  
  
- Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.  
  
- Rozszerzanie pliku konfiguracji.  
  
 Ten przykład używa atrybutu niestandardowego. <xref:System.ServiceModel.ServiceHost> Gdy jest konstruowany, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 `,` Interfejsma`,` trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>i. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> <xref:System.ServiceModel.Description.IServiceBehavior> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Te metody są wywoływane przez funkcję WCF, <xref:System.ServiceModel.ServiceHost> gdy jest inicjowana. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>jest wywoływana jako pierwszy; pozwala ona na badanie niespójności usługi. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>jest wywoływana dalej; Ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>jest określany jako ostatni i jest odpowiedzialny za skonfigurowanie środowiska uruchomieniowego. Następujące parametry są przesyłane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
- `Description`: Ten parametr zawiera opis usługi dla całej usługi. Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane skojarzone z usługą.  
  
- `ServiceHostBase`: Ten parametr zapewnia <xref:System.ServiceModel.ServiceHostBase> , że jest aktualnie inicjowany.  
  
 W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe `ObjectPoolInstanceProvider` wystąpienie jest tworzone i przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.ServiceHostBase>właściwości w każdym z nich <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączonym do.  
  
```  
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
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Oprócz`ObjectPoolingAttribute` implementacji Klasa ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów. Te elementy członkowskie `MaxSize`obejmują `MinSize` `Enabled` , i`CreationTimeout`, aby dopasować zestaw funkcji buforowania obiektów zapewniany przez usługi .NET Enterprise.  
  
 Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF, dodając adnotację do implementacji usługi z nowo utworzonym atrybutem `ObjectPooling` niestandardowym.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Podłączanie aktywacji i dezaktywacji  
 Głównym celem tworzenia pul obiektów jest Optymalizowanie długotrwałych obiektów przy stosunkowo kosztownym tworzeniu i inicjowaniu. W związku z tym może zapewnić znaczne zwiększenie wydajności aplikacji w razie potrzeby. Ponieważ obiekt jest zwracany z puli, Konstruktor jest wywoływany tylko raz. Niektóre aplikacje wymagają jednak pewnego poziomu kontroli, dzięki czemu mogą inicjować i czyścić zasoby używane w ramach jednego kontekstu. Na przykład obiekt używany na potrzeby zestawu obliczeń może zresetować swoje pola prywatne przed przetworzeniem kolejnego obliczenia. Usługi dla przedsiębiorstw obsługują ten rodzaj inicjalizacji specyficznej dla kontekstu, umożliwiając deweloperom `Activate` obiektów `Deactivate` zastępowanie i <xref:System.EnterpriseServices.ServicedComponent> metody z klasy bazowej.  
  
 Pula obiektów wywołuje `Activate` metodę tuż przed zwróceniem obiektu z puli. `Deactivate`jest wywoływana, gdy obiekt zwraca z powrotem do puli. Klasa bazowa ma również właściwość o nazwie `CanBePooled`, która może być używana do powiadamiania puli o tym, czy obiekt może być dodatkowo puli. `boolean` <xref:System.EnterpriseServices.ServicedComponent>  
  
 Aby naśladować tę funkcję, przykład deklaruje publiczny interfejs`IObjectControl`(), który ma wyżej wspomniane elementy członkowskie. Ten interfejs jest następnie implementowany przez klasy usług przeznaczone do zapewniania inicjalizacji specyficznej dla kontekstu. Implementację należy zmodyfikować, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> aby spełniała te wymagania. Teraz za każdym razem, gdy otrzymujesz obiekt przez wywołanie `GetInstance` metody, należy sprawdzić, czy obiekt implementuje `IObjectControl.` `Activate` , jeśli tak, należy wywołać metodę odpowiednio.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Podczas zwracania obiektu do puli należy sprawdzić, czy `CanBePooled` właściwość jest wymagana przed dodaniem obiektu z powrotem do puli.  
  
```  
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
  
```  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
