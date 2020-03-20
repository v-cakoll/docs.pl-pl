---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185394"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
Rozszerzenie <xref:System.ServiceModel.Activities.SendMessageChannelCache> umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów i ustawień pamięci podręcznej kanału dla <xref:System.ServiceModel.Activities.Send> przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu działań obsługi wiadomości. Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>. Pamięć podręczna fabryki <xref:System.ServiceModel.ChannelFactory%601> kanałów zawiera obiekty buforowane. Pamięć podręczna kanału zawiera buforowane kanały.  
  
> [!NOTE]
> Przepływy pracy <xref:System.ServiceModel.Activities.Send> mogą używać działań obsługi wiadomości do wysyłania wiadomości lub parametrów. Środowisko wykonawcze przepływu pracy dodaje fabryki kanałów do <xref:System.ServiceModel.Channels.IRequestChannel> pamięci podręcznej, które tworzą kanały typu podczas używania <xref:System.ServiceModel.Activities.ReceiveReply> działania <xref:System.ServiceModel.Activities.Send> z działaniem, a <xref:System.ServiceModel.Channels.IOutputChannel> gdy po prostu przy użyciu <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Poziomy udostępniania pamięci podręcznej  
 Domyślnie w przepływie pracy obsługiwanym przez pamięć podręczną używaną <xref:System.ServiceModel.WorkflowServiceHost> przez <xref:System.ServiceModel.Activities.Send> działania obsługi <xref:System.ServiceModel.WorkflowServiceHost> wiadomości jest współużytkowany przez wszystkie wystąpienia przepływu pracy w (buforowanie na poziomie hosta). Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia). Pamięć podręczna jest <xref:System.ServiceModel.Activities.Send> dostępna tylko dla działań, które nie używają punktów końcowych zdefiniowanych w konfiguracji, chyba że jest włączone buforowanie niebezpieczne.  
  
 Poniżej przedstawiono różne poziomy <xref:System.ServiceModel.Activities.Send> udostępniania pamięci podręcznej dostępne dla działań w przepływie pracy i ich zalecane użycie:  
  
- **Poziom hosta:** Na poziomie udostępniania hosta pamięć podręczna jest dostępna tylko dla wystąpień przepływu pracy hostowanych na hoście usługi przepływu pracy. Pamięć podręczna może być również współużytkowana między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.  
  
- **Poziom wystąpienia:** Na poziomie udostępniania wystąpienia pamięć podręczna jest dostępna dla określonego wystąpienia przepływu pracy przez cały okres jego istnienia, ale pamięć podręczna nie jest dostępna dla innych wystąpień przepływu pracy.  
  
