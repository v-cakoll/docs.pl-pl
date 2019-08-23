---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 587440bd343513aeff51f1ed0947573fbe612f22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952589"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
Rozszerzenie umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów oraz ustawień pamięci podręcznej kanału dla przepływów pracy, które wysyłają komunikaty do punktów <xref:System.ServiceModel.Activities.Send> końcowych usługi przy użyciu działań związanych z obsługą komunikatów. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>. Pamięć podręczna fabryki kanałów zawiera <xref:System.ServiceModel.ChannelFactory%601> buforowane obiekty. Pamięć podręczna kanału zawiera buforowane kanały.  
  
> [!NOTE]
> Przepływy pracy <xref:System.ServiceModel.Activities.Send> mogą wysyłać komunikaty lub parametry za pomocą działań związanych z wiadomościami. Środowisko uruchomieniowe przepływu pracy dodaje fabryki kanałów do pamięci podręcznej, która <xref:System.ServiceModel.Channels.IRequestChannel> tworzy kanały typu w <xref:System.ServiceModel.Activities.ReceiveReply> przypadku używania działania <xref:System.ServiceModel.Activities.Send> z <xref:System.ServiceModel.Activities.Send> działaniem, <xref:System.ServiceModel.Channels.IOutputChannel> a kiedy tylko używa działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Poziomy udostępniania pamięci podręcznej  
 Domyślnie, w przepływie pracy hostowanym przez <xref:System.ServiceModel.WorkflowServiceHost> pamięć podręczną używaną przez <xref:System.ServiceModel.Activities.Send> działania obsługi komunikatów jest współużytkowany przez <xref:System.ServiceModel.WorkflowServiceHost> wszystkie wystąpienia przepływu pracy w (buforowanie na poziomie hosta). Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia). Pamięć podręczna jest dostępna tylko <xref:System.ServiceModel.Activities.Send> dla działań, które nie korzystają z punktów końcowych zdefiniowanych w konfiguracji, chyba że jest włączone bezpieczne buforowanie.  
  
 Poniżej przedstawiono różne poziomy udostępniania pamięci podręcznej dostępne <xref:System.ServiceModel.Activities.Send> dla działań w przepływie pracy i ich zalecane użycie:  
  
- **Poziom hosta**: Na poziomie udostępniania hosta pamięć podręczna jest dostępna tylko dla wystąpień przepływu pracy hostowanych na hoście usługi przepływu pracy. Pamięć podręczna może być również współużytkowana przez hosty usługi przepływu pracy w pamięci podręcznej dla całego procesu.  
  
- **Poziom wystąpienia**: Na poziomie udostępniania wystąpienia pamięć podręczna jest dostępna dla określonego wystąpienia przepływu pracy w całym okresie istnienia, ale pamięć podręczna nie jest dostępna dla innych wystąpień przepływu pracy.  
  
- **Brak pamięci**podręcznej: Pamięć podręczna jest domyślnie wyłączona, jeśli istnieje przepływ pracy korzystający z punktów końcowych zdefiniowanych w konfiguracji. Zalecane jest również, aby pamięć podręczna była wyłączona w tym przypadku, ponieważ jej włączenie może być niezabezpieczone. Na przykład, jeśli dla każdego wysłania jest wymagana inna tożsamość (różne poświadczenia lub personifikacja).  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Zmiana poziomu udostępniania pamięci podręcznej dla przepływu pracy klienta  
 Aby ustawić udostępnianie pamięci podręcznej w przepływie pracy klienta, Dodaj wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie do żądanego zestawu wystąpień przepływu pracy. Powoduje to udostępnienie pamięci podręcznej we wszystkich wystąpieniach przepływu pracy. Poniższy przykład kodu pokazuje, jak wykonać te kroki.  
  
 Najpierw Zadeklaruj wystąpienie typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Następnie Dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Zmiana poziomu udostępniania pamięci podręcznej dla hostowanej usługi przepływu pracy  
 Aby ustawić udostępnianie pamięci podręcznej w hostowanej usłudze przepływu pracy, Dodaj wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie do wszystkich hostów usługi przepływu pracy. Powoduje to udostępnienie pamięci podręcznej na wszystkich hostach usługi przepływu pracy. Poniższy przykład kodu pokazuje, aby wykonać te kroki.  
  
 Najpierw Zadeklaruj wystąpienie typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na poziomie klasy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Następnie Dodaj rozszerzenie statycznej pamięci podręcznej do każdego hosta usługi przepływu pracy.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Aby skonfigurować udostępnianie pamięci podręcznej w hostowanej usłudze przepływu pracy na poziomie wystąpienia, `Func<SendMessageChannelCache>` Dodaj delegata jako rozszerzenie hosta usługi przepływu pracy i przypisz tego delegata do kodu, który tworzy wystąpienie nowego wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy. Powoduje to inną pamięć podręczną dla każdego pojedynczego wystąpienia przepływu pracy, a nie pojedynczej pamięci podręcznej udostępnionej przez wszystkie wystąpienia przepływu pracy na hoście usługi przepływu pracy. Poniższy przykład kodu pokazuje, jak to osiągnąć za pomocą wyrażenia lambda do bezpośredniego definiowania <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenia, do którego odwołuje się delegat.  
  
