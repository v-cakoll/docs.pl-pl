---
title: '&lt;Obiektu DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747401"
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="94264-102">&lt;Obiektu DiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="94264-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="94264-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania.</span><span class="sxs-lookup"><span data-stu-id="94264-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="94264-104">Po dodaniu do konfiguracji usługi, określa gdzie nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="94264-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="94264-105">Po dodaniu do konfiguracji klienta Określa gdzie wysyłanie zapytań odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="94264-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="94264-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94264-106">\<system.serviceModel></span></span>  
<span data-ttu-id="94264-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="94264-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94264-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="94264-108">Syntax</span></span>

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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94264-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94264-109">Attributes and elements</span></span>

<span data-ttu-id="94264-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94264-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94264-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94264-111">Attributes</span></span>

| <span data-ttu-id="94264-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94264-112">Attribute</span></span>        | <span data-ttu-id="94264-113">Opis</span><span class="sxs-lookup"><span data-stu-id="94264-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="94264-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="94264-114">discoveryMode</span></span>    | <span data-ttu-id="94264-115">Ciąg, który określa tryb protokół RDP.</span><span class="sxs-lookup"><span data-stu-id="94264-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="94264-116">Prawidłowe wartości to "Ad hoc" i "Zarządzany".</span><span class="sxs-lookup"><span data-stu-id="94264-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="94264-117">W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, która działa jako repozytorium wykrywalny usług.</span><span class="sxs-lookup"><span data-stu-id="94264-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="94264-118">W trybie ad hoc wymagane używany protokół UDP mechanizmu multiemisji można znaleźć dostępne usługi.</span><span class="sxs-lookup"><span data-stu-id="94264-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="94264-119">Aby uzyskać więcej informacji dotyczących właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="94264-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="94264-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="94264-120">discoveryVersion</span></span> | <span data-ttu-id="94264-121">Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="94264-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="94264-122">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="94264-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="94264-123">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="94264-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="94264-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="94264-124">maxResponseDelay</span></span> | <span data-ttu-id="94264-125">Wartość Timespan określający maksymalną wartość opóźnienia odnajdywania protokołu będzie czekać przed wysłaniem niektóre komunikaty, takie jak sondowania Match lub rozwiązać dopasowania.</span><span class="sxs-lookup"><span data-stu-id="94264-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="94264-126">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci.</span><span class="sxs-lookup"><span data-stu-id="94264-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="94264-127">Aby temu zapobiec, ProbeMatches są wysyłane z losowego opóźnienia między każdym ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="94264-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="94264-128">Opóźnienie losowe jest z zakresu od 0 do wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="94264-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="94264-129">Jeśli ten atrybut jest ustawiony na 0, ProbeMatches komunikaty są wysyłane w pętli ścisłej bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="94264-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="94264-130">W przeciwnym razie ProbeMatches komunikaty są wysyłane z niektórych losowe opóźnienie tak, aby całkowity czas wykonywania wszystkich wysyłać ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="94264-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="94264-131">Ta wartość ma zastosowanie tylko dla usług, nie jest on używany przez klientów.</span><span class="sxs-lookup"><span data-stu-id="94264-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="94264-132">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94264-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="94264-133">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="94264-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="94264-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94264-134">Child elements</span></span>

<span data-ttu-id="94264-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="94264-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94264-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94264-136">Parent elements</span></span>

| <span data-ttu-id="94264-137">Element</span><span class="sxs-lookup"><span data-stu-id="94264-137">Element</span></span> | <span data-ttu-id="94264-138">Opis</span><span class="sxs-lookup"><span data-stu-id="94264-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="94264-139">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="94264-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="94264-140">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="94264-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="94264-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="94264-141">Example</span></span>

<span data-ttu-id="94264-142">W poniższym przykładzie pokazano usługi nasłuchiwania komunikatów odnajdywania za pośrednictwem elementu równorzędnego net transportu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="94264-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="94264-143">W przykładzie jawnie określa WS-Discovery wersji z kwietnia 2005.</span><span class="sxs-lookup"><span data-stu-id="94264-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="94264-144">Konfiguracja standardowego punktu końcowego jest zdefiniowany dla usługi i nie może być współużytkowana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94264-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="94264-145">Inna usługa chcą mieć tego samego punktu końcowego odnajdywania, taką samą konfigurację musi zostać dodany do sekcji tej usługi.</span><span class="sxs-lookup"><span data-stu-id="94264-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94264-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94264-146">See also</span></span>

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
