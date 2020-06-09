---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 82b81637deb0715d19109794348d2a2bcda7f0d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594624"
---
# <a name="pooling"></a>Buforowanie
W tym przykładzie pokazano, jak rozszerzając Windows Communication Foundation (WCF), aby obsługiwał buforowanie obiektów. W przykładzie pokazano, jak utworzyć atrybut, który jest syntaktycznie i semantycznie podobny do `ObjectPoolingAttribute` funkcji atrybutów usług przedsiębiorstwa. Buforowanie obiektów może stanowić znaczący wzrost wydajności aplikacji. Może jednak mieć odwrotny efekt, jeśli nie jest on używany prawidłowo. Buforowanie obiektów pomaga zmniejszyć obciążenie odtwarzania często używanych obiektów, które wymagają obszernej inicjalizacji. Jeśli jednak wywołanie metody w obiekcie w puli trwa znaczną ilość czasu, w przypadku osiągnięcia limitu maksymalnego rozmiaru puli obiekty będą kolejkować dodatkowe żądania. W ten sposób może nie obtworzyć niektórych żądań utworzenia obiektów przez wygenerowanie wyjątku limitu czasu.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Pierwszym krokiem tworzenia rozszerzenia WCF jest określenie punktu rozszerzalności, który ma być używany.  
  
 W programie WCF termin *dyspozytora* odnosi się do składnika czasu wykonywania, który jest odpowiedzialny za konwertowanie przychodzących komunikatów na wywołania metody w usłudze użytkownika i na potrzeby konwertowania wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy dyspozytora dla każdego punktu końcowego. Klient WCF musi użyć dyspozytora, jeśli kontrakt skojarzony z tym klientem jest kontraktem dwukierunkowym.  
  
 Dyspozytory kanału i punktu końcowego oferują rozszerzalność obejmującą wiele kanałów i kontraktu przez ujawnienie różnych właściwości, które kontrolują zachowanie wysyłania. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A>Właściwość umożliwia również sprawdzanie, modyfikowanie lub Dostosowywanie procesu wysyłania. Ten przykład koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości, która wskazuje na obiekt, który dostarcza wystąpienia klasy usługi.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 W programie WCF Dyspozytor tworzy wystąpienia klasy usługi przy użyciu <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> , która implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs. Ten interfejs ma trzy metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po nadejściu komunikatu przez dyspozytora wywoływana jest <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metoda tworzenia wystąpienia klasy usługi w celu przetworzenia komunikatu. Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Właściwość. Na przykład, jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall> nowe wystąpienie klasy usługi jest tworzone w celu przetworzenia każdego odebranego komunikatu, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest wywoływana za każdym razem, gdy wiadomość zostanie odebrana.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest taka sama jak w poprzedniej metodzie, z tą różnicą, że jest wywoływana, gdy nie ma argumentu Message.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upłynięciu okresu istnienia wystąpienia usługi Dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodę. Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Właściwość.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Implementacja niestandardowa <xref:System.ServiceModel.Dispatcher.IInstanceProvider> zapewnia wymaganą semantykę buforowania obiektów dla usługi. W związku z tym, ten przykład zawiera `ObjectPoolingInstanceProvider` Typ, który zapewnia niestandardową implementację <xref:System.ServiceModel.Dispatcher.IInstanceProvider> do buforowania. Gdy `Dispatcher` wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę, zamiast tworzyć nowe wystąpienie, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jest dostępna, jest zwracana. W przeciwnym razie tworzony jest nowy obiekt. Implementacja programu `GetInstance` jest pokazana w poniższym przykładowym kodzie.  
  
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
  
 Implementacja niestandardowa `ReleaseInstance` dodaje wydane wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość. `Dispatcher`Może wywoływać te metody z różnych wątków, w związku z czym synchronizacja dostępu do elementów członkowskich na poziomie klasy w `ObjectPoolingInstanceProvider` klasie jest wymagana.  
  
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
  
 `ReleaseInstance`Metoda zawiera funkcję "oczyszczanie inicjacji". Zwykle Pula utrzymuje minimalną liczbę obiektów w okresie istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają utworzenia dodatkowych obiektów w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Ostatecznie, gdy pula stanie się mniej aktywna, te nadwyżkowe obiekty mogą stać się dodatkowymi kosztami. W związku z tym, gdy `activeObjectsCount` osiągnie zero, uruchamiany jest czasomierz bezczynny, który wyzwala wyzwalacz i wykonuje oczyszczanie.  
  