- **Brak pamięci podręcznej:** Pamięć podręczna jest domyślnie wyłączona, jeśli masz przepływ pracy, który używa punktów końcowych zdefiniowanych w konfiguracji. Zaleca się również, aby zachować pamięć podręczną wyłączoną w tym przypadku, ponieważ włączenie jej może być niezabezpieczone. Na przykład jeśli dla każdego wysyłania wymagana jest inna tożsamość (różne poświadczenia lub użycie personifikacji).  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Zmiana poziomu udostępniania pamięci podręcznej dla przepływu pracy klienta  
 Aby ustawić udostępnianie pamięci podręcznej w przepływie <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracy klienta, dodaj wystąpienie klasy jako rozszerzenie do żądanego zestawu wystąpień przepływu pracy. Powoduje to udostępnianie pamięci podręcznej we wszystkich wystąpieniach przepływu pracy. Poniższe przykłady kodu pokazują, jak wykonać te kroki.  
  
 Najpierw zadeklaruj <xref:System.ServiceModel.Activities.SendMessageChannelCache>wystąpienie typu .  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Następnie dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Zmiana poziomu udostępniania pamięci podręcznej dla usługi hostowanego przepływu pracy  
 Aby ustawić udostępnianie pamięci podręcznej w obsługiwanej usłudze <xref:System.ServiceModel.Activities.SendMessageChannelCache> przepływu pracy, dodaj wystąpienie klasy jako rozszerzenie do wszystkich hostów usługi przepływu pracy. Powoduje to udostępnianie pamięci podręcznej we wszystkich hostach usługi przepływu pracy. Poniższe przykłady kodu pokazują, aby wykonać te kroki.  
  
 Najpierw zadeklarować wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> typu na poziomie klasy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Następnie dodaj statyczne rozszerzenie pamięci podręcznej do każdego hosta usługi przepływu pracy.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Aby ustawić udostępnianie pamięci podręcznej w hostowanej usłudze `Func<SendMessageChannelCache>` przepływu pracy na poziomie wystąpienia, dodaj pełnomocnika jako rozszerzenie do hosta usługi <xref:System.ServiceModel.Activities.SendMessageChannelCache> przepływu pracy i przypisz tego pełnomocnika do kodu, który powoduje utworzenie nowego wystąpienia klasy. Powoduje to inną pamięć podręczną dla każdego wystąpienia przepływu pracy, a nie pojedynczą pamięć podręczną współużytkowaną przez wszystkie wystąpienia przepływu pracy w hoście usługi przepływu pracy. Poniższy przykład kodu pokazuje, jak to osiągnąć za pomocą wyrażenia <xref:System.ServiceModel.Activities.SendMessageChannelCache> lambda, aby bezpośrednio zdefiniować rozszerzenie, które wskazuje delegata.  
  
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
 Można dostosować ustawienia pamięci podręcznej dla pamięci podręcznej fabryki kanałów i pamięci podręcznej kanału. Ustawienia pamięci podręcznej <xref:System.ServiceModel.Activities.ChannelCacheSettings> są zdefiniowane w klasie. Klasa <xref:System.ServiceModel.Activities.SendMessageChannelCache> definiuje domyślne ustawienia pamięci podręcznej pamięci podręcznej fabryki kanałów i pamięci podręcznej kanału w konstruktorze bez parametrów. W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.  
  
|Ustawienia|LeaseTimeout (min)|Czas bezczynny (min)|MaxItemsInCache|  
|-|-|-|-|  
|Domyślna pamięć podręczna fabryki|TimeSpan.MaxValue|2|16|  
|Domyślna pamięć podręczna kanału|5|2|16|  
  
 Aby dostosować ustawienia pamięci podręcznej i pamięci <xref:System.ServiceModel.Activities.SendMessageChannelCache> podręcznej kanału, wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> klasy przy użyciu <xref:System.ServiceModel.Activities.ChannelCacheSettings> konstruktora sparametryzowanego i przekazać nowe wystąpienie z wartościami niestandardowymi do każdego z `factorySettings` parametrów i. `channelSettings` Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy. W poniższym przykładzie kodu pokazano, jak wykonać te kroki dla wystąpienia przepływu pracy.  
  
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
  
 Aby włączyć buforowanie, gdy usługa przepływu pracy ma punkty końcowe <xref:System.ServiceModel.Activities.SendMessageChannelCache> zdefiniowane w konfiguracji, wystąpienia klasy przy użyciu konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> sparametryzowanego z parametrem ustawionym `allowUnsafeCaching` na `true`. Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy. W poniższym przykładzie kodu pokazano, jak włączyć buforowanie dla wystąpienia przepływu pracy.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Aby całkowicie wyłączyć pamięć podręczną dla fabryk kanałów i kanałów, należy wyłączyć pamięć podręczną fabryki kanałów. W ten sposób wyłącza również pamięć podręczną kanału, ponieważ kanały są własnością odpowiednich fabryk kanałów. Aby wyłączyć pamięć podręczną `factorySettings` fabryki kanału, należy przekazać parametr do <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktora zainicjowanego do <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia o <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartości 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Można użyć tylko pamięci podręcznej fabryki kanału i wyłączyć `channelSettings` pamięć <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> podręczną kanału, <xref:System.ServiceModel.Activities.ChannelCacheSettings> przekazując <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> parametr do konstruktora zainicjowanego do wystąpienia o wartości 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 W obsługiwanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i pamięci podręcznej kanału w pliku konfiguracji aplikacji. W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą. W poniższym przykładzie przedstawiono zawartość `MyChannelCacheBehavior` pliku konfiguracyjnego, który zawiera zachowanie usługi z niestandardowymi ustawieniami pamięci podręcznej fabryki i pamięci podręcznej kanału. To zachowanie usługi jest dodawany `behaviorConfiguration` do usługi za pośrednictwem atrybutu.  
  
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
