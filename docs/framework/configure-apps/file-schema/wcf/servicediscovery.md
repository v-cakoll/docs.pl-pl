---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399644"
---
# \<serviceDiscovery>
<span data-ttu-id="80a01-101">Określa możliwość odnajdywania punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="80a01-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="80a01-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="80a01-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80a01-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80a01-103">Attributes and Elements</span></span>  
 <span data-ttu-id="80a01-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80a01-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80a01-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80a01-105">Attributes</span></span>  
 <span data-ttu-id="80a01-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="80a01-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80a01-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80a01-107">Child Elements</span></span>  
  
|<span data-ttu-id="80a01-108">Element</span><span class="sxs-lookup"><span data-stu-id="80a01-108">Element</span></span>|<span data-ttu-id="80a01-109">Opis</span><span class="sxs-lookup"><span data-stu-id="80a01-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="80a01-110">Kolekcja punktów końcowych anonsów.</span><span class="sxs-lookup"><span data-stu-id="80a01-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="80a01-111">Ta sekcja służy do określania punktów końcowych, które mają być używane do wysyłania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="80a01-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="80a01-112">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="80a01-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="80a01-113">Użyj tej sekcji, aby określić punkty końcowe, w których mają być nasłuchiwani wiadomości odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="80a01-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80a01-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80a01-114">Parent Elements</span></span>  
  
|<span data-ttu-id="80a01-115">Element</span><span class="sxs-lookup"><span data-stu-id="80a01-115">Element</span></span>|<span data-ttu-id="80a01-116">Opis</span><span class="sxs-lookup"><span data-stu-id="80a01-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="80a01-117">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="80a01-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80a01-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80a01-118">Remarks</span></span>  
 <span data-ttu-id="80a01-119">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji udostępnia wszystkie punkty końcowe tej usługi.</span><span class="sxs-lookup"><span data-stu-id="80a01-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="80a01-120">Można skonfigurować funkcje odnajdywania takich punktów końcowych przy użyciu [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) elementów podrzędnych lub.</span><span class="sxs-lookup"><span data-stu-id="80a01-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="80a01-121">Skorzystaj z [\<announcementEndpoint>](announcementendpoint.md) sekcji, aby skonfigurować Anonsy, określając konfigurację punktu końcowego, który ma być używany do wysyłania anonsów usługi (online/Hello i offline/bye).</span><span class="sxs-lookup"><span data-stu-id="80a01-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="80a01-122">Użyj [\<discoveryEndpoint>](discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy, w którym mają być nasłuchiwani wiadomości odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="80a01-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80a01-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="80a01-123">Example</span></span>  
 <span data-ttu-id="80a01-124">Poniższy przykład konfiguracji określa, że CalculatorService ma być wykrywalny, i opcjonalnie określa punkt końcowy anonsu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="80a01-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80a01-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80a01-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
