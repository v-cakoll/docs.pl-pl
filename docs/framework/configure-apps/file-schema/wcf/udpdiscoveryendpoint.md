---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 180763404ee9070e9ed6e5476d4568a0a018dcb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203369"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="24ede-101">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="24ede-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="24ede-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązania multiemisji.</span><span class="sxs-lookup"><span data-stu-id="24ede-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="24ede-103">Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="24ede-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="24ede-104">Ponadto ma stały powiązanie protokołu UDP oraz domyślny adres określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery).</span><span class="sxs-lookup"><span data-stu-id="24ede-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="24ede-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24ede-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="24ede-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="24ede-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ede-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="24ede-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24ede-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24ede-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24ede-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24ede-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24ede-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24ede-110">Attributes</span></span>  
  
|<span data-ttu-id="24ede-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24ede-111">Attribute</span></span>|<span data-ttu-id="24ede-112">Opis</span><span class="sxs-lookup"><span data-stu-id="24ede-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24ede-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="24ede-113">discoveryMode</span></span>|<span data-ttu-id="24ede-114">Ciąg, który określa tryb protokół RDP.</span><span class="sxs-lookup"><span data-stu-id="24ede-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="24ede-115">Prawidłowe wartości to "Ad hoc" i "Zarządzane".</span><span class="sxs-lookup"><span data-stu-id="24ede-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="24ede-116">W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, który działa jako repozytorium wykrywalny usług.</span><span class="sxs-lookup"><span data-stu-id="24ede-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="24ede-117">W trybie ad hoc wymagane używany protokół UDP mechanizm multiemisji, aby znaleźć dostępne usługi.</span><span class="sxs-lookup"><span data-stu-id="24ede-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="24ede-118">Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="24ede-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="24ede-119">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="24ede-119">discoveryVersion</span></span>|<span data-ttu-id="24ede-120">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="24ede-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="24ede-121">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="24ede-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="24ede-122">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="24ede-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="24ede-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="24ede-123">maxResponseDelay</span></span>|<span data-ttu-id="24ede-124">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem niektóre komunikaty, takie jak dopasowanie sondowania lub rozwiązać dopasowania.</span><span class="sxs-lookup"><span data-stu-id="24ede-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="24ede-125">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci.</span><span class="sxs-lookup"><span data-stu-id="24ede-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="24ede-126">Aby temu zapobiec, ProbeMatches są wysyłane z losowo wybranym opóźnieniem między każdym ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="24ede-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="24ede-127">Opóźnienie losowe jest z zakresu od 0 do wartość ustawioną przy użyciu tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="24ede-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="24ede-128">Jeśli ten atrybut jest ustawiony na wartość 0, ProbeMatches komunikaty są wysyłane w pętli bez żadnego opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="24ede-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="24ede-129">W przeciwnym razie wiadomości ProbeMatches są wysyłane z pewne opóźnienie losowe w taki sposób, że całkowity czas wykonywania, aby wysłać wszystkie wiadomości ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="24ede-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="24ede-130">Ta wartość ma zastosowanie tylko dla usług, nie jest używany przez klientów.</span><span class="sxs-lookup"><span data-stu-id="24ede-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="24ede-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="24ede-131">multicastAddress</span></span>|<span data-ttu-id="24ede-132">Identyfikator Uri, który określa adres multiemisji służące do wysyłania i odbierania komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="24ede-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="24ede-133">Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="24ede-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="24ede-134">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="24ede-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="24ede-135">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="24ede-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24ede-136">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24ede-136">Child Elements</span></span>  
  
|<span data-ttu-id="24ede-137">Element</span><span class="sxs-lookup"><span data-stu-id="24ede-137">Element</span></span>|<span data-ttu-id="24ede-138">Opis</span><span class="sxs-lookup"><span data-stu-id="24ede-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24ede-139">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="24ede-139">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="24ede-140">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="24ede-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24ede-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24ede-141">Parent Elements</span></span>  
  
|<span data-ttu-id="24ede-142">Element</span><span class="sxs-lookup"><span data-stu-id="24ede-142">Element</span></span>|<span data-ttu-id="24ede-143">Opis</span><span class="sxs-lookup"><span data-stu-id="24ede-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24ede-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="24ede-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="24ede-145">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="24ede-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24ede-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="24ede-146">Example</span></span>  
 <span data-ttu-id="24ede-147">Poniższy przykład pokazuje usługi nasłuchiwać komunikatów odnajdywania za pośrednictwem protokołu UDP transportu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="24ede-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24ede-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24ede-148">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
