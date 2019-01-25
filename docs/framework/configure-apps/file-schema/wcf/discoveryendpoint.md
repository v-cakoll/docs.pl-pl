---
title: '&lt;discoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: b3254a1c3d7fa581b4f7573d693261f5a224515d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524172"
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="2db15-102">&lt;discoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2db15-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="2db15-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania.</span><span class="sxs-lookup"><span data-stu-id="2db15-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="2db15-104">Po dodaniu do konfiguracji usługi, określa, gdzie nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="2db15-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="2db15-105">Po dodaniu do konfiguracji klienta określa, gdzie wysyłać zapytania odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="2db15-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="2db15-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2db15-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2db15-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2db15-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db15-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2db15-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2db15-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2db15-109">Attributes and elements</span></span>

<span data-ttu-id="2db15-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2db15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2db15-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2db15-111">Attributes</span></span>

| <span data-ttu-id="2db15-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2db15-112">Attribute</span></span>        | <span data-ttu-id="2db15-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2db15-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="2db15-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="2db15-114">discoveryMode</span></span>    | <span data-ttu-id="2db15-115">Ciąg, który określa tryb protokół RDP.</span><span class="sxs-lookup"><span data-stu-id="2db15-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="2db15-116">Prawidłowe wartości to "Ad hoc" i "Zarządzane".</span><span class="sxs-lookup"><span data-stu-id="2db15-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="2db15-117">W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, który działa jako repozytorium wykrywalny usług.</span><span class="sxs-lookup"><span data-stu-id="2db15-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="2db15-118">W trybie ad hoc wymagane używany protokół UDP mechanizm multiemisji, aby znaleźć dostępne usługi.</span><span class="sxs-lookup"><span data-stu-id="2db15-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="2db15-119">Aby uzyskać więcej informacji na temat właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="2db15-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="2db15-120">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="2db15-120">discoveryVersion</span></span> | <span data-ttu-id="2db15-121">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="2db15-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="2db15-122">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="2db15-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="2db15-123">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="2db15-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="2db15-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="2db15-124">maxResponseDelay</span></span> | <span data-ttu-id="2db15-125">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem niektóre komunikaty, takie jak dopasowanie sondowania lub rozwiązać dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2db15-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="2db15-126">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci.</span><span class="sxs-lookup"><span data-stu-id="2db15-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="2db15-127">Aby temu zapobiec, ProbeMatches są wysyłane z losowo wybranym opóźnieniem między każdym ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="2db15-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="2db15-128">Opóźnienie losowe jest z zakresu od 0 do wartość ustawioną przy użyciu tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2db15-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="2db15-129">Jeśli ten atrybut jest ustawiony na wartość 0, ProbeMatches komunikaty są wysyłane w pętli bez żadnego opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="2db15-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="2db15-130">W przeciwnym razie wiadomości ProbeMatches są wysyłane z pewne opóźnienie losowe w taki sposób, że całkowity czas wykonywania, aby wysłać wszystkie wiadomości ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="2db15-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="2db15-131">Ta wartość ma zastosowanie tylko dla usług, nie jest używany przez klientów.</span><span class="sxs-lookup"><span data-stu-id="2db15-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="2db15-132">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="2db15-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="2db15-133">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2db15-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="2db15-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2db15-134">Child elements</span></span>

<span data-ttu-id="2db15-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="2db15-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2db15-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2db15-136">Parent elements</span></span>

| <span data-ttu-id="2db15-137">Element</span><span class="sxs-lookup"><span data-stu-id="2db15-137">Element</span></span> | <span data-ttu-id="2db15-138">Opis</span><span class="sxs-lookup"><span data-stu-id="2db15-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="2db15-139">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2db15-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="2db15-140">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="2db15-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="2db15-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="2db15-141">Example</span></span>

<span data-ttu-id="2db15-142">Poniższy przykład pokazuje usługi nasłuchiwać komunikatów odnajdywania za pośrednictwem elementu równorzędnego netto transportu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="2db15-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="2db15-143">Przykład jawnie określa WS-Discovery w wersji 2005 kwietnia.</span><span class="sxs-lookup"><span data-stu-id="2db15-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="2db15-144">Konfiguracja standardowego punktu końcowego jest zdefiniowana na usługę i nie może być współużytkowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2db15-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="2db15-145">Jeśli inna usługa chce mieć ten sam punkt końcowy odnajdywania, tę samą konfigurację musi można dodawać do sekcji tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2db15-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="2db15-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2db15-146">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
