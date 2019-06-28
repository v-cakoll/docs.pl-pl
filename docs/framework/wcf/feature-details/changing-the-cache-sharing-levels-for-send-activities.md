---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 079eb037f074155aec3ad5473480bbf5d4d341b2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425156"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozszerzenie umożliwia dostosowywania pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawień kanału pamięci podręcznej dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi za pomocą <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów. Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>. Zawiera pamięci podręcznej fabryki kanału pamięci podręcznej <xref:System.ServiceModel.ChannelFactory%601> obiektów. Pamięci podręcznej kanału zawiera kanały pamięci podręcznej.  
  
> [!NOTE]
>  Przepływy pracy można użyć <xref:System.ServiceModel.Activities.Send> wiadomości działania na wysyłanie wiadomości lub parametrów. Środowiska wykonawczego przepływów pracy, dodaje fabryki kanałów do pamięci podręcznej, którą tworzyć kanały typu <xref:System.ServiceModel.Channels.IRequestChannel> zastosowania <xref:System.ServiceModel.Activities.ReceiveReply> działanie przy użyciu <xref:System.ServiceModel.Activities.Send> działania i <xref:System.ServiceModel.Channels.IOutputChannel> korzystając tylko <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Poziomów współużytkowania pamięci podręcznej  
 Domyślnie w przepływie pracy pracujących <xref:System.ServiceModel.WorkflowServiceHost> pamięci podręcznej używanej przez <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów jest współużytkowany przez wszystkie wystąpienia przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania). Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia). Pamięć podręczna jest dostępna tylko dla <xref:System.ServiceModel.Activities.Send> działań, które nie korzystają z punktów końcowych zdefiniowanych w konfiguracji, o ile nie jest włączone buforowanie niebezpieczne.  
  
 Oto różnych pamięci podręcznej udostępnianie poziomy dostępne dla <xref:System.ServiceModel.Activities.Send> działania w przepływie pracy oraz ich zalecane użycie:  
  
- **Hostowanie poziom**: Na hoście, poziomu udostępniania pamięć podręczna jest dostępna tylko dla wystąpienia przepływu pracy, hostowana w hosta usługi przepływu pracy. Pamięć podręczna również mogą być współużytkowane między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.  
  
- **Wystąpienie poziomu**: W wystąpieniu, poziomu udostępniania, pamięć podręczna jest dostępna dla wystąpienia określonego przepływu pracy, w okresie swojego istnienia, ale pamięci podręcznej nie jest dostępna dla innych wystąpień przepływu pracy.  
  
- **Brak pamięci podręcznej**: Pamięć podręczna jest domyślnie wyłączona w przypadku przepływu pracy, który używa punktów końcowych zdefiniowanych w konfiguracji. Zalecane jest także zachowywać pamięci podręcznej wyłączone w tym przypadku, ponieważ jej włączeniu, może być niebezpieczne. Na przykład w przypadku określenia innej tożsamości (inne poświadczenia lub korzystanie z personifikacji) jest wymagana dla każdego wysyłania.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Zmienianie poziomu udostępniania dla przepływu pracy klienta pamięci podręcznej  
 Aby ustawić pamięci podręcznej udostępnianie w przepływie pracy klienta, należy dodać wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie dla żądanej grupy wystąpień przepływu pracy. Powoduje to udostępnianie pamięci podręcznej przez wszystkie wystąpienia przepływu pracy. W poniższych przykładach kodu pokazano, jak wykonać te kroki.  
  
 Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
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
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Zmienianie poziomu udostępniania w usłudze hostowanej przepływu pracy w pamięci podręcznej  
 Aby ustawić pamięci podręcznej udostępnianie w usłudze hostowanej przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie dla wszystkich hostów usługi przepływu pracy. Powoduje to udostępnianie pamięci podręcznej na wszystkich hostach usługi przepływu pracy. W poniższych przykładach kodu pokazano wykonania tych kroków.  
  
 Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na poziomie klasy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Następnie dodaj rozszerzenie statycznej pamięci podręcznej do każdego hosta usługi przepływu pracy.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Aby ustawić udostępnianie w usłudze hostowanej przepływu pracy na poziomie wystąpienia pamięci podręcznej, należy dodać `Func<SendMessageChannelCache>` delegować jako rozszerzenie hosta usługi przepływu pracy i Przypisz ten delegat do kodu, który tworzy nowe wystąpienie klasy <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy. Skutkuje to różne pamięci podręcznej dla każdego wystąpienia określonego przepływu pracy zamiast jednej pamięci podręcznej współużytkowane przez wszystkie wystąpienia przepływu pracy w hoście usług przepływu pracy. Poniższy przykład kodu pokazuje, jak to osiągnąć przy użyciu wyrażenia lambda do definiowania bezpośrednio <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenia, które wskazuje delegata.  
  
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
 Można dostosować ustawienia pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału. Ustawienia pamięci podręcznej są zdefiniowane w <xref:System.ServiceModel.Activities.ChannelCacheSettings> klasy. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Klasa definiuje domyślnych ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału w jej konstruktora domyślnego. W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.  
  
|Ustawienia|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Domyślne pamięci podręcznej|TimeSpan.MaxValue|2|16|  
|Domyślna pamięci podręcznej kanału|5|2|16|  
  
 Aby dostosować ustawienia pamięci podręcznej pamięci podręcznej i kanał fabryki, utworzyć <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy za pomocą sparametryzowanego konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> i przekazać nowe wystąpienie klasy <xref:System.ServiceModel.Activities.ChannelCacheSettings> przy użyciu niestandardowej wartości do poszczególnych `factorySettings` i `channelSettings` Parametry. Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy. W poniższym przykładzie kodu pokazano, jak wykonać te kroki dla wystąpienia przepływu pracy.  
  
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
  
 Aby włączyć buforowanie, gdy usługa przepływu pracy ma punktów końcowych zdefiniowanych w konfiguracji, tworzenia wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy za pomocą sparametryzowanego konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> z `allowUnsafeCaching` parametr `true`. Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy. Poniższy przykład kodu pokazuje, jak włączyć buforowanie dla wystąpienia przepływu pracy.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Aby wyłączyć pamięć podręczną całkowicie dla fabryki kanałów i kanały, należy wyłączyć pamięci podręcznej fabryki kanału. Również sposób powoduje wyłączenie pamięci podręcznej kanału, jak te kanały są własnością ich odpowiednich fabryki kanałów. Aby wyłączyć pamięci podręcznej fabryki kanału, należy przekazać `factorySettings` parametru, aby <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Konstruktor inicjowany do <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Użytkownik może korzystać tylko cache fabryki kanałów i wyłączanie pamięci podręcznej kanału, przekazując `channelSettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> inicjowane Konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0. Poniższy przykład kodu pokazuje to.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 W usłudze hostowanej przepływu pracy można określić fabryki pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji. W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą. W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` usługi zachowanie przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej. To zachowanie usługi jest dodawany do usługi za pośrednictwem `behaviorConfiguration` atrybutu.  
  
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
