---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 15d60cd277b77fd52b2b77bfcdf4d0da1de7167a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351829"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="0e999-102">&lt;AnnouncementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="0e999-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="0e999-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym.</span><span class="sxs-lookup"><span data-stu-id="0e999-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="0e999-104">Usługi można opcjonalnie ogłaszamy jego dostępność, wysyłając wiadomość online i offline powiadomienia, gdy jest otwarty lub zamknięty odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0e999-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="0e999-105">Usługi Windows Communication Foundation (WCF) określa punktów końcowych powiadomienia w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element i używa AnnouncementClient przeprowadzić anonsów.</span><span class="sxs-lookup"><span data-stu-id="0e999-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="0e999-106">Klient chcą nasłuchiwania anonsu z innej usługi rzeczywiście działa jako usługa WCF; w związku z tym należy skonfigurować punktów końcowych powiadomienia dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="0e999-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="0e999-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0e999-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e999-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0e999-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e999-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e999-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e999-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0e999-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e999-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0e999-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e999-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0e999-112">Attributes</span></span>  
  
|<span data-ttu-id="0e999-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0e999-113">Attribute</span></span>|<span data-ttu-id="0e999-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0e999-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e999-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="0e999-115">discoveryVersion</span></span>|<span data-ttu-id="0e999-116">Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="0e999-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="0e999-117">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="0e999-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="0e999-118">Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="0e999-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="0e999-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="0e999-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="0e999-120">Wartość Timespan określający maksymalną wartość opóźnienia protokołu Discovery będzie czekać przed wysłaniem wiadomości powitania.</span><span class="sxs-lookup"><span data-stu-id="0e999-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="0e999-121">Przed wysłaniem wiadomości będą oczekiwać losowo wartość z zakresu od 0 i wartość tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0e999-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="0e999-122">Ten atrybut służy do ustawiania małe, losowe opóźnienie do uniknięcia sieci "burz", gdy sieć trafia i wszystkich usług powróci w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="0e999-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="0e999-123">nazwa</span><span class="sxs-lookup"><span data-stu-id="0e999-123">name</span></span>|<span data-ttu-id="0e999-124">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e999-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0e999-125">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0e999-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e999-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0e999-126">Child Elements</span></span>  
 <span data-ttu-id="0e999-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="0e999-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e999-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0e999-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0e999-129">Element</span><span class="sxs-lookup"><span data-stu-id="0e999-129">Element</span></span>|<span data-ttu-id="0e999-130">Opis</span><span class="sxs-lookup"><span data-stu-id="0e999-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e999-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0e999-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0e999-132">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="0e999-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e999-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e999-133">Example</span></span>  
 <span data-ttu-id="0e999-134">W poniższym przykładzie pokazano nasłuchiwanie komunikaty anonsów za pośrednictwem protokołu http i peernet klienta.</span><span class="sxs-lookup"><span data-stu-id="0e999-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e999-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e999-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
