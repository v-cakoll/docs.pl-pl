---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ae01254760219f2b408ef9d9663c4158e2802be8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="instancing-initialization"></a>Tworzenie wystąpienia inicjowania
W tym przykładzie rozszerza [buforowanie](../../../../docs/framework/wcf/samples/pooling.md) przykładowa przez definiowanie interfejsu `IObjectControl`, który dostosowuje inicjowania obiektu przez aktywowanie i dezaktywowanie go. Klient wywołuje metody, które zwracają obiekt do puli, a które nie zwracają obiekt do puli.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="extensibility-points"></a>Punkty rozszerzeń  
 Pierwszym krokiem tworzenia rozszerzenia programu Windows Communication Foundation (WCF) jest podjęcie punkcie rozszerzenia do użycia. W programie WCF termin *EndpointDispatcher* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołań metod w usłudze użytkownika i konwertowania wartości zwracanych z tej metody do wysyłanej wiadomości . Usługi WCF tworzy EndpointDispatcher dla każdego punktu końcowego.  
  
 Oferuje EndpointDispatcher punktu końcowego zakresu (dla wszystkich wiadomości wysłanych i odebranych przez usługę) rozszerzalności za pomocą <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> klasy. Ta klasa umożliwia dostosowanie różne właściwości sterujące zachowaniem elementu EndpointDispatcher. W tym przykładzie koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość, która wskazuje obiekt, który zapewnia wystąpienia klasy usługi.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 W programie WCF, EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia, który implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu. Ten interfejs ma tylko dwie metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Gdy nadejścia wiadomości, wywołania dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę w celu utworzenia wystąpienia klasy usługi, aby przetworzyć komunikatu. Częstotliwość połączeń do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi służy do przetwarzania każdy komunikat przychodzący, dlatego <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana w momencie nadejścia wiadomości.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Gdy wystąpienie usługi zakończy przetwarzanie komunikatu, wywołuje EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metody. Podobnie jak w <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, częstotliwość wywołania do tej metody jest określany przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 `ObjectPoolInstanceProvider` Klasa zawiera implementację dla obiekt puli. Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu do interakcji z warstwy modelu usług. Gdy wywołuje EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, zamiast tworzyć nowe wystąpienie implementacji niestandardowych szuka istniejący obiekt w puli w pamięci. Jeśli jest dostępny, jest zwracana. W przeciwnym razie `ObjectPoolInstanceProvider` sprawdza, czy `ActiveObjectsCount` właściwości (liczba obiektów zwrócona z puli) osiągnął maksymalny rozmiar puli. Jeśli nie, nowe wystąpienie jest tworzony i zwracany do obiektu wywołującego i `ActiveObjectsCount` jest zwiększany później. W przeciwnym razie żądanie utworzenia obiektu jest w kolejce w skonfigurowanym okresie czasu. Implementację `GetObjectFromThePool` jest wyświetlany w następujący przykładowy kod.  
  
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
  
 Niestandardowa `ReleaseInstance` implementacji dodaje Zwolniono wystąpienie puli i zmniejsza `ActiveObjectsCount` wartość. EndpointDispatcher można wywołać metody te z różnych wątkach i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolInstanceProvider` klasa jest wymagana.  
  
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
  
 `ReleaseInstance` Metoda zapewnia *oczyszczania inicjowania* funkcji. Zwykle puli obsługuje minimalną liczbę obiektów, dla okresu istnienia puli. Jednak może być okresów nadmiernego użycia, które wymaga tworzenia dodatkowe obiekty w puli do osiągnięcia maksymalnego limitu określonego w konfiguracji. Gdy puli staje się mniej aktywne tych pozostałe obiekty mogą przestać dodatkowego obciążenia. W związku z tym podczas `activeObjectsCount` osiągnie zero czasomierza bezczynności została uruchomiona, który wyzwala i wykonuje cyklu czyszczenia.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozszerzenia warstwy modelu ServiceModel są podłączonymi przy użyciu następujących problemów:  
  
-   Zachowania usług: Umożliwiają one dostosowywania środowiska uruchomieniowego całej usługi.  
  
-   Zachowania punktu końcowego: Umożliwiają one do dostosowania określonej usługi punktu końcowego, w tym EndpointDispatcher.  
  
-   Zachowania kontraktu: Umożliwiają one dostosowywania albo <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> odpowiednio klasy po stronie klienta lub usługi.  
  
-   Operacja zachowania: Umożliwiają one dostosowywania jednej <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> odpowiednio klasy po stronie klienta lub usługi.  
  
 Na potrzeby obiektu rozszerzenia puli można utworzyć zachowania punktu końcowego lub zachowania usługi. W tym przykładzie używamy zachowanie usługi stosuje obiektu buforowanie zdolność do każdego punktu końcowego usługi. Zachowania usług są tworzone z zastosowaniem <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów uświadomić ServiceModel niestandardowe zachowania:  
  
-   Przy użyciu atrybutu niestandardowego.  
  
-   Imperatively dodanie go do kolekcji zachowań opisu usługi.  
  
-   Rozszerzenie pliku konfiguracji.  
  
 W przykładzie użyto atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest utworzone, jego sprawdza atrybuty używane w definicji typu usługi, jak i dodaje zachowania dostępne do kolekcji zachowań opisu usługi.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Interfejs ma trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Te metody są wywoływane przez WCF podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> jest nazywana najpierw; Umożliwia usługi poddanych niespójności. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> jest nazywana obok; Ta metoda jest wymagana tylko w scenariuszach bardzo zaawansowane. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> jest nazywana ostatnio i jest odpowiedzialny za konfigurację środowiska uruchomieniowego. Następujące parametry są przekazywane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Ten parametr zawiera opis usługi dla całej usługi. Może być używany do zbadania opis danych dotyczących punktów końcowych usługi, kontrakty, powiązania i innych danych związanych z usługą.  
  
-   `ServiceHostBase`: Ten parametr zawiera <xref:System.ServiceModel.ServiceHostBase> który jest obecnie inicjowany.  
  
 W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji, nowe wystąpienie klasy `ObjectPoolInstanceProvider` wystąpienia i ma przypisaną do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości w każdym <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączona do <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji `ObjectPoolingAttribute` klasa ma kilka elementów członkowskich, aby dostosować puli obiektów przy użyciu argumentów atrybutu. Elementy te obejmują `MaxSize`, `MinSize`, `Enabled` i `CreationTimeout`, aby odpowiadać obiektowi buforowanie zestaw funkcji udostępniane przez usługi .NET Enterprise.  
  
 Obiekt buforowanie zachowanie można teraz dodać do usługi WCF przez dodawanie adnotacji do implementacji usługi z nowo utworzonych niestandardowych `ObjectPooling` atrybutu.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Aktywacja i dezaktywacja Przechwytywanie  
 Głównym celem buforowanie obiektów jest w celu zoptymalizowania krótkim okresie obiektów o stosunkowo drogie tworzenia i inicjowania. W związku z tym wzrost wydajności znacznej go można udostępnić aplikacji, jeśli używana poprawnie. Ponieważ obiekt jest zwracany z puli, konstruktora zostanie wywołana tylko raz. Jednak niektóre aplikacje wymagają pewnego poziomu kontroli, tak aby mogli inicjowanie i oczyszczanie zasobów używanych w pojedynczym kontekście. Na przykład obiekt używany dla zestawu obliczeń zresetować swoich pól prywatnych przed przetworzeniem dalej obliczeń. Usługi Enterprise włączone tego rodzaju inicjowanie zależne od kontekstu, umożliwiając developer obiektu zastąpienie `Activate` i `Deactivate` metody <xref:System.EnterpriseServices.ServicedComponent> klasy podstawowej.  
  
 Wywołań puli obiektów `Activate` metody bezpośrednio przed powrotem obiektu z puli. `Deactivate` jest wywoływana po powrocie obiekt z powrotem do puli. <xref:System.EnterpriseServices.ServicedComponent> Klasy podstawowej ma również `boolean` właściwość o nazwie `CanBePooled`, które mogą służyć do powiadamiania puli, czy obiekt może dodatkowo puli.  
  
 Aby naśladował tę funkcję, próbki deklaruje interfejs publiczny (`IObjectControl`) mający wyżej wymienione elementy członkowskie. Ten interfejs jest następnie wdrażany przez usługę klasy mają na celu dostarczenie inicjowania określonego kontekstu. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Wdrożenia muszą zostać zmodyfikowane w celu spełnienia tych wymagań. Teraz, zawsze można uzyskać obiektu przez wywołanie metody `GetInstance` metody, musisz sprawdzić, czy obiekt implementuje `IObjectControl.` Jeśli tak, należy wywołać `Activate` metody odpowiednio.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Gdy do puli, zwracając obiekt, sprawdzenie jest wymagany dla `CanBePooled` właściwość przed dodaniem obiekt z powrotem do puli.  
  
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
  
 Ponieważ dewelopera usługi można zdecydować, czy puli obiektu liczba obiektów w puli w danym momencie może zejść poniżej minimalnego rozmiaru. W związku z tym należy sprawdzić, czy liczba obiektów stała się poniżej minimalnego poziomu, a następnie wykonaj konieczne zainicjowanie procedury czyszczenia.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz Enter w każdym okna konsoli można zamknąć usługę i klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>Zobacz też
