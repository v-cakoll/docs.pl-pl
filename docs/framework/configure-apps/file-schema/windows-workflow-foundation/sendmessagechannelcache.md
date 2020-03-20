---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152004"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="8baa8-101">\<> sendMessageChannelCache</span><span class="sxs-lookup"><span data-stu-id="8baa8-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="8baa8-102">Zachowanie usługi, która umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu wysyłania działań obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8baa8-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="8baa8-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8baa8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8baa8-104">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8baa8-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="8baa8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8baa8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8baa8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8baa8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8baa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8baa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="8baa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sendMessageChannelCache**</span><span class="sxs-lookup"><span data-stu-id="8baa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8baa8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8baa8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8baa8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8baa8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8baa8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8baa8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8baa8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8baa8-112">Attributes</span></span>  
  
|<span data-ttu-id="8baa8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8baa8-113">Attribute</span></span>|<span data-ttu-id="8baa8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8baa8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8baa8-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="8baa8-115">allowUnsafeCaching</span></span>|<span data-ttu-id="8baa8-116">Wartość logiczna, która wskazuje, czy należy włączyć buforowanie.</span><span class="sxs-lookup"><span data-stu-id="8baa8-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="8baa8-117">Jeśli usługa przepływu pracy ma powiązań niestandardowe lub niestandardowe zachowania, buforowanie może być niebezpieczne i dlatego jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8baa8-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="8baa8-118">Jednak jeśli chcesz włączyć buforowanie na ustaw tę właściwość do **true**.</span><span class="sxs-lookup"><span data-stu-id="8baa8-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8baa8-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8baa8-119">Child Elements</span></span>  
  
|<span data-ttu-id="8baa8-120">Element</span><span class="sxs-lookup"><span data-stu-id="8baa8-120">Element</span></span>|<span data-ttu-id="8baa8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8baa8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8baa8-122">\<>kanałów</span><span class="sxs-lookup"><span data-stu-id="8baa8-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="8baa8-123">Określa ustawienia pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="8baa8-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="8baa8-124">\<fabrykiSzesje></span><span class="sxs-lookup"><span data-stu-id="8baa8-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="8baa8-125">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="8baa8-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8baa8-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8baa8-126">Parent Elements</span></span>  
  
|<span data-ttu-id="8baa8-127">Element</span><span class="sxs-lookup"><span data-stu-id="8baa8-127">Element</span></span>|<span data-ttu-id="8baa8-128">Opis</span><span class="sxs-lookup"><span data-stu-id="8baa8-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8baa8-129">\<zachowanie> \<usługZachod></span><span class="sxs-lookup"><span data-stu-id="8baa8-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8baa8-130">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="8baa8-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8baa8-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8baa8-131">Remarks</span></span>  
 <span data-ttu-id="8baa8-132">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="8baa8-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="8baa8-133">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8baa8-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="8baa8-134">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="8baa8-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="8baa8-135">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="8baa8-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="8baa8-136">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8baa8-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="8baa8-137">Aby uzyskać więcej informacji na temat zmieniania domyślnych poziomów udostępniania pamięci podręcznej i ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanałów i kanału, zobacz [Zmienianie poziomów udostępniania pamięci podręcznej dla działań wysyłania](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="8baa8-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8baa8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="8baa8-138">Example</span></span>  
 <span data-ttu-id="8baa8-139">W obsługiwanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i pamięci podręcznej kanału w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8baa8-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="8baa8-140">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="8baa8-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="8baa8-141">W poniższym przykładzie przedstawiono zawartość `MyChannelCacheBehavior` pliku konfiguracyjnego, który zawiera zachowanie usługi z niestandardowymi ustawieniami pamięci podręcznej fabryki i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="8baa8-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="8baa8-142">To zachowanie usługi jest dodawany `behaviorConfiguration` do usługi za pośrednictwem atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8baa8-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8baa8-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8baa8-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="8baa8-144">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="8baa8-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
