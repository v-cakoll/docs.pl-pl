---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 73943f5f962a6963809e2c65ce8593f6181559f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587336"
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="ecfde-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="ecfde-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="ecfde-103">Określa wykrywalność usługi punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ecfde-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="ecfde-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ecfde-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ecfde-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ecfde-105">\<behaviors></span></span>  
<span data-ttu-id="ecfde-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ecfde-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ecfde-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ecfde-107">\<behavior></span></span>  
<span data-ttu-id="ecfde-108">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="ecfde-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecfde-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecfde-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecfde-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ecfde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ecfde-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ecfde-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecfde-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ecfde-112">Attributes</span></span>  
 <span data-ttu-id="ecfde-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="ecfde-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecfde-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ecfde-114">Child Elements</span></span>  
  
|<span data-ttu-id="ecfde-115">Element</span><span class="sxs-lookup"><span data-stu-id="ecfde-115">Element</span></span>|<span data-ttu-id="ecfde-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ecfde-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecfde-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="ecfde-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="ecfde-118">Kolekcja punktów końcowych anonsu.</span><span class="sxs-lookup"><span data-stu-id="ecfde-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="ecfde-119">Ta sekcja umożliwia określenie punktów końcowych, używany do wysyłania wiadomości anonsów.</span><span class="sxs-lookup"><span data-stu-id="ecfde-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="ecfde-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="ecfde-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="ecfde-121">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecfde-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="ecfde-122">Ta sekcja umożliwia określenie punktów końcowych, na którym chcesz nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecfde-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecfde-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ecfde-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ecfde-124">Element</span><span class="sxs-lookup"><span data-stu-id="ecfde-124">Element</span></span>|<span data-ttu-id="ecfde-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ecfde-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecfde-126">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ecfde-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ecfde-127">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ecfde-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecfde-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecfde-128">Remarks</span></span>  
 <span data-ttu-id="ecfde-129">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji sprawia, że wszystkie punkty końcowe usługi wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="ecfde-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="ecfde-130">Można dodatkowo skonfigurować funkcji odnajdywania tych punktów końcowych przy użyciu [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) lub [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ecfde-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="ecfde-131">Użyj [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) sekcji, aby skonfigurować anonsów, określając konfiguracji punktu końcowego na potrzeby wysyłania zawiadomienia dotyczące usługi (online/Hello i offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="ecfde-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="ecfde-132">Użyj [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy do nasłuchiwania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecfde-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecfde-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecfde-133">Example</span></span>  
 <span data-ttu-id="ecfde-134">W poniższym przykładzie konfiguracja Określa, że CalculatorService być wykrywalny i opcjonalnie określa punkt końcowy anonsu do użycia.</span><span class="sxs-lookup"><span data-stu-id="ecfde-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="ecfde-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecfde-135">See also</span></span>
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
