---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 4f3cf2748acc75b0ec83732664c5f97114f3663a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195127"
---
# <a name="announcementendpoint"></a><span data-ttu-id="041dd-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="041dd-101">\<announcementEndpoint></span></span>
<span data-ttu-id="041dd-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym.</span><span class="sxs-lookup"><span data-stu-id="041dd-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="041dd-103">Usługa może opcjonalnie ogłaszają jego dostępność, wysyłając anonse online i offline, po otwarciu lub zamknięciu odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="041dd-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="041dd-104">Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu i używa AnnouncementClient przeprowadzić anonsów.</span><span class="sxs-lookup"><span data-stu-id="041dd-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="041dd-105">Klient chcą nasłuchiwanie anonsu z innej usługi faktycznie działa jako usługa WCF; dlatego musisz skonfigurować punkty końcowe anonsu dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="041dd-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="041dd-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="041dd-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="041dd-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="041dd-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="041dd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="041dd-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="041dd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="041dd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="041dd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="041dd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="041dd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="041dd-111">Attributes</span></span>  
  
|<span data-ttu-id="041dd-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="041dd-112">Attribute</span></span>|<span data-ttu-id="041dd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="041dd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="041dd-114">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="041dd-114">discoveryVersion</span></span>|<span data-ttu-id="041dd-115">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="041dd-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="041dd-116">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="041dd-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="041dd-117">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="041dd-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="041dd-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="041dd-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="041dd-119">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem wiadomości powitania.</span><span class="sxs-lookup"><span data-stu-id="041dd-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="041dd-120">Przed wysłaniem wiadomości będą oczekiwać czasu losowego wartość z zakresu od 0 i wartość tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="041dd-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="041dd-121">Ten atrybut służy do ustawiania małe, losowego opóźnienia, aby zapobiec nadmiarem sieci, gdy trafia do sieci i wszystkich usług pochodzą wróci do trybu online w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="041dd-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="041dd-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="041dd-122">name</span></span>|<span data-ttu-id="041dd-123">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="041dd-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="041dd-124">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="041dd-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="041dd-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="041dd-125">Child Elements</span></span>  
 <span data-ttu-id="041dd-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="041dd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="041dd-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="041dd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="041dd-128">Element</span><span class="sxs-lookup"><span data-stu-id="041dd-128">Element</span></span>|<span data-ttu-id="041dd-129">Opis</span><span class="sxs-lookup"><span data-stu-id="041dd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="041dd-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="041dd-130">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="041dd-131">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="041dd-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="041dd-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="041dd-132">Example</span></span>  
 <span data-ttu-id="041dd-133">W poniższym przykładzie pokazano nasłuchiwanie komunikaty anonsów za pośrednictwem protokołu http i peernet klienta.</span><span class="sxs-lookup"><span data-stu-id="041dd-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="041dd-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="041dd-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
