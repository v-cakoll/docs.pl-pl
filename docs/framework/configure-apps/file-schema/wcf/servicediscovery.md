---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936272"
---
# <a name="servicediscovery"></a><span data-ttu-id="6a506-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="6a506-101">\<serviceDiscovery></span></span>
<span data-ttu-id="6a506-102">Określa możliwość odnajdywania punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="6a506-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="6a506-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a506-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a506-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="6a506-104">\<behaviors></span></span>  
<span data-ttu-id="6a506-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6a506-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6a506-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="6a506-106">\<behavior></span></span>  
<span data-ttu-id="6a506-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="6a506-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a506-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a506-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a506-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a506-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a506-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a506-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a506-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a506-111">Attributes</span></span>  
 <span data-ttu-id="6a506-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a506-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a506-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a506-113">Child Elements</span></span>  
  
|<span data-ttu-id="6a506-114">Element</span><span class="sxs-lookup"><span data-stu-id="6a506-114">Element</span></span>|<span data-ttu-id="6a506-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6a506-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a506-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="6a506-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="6a506-117">Kolekcja punktów końcowych anonsów.</span><span class="sxs-lookup"><span data-stu-id="6a506-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="6a506-118">Ta sekcja służy do określania punktów końcowych, które mają być używane do wysyłania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="6a506-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="6a506-119">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="6a506-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="6a506-120">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="6a506-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="6a506-121">Użyj tej sekcji, aby określić punkty końcowe, w których mają być nasłuchiwani wiadomości odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="6a506-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a506-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a506-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6a506-123">Element</span><span class="sxs-lookup"><span data-stu-id="6a506-123">Element</span></span>|<span data-ttu-id="6a506-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6a506-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a506-125">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="6a506-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6a506-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="6a506-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a506-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a506-127">Remarks</span></span>  
 <span data-ttu-id="6a506-128">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji udostępnia wszystkie punkty końcowe tej usługi.</span><span class="sxs-lookup"><span data-stu-id="6a506-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="6a506-129">Można skonfigurować funkcje odnajdywania takich punktów końcowych za pomocą [ \<DiscoveryEndpoint >](discoveryendpoint.md) lub [ \<announcementEndpoint >](announcementendpoint.md) elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a506-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="6a506-130">Użyj sekcji announcementEndpoint >, aby skonfigurować anonse, określając konfigurację punktu końcowego, który ma być używany do wysyłania anonsów usługi (online/Hello i offline/bye). [ \<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="6a506-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="6a506-131">Za pomocą sekcji [> DiscoveryEndpointręcznieOkreślpunktkońcowy,wktórymmająbyćnasłuchiwaniwiadomościodnajdowania.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="6a506-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a506-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a506-132">Example</span></span>  
 <span data-ttu-id="6a506-133">Poniższy przykład konfiguracji określa, że CalculatorService ma być wykrywalny, i opcjonalnie określa punkt końcowy anonsu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="6a506-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a506-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a506-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
