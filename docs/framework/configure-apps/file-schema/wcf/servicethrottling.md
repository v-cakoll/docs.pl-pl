---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: b0f5197bf4e9017007f29f86048756b43e3b15fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750170"
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="408cc-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="408cc-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="408cc-103">Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="408cc-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="408cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="408cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="408cc-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="408cc-105">\<behaviors></span></span>  
<span data-ttu-id="408cc-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="408cc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="408cc-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="408cc-107">\<behavior></span></span>  
<span data-ttu-id="408cc-108">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="408cc-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408cc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="408cc-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="408cc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="408cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="408cc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="408cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="408cc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="408cc-112">Attributes</span></span>  
  
|<span data-ttu-id="408cc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="408cc-113">Attribute</span></span>|<span data-ttu-id="408cc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="408cc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="408cc-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="408cc-115">maxConcurrentCalls</span></span>|<span data-ttu-id="408cc-116">Dodatnia liczba całkowita, która ogranicza liczbę wiadomości, które obecnie procesu na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="408cc-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="408cc-117">Wywołania poza limitem są umieszczane w kolejce.</span><span class="sxs-lookup"><span data-stu-id="408cc-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="408cc-118">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem jego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="408cc-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="408cc-119">Wartość domyślna to 16 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="408cc-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="408cc-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="408cc-120">maxConcurrentInstances</span></span>|<span data-ttu-id="408cc-121">Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie przez <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="408cc-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="408cc-122">Żądania utworzenia dodatkowe wystąpienia są umieszczane w kolejce i ukończyć po udostępnieniu miejsca poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="408cc-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="408cc-123">Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="408cc-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="408cc-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="408cc-124">maxConcurrentSessions</span></span>|<span data-ttu-id="408cc-125">Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="408cc-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="408cc-126">Usługa będzie akceptować połączenia poza limitem, ale są aktywne tylko kanały poniżej limitu (wiadomości są odczytywane z kanału).</span><span class="sxs-lookup"><span data-stu-id="408cc-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="408cc-127">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem jego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="408cc-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="408cc-128">Wartość domyślna to 100 \* Liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="408cc-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="408cc-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="408cc-129">Child Elements</span></span>  
 <span data-ttu-id="408cc-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="408cc-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="408cc-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="408cc-131">Parent Elements</span></span>  
  
|<span data-ttu-id="408cc-132">Element</span><span class="sxs-lookup"><span data-stu-id="408cc-132">Element</span></span>|<span data-ttu-id="408cc-133">Opis</span><span class="sxs-lookup"><span data-stu-id="408cc-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="408cc-134">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="408cc-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="408cc-135">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="408cc-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408cc-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="408cc-136">Remarks</span></span>  
 <span data-ttu-id="408cc-137">Formanty ograniczania przepustowości umieść limity liczby równoczesnych wywołań, obiektów lub sesji, aby uniknąć nadmiernego zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="408cc-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="408cc-138">Śledzenia są zapisywane za każdym razem, gdy wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="408cc-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="408cc-139">Pierwszy śledzenia są zapisywane jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="408cc-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="408cc-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="408cc-140">Example</span></span>  
 <span data-ttu-id="408cc-141">W poniższym przykładzie konfiguracja Określa, że usługa ogranicza maksymalną równoczesnych wywołań 2 i maksymalnej liczby równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="408cc-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="408cc-142">Aby uzyskać szczegółowy przykład uruchomionych w tym przykładzie, zobacz [ograniczania](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="408cc-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="408cc-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="408cc-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [<span data-ttu-id="408cc-144">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="408cc-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
