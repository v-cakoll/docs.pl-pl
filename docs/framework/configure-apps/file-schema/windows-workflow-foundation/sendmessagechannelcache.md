---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152004"
---
# \<sendMessageChannelCache>
<span data-ttu-id="f1482-101">Zachowanie usługi, które umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów oraz ustawień pamięci podręcznej kanału dla przepływów pracy, które wysyłają komunikaty do punktów końcowych usługi przy użyciu działań wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f1482-101">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a><span data-ttu-id="f1482-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1482-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1482-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1482-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f1482-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1482-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1482-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1482-105">Attributes</span></span>  
  
|<span data-ttu-id="f1482-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1482-106">Attribute</span></span>|<span data-ttu-id="f1482-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f1482-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1482-108">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="f1482-108">allowUnsafeCaching</span></span>|<span data-ttu-id="f1482-109">Wartość logiczna, która wskazuje, czy należy włączyć buforowanie.</span><span class="sxs-lookup"><span data-stu-id="f1482-109">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="f1482-110">Jeśli usługa przepływu pracy ma powiązań niestandardowe lub niestandardowe zachowania, buforowanie może być niebezpieczne i dlatego jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f1482-110">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="f1482-111">Jeśli jednak chcesz włączyć buforowanie, ustaw dla tej właściwości **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="f1482-111">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1482-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1482-112">Child Elements</span></span>  
  
|<span data-ttu-id="f1482-113">Element</span><span class="sxs-lookup"><span data-stu-id="f1482-113">Element</span></span>|<span data-ttu-id="f1482-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f1482-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|<span data-ttu-id="f1482-115">Określa ustawienia pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="f1482-115">Specifies the settings of the channel cache.</span></span>|  
|[\<factorySettings>](factorysettings.md)|<span data-ttu-id="f1482-116">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="f1482-116">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1482-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1482-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f1482-118">Element</span><span class="sxs-lookup"><span data-stu-id="f1482-118">Element</span></span>|<span data-ttu-id="f1482-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f1482-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1482-120">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f1482-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f1482-121">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="f1482-121">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1482-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1482-122">Remarks</span></span>  
 <span data-ttu-id="f1482-123">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="f1482-123">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="f1482-124">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f1482-124">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="f1482-125">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="f1482-125">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="f1482-126">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="f1482-126">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="f1482-127">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f1482-127">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="f1482-128">Aby uzyskać więcej informacji na temat zmiany domyślnych poziomów udostępniania pamięci podręcznej i ustawień pamięci podręcznej dla fabryki kanałów i pamięci podręcznej kanałów, zobacz [Zmiana poziomów udostępniania pamięci podręcznej dla działań wysyłania](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f1482-128">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1482-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1482-129">Example</span></span>  
 <span data-ttu-id="f1482-130">W hostowanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i ustawień pamięci podręcznej kanału w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1482-130">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="f1482-131">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="f1482-131">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="f1482-132">Poniższy przykład pokazuje zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` zachowanie usługi z niestandardową pamięcią podręczną i ustawieniami pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="f1482-132">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="f1482-133">To zachowanie usługi jest dodawane do usługi za pomocą `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f1482-133">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1482-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1482-134">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="f1482-135">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="f1482-135">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
