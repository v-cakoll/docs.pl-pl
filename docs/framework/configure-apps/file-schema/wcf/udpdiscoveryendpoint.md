---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 1729255c68c75f824b8cd8c87f106a4a9b3550f6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854895"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="7fe3e-101">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="7fe3e-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="7fe3e-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie skonfigurowany dla operacji odnajdywania za pośrednictwem powiązania multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="7fe3e-103">Ten punkt końcowy ma stały kontrakt i obsługuje dwie wersje protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="7fe3e-104">Ponadto ma stałe powiązanie UDP i domyślny adres określony w specyfikacjach WS-Discovery (WS-Discovery Kwiecień 2005 lub WS-Discovery V 1.1).</span><span class="sxs-lookup"><span data-stu-id="7fe3e-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
<span data-ttu-id="7fe3e-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7fe3e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7fe3e-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7fe3e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7fe3e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="7fe3e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="7fe3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpDiscoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="7fe3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe3e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fe3e-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fe3e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7fe3e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7fe3e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fe3e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7fe3e-112">Attributes</span></span>  
  
|<span data-ttu-id="7fe3e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7fe3e-113">Attribute</span></span>|<span data-ttu-id="7fe3e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7fe3e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fe3e-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="7fe3e-115">discoveryMode</span></span>|<span data-ttu-id="7fe3e-116">Ciąg określający tryb protokołu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="7fe3e-117">Prawidłowe wartości to "AdHoc" i "Managed".</span><span class="sxs-lookup"><span data-stu-id="7fe3e-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="7fe3e-118">W trybie zarządzanym protokół polega na serwerze proxy odnajdywania, który działa jako repozytorium usług, które można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="7fe3e-119">Tryb ad hoc wymaga, aby protokół używał mechanizmu multiemisji UDP do znajdowania dostępnych usług.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="7fe3e-120">Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-120">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="7fe3e-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="7fe3e-121">discoveryVersion</span></span>|<span data-ttu-id="7fe3e-122">Ciąg określający jedną z dwóch wersji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="7fe3e-123">Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="7fe3e-124">Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="7fe3e-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="7fe3e-125">maxResponseDelay</span></span>|<span data-ttu-id="7fe3e-126">Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem pewnych komunikatów, takich jak dopasowanie sondy lub rozpoznanie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="7fe3e-127">Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może to być burza sieci.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="7fe3e-128">Aby temu zapobiec, ProbeMatches są wysyłane z losowym opóźnieniem między poszczególnymi ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="7fe3e-129">Opóźnienie losowe jest z zakresu od 0 do wartości ustawionej przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="7fe3e-130">Jeśli ten atrybut ma wartość 0, komunikaty ProbeMatches są wysyłane w ścisłej pętli bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="7fe3e-131">W przeciwnym razie komunikaty ProbeMatches są wysyłane z przypadkowym opóźnieniem, w którym łączny czas wysłania wszystkich komunikatów ProbeMatches nie przekracza maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="7fe3e-132">Ta wartość dotyczy tylko usług, ale nie jest używana przez klientów.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-132">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="7fe3e-133">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="7fe3e-133">multicastAddress</span></span>|<span data-ttu-id="7fe3e-134">Identyfikator URI, który określa adres multiemisji używany do wysyłania i otrzymywania komunikatów odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-134">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="7fe3e-135">Wartość domyślna to adres multiemisji zgodny ze specyfikacją protokołu.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-135">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="7fe3e-136">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-136">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="7fe3e-137">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-137">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fe3e-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7fe3e-138">Child Elements</span></span>  
  
|<span data-ttu-id="7fe3e-139">Element</span><span class="sxs-lookup"><span data-stu-id="7fe3e-139">Element</span></span>|<span data-ttu-id="7fe3e-140">Opis</span><span class="sxs-lookup"><span data-stu-id="7fe3e-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe3e-141">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="7fe3e-141">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="7fe3e-142">Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego UDP.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-142">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fe3e-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7fe3e-143">Parent Elements</span></span>  
  
|<span data-ttu-id="7fe3e-144">Element</span><span class="sxs-lookup"><span data-stu-id="7fe3e-144">Element</span></span>|<span data-ttu-id="7fe3e-145">Opis</span><span class="sxs-lookup"><span data-stu-id="7fe3e-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe3e-146">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7fe3e-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="7fe3e-147">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="7fe3e-147">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7fe3e-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fe3e-148">Example</span></span>  
 <span data-ttu-id="7fe3e-149">W poniższym przykładzie pokazano, jak usługa nasłuchuje komunikatów odnajdywania za pośrednictwem transportu multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="7fe3e-149">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fe3e-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fe3e-150">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
