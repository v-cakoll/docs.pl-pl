---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: d8e87799962638ac6514ebb31bbc9e209b39c98d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090930"
---
# <a name="factorysettings"></a><span data-ttu-id="86a2a-101">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="86a2a-101">\<factorySettings></span></span>
<span data-ttu-id="86a2a-102">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="86a2a-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="86a2a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86a2a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="86a2a-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="86a2a-104">\<behaviors></span></span>  
<span data-ttu-id="86a2a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="86a2a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="86a2a-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="86a2a-106">\<behavior></span></span>  
<span data-ttu-id="86a2a-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="86a2a-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="86a2a-108">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="86a2a-108">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a2a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="86a2a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86a2a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="86a2a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86a2a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="86a2a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86a2a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="86a2a-112">Attributes</span></span>  
  
|<span data-ttu-id="86a2a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="86a2a-113">Attribute</span></span>|<span data-ttu-id="86a2a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="86a2a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86a2a-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="86a2a-115">idleTimeout</span></span>|<span data-ttu-id="86a2a-116">Wartość przedziału czasu, która określa maksymalny interwał czasu, dla którego obiekt może być nieaktywna w pamięci podręcznej zanim zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="86a2a-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="86a2a-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="86a2a-117">leaseTimeout</span></span>|<span data-ttu-id="86a2a-118">Wartość przedziału czasu, który określa przedział czasu, po którym obiekt zostanie usunięty z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="86a2a-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="86a2a-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="86a2a-119">maxItemsInCache</span></span>|<span data-ttu-id="86a2a-120">Liczba całkowita określająca maksymalną liczbę obiektów, które mogą być w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="86a2a-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86a2a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="86a2a-121">Child Elements</span></span>  
 <span data-ttu-id="86a2a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="86a2a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86a2a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="86a2a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="86a2a-124">Element</span><span class="sxs-lookup"><span data-stu-id="86a2a-124">Element</span></span>|<span data-ttu-id="86a2a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="86a2a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86a2a-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="86a2a-126">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="86a2a-127">Zachowanie usługi, który umożliwia dostosowywania pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału do wysyłania wiadomości do punktów końcowych usługi za pomocą wysyłania wiadomości działania przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="86a2a-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86a2a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86a2a-128">Remarks</span></span>  
 <span data-ttu-id="86a2a-129">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="86a2a-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="86a2a-130">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="86a2a-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="86a2a-131">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="86a2a-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="86a2a-132">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="86a2a-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="86a2a-133">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="86a2a-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="86a2a-134">Aby uzyskać więcej informacji o tym, jak zmienić domyślny pamięci podręcznej udostępnianie poziomy i ustawienia pamięci podręcznej fabryki kanałów i pamięci podręcznej kanału, zobacz [Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="86a2a-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a2a-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="86a2a-135">Example</span></span>  
 <span data-ttu-id="86a2a-136">W usłudze hostowanej przepływu pracy można określić fabryki pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86a2a-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="86a2a-137">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="86a2a-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="86a2a-138">W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera **MyChannelCacheBehavior** usługi zachowanie przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="86a2a-138">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="86a2a-139">To zachowanie usługi jest dodawany do usługi za pośrednictwem **behaviorConfiguarion** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="86a2a-139">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86a2a-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86a2a-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="86a2a-141">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="86a2a-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
