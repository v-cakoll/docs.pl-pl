---
title: Tworzenie wystąpienia inicjowania
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 1414908025416f4cdd6e5b51c052799631ab52cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989914"
---
# <a name="instancing-initialization"></a>Tworzenie wystąpienia inicjowania
Rozszerza w tym przykładzie [Pooling](../../../../docs/framework/wcf/samples/pooling.md) próbki przez definiowanie interfejsu `IObjectControl`, który dostosowuje inicjalizację obiektu za aktywowanie i dezaktywowanie go. Klient wywołuje metody, które zwracają obiekt do puli, a które nie zwracają obiekt do puli.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="extensibility-points"></a>Punkty rozszerzeń  
 Pierwszym krokiem tworzenia rozszerzenia programu Windows Communication Foundation (WCF) jest podjęcie decyzji, punkt rozszerzeń do użycia. W programie WCF termin *EndpointDispatcher* odwołuje się do składnika środowiska wykonawczego odpowiedzialny za konwersji komunikatów przychodzących do wywołania metody usługi przez użytkownika i konwertowania wartości zwracane z tej metody do wysyłanej wiadomości . Usługa WCF tworzy EndpointDispatcher dla każdego punktu końcowego.  
  
 EndpointDispatcher oferuje punktu końcowego zakresu (dla wszystkich wiadomości wysłanych i odebranych przez usługę) extensibility za pomocą <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> klasy. Ta klasa umożliwia dostosowanie różne właściwości tej kontroli sposobu działania programu. Ten przykład koncentruje się na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości, który wskazuje na obiekt, który udostępnia wystąpienia klasy usługi.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 W programie WCF, EndpointDispatcher tworzy wystąpienia klasy usługi przy użyciu dostawcy wystąpienia, która implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejsu. Ten interfejs ma tylko dwie metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Po umieszczeniu komunikatu, wywołuje dyspozytora <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodę, aby utworzyć wystąpienie klasy usługi przetworzyć komunikatu. Częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, nowe wystąpienie klasy usługi zostanie utworzona przetworzenie każdego komunikatu przychodzący, więc <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jest wywoływana w momencie nadejścia wiadomości.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Gdy wystąpienie usługi zakończy przetwarzanie komunikatu, wywołuje EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metody. Podobnie jak w <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody częstotliwość połączeń do tej metody jest określana przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości.  
  
## <a name="the-object-pool"></a>Pula obiektów  
 `ObjectPoolInstanceProvider` Klasa zawiera implementację dla puli obiektów. Ta klasa implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interfejs do interakcji z warstwy modelu usług. Kiedy wywołuje EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, zamiast tworzenia nowego wystąpienia, implementacja niestandardowa szuka istniejący obiekt w puli w pamięci. Jeśli jest dostępny, jest zwracany. W przeciwnym razie `ObjectPoolInstanceProvider` sprawdza, czy `ActiveObjectsCount` właściwości (liczba obiektów zwróconych z puli), osiągnęła maksymalny rozmiar puli. Jeśli nie, nowe wystąpienie jest tworzony i zwracany do wywołującego i `ActiveObjectsCount` następnie rośnie. W przeciwnym razie żądanie utworzenia obiektu jest kolejkowana w skonfigurowanym okresie czasu. Wykonania na `GetObjectFromThePool` przedstawiono w poniższym przykładowym kodzie.  
  
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
  
 Niestandardowy `ReleaseInstance` implementacji dodaje wydana wystąpienie do puli i zmniejsza `ActiveObjectsCount` wartość. EndpointDispatcher może wywoływać te metody z różnych wątków i w związku z tym zsynchronizowany dostęp do poziomu elementów członkowskich klasy w `ObjectPoolInstanceProvider` klasy jest wymagana.  
  
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
  
 `ReleaseInstance` Metoda zapewnia *oczyszczania inicjowania* funkcji. Zwykle puli obsługuje minimalnej liczby obiektów, dla okresu istnienia puli. Jednak może być okresy nadmiernego użycia, które wymagają, tworząc dodatkowe obiekty w puli w celu osiągnięcia maksymalnego limitu określonego w konfiguracji. Po pewnym czasie po puli staje się mniej aktywne tych pozostałe obiekty mogą stać się dodatkowe obciążenie. W związku z tym gdy `activeObjectsCount` osiągnie zero uruchomieniu czasomierza bezczynności, który wyzwala i wykonuje cyklu czyszczenia.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozszerzenia warstwy modelu ServiceModel są podłączone, wykonując następujące zachowania:  
  
- Zachowania usług: Umożliwiają one do dostosowywania środowiska uruchomieniowego całą usługę.  
  
- Zachowań punktu końcowego: Te umożliwiają dostosowanie punktu końcowego określonej usługi, w tym elemencie EndpointDispatcher.  
  
- Kontrakt zachowania: Umożliwiają one do dostosowania albo <xref:System.ServiceModel.Dispatcher.ClientRuntime> lub <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy po stronie klienta lub usługę, odpowiednio.  
  
