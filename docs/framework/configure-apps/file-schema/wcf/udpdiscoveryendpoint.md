---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f0165f8cda6701aa11058f2dac1bdde0f9ebbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="f5c9d-102">&lt;udpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f5c9d-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="f5c9d-103">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązanie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="f5c9d-104">Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="f5c9d-105">Ponadto ma stałym powiązaniem UDP i domyślny adres zgodnie ze specyfikacją WS-Discovery (WS-Discovery kwietnia 2005 lub WS-Discovery w wersji 1.1).</span><span class="sxs-lookup"><span data-stu-id="f5c9d-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1)..</span></span>  
  
 <span data-ttu-id="f5c9d-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f5c9d-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5c9d-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f5c9d-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c9d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5c9d-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5c9d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f5c9d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f5c9d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5c9d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f5c9d-111">Attributes</span></span>  
  
|<span data-ttu-id="f5c9d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f5c9d-112">Attribute</span></span>|<span data-ttu-id="f5c9d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c9d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5c9d-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="f5c9d-114">discoveryMode</span></span>|<span data-ttu-id="f5c9d-115">Ciąg, który określa tryb protokół RDP.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="f5c9d-116">Prawidłowe wartości to "Ad hoc" i "Zarządzany".</span><span class="sxs-lookup"><span data-stu-id="f5c9d-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="f5c9d-117">W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, która działa jako repozytorium wykrywalny usług.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="f5c9d-118">W trybie ad hoc wymagane używany protokół UDP mechanizmu multiemisji można znaleźć dostępne usługi.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="f5c9d-119">Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="f5c9d-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f5c9d-120">discoveryVersion</span></span>|<span data-ttu-id="f5c9d-121">Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f5c9d-122">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f5c9d-123">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f5c9d-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="f5c9d-124">maxResponseDelay</span></span>|<span data-ttu-id="f5c9d-125">Wartość Timespan określający maksymalną wartość opóźnienia odnajdywania protokołu będzie czekać przed wysłaniem niektóre komunikaty, takie jak sondowania Match lub rozwiązać dopasowania.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="f5c9d-126">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="f5c9d-127">Aby temu zapobiec, ProbeMatches są wysyłane z losowego opóźnienia między każdym ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="f5c9d-128">Opóźnienie losowe jest z zakresu od 0 do wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="f5c9d-129">Jeśli ten atrybut jest ustawiony na 0, ProbeMatches komunikaty są wysyłane w pętli ścisłej bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="f5c9d-130">W przeciwnym razie ProbeMatches komunikaty są wysyłane z niektórych losowe opóźnienie tak, aby całkowity czas wykonywania wszystkich wysyłać ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="f5c9d-131">Ta wartość ma zastosowanie tylko dla usług, nie jest on używany przez klientów.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="f5c9d-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="f5c9d-132">multicastAddress</span></span>|<span data-ttu-id="f5c9d-133">Identyfikator Uri, który określa adres multiemisji do użycia na potrzeby wysyłania i odbierania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="f5c9d-134">Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="f5c9d-135">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f5c9d-136">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5c9d-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f5c9d-137">Child Elements</span></span>  
  
|<span data-ttu-id="f5c9d-138">Element</span><span class="sxs-lookup"><span data-stu-id="f5c9d-138">Element</span></span>|<span data-ttu-id="f5c9d-139">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c9d-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5c9d-140">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="f5c9d-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="f5c9d-141">Kolekcja ustawień, które pozwalają na skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5c9d-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f5c9d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f5c9d-143">Element</span><span class="sxs-lookup"><span data-stu-id="f5c9d-143">Element</span></span>|<span data-ttu-id="f5c9d-144">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c9d-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5c9d-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f5c9d-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f5c9d-146">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5c9d-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5c9d-147">Example</span></span>  
 <span data-ttu-id="f5c9d-148">W poniższym przykładzie pokazano nasłuchiwanie odnajdywania komunikaty za pośrednictwem protokołu UDP usługi multiemisji transportu.</span><span class="sxs-lookup"><span data-stu-id="f5c9d-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <endpoint binding="basicHttpBinding"   
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="DiscoveryEndpoint"  
              kind="udpDiscoveryEndpoint" />  
  </service>  
  <standardEndpoints>  
    <udpDiscoveryEndpoint>  
      <standardEndpoint name="DiscoveryEndpoint"                         
                        version="WSDiscoveryApril2005" />  
    </udpDiscoveryEndpoint>  
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="f5c9d-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5c9d-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
