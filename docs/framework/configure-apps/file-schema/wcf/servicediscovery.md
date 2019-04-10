---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 54a9833f56927568af711a103bd3831b767711e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209999"
---
# <a name="servicediscovery"></a><span data-ttu-id="b5310-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="b5310-101">\<serviceDiscovery></span></span>
<span data-ttu-id="b5310-102">Określa wykrywalność usługi punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b5310-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="b5310-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b5310-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5310-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b5310-104">\<behaviors></span></span>  
<span data-ttu-id="b5310-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b5310-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b5310-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b5310-106">\<behavior></span></span>  
<span data-ttu-id="b5310-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="b5310-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5310-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5310-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5310-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5310-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b5310-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5310-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5310-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5310-111">Attributes</span></span>  
 <span data-ttu-id="b5310-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="b5310-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5310-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5310-113">Child Elements</span></span>  
  
|<span data-ttu-id="b5310-114">Element</span><span class="sxs-lookup"><span data-stu-id="b5310-114">Element</span></span>|<span data-ttu-id="b5310-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b5310-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5310-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="b5310-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="b5310-117">Kolekcja punktów końcowych anonsu.</span><span class="sxs-lookup"><span data-stu-id="b5310-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="b5310-118">Ta sekcja umożliwia określenie punktów końcowych, używany do wysyłania wiadomości anonsów.</span><span class="sxs-lookup"><span data-stu-id="b5310-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="b5310-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="b5310-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="b5310-120">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="b5310-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="b5310-121">Ta sekcja umożliwia określenie punktów końcowych, na którym chcesz nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="b5310-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5310-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5310-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5310-123">Element</span><span class="sxs-lookup"><span data-stu-id="b5310-123">Element</span></span>|<span data-ttu-id="b5310-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b5310-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5310-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b5310-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b5310-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="b5310-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5310-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5310-127">Remarks</span></span>  
 <span data-ttu-id="b5310-128">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji sprawia, że wszystkie punkty końcowe usługi wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="b5310-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="b5310-129">Można dodatkowo skonfigurować funkcji odnajdywania tych punktów końcowych przy użyciu [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) lub [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b5310-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="b5310-130">Użyj [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) sekcji, aby skonfigurować anonsów, określając konfiguracji punktu końcowego na potrzeby wysyłania zawiadomienia dotyczące usługi (online/Hello i offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="b5310-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="b5310-131">Użyj [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy do nasłuchiwania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="b5310-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5310-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5310-132">Example</span></span>  
 <span data-ttu-id="b5310-133">W poniższym przykładzie konfiguracja Określa, że CalculatorService być wykrywalny i opcjonalnie określa punkt końcowy anonsu do użycia.</span><span class="sxs-lookup"><span data-stu-id="b5310-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5310-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5310-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
