---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 04f5fb27a0da7e553ff3c0308f7fb2e2df2e0b20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788261"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="08e92-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="08e92-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="08e92-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons z powiązania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="08e92-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="08e92-103">Ma stały kontraktu i obsługuje dwie wersje odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="08e92-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="08e92-104">Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery).</span><span class="sxs-lookup"><span data-stu-id="08e92-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="08e92-105">Możesz określić adres multiemisji na potrzeby wysyłania i odbierania wiadomości anonsów.</span><span class="sxs-lookup"><span data-stu-id="08e92-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="08e92-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="08e92-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="08e92-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="08e92-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e92-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="08e92-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08e92-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="08e92-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08e92-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="08e92-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08e92-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="08e92-111">Attributes</span></span>  
  
|<span data-ttu-id="08e92-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="08e92-112">Attribute</span></span>|<span data-ttu-id="08e92-113">Opis</span><span class="sxs-lookup"><span data-stu-id="08e92-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08e92-114">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="08e92-114">discoveryVersion</span></span>|<span data-ttu-id="08e92-115">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="08e92-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="08e92-116">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="08e92-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="08e92-117">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="08e92-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="08e92-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="08e92-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="08e92-119">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem wiadomości powitania.</span><span class="sxs-lookup"><span data-stu-id="08e92-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="08e92-120">Przed wysłaniem wiadomości będą oczekiwać czasu losowego wartość z zakresu od 0 i wartość tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="08e92-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="08e92-121">Ten atrybut służy do ustawiania małe, losowego opóźnienia, aby zapobiec nadmiarem sieci, gdy trafia do sieci i wszystkich usług pochodzą wróci do trybu online w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="08e92-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="08e92-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="08e92-122">multicastAddress</span></span>|<span data-ttu-id="08e92-123">Identyfikator URI, który określa adres multiemisji służące do wysyłania i odbierania komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="08e92-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="08e92-124">Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="08e92-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="08e92-125">nazwa</span><span class="sxs-lookup"><span data-stu-id="08e92-125">name</span></span>|<span data-ttu-id="08e92-126">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="08e92-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="08e92-127">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="08e92-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08e92-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="08e92-128">Child Elements</span></span>  
  
|<span data-ttu-id="08e92-129">Element</span><span class="sxs-lookup"><span data-stu-id="08e92-129">Element</span></span>|<span data-ttu-id="08e92-130">Opis</span><span class="sxs-lookup"><span data-stu-id="08e92-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08e92-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="08e92-131">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="08e92-132">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="08e92-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08e92-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="08e92-133">Parent Elements</span></span>  
  
|<span data-ttu-id="08e92-134">Element</span><span class="sxs-lookup"><span data-stu-id="08e92-134">Element</span></span>|<span data-ttu-id="08e92-135">Opis</span><span class="sxs-lookup"><span data-stu-id="08e92-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08e92-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="08e92-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="08e92-137">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="08e92-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08e92-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="08e92-138">Example</span></span>  
 <span data-ttu-id="08e92-139">W poniższym przykładzie pokazano klienta nasłuchiwanie anonsu za pośrednictwem protokołu UDP transportu multiemisji za pomocą domyślny adres multiemisji i UDP transportu multiemisji przy użyciu określonego adresu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="08e92-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="08e92-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08e92-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
