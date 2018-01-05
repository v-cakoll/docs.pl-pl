---
title: Buforowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bdd1874004af1ebbde69c622853d5fdcd982005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pooling"></a>Buforowanie
W tym przykładzie pokazano, jak rozszerzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] do obsługi buforowanie obiektów. Przykład przedstawia sposób tworzenia atrybutu składnię i semantycznie podobny do `ObjectPoolingAttribute` atrybutu funkcji usług dla przedsiębiorstw. Buforowanie obiektu może zapewnić znaczne zwiększenie wydajności na wydajność aplikacji. Jednak jeśli nie jest prawidłowo używana może mieć odwrotny efekt. Buforowanie obiektu pomaga zmniejszyć koszty odtworzenie często używanych obiektów, które wymagają szeroką gamę inicjowania. Jednak jeśli wywołanie do metody w obiekcie puli przyjmuje znaczną ilość czasu, buforowanie obiektów kolejek dodatkowych żądań zaraz po osiągnięciu maksymalny rozmiar puli. W związku z tym może nie obsługiwać niektórych obiektów żądania tworzenia przez zgłaszanie wyjątków przekroczenia limitu czasu.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Pierwszym krokiem tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzenia jest określenie punkcie rozszerzenia do użycia.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] termin *dyspozytora* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołań metod w usłudze użytkownika i konwertowania wartości zwracanych z tej metody wychodzący Komunikat. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa tworzy dyspozytora dla każdego punktu końcowego. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, należy użyć dyspozytora kontrakt skojarzony z tego klienta jest kontraktu dwukierunkowego.  
  
 Dystrybucja kanału i punktu końcowego oferują kanału- i rozszerzalność całej kontraktu w przypadku wystawianego różne właściwości, które określają zachowanie Dyspozytor. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Właściwości umożliwia również sprawdzać, zmodyfikować lub dostosowania procesu wysyłania. W tym przykładzie koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość, która wskazuje obiekt, który zapewnia wystąpienia klasy usługi.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Dyspozytor tworzy wystąpienia przy użyciu klasy usługi <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu. Ten interfejs zawiera trzy metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Podczas wywołania dyspozytora nadejścia wiadomości <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę w celu utworzenia wystąpienia klasy usługi, aby przetworzyć komunikatu. Częstotliwość połączeń do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi służy do przetwarzania każdy komunikat przychodzący, dlatego <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana w momencie nadejścia wiadomości.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest taki sam jak poprzednie metody, z wyjątkiem to wywoływane, gdy istnieje żaden argument komunikatu.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Gdy upłynął okres istnienia wystąpienie usługi, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody. Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, częstotliwość wywołania do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Niestandardowy <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementacja udostępnia wymaganego obiektu buforowanie semantyki dla usługi. Ten przykład ma `ObjectPoolingInstanceProvider` typu, który udostępnia implementację niestandardowych <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do umieszczenia w puli. Gdy `Dispatcher` wywołania <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, zamiast tworzyć nowe wystąpienie implementacji niestandardowych szuka istniejący obiekt w puli w pamięci. Jeśli jest dostępny, jest zwracana. W przeciwnym razie jest tworzony nowy obiekt. Implementację `GetInstance` jest wyświetlany w następujący przykładowy kod.  
  
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
  
 Niestandardowa `ReleaseInstance` implementacji dodaje Zwolniono wystąpienie puli i zmniejsza `ActiveObjectsCount` wartość. `Dispatcher` Można wywołać metody te z różnych wątkach i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolingInstanceProvider` klasa jest wymagana.  
  
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
  
 `ReleaseInstance` Metoda zawiera funkcję "oczyszczania inicjowania". Zwykle puli obsługuje minimalną liczbę obiektów, dla okresu istnienia puli. Jednak może być okresów nadmiernego użycia, które wymaga tworzenia dodatkowe obiekty w puli do osiągnięcia maksymalnego limitu określonego w konfiguracji. Po pewnym czasie gdy puli staje się mniej aktywne, te pozostałe obiekty mogą stać się dodatkowego obciążenia. W związku z tym, kiedy `activeObjectsCount` osiągnie zero, czasomierza bezczynności została uruchomiona, który wyzwala i wykonuje cyklu czyszczenia.  
  
## <a name="adding-the-behavior"></a>Dodawanie zachowania  
 Rozszerzenia warstwie dyspozytora są podłączonymi przy użyciu następujących problemów:  
  
-   Zachowania usług. Umożliwiają one dostosowywania środowiska uruchomieniowego całej usługi.  
  
-   Zachowania punktu końcowego. Umożliwiają one dostosowywania punktów końcowych usługi, w szczególności kanału i Dyspozytor punktu końcowego.  
  
-   Zachowania kontraktu. Umożliwiają one dostosowywania, zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy odpowiednio na kliencie i usługi.  
  
 Na potrzeby buforowania rozszerzenie obiektu można utworzyć zachowania usługi. Zachowania usług są tworzone z zastosowaniem <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów uświadomić modelu usług niestandardowych zachowania:  
  
-   Przy użyciu atrybutu niestandardowego.  
  
-   Imperatively dodanie go do kolekcji zachowań opisu usługi.  
  
-   Rozszerzenie pliku konfiguracji.  
  
 W przykładzie użyto atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest tworzony poszczególne atrybuty, są używane w definicji typu usługi i dodaje zachowania dostępne do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody w-- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda służy do zapewnienia, że zachowanie może odnosić się do usługi. W tym przykładzie wdrożenia gwarantuje, że usługa nie jest skonfigurowany z <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania powiązań usługi. Nie jest wymagane w tym scenariuszu. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Służy do konfigurowania usługi dyspozytorów. Ta metoda jest wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany. Następujące parametry są przekazywane do tej metody:  
  
-   `Description`: Ten argument zawiera opis usługi dla całej usługi. Może być używany do zbadania opis danych dotyczących punktów końcowych usługi, kontrakty, powiązania i innych danych.  
  
-   `ServiceHostBase`: Ten argument zawiera <xref:System.ServiceModel.ServiceHostBase> który jest obecnie inicjowany.  
  
 W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji nowe wystąpienie elementu `ObjectPoolingInstanceProvider` to wystąpienie zostało utworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w obiektu ServiceHostBase.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka elementów członkowskich, aby dostosować puli obiektów przy użyciu argumentów atrybutu. Elementy te obejmują <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpowiadać obiektowi buforowanie zestaw funkcji udostępniane przez usługi .NET Enterprise.  
  
 Obiekt, buforowanie zachowanie można teraz dodać do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przez dodawanie adnotacji do implementacji usługi z nowo utworzonych niestandardowych `ObjectPooling` atrybutu.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 W przykładzie pokazano zwiększenia wydajności, które mogą zostać uzyskane przy użyciu buforowanie obiektów w niektórych scenariuszach.  
  
 Aplikacja usługi implementuje dwóch usług — `WorkService` i `ObjectPooledWorkService`. Zarówno usługi Udostępnianie tego samego wykonania — one zarówno wymagają inicjalizacji kosztowne i następnie uwidaczniaj `DoWork()` metody względnie niedrogie. Jedyną różnicą jest to, że `ObjectPooledWorkService` ma skonfigurowany buforowanie obiektów:  
  
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
  
 Po uruchomieniu klienta upłynie wywołania `WorkService` 5 razy. Następnie czasu wywołania `ObjectPooledWorkService` 5 razy. Różnica czasu są następnie wyświetlane:  
  
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
>  Klient jest uruchamiany po raz pierwszy obie te usługi są wyświetlane podjęcie o tej samej ilość czasu. Jeśli ponownie uruchomić przykład, można stwierdzić, że `ObjectPooledWorkService` zwraca znacznie szybsza, ponieważ istnieje już wystąpienie tego obiektu w puli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a>Zobacz też
