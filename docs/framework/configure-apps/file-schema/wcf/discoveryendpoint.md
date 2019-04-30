---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704059"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="896c5-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="896c5-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="896c5-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania.</span><span class="sxs-lookup"><span data-stu-id="896c5-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="896c5-103">Po dodaniu do konfiguracji usługi, określa, gdzie nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="896c5-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="896c5-104">Po dodaniu do konfiguracji klienta określa, gdzie wysyłać zapytania odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="896c5-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="896c5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="896c5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="896c5-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="896c5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="896c5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="896c5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="896c5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="896c5-108">Attributes and elements</span></span>

<span data-ttu-id="896c5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="896c5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="896c5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="896c5-110">Attributes</span></span>

| <span data-ttu-id="896c5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="896c5-111">Attribute</span></span>        | <span data-ttu-id="896c5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="896c5-112">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="896c5-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="896c5-113">discoveryMode</span></span>    | <span data-ttu-id="896c5-114">Ciąg, który określa tryb protokół RDP.</span><span class="sxs-lookup"><span data-stu-id="896c5-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="896c5-115">Prawidłowe wartości to "Ad hoc" i "Zarządzane".</span><span class="sxs-lookup"><span data-stu-id="896c5-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="896c5-116">W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, który działa jako repozytorium wykrywalny usług.</span><span class="sxs-lookup"><span data-stu-id="896c5-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="896c5-117">W trybie ad hoc wymagane używany protokół UDP mechanizm multiemisji, aby znaleźć dostępne usługi.</span><span class="sxs-lookup"><span data-stu-id="896c5-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="896c5-118">Aby uzyskać więcej informacji na temat właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="896c5-118">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="896c5-119">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="896c5-119">discoveryVersion</span></span> | <span data-ttu-id="896c5-120">Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="896c5-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="896c5-121">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="896c5-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="896c5-122">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="896c5-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="896c5-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="896c5-123">maxResponseDelay</span></span> | <span data-ttu-id="896c5-124">Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem niektóre komunikaty, takie jak dopasowanie sondowania lub rozwiązać dopasowania.</span><span class="sxs-lookup"><span data-stu-id="896c5-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="896c5-125">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci.</span><span class="sxs-lookup"><span data-stu-id="896c5-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="896c5-126">Aby temu zapobiec, ProbeMatches są wysyłane z losowo wybranym opóźnieniem między każdym ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="896c5-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="896c5-127">Opóźnienie losowe jest z zakresu od 0 do wartość ustawioną przy użyciu tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="896c5-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="896c5-128">Jeśli ten atrybut jest ustawiony na wartość 0, ProbeMatches komunikaty są wysyłane w pętli bez żadnego opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="896c5-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="896c5-129">W przeciwnym razie wiadomości ProbeMatches są wysyłane z pewne opóźnienie losowe w taki sposób, że całkowity czas wykonywania, aby wysłać wszystkie wiadomości ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="896c5-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="896c5-130">Ta wartość ma zastosowanie tylko dla usług, nie jest używany przez klientów.</span><span class="sxs-lookup"><span data-stu-id="896c5-130">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="896c5-131">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="896c5-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="896c5-132">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="896c5-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="896c5-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="896c5-133">Child elements</span></span>

<span data-ttu-id="896c5-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="896c5-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="896c5-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="896c5-135">Parent elements</span></span>

| <span data-ttu-id="896c5-136">Element</span><span class="sxs-lookup"><span data-stu-id="896c5-136">Element</span></span> | <span data-ttu-id="896c5-137">Opis</span><span class="sxs-lookup"><span data-stu-id="896c5-137">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="896c5-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="896c5-138">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="896c5-139">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="896c5-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="896c5-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="896c5-140">Example</span></span>

<span data-ttu-id="896c5-141">Poniższy przykład pokazuje usługi nasłuchiwać komunikatów odnajdywania za pośrednictwem elementu równorzędnego netto transportu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="896c5-141">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="896c5-142">Przykład jawnie określa WS-Discovery w wersji 2005 kwietnia.</span><span class="sxs-lookup"><span data-stu-id="896c5-142">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="896c5-143">Konfiguracja standardowego punktu końcowego jest zdefiniowana na usługę i nie może być współużytkowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="896c5-143">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="896c5-144">Jeśli inna usługa chce mieć ten sam punkt końcowy odnajdywania, tę samą konfigurację musi można dodawać do sekcji tej usługi.</span><span class="sxs-lookup"><span data-stu-id="896c5-144">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="896c5-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="896c5-145">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
