---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183593"
---
# <a name="instancing-initialization"></a>Tworzenie wystąpienia inicjowania
Ten przykład rozszerza [próbkę buforowania,](../../../../docs/framework/wcf/samples/pooling.md) definiując interfejs, `IObjectControl`który dostosowuje inicjowanie obiektu przez aktywowanie i dezaktywację. Klient wywołuje metody, które zwracają obiekt do puli i które nie zwracają obiektu do puli.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="extensibility-points"></a>Punkty rozszerzalności  
 Pierwszym krokiem w tworzeniu rozszerzenia Windows Communication Foundation (WCF) jest podjęcie decyzji o punkt rozszerzalności do użycia. W WCF termin *EndpointDispatcher* odnosi się do składnika czasu wykonywania odpowiedzialnego za konwertowanie wiadomości przychodzących na wywołania metody w usłudze użytkownika i za konwertowanie wartości zwracanych z tej metody na komunikat wychodzący. Usługa WCF tworzy EndpointDispatcher dla każdego punktu końcowego.  
  
 EndpointDispatcher oferuje zakres punktu końcowego (dla wszystkich wiadomości odebranych lub <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> wysłanych przez usługę) rozszerzalność przy użyciu klasy. Ta klasa umożliwia dostosowanie różnych właściwości, które kontrolują zachowanie EndpointDispatcher. Ten przykład koncentruje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> się na właściwość, która wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.  
  
## <a name="iinstanceprovider"></a>Iinstanceprovider  
 W WCF EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs. Ten interfejs ma tylko dwie metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Po odebraniu wiadomości dyspozytor wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, aby utworzyć wystąpienie klasy usługi do przetwarzania wiadomości. Częstotliwość wywołań tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość. Na przykład, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> jeśli właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> usługi jest tworzony do przetwarzania każdej wiadomości, która nadejdzie, więc jest wywoływana, gdy pojawia się komunikat.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Po zakończeniu przetwarzania komunikatu wystąpienie usługi, EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metodę. Podobnie jak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> w metodzie, częstotliwość wywołań tej <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody jest określana przez właściwość.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 Klasa `ObjectPoolInstanceProvider` zawiera implementację puli obiektów. Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs do interakcji z warstwą modelu usługi. Gdy EndpointDispatcher wywołuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa wyszukuje istniejący obiekt w puli w pamięci. Jeśli jeden jest dostępny, jest zwracany. W `ObjectPoolInstanceProvider` przeciwnym razie `ActiveObjectsCount` sprawdza, czy właściwość (liczba obiektów zwróconych z puli) osiągnęła maksymalny rozmiar puli. Jeśli nie, nowe wystąpienie jest tworzony i `ActiveObjectsCount` zwracany do wywołującego, a następnie zwiększa. W przeciwnym razie żądanie utworzenia obiektu jest umieszczane w kolejce przez skonfigurowany okres czasu. Implementacja `GetObjectFromThePool` dla jest pokazana w poniższym przykładowym kodzie.  
  
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
  
 Implementacja `ReleaseInstance` niestandardowa dodaje zwolnione wystąpienie z powrotem do puli i zmniejsza `ActiveObjectsCount` wartość. EndpointDispatcher można wywołać te metody z różnych wątków i dlatego zsynchronizowanego dostępu do elementów członkowskich poziomu klasy w `ObjectPoolInstanceProvider` klasie jest wymagane.  
  
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
  
 Metoda `ReleaseInstance` zapewnia funkcję *oczyszczania inicjowania.* Zwykle pula utrzymuje minimalną liczbę obiektów przez cały okres istnienia puli. Jednak mogą istnieć okresy nadmiernego użycia, które wymagają tworzenia dodatkowych obiektów w puli, aby osiągnąć maksymalny limit określony w konfiguracji. Po pewnym czasie, gdy pula staje się mniej aktywna, te nadwyżki obiektów może stać się dodatkowym obciążeniem. W związku `activeObjectsCount` z tym po osiągnięciu zera jest uruchamiany czasomierz bezczynny, który wyzwala i wykonuje cykl oczyszczania.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 Rozszerzenia warstwy ServiceModel są podłączone przy użyciu następujących zachowań:  
  
- Zachowania usługi: umożliwiają one dostosowanie całego środowiska uruchomieniowego usługi.  
  
- Zachowania punktu końcowego: umożliwiają one dostosowanie określonego punktu końcowego usługi, w tym EndpointDispatcher.  
  
- Zachowania kontraktów: umożliwiają one dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas na klienta lub usługi odpowiednio.  
  
- Zachowania operacji: Umożliwiają one dostosowanie albo <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> klas na kliencie lub usługi odpowiednio.  
  
 Na potrzeby rozszerzenia buforowania obiektów można utworzyć zachowanie punktu końcowego lub zachowanie usługi. W tym przykładzie używamy zachowania usługi, która stosuje zdolność buforowania obiektów do każdego punktu końcowego usługi. Zachowania usługi są tworzone przez <xref:System.ServiceModel.Description.IServiceBehavior> implementowanie interfejsu. Istnieje kilka sposobów, aby ServiceModel świadomość zachowań niestandardowych:  
  
