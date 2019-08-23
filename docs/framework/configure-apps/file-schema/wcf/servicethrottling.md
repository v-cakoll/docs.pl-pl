---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937105"
---
# <a name="servicethrottling"></a><span data-ttu-id="5bc0a-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="5bc0a-101">\<serviceThrottling></span></span>
<span data-ttu-id="5bc0a-102">Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5bc0a-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="5bc0a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5bc0a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5bc0a-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="5bc0a-104">\<behaviors></span></span>  
<span data-ttu-id="5bc0a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5bc0a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5bc0a-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="5bc0a-106">\<behavior></span></span>  
<span data-ttu-id="5bc0a-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="5bc0a-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc0a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bc0a-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bc0a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5bc0a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5bc0a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bc0a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5bc0a-111">Attributes</span></span>  
  
|<span data-ttu-id="5bc0a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5bc0a-112">Attribute</span></span>|<span data-ttu-id="5bc0a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5bc0a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bc0a-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="5bc0a-114">maxConcurrentCalls</span></span>|<span data-ttu-id="5bc0a-115">Dodatnia liczba całkowita, która ogranicza liczbę komunikatów przetwarzanych obecnie w <xref:System.ServiceModel.ServiceHost>ramach.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5bc0a-116">Wywołania przekraczające limit są umieszczane w kolejce.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="5bc0a-117">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="5bc0a-118">Wartość domyślna to 16 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="5bc0a-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="5bc0a-119">maxConcurrentInstances</span></span>|<span data-ttu-id="5bc0a-120">Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie w czasie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5bc0a-121">Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i uzupełniane, gdy zostanie udostępnione miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="5bc0a-122">Wartość domyślna to suma wartości maxConcurrentSessions i MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="5bc0a-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="5bc0a-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="5bc0a-123">maxConcurrentSessions</span></span>|<span data-ttu-id="5bc0a-124">Dodatnia liczba całkowita, która ogranicza liczbę sesji akceptowanych przez <xref:System.ServiceModel.ServiceHost> obiekt.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="5bc0a-125">Usługa będzie akceptować połączenia o przekroczeniu limitu, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału).</span><span class="sxs-lookup"><span data-stu-id="5bc0a-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="5bc0a-126">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="5bc0a-127">Wartość domyślna to 100 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bc0a-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5bc0a-128">Child Elements</span></span>  
 <span data-ttu-id="5bc0a-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bc0a-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5bc0a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5bc0a-131">Element</span><span class="sxs-lookup"><span data-stu-id="5bc0a-131">Element</span></span>|<span data-ttu-id="5bc0a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5bc0a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bc0a-133">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="5bc0a-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5bc0a-134">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc0a-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bc0a-135">Remarks</span></span>  
 <span data-ttu-id="5bc0a-136">Kontrolki ograniczania nakładają limity liczby współbieżnych wywołań, wystąpień lub sesji, aby zapobiec nadmiernemu zużyciu zasobów.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="5bc0a-137">Ślad jest zapisywana za każdym razem, gdy wartość atrybutu zostanie osiągnięta.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="5bc0a-138">Pierwszy ślad jest zapisywana jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bc0a-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bc0a-139">Example</span></span>  
 <span data-ttu-id="5bc0a-140">Poniższy przykład konfiguracji określa, że usługa ogranicza maksymalną liczbę współbieżnych wywołań do 2, a maksymalna liczba równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="5bc0a-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="5bc0a-141">Aby zapoznać się z szczegółowym przykładem uruchamiania tego przykładu, zobacz [ograniczanie przepustowości](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="5bc0a-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5bc0a-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bc0a-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="5bc0a-143">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="5bc0a-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
