---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854912"
---
# \<udpAnnouncementEndpoint>
<span data-ttu-id="97d07-101">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu za pośrednictwem powiązania UDP.</span><span class="sxs-lookup"><span data-stu-id="97d07-101">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="97d07-102">Ma ona ustaloną umowę i obsługuje dwie wersje odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="97d07-102">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="97d07-103">Oprócz tego ma stałe powiązanie UDP i domyślną wartość adresu określoną w specyfikacjach WS-Discovery (WS-Discovery Kwiecień 2005 lub WS-Discovery w wersji 1,1).</span><span class="sxs-lookup"><span data-stu-id="97d07-103">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="97d07-104">Można określić adres multiemisji, który będzie używany do wysyłania i otrzymywania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="97d07-104">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="97d07-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d07-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97d07-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97d07-106">Attributes and Elements</span></span>  
 <span data-ttu-id="97d07-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97d07-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97d07-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97d07-108">Attributes</span></span>  
  
|<span data-ttu-id="97d07-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97d07-109">Attribute</span></span>|<span data-ttu-id="97d07-110">Opis</span><span class="sxs-lookup"><span data-stu-id="97d07-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97d07-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="97d07-111">discoveryVersion</span></span>|<span data-ttu-id="97d07-112">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="97d07-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="97d07-113">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="97d07-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="97d07-114">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="97d07-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="97d07-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="97d07-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="97d07-116">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem komunikatu powitania.</span><span class="sxs-lookup"><span data-stu-id="97d07-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="97d07-117">Komunikaty będą oczekiwać na losową wartość czasu z przedziału od 0 do wartości tego atrybutu przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="97d07-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="97d07-118">Ten atrybut służy do ustawiania małego, losowego opóźnienia, aby zapobiec burzom sieci, gdy sieć przejdzie w tryb online, a wszystkie usługi są w tym samym czasie przywracane.</span><span class="sxs-lookup"><span data-stu-id="97d07-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="97d07-119">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="97d07-119">multicastAddress</span></span>|<span data-ttu-id="97d07-120">Identyfikator URI, który określa adres multiemisji używany do wysyłania i otrzymywania komunikatów odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="97d07-120">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="97d07-121">Wartość domyślna to adres multiemisji zgodny ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="97d07-121">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="97d07-122">name</span><span class="sxs-lookup"><span data-stu-id="97d07-122">name</span></span>|<span data-ttu-id="97d07-123">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="97d07-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="97d07-124">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="97d07-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97d07-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97d07-125">Child Elements</span></span>  
  
|<span data-ttu-id="97d07-126">Element</span><span class="sxs-lookup"><span data-stu-id="97d07-126">Element</span></span>|<span data-ttu-id="97d07-127">Opis</span><span class="sxs-lookup"><span data-stu-id="97d07-127">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="97d07-128">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego UDP.</span><span class="sxs-lookup"><span data-stu-id="97d07-128">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97d07-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97d07-129">Parent Elements</span></span>  
  
|<span data-ttu-id="97d07-130">Element</span><span class="sxs-lookup"><span data-stu-id="97d07-130">Element</span></span>|<span data-ttu-id="97d07-131">Opis</span><span class="sxs-lookup"><span data-stu-id="97d07-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="97d07-132">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="97d07-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97d07-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="97d07-133">Example</span></span>  
 <span data-ttu-id="97d07-134">Poniższy przykład pokazuje, że klient nasłuchuje anonsu za pośrednictwem transportu multiemisji UDP z domyślnym adresem multiemisji i transportem multiemisji UDP z określonym adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="97d07-134">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97d07-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97d07-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