- Korzystanie z atrybutu niestandardowego.  
  
- Konieczne dodanie go do kolekcji zachowań opisu usługi.  
  
- Rozszerzenie pliku konfiguracyjnego.  
  
 W tym przykładzie użyto atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, sprawdza atrybuty używane w definicji typu usługi i dodaje dostępne zachowania do kolekcji zachowań opisu usługi.  
  
 Interfejs <xref:System.ServiceModel.Description.IServiceBehavior> ma trzy <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` metody: i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Metody te są wywoływane przez <xref:System.ServiceModel.ServiceHost> WCF podczas inicjowania. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>nazywa się pierwszy; pozwala na sprawdzenie usługi pod kątem niespójności. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>nazywa się dalej; ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>jest nazywany ostatni i jest odpowiedzialny za konfigurowanie środowiska wykonawczego. Następujące parametry są <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>przekazywane do:  
  
- `Description`: Ten parametr zawiera opis usługi dla całej usługi. Może to służyć do sprawdzania danych opisu dotyczących punktów końcowych usługi, umów, powiązań i innych danych skojarzonych z usługą.  
  
- `ServiceHostBase`: Ten parametr <xref:System.ServiceModel.ServiceHostBase> zapewnia, że jest obecnie inicjowany.  
  
 W <xref:System.ServiceModel.Description.IServiceBehavior> implementacji niestandardowej nowe `ObjectPoolInstanceProvider` wystąpienie jest tworzone i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> przypisywane <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> do właściwości w <xref:System.ServiceModel.ServiceHostBase>każdym, który jest dołączony do .  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji `ObjectPoolingAttribute` klasa ma kilka elementów członkowskich, aby dostosować pulę obiektów przy użyciu argumentów atrybutu. Te elementy `MaxSize` `MinSize`członkowskie `Enabled` `CreationTimeout`obejmują , i , aby dopasować zestaw funkcji buforowania obiektów dostarczonych przez usługi .NET Enterprise Services.  
  
 Zachowanie buforowania obiektów można teraz dodać do usługi WCF, dokonując adnotacji implementacji usługi za pomocą nowo utworzonego atrybutu niestandardowego. `ObjectPooling`  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Aktywacja i dezaktywacja hakowania  
 Głównym celem buforowania obiektów jest optymalizacja obiektów krótkotrwałych przy stosunkowo kosztownym tworzeniu i inicjowaniu. W związku z tym może dać dramatyczny wzrost wydajności aplikacji, jeśli jest prawidłowo używany. Ponieważ obiekt jest zwracany z puli, konstruktor jest wywoływany tylko raz. Jednak niektóre aplikacje wymagają pewnego poziomu kontroli, dzięki czemu można zainicjować i oczyścić zasoby używane w jednym kontekście. Na przykład obiekt używany do zestawu obliczeń może zresetować swoje pola prywatne przed przetworzeniem następnego obliczenia. Usługi dla przedsiębiorstw włączyły tego rodzaju inicjalizację specyficzne `Activate` `Deactivate` dla kontekstu, zezwalając deweloperowi na zastępowanie obiektów i metody z klasy podstawowej. <xref:System.EnterpriseServices.ServicedComponent>  
  
 Pula obiektów `Activate` wywołuje metodę tuż przed zwróceniem obiektu z puli. `Deactivate`jest wywoływana, gdy obiekt powraca do puli. Klasa <xref:System.EnterpriseServices.ServicedComponent> podstawowa ma `boolean` również `CanBePooled`właściwość o nazwie , która może służyć do powiadamiania puli, czy obiekt może być dalej łączony.  
  
 Aby naśladować tę funkcję, w próbce`IObjectControl`deklaruje interfejs publiczny ( ), który ma wyżej wymienionych elementów członkowskich. Ten interfejs jest następnie implementowane przez klasy usług przeznaczone do zapewnienia inicjowania specyficzne dla kontekstu. Implementacja <xref:System.ServiceModel.Dispatcher.IInstanceProvider> musi zostać zmodyfikowana, aby spełnić te wymagania. Teraz za każdym razem, gdy `GetInstance` otrzymasz obiekt, wywołując metodę, `IObjectControl.` należy sprawdzić, czy `Activate` obiekt implementuje Jeśli tak, należy wywołać metodę odpowiednio.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Podczas zwracania obiektu do puli, sprawdzanie jest `CanBePooled` wymagane dla właściwości przed dodaniem obiektu z powrotem do puli.  
  
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
  
 Ponieważ deweloper usługi może zdecydować, czy obiekt może być łączony, liczba obiektów w puli w danym czasie może zejść poniżej minimalnego rozmiaru. W związku z tym należy sprawdzić, czy liczba obiektów spadła poniżej minimalnego poziomu i wykonać niezbędne inicjowanie w procedurze oczyszczania.  
  
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
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz Enter w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
