---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 717dafb6ba9467590201511cbc0ac17690c931ae
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424283"
---
# <a name="pooling"></a>Buforowanie
W tym przykładzie pokazano, jak rozszerzając Windows Communication Foundation (WCF), aby obsługiwał buforowanie obiektów. W przykładzie pokazano, jak utworzyć atrybut, który jest syntaktycznie i semantycznie podobny do funkcji atrybutu `ObjectPoolingAttribute` usług przedsiębiorstwa. Buforowanie obiektów może stanowić znaczący wzrost wydajności aplikacji. Może jednak mieć odwrotny efekt, jeśli nie jest on używany prawidłowo. Buforowanie obiektów pomaga zmniejszyć obciążenie odtwarzania często używanych obiektów, które wymagają obszernej inicjalizacji. Jeśli jednak wywołanie metody w obiekcie w puli trwa znaczną ilość czasu, w przypadku osiągnięcia limitu maksymalnego rozmiaru puli obiekty będą kolejkować dodatkowe żądania. W ten sposób może nie obtworzyć niektórych żądań utworzenia obiektów przez wygenerowanie wyjątku limitu czasu.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Pierwszym krokiem tworzenia rozszerzenia WCF jest określenie punktu rozszerzalności, który ma być używany.  
  
 W programie WCF termin *dyspozytora* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy dyspozytora dla każdego punktu końcowego. Klient WCF musi użyć dyspozytora, jeśli kontrakt skojarzony z tym klientem jest kontraktem dwukierunkowym.  
  
 Dyspozytory kanału i punktu końcowego oferują rozszerzalność obejmującą wiele kanałów i kontraktu przez ujawnienie różnych właściwości, które kontrolują zachowanie wysyłania. Właściwość <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> umożliwia także inspekcję, modyfikowanie lub Dostosowywanie procesu wysyłania. Ten przykład koncentruje się na właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 W programie WCF Dyspozytor tworzy wystąpienia klasy usługi przy użyciu <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, który implementuje interfejs <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Ten interfejs ma trzy metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: po nadejściu komunikatu przez dyspozytora wywoływana jest metoda <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, aby utworzyć wystąpienie klasy usługi w celu przetworzenia komunikatu. Częstotliwość wywołań tej metody jest określana przez właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Na przykład, jeśli właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi zostanie utworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: jest identyczna z poprzednią metodą, z tą różnicą, że jest wywoływana, gdy nie ma argumentu Message.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: po upłynięciu okresu istnienia wystąpienia usługi Dyspozytor wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>. Podobnie jak w przypadku metody <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> częstotliwość wywołań tej metody jest określana na podstawie właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Niestandardowa implementacja <xref:System.ServiceModel.Dispatcher.IInstanceProvider> zapewnia wymaganą semantykę buforowania obiektów dla usługi. W związku z tym ten przykład ma `ObjectPoolingInstanceProvider` typ, który zapewnia niestandardową implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do buforowania. Gdy `Dispatcher` wywołuje metodę <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jest dostępna, jest zwracana. W przeciwnym razie tworzony jest nowy obiekt. Implementacja dla `GetInstance` jest pokazana w poniższym przykładowym kodzie.  
  
```csharp  
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
  
 Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza wartość `ActiveObjectsCount`. `Dispatcher` może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do elementów członkowskich na poziomie klasy w klasie `ObjectPoolingInstanceProvider` jest wymagana.  
  
```csharp  
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
  
 Metoda `ReleaseInstance` zapewnia funkcję "oczyszczanie inicjacji". Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Ostatecznie, gdy pula stanie się mniej aktywna, te nadwyżkowe obiekty mogą stać się dodatkowymi kosztami. W związku z tym, gdy `activeObjectsCount` osiągnie zero, uruchamiany jest czasomierz bezczynny, który wyzwala i wykonuje oczyszczanie.  
  
## <a name="adding-the-behavior"></a>Dodawanie zachowania  
 Dyspozytor — rozszerzenia warstwy są podłączane przy użyciu następujących zachowań:  
  
- Zachowania usługi. Umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.  
  
- Zachowania punktów końcowych. Umożliwiają one dostosowanie punktów końcowych usługi, a w odniesieniu do kanału i dyspozytora punktów końcowych.  
  
- Zachowania kontraktu. Umożliwiają one dostosowanie zarówno klas <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na kliencie, jak i w usłudze.  
  
 Na potrzeby rozszerzenia puli obiektów należy utworzyć zachowanie usługi. Zachowania usługi są tworzone przez implementację interfejsu <xref:System.ServiceModel.Description.IServiceBehavior>. Istnieje kilka sposobów, aby model usług był świadomy niestandardowych zachowań:  
  
- Przy użyciu atrybutu niestandardowego.  
  
- Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.  
  
- Rozszerzanie pliku konfiguracji.  
  
 Ten przykład używa atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest skonstruowana, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody w nim — <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> służy do upewnienia się, że zachowanie można zastosować do usługi. W tym przykładzie implementacja zapewnia, że usługa nie jest skonfigurowana przy użyciu <xref:System.ServiceModel.InstanceContextMode.Single>. Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> służy do konfigurowania powiązań usługi. Nie jest to wymagane w tym scenariuszu. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> służy do konfigurowania nadawców usługi. Ta metoda jest wywoływana przez funkcję WCF, gdy <xref:System.ServiceModel.ServiceHost> jest inicjowana. Do tej metody są przesyłane następujące parametry:  
  
- `Description`: ten argument zawiera opis usługi dla całej usługi. Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane dotyczące usługi.  
  
- `ServiceHostBase`: ten argument zapewnia <xref:System.ServiceModel.ServiceHostBase>, który jest aktualnie zainicjowany.  
  
 W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe wystąpienie `ObjectPoolingInstanceProvider` jest tworzone i przypisywane do właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w obiektu ServiceHostBase.  
  
```csharp  
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
                throttle ??= cd.ServiceThrottle;
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
  
 Oprócz implementacji <xref:System.ServiceModel.Description.IServiceBehavior> Klasa <xref:System.EnterpriseServices.ObjectPoolingAttribute> ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów. Te elementy członkowskie obejmują <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>w celu dopasowania do zestawu funkcji puli obiektów dostarczonego przez usługi .NET Enterprise.  
  
 Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF poprzez dodanie adnotacji do implementacji usługi z nowo utworzonym atrybutem `ObjectPooling` niestandardowego.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 W przykładzie przedstawiono korzyści z wydajności, które można uzyskać przy użyciu pul obiektów w niektórych scenariuszach.  
  
 Aplikacja usługi implementuje dwie usługi — `WorkService` i `ObjectPooledWorkService`. Obie usługi korzystają z tej samej implementacji — obie wymagają kosztownej inicjalizacji, a następnie uwidaczniają `DoWork()` metodę, która jest stosunkowo tani. Jedyną różnicą jest to, że `ObjectPooledWorkService` ma skonfigurowanych pul obiektów:  
  
```csharp  
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
  
 Po uruchomieniu klienta czas jest wywoływany `WorkService` 5 razy. Następnie czas wywoływania `ObjectPooledWorkService` 5 razy. Zostanie wyświetlona różnica w czasie:  
  
```console
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
> Gdy klient jest uruchamiany po raz pierwszy, zostanie wyświetlona taka sama ilość czasu. Po ponownym uruchomieniu przykładu można zobaczyć, że `ObjectPooledWorkService` zwraca dużo szybszy, ponieważ wystąpienie tego obiektu już istnieje w puli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
