---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 000124c8d0dda81f99668cd330f7cc97c2520464
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145266"
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="727ac-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="727ac-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="727ac-103">Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="727ac-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="727ac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="727ac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="727ac-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="727ac-105">\<behaviors></span></span>  
<span data-ttu-id="727ac-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="727ac-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="727ac-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="727ac-107">\<behavior></span></span>  
<span data-ttu-id="727ac-108">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="727ac-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="727ac-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="727ac-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="727ac-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="727ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="727ac-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="727ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="727ac-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="727ac-112">Attributes</span></span>  
  
|<span data-ttu-id="727ac-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="727ac-113">Attribute</span></span>|<span data-ttu-id="727ac-114">Opis</span><span class="sxs-lookup"><span data-stu-id="727ac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="727ac-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="727ac-115">maxConcurrentCalls</span></span>|<span data-ttu-id="727ac-116">Dodatnia liczba całkowita, która ogranicza liczbę wiadomości, które aktualnie przetworzyć w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="727ac-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="727ac-117">Wywołania poza limitem zostaną umieszczone w kolejce.</span><span class="sxs-lookup"><span data-stu-id="727ac-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="727ac-118">Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="727ac-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="727ac-119">Wartość domyślna to 16 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="727ac-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="727ac-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="727ac-120">maxConcurrentInstances</span></span>|<span data-ttu-id="727ac-121">Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiekty, które są wykonywane w tym samym czasie między <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="727ac-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="727ac-122">Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i ukończone, gdy miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="727ac-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="727ac-123">Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="727ac-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="727ac-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="727ac-124">maxConcurrentSessions</span></span>|<span data-ttu-id="727ac-125">Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="727ac-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="727ac-126">Usługa będzie akceptować połączeń poza limitem, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału).</span><span class="sxs-lookup"><span data-stu-id="727ac-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="727ac-127">Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="727ac-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="727ac-128">Wartość domyślna to 100 \* Liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="727ac-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="727ac-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="727ac-129">Child Elements</span></span>  
 <span data-ttu-id="727ac-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="727ac-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="727ac-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="727ac-131">Parent Elements</span></span>  
  
|<span data-ttu-id="727ac-132">Element</span><span class="sxs-lookup"><span data-stu-id="727ac-132">Element</span></span>|<span data-ttu-id="727ac-133">Opis</span><span class="sxs-lookup"><span data-stu-id="727ac-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="727ac-134">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="727ac-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="727ac-135">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="727ac-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="727ac-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="727ac-136">Remarks</span></span>  
 <span data-ttu-id="727ac-137">Formanty ograniczania przepływności ogranicza liczbę równoczesnych wywołań, wystąpienia lub sesji, aby uniknąć nadmiernego zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="727ac-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="727ac-138">Śledzenia są zapisywane, za każdym razem, gdy zostanie osiągnięty wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="727ac-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="727ac-139">Pierwszy śledzenia są zapisywane jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="727ac-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="727ac-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="727ac-140">Example</span></span>  
 <span data-ttu-id="727ac-141">W poniższym przykładzie konfiguracja Określa, że usługa ogranicza maksymalny współbieżnych wywołań 2 i maksymalnej liczby równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="727ac-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="727ac-142">Aby uzyskać szczegółowy przykład uruchomieniem tego przykładu, zobacz [ograniczania](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="727ac-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="727ac-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="727ac-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [<span data-ttu-id="727ac-144">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="727ac-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
