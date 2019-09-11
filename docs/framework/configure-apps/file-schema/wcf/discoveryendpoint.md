---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855392"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="7d931-101">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="7d931-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="7d931-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="7d931-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="7d931-103">Po dodaniu do konfiguracji usługi określa miejsce nasłuchiwania komunikatów odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="7d931-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="7d931-104">Po dodaniu do konfiguracji klienta określa, gdzie mają być wysyłane zapytania odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="7d931-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="7d931-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d931-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d931-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7d931-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7d931-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="7d931-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="7d931-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="7d931-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d931-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d931-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d931-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d931-110">Attributes and elements</span></span>

<span data-ttu-id="7d931-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d931-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d931-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d931-112">Attributes</span></span>

| <span data-ttu-id="7d931-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d931-113">Attribute</span></span>        | <span data-ttu-id="7d931-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d931-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="7d931-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="7d931-115">discoveryMode</span></span>    | <span data-ttu-id="7d931-116">Ciąg określający tryb protokołu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="7d931-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="7d931-117">Prawidłowe wartości to "AdHoc" i "Managed".</span><span class="sxs-lookup"><span data-stu-id="7d931-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="7d931-118">W trybie zarządzanym protokół polega na serwerze proxy odnajdywania, który działa jako repozytorium usług, które można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="7d931-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="7d931-119">Tryb ad hoc wymaga, aby protokół używał mechanizmu multiemisji UDP do znajdowania dostępnych usług.</span><span class="sxs-lookup"><span data-stu-id="7d931-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="7d931-120">Aby uzyskać więcej informacji na temat właściwości, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>Zobacz.</span><span class="sxs-lookup"><span data-stu-id="7d931-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="7d931-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="7d931-121">discoveryVersion</span></span> | <span data-ttu-id="7d931-122">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="7d931-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="7d931-123">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="7d931-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="7d931-124">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="7d931-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="7d931-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="7d931-125">maxResponseDelay</span></span> | <span data-ttu-id="7d931-126">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem pewnych komunikatów, takich jak dopasowanie sondy lub rozpoznanie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7d931-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="7d931-127">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może to być burza sieci.</span><span class="sxs-lookup"><span data-stu-id="7d931-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="7d931-128">Aby temu zapobiec, ProbeMatches są wysyłane z losowym opóźnieniem między poszczególnymi ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="7d931-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="7d931-129">Opóźnienie losowe jest z zakresu od 0 do wartości ustawionej przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="7d931-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="7d931-130">Jeśli ten atrybut ma wartość 0, komunikaty ProbeMatches są wysyłane w ścisłej pętli bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="7d931-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="7d931-131">W przeciwnym razie komunikaty ProbeMatches są wysyłane z przypadkowym opóźnieniem, w którym łączny czas wysłania wszystkich komunikatów ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="7d931-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="7d931-132">Ta wartość dotyczy tylko usług, ale nie jest używana przez klientów.</span><span class="sxs-lookup"><span data-stu-id="7d931-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="7d931-133">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7d931-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="7d931-134">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="7d931-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="7d931-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d931-135">Child elements</span></span>

<span data-ttu-id="7d931-136">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d931-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d931-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d931-137">Parent elements</span></span>

| <span data-ttu-id="7d931-138">Element</span><span class="sxs-lookup"><span data-stu-id="7d931-138">Element</span></span> | <span data-ttu-id="7d931-139">Opis</span><span class="sxs-lookup"><span data-stu-id="7d931-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="7d931-140">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7d931-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="7d931-141">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="7d931-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="7d931-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d931-142">Example</span></span>

<span data-ttu-id="7d931-143">W poniższym przykładzie pokazano, jak usługa nasłuchuje komunikatów odnajdywania za pośrednictwem transportowego ruchu multiemisji sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="7d931-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="7d931-144">Przykład jawnie określa wersję WS-Discovery z kwietnia 2005.</span><span class="sxs-lookup"><span data-stu-id="7d931-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="7d931-145">Standardowa konfiguracja punktu końcowego jest definiowana na usługę i nie może być współużytkowana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7d931-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="7d931-146">Jeśli inna usługa chce mieć ten sam punkt końcowy odnajdywania, należy dodać tę samą konfigurację do sekcji tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7d931-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d931-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d931-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
