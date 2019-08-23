---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: e6e567e8a657b4c1683ae4abfb14f96a0f272e4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934582"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="775a7-101">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="775a7-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="775a7-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie skonfigurowany dla operacji odnajdywania za pośrednictwem powiązania multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="775a7-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="775a7-103">Ten punkt końcowy ma stały kontrakt i obsługuje dwie wersje protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="775a7-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="775a7-104">Ponadto ma stałe powiązanie UDP i domyślny adres określony w specyfikacjach WS-Discovery (WS-Discovery Kwiecień 2005 lub WS-Discovery V 1.1).</span><span class="sxs-lookup"><span data-stu-id="775a7-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="775a7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="775a7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="775a7-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="775a7-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775a7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="775a7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="775a7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="775a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="775a7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="775a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="775a7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="775a7-110">Attributes</span></span>  
  
|<span data-ttu-id="775a7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="775a7-111">Attribute</span></span>|<span data-ttu-id="775a7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="775a7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="775a7-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="775a7-113">discoveryMode</span></span>|<span data-ttu-id="775a7-114">Ciąg określający tryb protokołu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="775a7-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="775a7-115">Prawidłowe wartości to "AdHoc" i "Managed".</span><span class="sxs-lookup"><span data-stu-id="775a7-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="775a7-116">W trybie zarządzanym protokół polega na serwerze proxy odnajdywania, który działa jako repozytorium usług, które można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="775a7-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="775a7-117">Tryb ad hoc wymaga, aby protokół używał mechanizmu multiemisji UDP do znajdowania dostępnych usług.</span><span class="sxs-lookup"><span data-stu-id="775a7-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="775a7-118">Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="775a7-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="775a7-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="775a7-119">discoveryVersion</span></span>|<span data-ttu-id="775a7-120">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="775a7-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="775a7-121">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="775a7-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="775a7-122">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="775a7-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="775a7-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="775a7-123">maxResponseDelay</span></span>|<span data-ttu-id="775a7-124">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem pewnych komunikatów, takich jak dopasowanie sondy lub rozpoznanie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="775a7-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="775a7-125">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może to być burza sieci.</span><span class="sxs-lookup"><span data-stu-id="775a7-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="775a7-126">Aby temu zapobiec, ProbeMatches są wysyłane z losowym opóźnieniem między poszczególnymi ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="775a7-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="775a7-127">Opóźnienie losowe jest z zakresu od 0 do wartości ustawionej przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="775a7-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="775a7-128">Jeśli ten atrybut ma wartość 0, komunikaty ProbeMatches są wysyłane w ścisłej pętli bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="775a7-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="775a7-129">W przeciwnym razie komunikaty ProbeMatches są wysyłane z przypadkowym opóźnieniem, w którym łączny czas wysłania wszystkich komunikatów ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="775a7-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="775a7-130">Ta wartość dotyczy tylko usług, ale nie jest używana przez klientów.</span><span class="sxs-lookup"><span data-stu-id="775a7-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="775a7-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="775a7-131">multicastAddress</span></span>|<span data-ttu-id="775a7-132">Identyfikator URI, który określa adres multiemisji używany do wysyłania i otrzymywania komunikatów odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="775a7-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="775a7-133">Wartość domyślna to adres multiemisji zgodny ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="775a7-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="775a7-134">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="775a7-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="775a7-135">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="775a7-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="775a7-136">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="775a7-136">Child Elements</span></span>  
  
|<span data-ttu-id="775a7-137">Element</span><span class="sxs-lookup"><span data-stu-id="775a7-137">Element</span></span>|<span data-ttu-id="775a7-138">Opis</span><span class="sxs-lookup"><span data-stu-id="775a7-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="775a7-139">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="775a7-139">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="775a7-140">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego UDP.</span><span class="sxs-lookup"><span data-stu-id="775a7-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="775a7-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="775a7-141">Parent Elements</span></span>  
  
|<span data-ttu-id="775a7-142">Element</span><span class="sxs-lookup"><span data-stu-id="775a7-142">Element</span></span>|<span data-ttu-id="775a7-143">Opis</span><span class="sxs-lookup"><span data-stu-id="775a7-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="775a7-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="775a7-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="775a7-145">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="775a7-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="775a7-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="775a7-146">Example</span></span>  
 <span data-ttu-id="775a7-147">W poniższym przykładzie pokazano, jak usługa nasłuchuje komunikatów odnajdywania za pośrednictwem transportu multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="775a7-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="775a7-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="775a7-148">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
