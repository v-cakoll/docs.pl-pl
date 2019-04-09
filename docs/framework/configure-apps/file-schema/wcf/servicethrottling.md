---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 995ff9979096757225c9241e977f86f755955945
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158773"
---
# <a name="servicethrottling"></a><span data-ttu-id="54901-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="54901-101">\<serviceThrottling></span></span>
<span data-ttu-id="54901-102">Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="54901-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="54901-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="54901-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="54901-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="54901-104">\<behaviors></span></span>  
<span data-ttu-id="54901-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="54901-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="54901-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="54901-106">\<behavior></span></span>  
<span data-ttu-id="54901-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="54901-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54901-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="54901-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54901-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54901-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54901-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54901-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54901-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54901-111">Attributes</span></span>  
  
|<span data-ttu-id="54901-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="54901-112">Attribute</span></span>|<span data-ttu-id="54901-113">Opis</span><span class="sxs-lookup"><span data-stu-id="54901-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54901-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="54901-114">maxConcurrentCalls</span></span>|<span data-ttu-id="54901-115">Dodatnia liczba całkowita, która ogranicza liczbę wiadomości, które aktualnie przetworzyć w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="54901-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="54901-116">Wywołania poza limitem zostaną umieszczone w kolejce.</span><span class="sxs-lookup"><span data-stu-id="54901-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="54901-117">Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="54901-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="54901-118">Wartość domyślna to 16 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="54901-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="54901-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="54901-119">maxConcurrentInstances</span></span>|<span data-ttu-id="54901-120">Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiekty, które są wykonywane w tym samym czasie między <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="54901-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="54901-121">Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i ukończone, gdy miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="54901-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="54901-122">Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="54901-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="54901-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="54901-123">maxConcurrentSessions</span></span>|<span data-ttu-id="54901-124">Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="54901-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="54901-125">Usługa będzie akceptować połączeń poza limitem, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału).</span><span class="sxs-lookup"><span data-stu-id="54901-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="54901-126">Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="54901-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="54901-127">Wartość domyślna to 100 \* Liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="54901-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54901-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54901-128">Child Elements</span></span>  
 <span data-ttu-id="54901-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="54901-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54901-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54901-130">Parent Elements</span></span>  
  
|<span data-ttu-id="54901-131">Element</span><span class="sxs-lookup"><span data-stu-id="54901-131">Element</span></span>|<span data-ttu-id="54901-132">Opis</span><span class="sxs-lookup"><span data-stu-id="54901-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54901-133">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="54901-133">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="54901-134">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="54901-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54901-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54901-135">Remarks</span></span>  
 <span data-ttu-id="54901-136">Formanty ograniczania przepływności ogranicza liczbę równoczesnych wywołań, wystąpienia lub sesji, aby uniknąć nadmiernego zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="54901-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="54901-137">Śledzenia są zapisywane, za każdym razem, gdy zostanie osiągnięty wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="54901-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="54901-138">Pierwszy śledzenia są zapisywane jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="54901-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54901-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="54901-139">Example</span></span>  
 <span data-ttu-id="54901-140">W poniższym przykładzie konfiguracja Określa, że usługa ogranicza maksymalny współbieżnych wywołań 2 i maksymalnej liczby równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="54901-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="54901-141">Aby uzyskać szczegółowy przykład uruchomieniem tego przykładu, zobacz [ograniczania](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="54901-141">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54901-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54901-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="54901-143">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="54901-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
