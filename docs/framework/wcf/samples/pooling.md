---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: ee57763674d194f71c85b1318dbb116dc829bd55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393310"
---
# <a name="pooling"></a>Buforowanie
Niniejszy przykład pokazuje, jak rozszerzyć Windows Communication Foundation (WCF) do obsługi buforowanie obiektu. W przykładzie pokazano, jak utworzyć atrybut, który przypomina składniowo i semantycznie `ObjectPoolingAttribute` atrybutu funkcjonalność usług dla przedsiębiorstw. Buforowanie obiektu może zapewnić znaczne zwiększenie wydajności na wydajność aplikacji. Jednak jeśli nie jest poprawnie użyty może mieć odwrotny efekt. Buforowanie obiektu pomaga zmniejszyć koszty ponowne utworzenie często używanych obiektów, które wymagają rozbudowane inicjowania. Jednak jeśli wywołanie metody do obiektu puli zajmuje znaczną ilość czasu na ukończenie, buforowanie obiektu kolejki dodatkowych żądań tak szybko, jak Osiągnięto maksymalny rozmiar puli. Ten sposób może nie obsługiwać żądania tworzenia obiektu zgłaszając wyjątek limitu czasu.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Pierwszym krokiem w tworzeniu rozszerzenia WCF jest podjęcie decyzji, punkt rozszerzeń do użycia.  
  
 W programie WCF termin *dyspozytora* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołania metody usługi przez użytkownika i konwertowania wartości zwracane z tej metody do wysyłanej wiadomości. Usługa WCF tworzy dyspozytora dla każdego punktu końcowego. Klienta programu WCF, należy użyć dyspozytora, jeśli kontrakt skojarzony z tego klienta jest kontraktu dwukierunkowego.  
  
 Dyspozytorów kanału i punktu końcowego oferują kanału — i rozszerzalność całej kontraktu, zapewniając różne właściwości, które kontrolują zachowanie Dyspozytor. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Właściwość umożliwia również sprawdzić, zmodyfikować lub dostosować proces wysyłania. Ten przykład koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości, który wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 W programie WCF, Dyspozytor tworzy wystąpienia klasy usługi za pomocą <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu. Ten interfejs zawiera trzy metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po umieszczeniu wywołania funkcji wysyłania komunikatu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę, aby utworzyć wystąpienie klasy usługi przetworzyć komunikatu. Częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi zostanie utworzona przetworzenie każdego komunikatu przychodzący, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana w momencie nadejścia wiadomości.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: To taka sama jak Poprzednia metoda, z wyjątkiem wywoływane po żadnego argumentu dla wiadomości.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upłynięciu okresu istnienia wystąpienia usługi, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody. Podobnie jak w przypadku dla <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Niestandardowy <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementacja udostępnia wymaganego obiektu buforowanie semantyki dla usługi. Ten przykład ma `ObjectPoolingInstanceProvider` typ, który zawiera niestandardową implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do umieszczenia w puli. Gdy `Dispatcher` wywołania <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa szuka istniejący obiekt w puli w pamięci. Jeśli jest dostępny, jest zwracany. W przeciwnym razie zostanie utworzony nowy obiekt. Wykonania na `GetInstance` przedstawiono w poniższym przykładowym kodzie.  
  
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
  
 Niestandardowy `ReleaseInstance` implementacji dodaje wydana wystąpienie do puli i zmniejsza `ActiveObjectsCount` wartość. `Dispatcher` Może wywoływać te metody z różnych wątków i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolingInstanceProvider` klasy jest wymagana.  
  
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
  
 `ReleaseInstance` Metoda udostępnia funkcję "oczyszczania inicjowania". Zwykle puli obsługuje minimalnej liczby obiektów, dla okresu istnienia puli. Jednak może być okresy nadmiernego użycia, które wymagają, tworząc dodatkowe obiekty w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Po pewnym czasie gdy pula staje się mniej aktywne, te obiekty nadwyżki może stać się dodatkowego obciążenia. W związku z tym, kiedy `activeObjectsCount` osiągnie wartość zero, czasomierza bezczynności została uruchomiona, który wyzwala i wykonuje cyklu czyszczenia.  
  
## <a name="adding-the-behavior"></a>Dodawanie zachowania  
 Rozszerzenia dyspozytorów warstwy są podłączone, wykonując następujące zachowania:  
  
-   Zachowania usługi. Umożliwiają one do dostosowywania środowiska uruchomieniowego całą usługę.  
  
-   Zachowania punktu końcowego. Umożliwiają one do dostosowywania punktów końcowych usługi, w szczególności kanału i wysyłający punktu końcowego.  
  
-   Zachowania kontraktu. Umożliwiają one do dostosowania obu <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy na kliencie i usługę, odpowiednio.  
  
 Na potrzeby buforowania rozszerzenie obiektu zachowanie usługi, musi zostać utworzona. Zachowania usług są tworzone przez zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów, aby uświadomić modelu usługi niestandardowe zachowania:  
  
-   Za pomocą atrybutu niestandardowego.  
  
-   Obowiązkowo dodanie go do kolekcji zachowań opisu usługi.  
  
-   Rozszerzenie pliku konfiguracji.  
  
 Ta próbka używa atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany poszczególne atrybuty, są używane w definicji typu usługi i zachowania dostępne są dodawane do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> zawiera trzy metody — <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda służy do zapewnienia, że zachowanie może być stosowana w usłudze. W tym przykładzie wdrożenia gwarantuje, że usługa nie jest skonfigurowana za pomocą <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania usługi powiązania. Nie jest wymagane w tym scenariuszu. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Służy do konfigurowania dyspozytorów tej usługi. Ta metoda jest wywoływana przez architekturę WCF podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany. Następujące parametry są przekazywane do tej metody:  
  
-   `Description`: Ten argument zawiera opis usługi dla całej usługi. To może służyć do opisu danych dotyczących punktów końcowych usługi, kontrakty, powiązania i inne dane inspekcji.  
  
-   `ServiceHostBase`: Ten argument zawiera <xref:System.ServiceModel.ServiceHostBase> , jest obecnie inicjowany.  
  
 W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji nowe wystąpienie elementu `ObjectPoolingInstanceProvider` jest tworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w ServiceHostBase.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka składowych, aby dostosować puli obiektów przy użyciu argumentów atrybutu. Te elementy Członkowskie zawierają <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpowiadać obiektowi buforowania zestawu funkcji udostępnianego przez usługi Enterprise .NET.  
  
 Zachowanie buforowania można teraz można dodać obiektu do usługi WCF przez dodawanie adnotacji do implementacji usługi przy użyciu nowo utworzony niestandardowy `ObjectPooling` atrybutu.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 W przykładzie pokazano korzyści w zakresie wydajności, które można uzyskać za pomocą buforowanie obiektów w niektórych scenariuszach.  
  
 Aplikacja usługi implementuje dwóch usług — `WorkService` i `ObjectPooledWorkService`. Zarówno usługi udostępniać tego samego wdrożenia — mogą wymagać kosztownych inicjowania i następnie udostępnić `DoWork()` metoda względnie niedrogie. Jedyną różnicą jest to, że `ObjectPooledWorkService` ma, skonfigurować buforowanie obiektu:  
  
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
  
 Po uruchomieniu klienta, czasu jego wywołania `WorkService` 5 razy. Następnie czasu wywołania `ObjectPooledWorkService` 5 razy. Różnica w czasie zostanie wyświetlona:  
  
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
>  Podczas pierwszego uruchomienia klienta obie te usługi są wyświetlane potrwać około tyle samo czasu. Jeśli ponownie uruchomić przykład, możesz zobaczyć, że `ObjectPooledWorkService` zwraca znacznie szybciej, ponieważ istnieje już wystąpienie tego obiektu w puli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a>Zobacz też
