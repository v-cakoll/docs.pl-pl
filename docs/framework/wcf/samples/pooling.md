---
title: Buforowanie
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183404"
---
# <a name="pooling"></a>Buforowanie
W tym przykładzie pokazano, jak rozszerzyć Program Windows Communication Foundation (WCF) do obsługi buforowania obiektów. W przykładzie pokazano, jak utworzyć atrybut, który jest syntaktycznie `ObjectPoolingAttribute` i semantycznie podobny do funkcji atrybutu enterprise services. Buforowanie obiektów może zapewnić dramatyczny wzrost wydajności aplikacji. Jednak może mieć odwrotny skutek, jeśli nie jest prawidłowo stosowany. Buforowanie obiektów pomaga zmniejszyć obciążenie związane z odtwarzaniem często używanych obiektów, które wymagają rozbudowanej inicjalizacji. Jednak jeśli wywołanie metody na obiekcie puli zajmuje dużo czasu, aby zakończyć, buforowanie obiektów kolejkuje dodatkowe żądania, gdy tylko zostanie osiągnięty maksymalny rozmiar puli. W związku z tym może nie służyć niektóre żądania tworzenia obiektów, zgłaszając wyjątek limitu czasu.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Pierwszym krokiem w tworzeniu rozszerzenia WCF jest podjęcie decyzji o punkt rozszerzalności do użycia.  
  
 W WCF termin *dyspozytor* odnosi się do składnika czasu wykonywania odpowiedzialnego za konwertowanie wiadomości przychodzących na wywołania metody w usłudze użytkownika i za konwertowanie wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy dyspozytora dla każdego punktu końcowego. Klient WCF musi używać dyspozytora, jeśli umowa skojarzona z tym klientem jest umową dupleksu.  
  
 Dyspozytorzy kanału i punktu końcowego oferują rozszerzalność całego kanału i umowy, ujawniając różne właściwości, które kontrolują zachowanie dyspozytora. Właściwość <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> umożliwia również sprawdzanie, modyfikowanie lub dostosowywanie procesu wysyłki. Ten przykład koncentruje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> się na właściwość, która wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.  
  
## <a name="the-iinstanceprovider"></a>The IInstanceProvider  
 W WCF dyspozytor tworzy wystąpienia klasy <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>usługi przy użyciu <xref:System.ServiceModel.Dispatcher.IInstanceProvider> , który implementuje interfejs. Ten interfejs ma trzy metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Po odebraniu komunikatu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> Dyspozytor wywołuje metodę, aby utworzyć wystąpienie klasy usługi do przetwarzania wiadomości. Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość <xref:System.ServiceModel.InstanceContextMode.PerCall> jest ustawiona na nowe wystąpienie klasy usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> jest tworzony do przetwarzania każdej wiadomości, która nadejdzie, więc jest wywoływana za każdym razem, gdy pojawia się komunikat.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jest to identyczne z poprzednią metodą, z tą różnicą, że jest wywoływana, gdy nie ma żadnego argumentu Message.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po upłynięciu okresu istnienia wystąpienia usługi, Dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodę. Podobnie jak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> w przypadku metody, częstotliwość wywołań tej <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody jest określana przez właściwość.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceProvider> niestandardowa zapewnia semantyka buforowania wymaganych obiektów dla usługi. W związku z tym `ObjectPoolingInstanceProvider` ten przykład ma <xref:System.ServiceModel.Dispatcher.IInstanceProvider> typ, który zapewnia niestandardową implementację do buforowania. Gdy `Dispatcher` wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodę, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jeden jest dostępny, jest zwracany. W przeciwnym razie tworzony jest nowy obiekt. Implementacja `GetInstance` dla jest pokazana w poniższym przykładowym kodzie.  
  
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
  
 Implementacja `ReleaseInstance` niestandardowa dodaje zwolnione wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość. Można `Dispatcher` wywołać te metody z różnych wątków, a zatem wymagany `ObjectPoolingInstanceProvider` jest zsynchronizowany dostęp do elementów członkowskich poziomu klasy w klasie.  
  
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
  
 Metoda `ReleaseInstance` zapewnia funkcję "oczyszczania inicjowania". Zwykle pula utrzymuje minimalną liczbę obiektów przez cały okres istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają tworzenia dodatkowych obiektów w puli, aby osiągnąć maksymalny limit określony w konfiguracji. Ostatecznie, gdy pula staje się mniej aktywne, te nadwyżki obiektów może stać się dodatkowym obciążeniem. W związku z `activeObjectsCount` tym po osiągnięciu zera, czasomierz bezczynny jest uruchamiany, który wyzwala i wykonuje cykl oczyszczania.  
  