```csharp 
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings   
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings   
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a>Dostosowywanie ustawień pamięci podręcznej  
 Można dostosować ustawienia pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału. Ustawienia pamięci podręcznej są zdefiniowane <xref:System.ServiceModel.Activities.ChannelCacheSettings> w klasie. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Klasa definiuje domyślne ustawienia pamięci podręcznej dla fabryki kanałów i pamięć podręczną kanału w konstruktorze bez parametrów. W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.  
  
|Ustawienia|LeaseTimeout (min.)|IdleTimeout (minimum)|MaxItemsInCache|  
|-|-|-|-|  
|Domyślna pamięć podręczna fabryki|TimeSpan.MaxValue|2|16|  
|Wartość domyślna pamięci podręcznej kanału|5|2|16|  
  
 Aby dostosować ustawienia pamięci podręcznej fabryki i pamięci podręcznej kanałów, <xref:System.ServiceModel.Activities.SendMessageChannelCache> Utwórz wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> klasy przy użyciu konstruktora sparametryzowanego i <xref:System.ServiceModel.Activities.ChannelCacheSettings> Przekaż nowe wystąpienie z wartościami niestandardowymi `channelSettings` na wszystkie `factorySettings` i wejściowe. Następnie Dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy. Poniższy przykład kodu pokazuje, jak wykonać te kroki dla wystąpienia przepływu pracy.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(5),   
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Aby włączyć buforowanie, gdy usługa przepływu pracy ma punkty końcowe zdefiniowane w konfiguracji, <xref:System.ServiceModel.Activities.SendMessageChannelCache> Utwórz wystąpienie klasy przy użyciu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktora sparametryzowanego z `allowUnsafeCaching` parametrem ustawionym na `true`. Następnie Dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy. Poniższy przykład kodu pokazuje, jak włączyć buforowanie dla wystąpienia przepływu pracy.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Aby całkowicie wyłączyć pamięć podręczną dla fabryk kanałów i kanałów, Wyłącz pamięć podręczną fabryki kanałów. Spowoduje to również wyłączenie pamięci podręcznej kanału, ponieważ kanały są własnością odpowiednich fabryk kanałów. Aby wyłączyć pamięć podręczną fabryki kanałów, Przekaż `factorySettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> do konstruktora, który został zainicjowany <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do wystąpienia o wartości 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Można wybrać opcję użycia tylko pamięci podręcznej fabryki kanału i wyłączyć pamięć podręczną kanału przez `channelSettings` przekazanie parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> do konstruktora, który <xref:System.ServiceModel.Activities.ChannelCacheSettings> został zainicjowany <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do wystąpienia o wartości 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 W hostowanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i ustawień pamięci podręcznej kanału w pliku konfiguracyjnym aplikacji. W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą. Poniższy przykład pokazuje zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` zachowanie usługi z niestandardową pamięcią podręczną i ustawieniami pamięci podręcznej kanału. To zachowanie usługi jest dodawane do usługi za pomocą `behaviorConfiguration` atrybutu.  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
