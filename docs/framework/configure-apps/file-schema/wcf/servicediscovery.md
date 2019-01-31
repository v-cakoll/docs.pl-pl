---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 564410fdc4085cc3ed14c394006551cddb028910
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267875"
---
# <a name="servicediscovery"></a><span data-ttu-id="3394c-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="3394c-101">\<serviceDiscovery></span></span>
<span data-ttu-id="3394c-102">Określa wykrywalność usługi punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3394c-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="3394c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3394c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3394c-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3394c-104">\<behaviors></span></span>  
<span data-ttu-id="3394c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3394c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3394c-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3394c-106">\<behavior></span></span>  
<span data-ttu-id="3394c-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="3394c-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3394c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3394c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3394c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3394c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3394c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3394c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3394c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3394c-111">Attributes</span></span>  
 <span data-ttu-id="3394c-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="3394c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3394c-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3394c-113">Child Elements</span></span>  
  
|<span data-ttu-id="3394c-114">Element</span><span class="sxs-lookup"><span data-stu-id="3394c-114">Element</span></span>|<span data-ttu-id="3394c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3394c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3394c-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="3394c-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="3394c-117">Kolekcja punktów końcowych anonsu.</span><span class="sxs-lookup"><span data-stu-id="3394c-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="3394c-118">Ta sekcja umożliwia określenie punktów końcowych, używany do wysyłania wiadomości anonsów.</span><span class="sxs-lookup"><span data-stu-id="3394c-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="3394c-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="3394c-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="3394c-120">Kolekcja punktów końcowych odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3394c-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="3394c-121">Ta sekcja umożliwia określenie punktów końcowych, na którym chcesz nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3394c-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3394c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3394c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3394c-123">Element</span><span class="sxs-lookup"><span data-stu-id="3394c-123">Element</span></span>|<span data-ttu-id="3394c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3394c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3394c-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3394c-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3394c-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="3394c-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3394c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3394c-127">Remarks</span></span>  
 <span data-ttu-id="3394c-128">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji sprawia, że wszystkie punkty końcowe usługi wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="3394c-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="3394c-129">Można dodatkowo skonfigurować funkcji odnajdywania tych punktów końcowych przy użyciu [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) lub [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3394c-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="3394c-130">Użyj [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) sekcji, aby skonfigurować anonsów, określając konfiguracji punktu końcowego na potrzeby wysyłania zawiadomienia dotyczące usługi (online/Hello i offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="3394c-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="3394c-131">Użyj [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy do nasłuchiwania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3394c-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3394c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3394c-132">Example</span></span>  
 <span data-ttu-id="3394c-133">W poniższym przykładzie konfiguracja Określa, że CalculatorService być wykrywalny i opcjonalnie określa punkt końcowy anonsu do użycia.</span><span class="sxs-lookup"><span data-stu-id="3394c-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3394c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3394c-134">See also</span></span>
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