## <a name="adding-the-behavior"></a>Dodawanie zachowania  
 Dyspozytor — rozszerzenia warstwy są podłączane przy użyciu następujących zachowań:  
  
- Zachowania usługi. Umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.  
  
- Zachowania punktów końcowych. Umożliwiają one dostosowanie punktów końcowych usługi, a w odniesieniu do kanału i dyspozytora punktów końcowych.  
  
- Zachowania kontraktu. Umożliwiają one odpowiednio dostosowanie obu <xref:System.ServiceModel.Dispatcher.ClientRuntime> klas i zarówno <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na kliencie, jak i w usłudze.  
  
 Na potrzeby rozszerzenia puli obiektów należy utworzyć zachowanie usługi. Zachowania usługi są tworzone przez implementację <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów, aby model usług był świadomy niestandardowych zachowań:  
  
- Przy użyciu atrybutu niestandardowego.  
  
- Należy je bezwzględnie dodać do kolekcji zachowań opisu usługi.  
  
- Rozszerzanie pliku konfiguracji.  
  
 Ten przykład używa atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, bada atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody w nim —,, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> . <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>Metoda jest używana w celu zapewnienia, że zachowanie można zastosować do usługi. W tym przykładzie implementacja zapewnia, że usługa nie jest skonfigurowana za pomocą programu <xref:System.ServiceModel.InstanceContextMode.Single> . Ta <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda służy do konfigurowania powiązań usługi. Nie jest to wymagane w tym scenariuszu. Służy <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> do konfigurowania nadawców usługi. Ta metoda jest wywoływana przez funkcję WCF, gdy <xref:System.ServiceModel.ServiceHost> jest inicjowana. Do tej metody są przesyłane następujące parametry:  
  
- `Description`: Ten argument zawiera opis usługi dla całej usługi. Można go użyć do sprawdzenia danych opisujących punkty końcowe, kontrakty, powiązania i inne dane dotyczące usługi.  
  
- `ServiceHostBase`: Ten argument zapewnia <xref:System.ServiceModel.ServiceHostBase> aktualnie inicjowany.  
  
 W implementacji niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> nowe wystąpienie `ObjectPoolingInstanceProvider` jest tworzone i przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości w każdym z <xref:System.ServiceModel.Dispatcher.DispatchRuntime> obiektu ServiceHostBase.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> Klasa ma kilku członków, aby dostosować pulę obiektów przy użyciu argumentów atrybutów. Te elementy członkowskie obejmują <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> , <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> i <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A> , aby dopasować zestaw funkcji buforowania obiektów zapewniany przez usługi .NET Enterprise.  
  
 Zachowanie tworzenia pul obiektów można teraz dodać do usługi WCF, dodając adnotację do implementacji usługi z nowo utworzonym atrybutem niestandardowym `ObjectPooling` .  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 W przykładzie przedstawiono korzyści z wydajności, które można uzyskać przy użyciu pul obiektów w niektórych scenariuszach.  
  
 Aplikacja usługi implementuje dwie usługi — `WorkService` i `ObjectPooledWorkService` . Obie usługi korzystają z tej samej implementacji — obie wymagają kosztownej inicjacji, a następnie uwidaczniają `DoWork()` metodę, która jest stosunkowo tani. Jedyną różnicą jest to, że `ObjectPooledWorkService` skonfigurowano pulę obiektów:  
  
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
  
 Po uruchomieniu klienta czas jest wywoływany `WorkService` 5 razy. Następnie czasy są wywoływane `ObjectPooledWorkService` 5 razy. Zostanie wyświetlona różnica w czasie:  
  
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
> Gdy klient jest uruchamiany po raz pierwszy, zostanie wyświetlona taka sama ilość czasu. Po ponownym uruchomieniu przykładu można zobaczyć, że `ObjectPooledWorkService` Funkcja zwraca dużo szybciej, ponieważ wystąpienie tego obiektu już istnieje w puli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!NOTE]
> Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