## <a name="adding-the-behavior"></a>Dodawanie zachowania  
 Rozszerzenia warstwy dyspozytora są podłączone przy użyciu następujących zachowań:  
  
- Zachowania usługi. Umożliwiają one dostosowanie całego środowiska wykonawczego usługi.  
  
- Zachowania punktu końcowego. Umożliwiają one dostosowanie punktów końcowych usługi, w szczególności dyspozytora kanału i punktu końcowego.  
  
- Zachowania kontraktowe. Umożliwiają one dostosowanie zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas na klienta i usługi odpowiednio.  
  
 Na potrzeby rozszerzenia buforowania obiektów należy utworzyć zachowanie usługi. Zachowania usługi są tworzone przez <xref:System.ServiceModel.Description.IServiceBehavior> implementowanie interfejsu. Istnieje kilka sposobów, aby model usługi świadomy zachowań niestandardowych:  
  
- Korzystanie z atrybutu niestandardowego.  
  
- Konieczne dodanie go do kolekcji zachowań opisu usługi.  
  
- Rozszerzenie pliku konfiguracyjnego.  
  
 W tym przykładzie użyto atrybutu niestandardowego. <xref:System.ServiceModel.ServiceHost> Po skonstruowaniu sprawdza atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy metody <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>-- <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>i . Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> jest używana w celu zapewnienia, że zachowanie może być stosowane do usługi. W tym przykładzie implementacja zapewnia, że usługa <xref:System.ServiceModel.InstanceContextMode.Single>nie jest skonfigurowana z . Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> jest używana do konfigurowania powiązań usługi. Nie jest wymagane w tym scenariuszu. Jest <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> używany do konfigurowania dyspozytorów usługi. Ta metoda jest wywoływana przez <xref:System.ServiceModel.ServiceHost> WCF podczas inicjowania. Następujące parametry są przekazywane do tej metody:  
  
- `Description`: Ten argument zawiera opis usługi dla całej usługi. Może to służyć do sprawdzania danych opisu dotyczących punktów końcowych usługi, umów, powiązań i innych danych.  
  
- `ServiceHostBase`: Ten argument <xref:System.ServiceModel.ServiceHostBase> zapewnia, że jest obecnie inicjowane.  
  
 W <xref:System.ServiceModel.Description.IServiceBehavior> niestandardowej implementacji `ObjectPoolingInstanceProvider` nowe wystąpienie jest tworzone <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> i przypisywane do właściwości w każdym <xref:System.ServiceModel.Dispatcher.DispatchRuntime> w ServiceHostBase.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji <xref:System.EnterpriseServices.ObjectPoolingAttribute> klasa ma kilka elementów członkowskich, aby dostosować pulę obiektów przy użyciu argumentów atrybutu. Te elementy <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>członkowskie <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>obejmują , i , aby dopasować zestaw funkcji buforowania obiektów dostarczonych przez usługi .NET Enterprise Services.  
  
 Zachowanie buforowania obiektów można teraz dodać do usługi WCF, dokonując adnotacji implementacji usługi za pomocą nowo utworzonego atrybutu niestandardowego. `ObjectPooling`  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Uruchamianie próbki  
 W przykładzie pokazano korzyści wydajności, które można uzyskać przy użyciu buforowania obiektów w niektórych scenariuszach.  
  
 Aplikacja usługi implementuje dwie `WorkService` usługi `ObjectPooledWorkService`- i . Obie usługi mają tę samą implementację — obie `DoWork()` wymagają kosztownej inicjalizacji, a następnie udostępniają metodę, która jest stosunkowo tania. Jedyną różnicą `ObjectPooledWorkService` jest to, że ma buforowanie obiektów skonfigurowane:  
  
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
  
 Po uruchomieniu klienta, to razy `WorkService` wywołanie 5 razy. To wtedy razy `ObjectPooledWorkService` wzywając 5 razy. Następnie wyświetlana jest różnica czasu:  
  
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
> Po raz pierwszy klient jest uruchamiany obie usługi wydają się zająć mniej więcej tyle samo czasu. Jeśli ponownie uruchomić próbki, widać, że `ObjectPooledWorkService` zwraca znacznie szybciej, ponieważ wystąpienie tego obiektu już istnieje w puli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
