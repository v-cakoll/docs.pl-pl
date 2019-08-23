---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926550"
---
# <a name="announcementendpoint"></a><span data-ttu-id="7a23b-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="7a23b-101">\<announcementEndpoint></span></span>
<span data-ttu-id="7a23b-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem anonsu.</span><span class="sxs-lookup"><span data-stu-id="7a23b-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="7a23b-103">Usługa może opcjonalnie ogłaszać swoją dostępność, wysyłając wiadomość w trybie online i w trybie offline, gdy zostanie ona otwarta lub ZAMKNIĘTA odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7a23b-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="7a23b-104">Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<elemencie servicediscovery >](servicediscovery.md) i używa AnnouncementClient do wykonywania anonsów.</span><span class="sxs-lookup"><span data-stu-id="7a23b-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="7a23b-105">Klient, który chce nasłuchiwać anonsu z innej usługi, działa jako usługa WCF. w tym celu należy skonfigurować punkty końcowe anonsu dla tego klienta w [ \<sekcji > usług](services.md) .</span><span class="sxs-lookup"><span data-stu-id="7a23b-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
<span data-ttu-id="7a23b-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7a23b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7a23b-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7a23b-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a23b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a23b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a23b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a23b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7a23b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a23b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a23b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a23b-111">Attributes</span></span>  
  
|<span data-ttu-id="7a23b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a23b-112">Attribute</span></span>|<span data-ttu-id="7a23b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7a23b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a23b-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="7a23b-114">discoveryVersion</span></span>|<span data-ttu-id="7a23b-115">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="7a23b-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="7a23b-116">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="7a23b-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="7a23b-117">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="7a23b-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="7a23b-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="7a23b-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="7a23b-119">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem komunikatu powitania.</span><span class="sxs-lookup"><span data-stu-id="7a23b-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="7a23b-120">Komunikaty będą oczekiwać na losową wartość czasu z przedziału od 0 do wartości tego atrybutu przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="7a23b-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="7a23b-121">Ten atrybut służy do ustawiania małego, losowego opóźnienia, aby zapobiec burzom sieci, gdy sieć przejdzie w tryb online, a wszystkie usługi są w tym samym czasie przywracane.</span><span class="sxs-lookup"><span data-stu-id="7a23b-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="7a23b-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="7a23b-122">name</span></span>|<span data-ttu-id="7a23b-123">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7a23b-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="7a23b-124">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="7a23b-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a23b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a23b-125">Child Elements</span></span>  
 <span data-ttu-id="7a23b-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="7a23b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a23b-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a23b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7a23b-128">Element</span><span class="sxs-lookup"><span data-stu-id="7a23b-128">Element</span></span>|<span data-ttu-id="7a23b-129">Opis</span><span class="sxs-lookup"><span data-stu-id="7a23b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a23b-130">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7a23b-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="7a23b-131">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="7a23b-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a23b-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a23b-132">Example</span></span>  
 <span data-ttu-id="7a23b-133">Poniższy przykład pokazuje, że klient nasłuchuje komunikatów za pośrednictwem protokołów HTTP i PEERNET.</span><span class="sxs-lookup"><span data-stu-id="7a23b-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a23b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a23b-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
