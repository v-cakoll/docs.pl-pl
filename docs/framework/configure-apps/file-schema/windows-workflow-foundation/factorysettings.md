---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: afb129407bc9dff752375f6e9fd69c728a809b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152187"
---
# <a name="factorysettings"></a><span data-ttu-id="afc09-101">\<fabrykiSzesje></span><span class="sxs-lookup"><span data-stu-id="afc09-101">\<factorySettings></span></span>
<span data-ttu-id="afc09-102">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="afc09-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="afc09-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="afc09-104">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="afc09-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="afc09-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="afc09-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="afc09-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>sendMessageChannelCache**](sendmessagechannelcache.md)</span><span class="sxs-lookup"><span data-stu-id="afc09-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span></span>\
<span data-ttu-id="afc09-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<fabrykiSzesje>**</span><span class="sxs-lookup"><span data-stu-id="afc09-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc09-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="afc09-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afc09-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="afc09-111">Attributes and Elements</span></span>  
 <span data-ttu-id="afc09-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="afc09-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afc09-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afc09-113">Attributes</span></span>  
  
|<span data-ttu-id="afc09-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="afc09-114">Attribute</span></span>|<span data-ttu-id="afc09-115">Opis</span><span class="sxs-lookup"><span data-stu-id="afc09-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afc09-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="afc09-116">idleTimeout</span></span>|<span data-ttu-id="afc09-117">Wartość przedziału czasu, która określa maksymalny interwał czasu, dla którego obiekt może być nieaktywna w pamięci podręcznej zanim zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="afc09-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="afc09-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="afc09-118">leaseTimeout</span></span>|<span data-ttu-id="afc09-119">TimeSpan wartość, która określa interwał czasu, po którym obiekt jest usuwany z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="afc09-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="afc09-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="afc09-120">maxItemsInCache</span></span>|<span data-ttu-id="afc09-121">Liczba całkowita określająca maksymalną liczbę obiektów, które mogą być w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="afc09-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afc09-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="afc09-122">Child Elements</span></span>  
 <span data-ttu-id="afc09-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="afc09-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afc09-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="afc09-124">Parent Elements</span></span>  
  
|<span data-ttu-id="afc09-125">Element</span><span class="sxs-lookup"><span data-stu-id="afc09-125">Element</span></span>|<span data-ttu-id="afc09-126">Opis</span><span class="sxs-lookup"><span data-stu-id="afc09-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afc09-127">\<>sendMessageChannelCache</span><span class="sxs-lookup"><span data-stu-id="afc09-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="afc09-128">Zachowanie usługi, która umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu wysyłania działań obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="afc09-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afc09-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afc09-129">Remarks</span></span>  
 <span data-ttu-id="afc09-130">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="afc09-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="afc09-131">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="afc09-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="afc09-132">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="afc09-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="afc09-133">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="afc09-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="afc09-134">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="afc09-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="afc09-135">Aby uzyskać więcej informacji na temat zmieniania domyślnych poziomów udostępniania pamięci podręcznej i ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanałów i kanału, zobacz [Zmienianie poziomów udostępniania pamięci podręcznej dla działań wysyłania](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="afc09-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="afc09-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="afc09-136">Example</span></span>  
 <span data-ttu-id="afc09-137">W obsługiwanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i pamięci podręcznej kanału w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afc09-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="afc09-138">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="afc09-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="afc09-139">W poniższym przykładzie przedstawiono zawartość `MyChannelCacheBehavior` pliku konfiguracyjnego, który zawiera zachowanie usługi z niestandardowymi ustawieniami pamięci podręcznej fabryki i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="afc09-139">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="afc09-140">To zachowanie usługi jest dodawany `behaviorConfiguration` do usługi za pośrednictwem atrybutu.</span><span class="sxs-lookup"><span data-stu-id="afc09-140">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afc09-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afc09-141">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="afc09-142">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="afc09-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
