---
title: "Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0254673277cf6435ec835351b89fc03db01b2ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozszerzenia umożliwia dostosowanie pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia kanału pamięci podręcznej dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi przy użyciu <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów. Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>. Pamięć podręczna fabryki kanału zawiera buforowane <xref:System.ServiceModel.ChannelFactory%601> obiektów. Pamięć podręczna kanału zawiera kanałów z pamięci podręcznej.  
  
> [!NOTE]
>  Przepływy pracy można użyć <xref:System.ServiceModel.Activities.Send> wiadomości działań do wysyłania wiadomości lub parametrów. Środowiska uruchomieniowego przepływu pracy, dodaje fabryk kanałów, które do pamięci podręcznej, która tworzenia kanałów typu <xref:System.ServiceModel.Channels.IRequestChannel> korzystając <xref:System.ServiceModel.Activities.ReceiveReply> działania o <xref:System.ServiceModel.Activities.Send> działania i <xref:System.ServiceModel.Channels.IOutputChannel> używając po prostu <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Poziomów współużytkowania pamięci podręcznej  
 Domyślnie w przepływie pracy obsługiwanych przez <xref:System.ServiceModel.WorkflowServiceHost> używanych przez pamięć podręczną <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów jest współużytkowana przez wszystkie wystąpienia przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (buforowanie hosta level). Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia). Pamięć podręczna jest dostępna tylko dla <xref:System.ServiceModel.Activities.Send> działania, które nie należy używać punktach końcowych zdefiniowanych w konfiguracji, chyba że jest włączone buforowanie niebezpieczne.  
  
 Poniżej przedstawiono różne pamięci podręcznej udostępnianie dostępnych dla poziomów <xref:System.ServiceModel.Activities.Send> działań w przepływie pracy oraz ich zalecane użycie:  
  
-   **Host poziom**: na hoście poziomu udostępniania pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy w hosta usługi przepływu pracy. Pamięć podręczna również może być udostępniane między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.  
  
-   **Wystąpienie poziomu**: W przypadku poziomu udostępniania, jest dostępna do wystąpienia określonego przepływu pracy przez jego okres istnienia pamięci podręcznej, ale pamięci podręcznej nie jest dostępna dla innych wystąpień przepływu pracy.  
  
-   **Brak pamięci podręcznej**: pamięci podręcznej jest domyślnie wyłączona w przypadku przepływu pracy korzystającego z punktów końcowych zdefiniowanych w konfiguracji. Zalecane jest również przechowywać w pamięci podręcznej wyłączone w tym przypadku ponieważ jej włączeniu, może być niebezpieczne. Na przykład, jeśli inną tożsamość (inne poświadczenia lub korzystanie z personifikacji) jest wymagane dla każdego wysyłania.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Zmiana poziomu udostępniania dla przepływu pracy klienta pamięci podręcznej  
 Aby skonfigurować udostępnianie w przepływie pracy klienta pamięci podręcznej, należy dodać wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy do żądany zestaw wystąpień przepływów pracy jako rozszerzenie. Powoduje to udostępnianie pamięci podręcznej dla wszystkich wystąpień przepływu pracy. W poniższych przykładach kodu pokazano, jak wykonać następujące kroki.  
  
 Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Następnie dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Zmiana pamięci podręcznej, poziomu udostępniania dla usługi hostowanej przepływu pracy  
 Aby ustawić pamięci podręcznej udostępnianie w usłudze hostowanej przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy do wszystkich hostów usługi przepływu pracy jako rozszerzenie. Powoduje to udostępnianie pamięci podręcznej na wszystkich hostach usługi przepływu pracy. W poniższych przykładach kodu pokazano do wykonania tych kroków.  
  
 Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na poziomie klasy.  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Następnie dodaj rozszerzenie statycznej pamięci podręcznej do każdego hosta usługi przepływu pracy.  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Aby skonfigurować udostępnianie w usłudze hostowanej przepływu pracy na poziomie wystąpienia pamięci podręcznej, należy dodać `Func<SendMessageChannelCache>` delegować do hosta usługi przepływu pracy jako rozszerzenie i Przypisz ten delegat do kodu, który tworzy nowe wystąpienie klasy <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy. Powoduje to różnych pamięci podręcznej dla każdego wystąpienia przepływu pracy zamiast jednej pamięci podręcznej, współużytkowana przez wszystkie wystąpienia przepływu pracy z hosta usługi przepływu pracy. Poniższy przykład kodu pokazuje, jak to osiągnąć za pomocą wyrażenia lambda do definiowania bezpośrednio <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenia, które wskazuje delegata.  
  
```  
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
 Można dostosować ustawienia pamięci podręcznej pamięci podręcznej fabryki kanału i pamięci podręcznej kanału. Ustawienia pamięci podręcznej są definiowane w <xref:System.ServiceModel.Activities.ChannelCacheSettings> klasy. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Klasa definiuje domyślnych ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału w jego domyślny konstruktor. W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.  
  
|Ustawienia|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Ustawienia fabryczne pamięci podręcznej|Wartość TimeSpan.MaxValue|2|16|  
|Domyślna pamięci podręcznej kanału|5|2|16|  
  
 Aby dostosować ustawienia pamięci podręcznej pamięci podręcznej i kanał fabryki, wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> przy użyciu sparametryzowanym konstruktorze <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> i przekaż nowe wystąpienie klasy <xref:System.ServiceModel.Activities.ChannelCacheSettings> z wartościami niestandardowymi wszystkie `factorySettings` i `channelSettings` Parametry. Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy. Poniższy przykład kodu pokazuje sposób wykonać te czynności dla wystąpienia przepływu pracy.  
  
```  
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
  
 Aby włączyć buforowanie w punktach końcowych zdefiniowanych w konfiguracji ma usługi przepływu pracy, należy utworzyć wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> przy użyciu sparametryzowanym konstruktorze <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> z `allowUnsafeCaching` ustawiono parametr `true`. Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy. Poniższy przykład kodu pokazuje, jak można włączyć buforowanie dla wystąpienia przepływu pracy.  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Aby wyłączyć w pamięci podręcznej całkowicie fabryk kanałów i kanały, należy wyłączyć pamięci podręcznej fabryki kanału. Również w ten sposób powoduje wyłączenie pamięci podręcznej kanału, jak kanały są własnością ich odpowiednich fabryk kanałów. Aby wyłączyć pamięci podręcznej fabryki kanału, należy przekazać `factorySettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> zainicjowany konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0. Poniższy przykład kodu pokazuje to.  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Można użyć tylko bufor fabryki kanału i wyłączenie pamięci podręcznej kanału przekazując `channelSettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> zainicjowany konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0. Poniższy przykład kodu pokazuje to.  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 W usłudze hostowanej przepływu pracy można określić fabrykę pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji. W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą. W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` zachowania usługi przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej. To zachowanie usługi zostanie dodany do usługi za pośrednictwem `behaviorConfiguarion` atrybutu.  
  
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
