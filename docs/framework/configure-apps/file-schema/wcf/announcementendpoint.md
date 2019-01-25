---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 8e180d53260ccf3364ab3c8d7b076f78917526d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729882"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="e78a6-102">&lt;AnnouncementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="e78a6-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="e78a6-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym.</span><span class="sxs-lookup"><span data-stu-id="e78a6-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="e78a6-104">Usługa może opcjonalnie ogłaszają jego dostępność, wysyłając anonse online i offline, po otwarciu lub zamknięciu odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e78a6-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="e78a6-105">Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu i używa AnnouncementClient przeprowadzić anonsów.</span><span class="sxs-lookup"><span data-stu-id="e78a6-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="e78a6-106">Klient chcą nasłuchiwanie anonsu z innej usługi faktycznie działa jako usługa WCF; dlatego musisz skonfigurować punkty końcowe anonsu dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="e78a6-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="e78a6-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e78a6-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="e78a6-108">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e78a6-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78a6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e78a6-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e78a6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e78a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e78a6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e78a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e78a6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e78a6-112">Attributes</span></span>  
  
|<span data-ttu-id="e78a6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e78a6-113">Attribute</span></span>|<span data-ttu-id="e78a6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e78a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e78a6-115">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="e78a6-115">discoveryVersion</span></span>|<span data-ttu-id="e78a6-116">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="e78a6-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="e78a6-117">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="e78a6-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="e78a6-118">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="e78a6-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="e78a6-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="e78a6-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="e78a6-120">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem wiadomości powitania.</span><span class="sxs-lookup"><span data-stu-id="e78a6-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="e78a6-121">Przed wysłaniem wiadomości będą oczekiwać czasu losowego wartość z zakresu od 0 i wartość tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e78a6-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="e78a6-122">Ten atrybut służy do ustawiania małe, losowego opóźnienia, aby zapobiec nadmiarem sieci, gdy trafia do sieci i wszystkich usług pochodzą wróci do trybu online w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="e78a6-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="e78a6-123">nazwa</span><span class="sxs-lookup"><span data-stu-id="e78a6-123">name</span></span>|<span data-ttu-id="e78a6-124">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e78a6-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e78a6-125">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e78a6-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e78a6-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e78a6-126">Child Elements</span></span>  
 <span data-ttu-id="e78a6-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="e78a6-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e78a6-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e78a6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e78a6-129">Element</span><span class="sxs-lookup"><span data-stu-id="e78a6-129">Element</span></span>|<span data-ttu-id="e78a6-130">Opis</span><span class="sxs-lookup"><span data-stu-id="e78a6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e78a6-131">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e78a6-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e78a6-132">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="e78a6-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e78a6-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="e78a6-133">Example</span></span>  
 <span data-ttu-id="e78a6-134">W poniższym przykładzie pokazano nasłuchiwanie komunikaty anonsów za pośrednictwem protokołu http i peernet klienta.</span><span class="sxs-lookup"><span data-stu-id="e78a6-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="e78a6-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e78a6-135">See also</span></span>
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
