---
title: <channelSettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
ms.openlocfilehash: 9caf87bdf2029d273a9d6d7ac90b83ba72bafc7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945834"
---
# <a name="channelsettings"></a><span data-ttu-id="d2e7b-101">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="d2e7b-101">\<channelSettings></span></span>
<span data-ttu-id="d2e7b-102">Określa ustawienia pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-102">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="d2e7b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2e7b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2e7b-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="d2e7b-104">\<behaviors></span></span>  
<span data-ttu-id="d2e7b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d2e7b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d2e7b-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="d2e7b-106">\<behavior></span></span>  
<span data-ttu-id="d2e7b-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="d2e7b-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="d2e7b-108">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="d2e7b-108">\<channelSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e7b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2e7b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2e7b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2e7b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2e7b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2e7b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2e7b-112">Attributes</span></span>  
  
|<span data-ttu-id="d2e7b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2e7b-113">Attribute</span></span>|<span data-ttu-id="d2e7b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d2e7b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2e7b-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="d2e7b-115">idleTimeout</span></span>|<span data-ttu-id="d2e7b-116">Wartość przedziału czasu, która określa maksymalny interwał czasu, dla którego obiekt może być nieaktywna w pamięci podręcznej zanim zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="d2e7b-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="d2e7b-117">leaseTimeout</span></span>|<span data-ttu-id="d2e7b-118">Wartość TimeSpan, która określa przedział czasu, po którym obiekt zostanie usunięty z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="d2e7b-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="d2e7b-119">maxItemsInCache</span></span>|<span data-ttu-id="d2e7b-120">Liczba całkowita określająca maksymalną liczbę obiektów, które mogą być w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2e7b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2e7b-121">Child Elements</span></span>  
 <span data-ttu-id="d2e7b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2e7b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2e7b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d2e7b-124">Element</span><span class="sxs-lookup"><span data-stu-id="d2e7b-124">Element</span></span>|<span data-ttu-id="d2e7b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d2e7b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2e7b-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="d2e7b-126">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="d2e7b-127">Zachowanie usługi, które umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów oraz ustawień pamięci podręcznej kanału dla przepływów pracy, które wysyłają komunikaty do punktów końcowych usługi przy użyciu działań wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2e7b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2e7b-128">Remarks</span></span>  
 <span data-ttu-id="d2e7b-129">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="d2e7b-130">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="d2e7b-131">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="d2e7b-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="d2e7b-132">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="d2e7b-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="d2e7b-133">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="d2e7b-134">Aby uzyskać więcej informacji na temat zmiany domyślnych poziomów udostępniania pamięci podręcznej i ustawień pamięci podręcznej dla fabryki kanałów i pamięci podręcznej kanałów, zobacz [Zmiana poziomów udostępniania pamięci podręcznej dla działań wysyłania](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="d2e7b-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2e7b-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2e7b-135">Example</span></span>  
 <span data-ttu-id="d2e7b-136">W hostowanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i ustawień pamięci podręcznej kanału w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="d2e7b-137">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="d2e7b-138">Poniższy przykład pokazuje zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` zachowanie usługi z niestandardową pamięcią podręczną i ustawieniami pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-138">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="d2e7b-139">To zachowanie usługi jest dodawane do usługi za pomocą `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2e7b-139">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2e7b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2e7b-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="d2e7b-141">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="d2e7b-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