- Operacja zachowania: Umożliwiają one do dostosowania albo <xref:System.ServiceModel.Dispatcher.ClientOperation> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy po stronie klienta lub usługę, odpowiednio.  
  
 Na potrzeby buforowania rozszerzenie obiektu zachowanie punktu końcowego lub zachowanie usługi mogą być tworzone. W tym przykładzie używamy zachowanie usługi, które stosuje obiekt buforowanie zdolność do każdego punktu końcowego usługi. Zachowania usług są tworzone przez zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu. Istnieje kilka sposobów, aby uświadomić ServiceModel niestandardowe zachowania:  
  
- Za pomocą atrybutu niestandardowego.  
  
- Obowiązkowo dodanie go do kolekcji zachowań opisu usługi.  
  
- Rozszerzenie pliku konfiguracji.  
  
 Ta próbka używa atrybutu niestandardowego. Gdy <xref:System.ServiceModel.ServiceHost> jest skonstruowany, jej poszczególne atrybuty, są używane w definicji typu usługi, jak i zachowania dostępne są dodawane do kolekcji zachowań opisu usługi.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Interfejs ma trzy metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` i <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Te metody są wywoływane przez architekturę WCF podczas <xref:System.ServiceModel.ServiceHost> jest inicjowany. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> nazywa się najpierw; Umożliwia usłudze poddanych niespójności. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> nazywa się obok; Ta metoda jest wymagana tylko w bardzo zaawansowanych scenariuszach. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> nazywa się ostatnio i jest odpowiedzialny za konfigurowanie środowiska uruchomieniowego. Następujące parametry są przekazywane do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
- `Description`: Ten parametr zawiera opis usługi dla całej usługi. To może służyć do wglądu opis danych dotyczących punktów końcowych usługi, kontrakty, powiązania i inne dane związane z usługą.  
  
- `ServiceHostBase`: Ten parametr zawiera <xref:System.ServiceModel.ServiceHostBase> , jest obecnie inicjowany.  
  
 W niestandardowej <xref:System.ServiceModel.Description.IServiceBehavior> implementacji, nowe wystąpienie klasy `ObjectPoolInstanceProvider` jest tworzone i przypisane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwość w każdym <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> dołączona do <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Oprócz <xref:System.ServiceModel.Description.IServiceBehavior> implementacji `ObjectPoolingAttribute` klasa ma kilka składowych, aby dostosować puli obiektów przy użyciu argumentów atrybutu. Te elementy Członkowskie zawierają `MaxSize`, `MinSize`, `Enabled` i `CreationTimeout`, aby odpowiadać obiektowi buforowania zestawu funkcji udostępnianego przez usługi Enterprise .NET.  
  
 Zachowanie buforowania można teraz można dodać obiektu do usługi WCF przez dodawanie adnotacji do implementacji usługi przy użyciu nowo utworzony niestandardowy `ObjectPooling` atrybutu.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Przechwytywanie, aktywacja i dezaktywacja  
 Podstawowym celem buforowanie obiektu jest zoptymalizować obiekty krótkotrwałe relatywnie kosztowne tworzenia i inicjowania. W związku z tym zwiększeniu wydajności znaczne go można udostępnić aplikację, czy poprawnie zastosowane. Ponieważ obiekt jest zwracany z puli, Konstruktor jest wywoływany tylko raz. Jednak niektóre aplikacje wymagają pewien stopień kontroli, tak aby mogli inicjowanie i oczyszczanie zasoby używane podczas pojedynczego kontekstu. Na przykład obiekt używany zbiór obliczenia można zresetować jego pola prywatne przed przetworzeniem dalej obliczeń. Usługi Enterprise włączone tento typ inicializace zależne od kontekstu, umożliwiając developer obiektu zastępują `Activate` i `Deactivate` metody z <xref:System.EnterpriseServices.ServicedComponent> klasy bazowej.  
  
 Wywołań puli obiektów `Activate` metoda tuż przed zwróceniem obiektu z puli. `Deactivate` jest wywoływana, gdy obiekt zwraca z powrotem do puli. <xref:System.EnterpriseServices.ServicedComponent> Ma również klasę bazową `boolean` właściwość o nazwie `CanBePooled`, który może służyć do powiadamiania w puli, czy obiekt może dodatkowo puli.  
  
 Aby naśladował tę funkcję, przykład deklaruje interfejsu publicznego (`IObjectControl`) zawierający wyżej wymienionych elementów członkowskich. Ten interfejs, następnie jest implementowany przez usługę klasy mają na celu dostarczenie Inicjalizacja określonego kontekstu. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementacji muszą zostać zmodyfikowane w celu spełnienia tych wymagań. Teraz zawsze możesz uzyskać obiektu przez wywołanie metody `GetInstance` metody, musisz sprawdzić, czy obiekt implementuje `IObjectControl.` Jeśli tak jest, należy wywołać `Activate` metoda odpowiednio.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Gdy zwracany obiekt do puli, kontrola jest wymagany dla `CanBePooled` właściwości przed dodaniem obiektu z powrotem do puli.  
  
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
  
 Ponieważ Deweloper usługi może zdecydować, czy obiekt może być gromadzone, liczba obiektów w puli w danym momencie może zejść poniżej minimalnego rozmiaru. W związku z tym musisz sprawdzić, czy liczba obiektów poniżej minimalnego poziomu i wykonywać niezbędne inicjowania procedury oczyszczania.  
  
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
  
 Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz Enter każdego okna konsoli, aby zamknąć usługę i klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
