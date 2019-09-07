---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399644"
---
# <a name="servicediscovery"></a><span data-ttu-id="93ee5-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="93ee5-101">\<serviceDiscovery></span></span>
<span data-ttu-id="93ee5-102">Określa możliwość odnajdywania punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="93ee5-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="93ee5-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93ee5-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="93ee5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="93ee5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="93ee5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="93ee5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> servicediscovery**</span><span class="sxs-lookup"><span data-stu-id="93ee5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ee5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="93ee5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93ee5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93ee5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93ee5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="93ee5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93ee5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93ee5-112">Attributes</span></span>  
 <span data-ttu-id="93ee5-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="93ee5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93ee5-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93ee5-114">Child Elements</span></span>  
  
|<span data-ttu-id="93ee5-115">Element</span><span class="sxs-lookup"><span data-stu-id="93ee5-115">Element</span></span>|<span data-ttu-id="93ee5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="93ee5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93ee5-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="93ee5-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="93ee5-118">Kolekcja punktów końcowych anonsów.</span><span class="sxs-lookup"><span data-stu-id="93ee5-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="93ee5-119">Ta sekcja służy do określania punktów końcowych, które mają być używane do wysyłania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="93ee5-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="93ee5-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="93ee5-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="93ee5-121">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="93ee5-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="93ee5-122">Użyj tej sekcji, aby określić punkty końcowe, w których mają być nasłuchiwani wiadomości odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="93ee5-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93ee5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93ee5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="93ee5-124">Element</span><span class="sxs-lookup"><span data-stu-id="93ee5-124">Element</span></span>|<span data-ttu-id="93ee5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="93ee5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93ee5-126">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="93ee5-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="93ee5-127">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="93ee5-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93ee5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93ee5-128">Remarks</span></span>  
 <span data-ttu-id="93ee5-129">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji udostępnia wszystkie punkty końcowe tej usługi.</span><span class="sxs-lookup"><span data-stu-id="93ee5-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="93ee5-130">Można skonfigurować funkcje odnajdywania takich punktów końcowych za pomocą [ \<DiscoveryEndpoint >](discoveryendpoint.md) lub [ \<announcementEndpoint >](announcementendpoint.md) elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="93ee5-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="93ee5-131">Użyj sekcji announcementEndpoint >, aby skonfigurować anonse, określając konfigurację punktu końcowego, który ma być używany do wysyłania anonsów usługi (online/Hello i offline/bye). [ \<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="93ee5-132">Za pomocą sekcji [> DiscoveryEndpointręcznieOkreślpunktkońcowy,wktórymmająbyćnasłuchiwaniwiadomościodnajdowania.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="93ee5-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ee5-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="93ee5-133">Example</span></span>  
 <span data-ttu-id="93ee5-134">Poniższy przykład konfiguracji określa, że CalculatorService ma być wykrywalny, i opcjonalnie określa punkt końcowy anonsu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="93ee5-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93ee5-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93ee5-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
