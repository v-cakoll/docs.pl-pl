---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854912"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="f4011-101">\<udpAnnouncementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="f4011-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="f4011-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu za pośrednictwem powiązania UDP.</span><span class="sxs-lookup"><span data-stu-id="f4011-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="f4011-103">Ma ona ustaloną umowę i obsługuje dwie wersje odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="f4011-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="f4011-104">Oprócz tego ma stałe powiązanie UDP i domyślną wartość adresu określoną w specyfikacjach WS-Discovery (WS-Discovery Kwiecień 2005 lub WS-Discovery w wersji 1,1).</span><span class="sxs-lookup"><span data-stu-id="f4011-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="f4011-105">Można określić adres multiemisji, który będzie używany do wysyłania i otrzymywania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="f4011-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="f4011-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4011-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4011-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f4011-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f4011-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="f4011-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="f4011-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpAnnouncementEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="f4011-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4011-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4011-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4011-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f4011-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4011-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4011-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4011-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4011-113">Attributes</span></span>  
  
|<span data-ttu-id="f4011-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f4011-114">Attribute</span></span>|<span data-ttu-id="f4011-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f4011-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4011-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f4011-116">discoveryVersion</span></span>|<span data-ttu-id="f4011-117">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f4011-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f4011-118">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f4011-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f4011-119">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f4011-119">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f4011-120">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="f4011-120">maxAnnouncementDelay</span></span>|<span data-ttu-id="f4011-121">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem komunikatu powitania.</span><span class="sxs-lookup"><span data-stu-id="f4011-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="f4011-122">Komunikaty będą oczekiwać na losową wartość czasu z przedziału od 0 do wartości tego atrybutu przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="f4011-122">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="f4011-123">Ten atrybut służy do ustawiania małego, losowego opóźnienia, aby zapobiec burzom sieci, gdy sieć przejdzie w tryb online, a wszystkie usługi są w tym samym czasie przywracane.</span><span class="sxs-lookup"><span data-stu-id="f4011-123">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="f4011-124">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="f4011-124">multicastAddress</span></span>|<span data-ttu-id="f4011-125">Identyfikator URI, który określa adres multiemisji używany do wysyłania i otrzymywania komunikatów odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="f4011-125">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="f4011-126">Wartość domyślna to adres multiemisji zgodny ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="f4011-126">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="f4011-127">nazwa</span><span class="sxs-lookup"><span data-stu-id="f4011-127">name</span></span>|<span data-ttu-id="f4011-128">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f4011-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f4011-129">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="f4011-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4011-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f4011-130">Child Elements</span></span>  
  
|<span data-ttu-id="f4011-131">Element</span><span class="sxs-lookup"><span data-stu-id="f4011-131">Element</span></span>|<span data-ttu-id="f4011-132">Opis</span><span class="sxs-lookup"><span data-stu-id="f4011-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4011-133">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="f4011-133">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="f4011-134">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego UDP.</span><span class="sxs-lookup"><span data-stu-id="f4011-134">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4011-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f4011-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f4011-136">Element</span><span class="sxs-lookup"><span data-stu-id="f4011-136">Element</span></span>|<span data-ttu-id="f4011-137">Opis</span><span class="sxs-lookup"><span data-stu-id="f4011-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4011-138">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f4011-138">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="f4011-139">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="f4011-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4011-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4011-140">Example</span></span>  
 <span data-ttu-id="f4011-141">Poniższy przykład pokazuje, że klient nasłuchuje anonsu za pośrednictwem transportu multiemisji UDP z domyślnym adresem multiemisji i transportem multiemisji UDP z określonym adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="f4011-141">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4011-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4011-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
