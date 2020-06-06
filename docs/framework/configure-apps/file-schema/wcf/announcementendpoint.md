---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: decaaa1cea5345ff971b16cbb20a85dd803a52d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850287"
---
# \<announcementEndpoint>
<span data-ttu-id="1f329-101">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem anonsu.</span><span class="sxs-lookup"><span data-stu-id="1f329-101">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="1f329-102">Usługa może opcjonalnie ogłaszać swoją dostępność, wysyłając wiadomość w trybie online i w trybie offline, gdy zostanie ona otwarta lub ZAMKNIĘTA odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1f329-102">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="1f329-103">Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [\<serviceDiscovery>](servicediscovery.md) elemencie i używa AnnouncementClient do wykonywania anonsów.</span><span class="sxs-lookup"><span data-stu-id="1f329-103">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="1f329-104">Klient, który chce nasłuchiwać anonsu z innej usługi, działa jako usługa WCF. w tym celu należy skonfigurować punkty końcowe anonsu dla tego klienta w [\<services>](services.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="1f329-104">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1f329-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f329-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f329-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f329-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1f329-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f329-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f329-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f329-108">Attributes</span></span>  
  
|<span data-ttu-id="1f329-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1f329-109">Attribute</span></span>|<span data-ttu-id="1f329-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1f329-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f329-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1f329-111">discoveryVersion</span></span>|<span data-ttu-id="1f329-112">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1f329-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1f329-113">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="1f329-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1f329-114">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="1f329-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1f329-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="1f329-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="1f329-116">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem komunikatu powitania.</span><span class="sxs-lookup"><span data-stu-id="1f329-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="1f329-117">Komunikaty będą oczekiwać na losową wartość czasu z przedziału od 0 do wartości tego atrybutu przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="1f329-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="1f329-118">Ten atrybut służy do ustawiania małego, losowego opóźnienia, aby zapobiec burzom sieci, gdy sieć przejdzie w tryb online, a wszystkie usługi są w tym samym czasie przywracane.</span><span class="sxs-lookup"><span data-stu-id="1f329-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="1f329-119">name</span><span class="sxs-lookup"><span data-stu-id="1f329-119">name</span></span>|<span data-ttu-id="1f329-120">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1f329-120">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1f329-121">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="1f329-121">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f329-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f329-122">Child Elements</span></span>  
 <span data-ttu-id="1f329-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f329-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f329-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f329-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1f329-125">Element</span><span class="sxs-lookup"><span data-stu-id="1f329-125">Element</span></span>|<span data-ttu-id="1f329-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1f329-126">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1f329-127">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="1f329-127">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f329-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f329-128">Example</span></span>  
 <span data-ttu-id="1f329-129">Poniższy przykład pokazuje, że klient nasłuchuje komunikatów za pośrednictwem protokołów HTTP i PEERNET.</span><span class="sxs-lookup"><span data-stu-id="1f329-129">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f329-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f329-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
