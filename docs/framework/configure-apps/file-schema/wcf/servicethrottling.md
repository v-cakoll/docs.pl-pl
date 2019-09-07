---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399564"
---
# <a name="servicethrottling"></a><span data-ttu-id="8d287-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="8d287-101">\<serviceThrottling></span></span>
<span data-ttu-id="8d287-102">Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8d287-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="8d287-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d287-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d287-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8d287-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8d287-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8d287-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8d287-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8d287-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="8d287-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8d287-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="8d287-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> serviceograniczenia**</span><span class="sxs-lookup"><span data-stu-id="8d287-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d287-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d287-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d287-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d287-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d287-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d287-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d287-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d287-112">Attributes</span></span>  
  
|<span data-ttu-id="8d287-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d287-113">Attribute</span></span>|<span data-ttu-id="8d287-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8d287-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d287-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="8d287-115">maxConcurrentCalls</span></span>|<span data-ttu-id="8d287-116">Dodatnia liczba całkowita, która ogranicza liczbę komunikatów przetwarzanych obecnie w <xref:System.ServiceModel.ServiceHost>ramach.</span><span class="sxs-lookup"><span data-stu-id="8d287-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8d287-117">Wywołania przekraczające limit są umieszczane w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8d287-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="8d287-118">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="8d287-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="8d287-119">Wartość domyślna to 16 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="8d287-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="8d287-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="8d287-120">maxConcurrentInstances</span></span>|<span data-ttu-id="8d287-121">Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie w czasie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8d287-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8d287-122">Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i uzupełniane, gdy zostanie udostępnione miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="8d287-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="8d287-123">Wartość domyślna to suma wartości maxConcurrentSessions i MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="8d287-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="8d287-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="8d287-124">maxConcurrentSessions</span></span>|<span data-ttu-id="8d287-125">Dodatnia liczba całkowita, która ogranicza liczbę sesji akceptowanych przez <xref:System.ServiceModel.ServiceHost> obiekt.</span><span class="sxs-lookup"><span data-stu-id="8d287-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="8d287-126">Usługa będzie akceptować połączenia o przekroczeniu limitu, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału).</span><span class="sxs-lookup"><span data-stu-id="8d287-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="8d287-127">Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="8d287-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="8d287-128">Wartość domyślna to 100 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="8d287-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d287-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d287-129">Child Elements</span></span>  
 <span data-ttu-id="8d287-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="8d287-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d287-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d287-131">Parent Elements</span></span>  
  
|<span data-ttu-id="8d287-132">Element</span><span class="sxs-lookup"><span data-stu-id="8d287-132">Element</span></span>|<span data-ttu-id="8d287-133">Opis</span><span class="sxs-lookup"><span data-stu-id="8d287-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d287-134">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="8d287-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8d287-135">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="8d287-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d287-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d287-136">Remarks</span></span>  
 <span data-ttu-id="8d287-137">Kontrolki ograniczania nakładają limity liczby współbieżnych wywołań, wystąpień lub sesji, aby zapobiec nadmiernemu zużyciu zasobów.</span><span class="sxs-lookup"><span data-stu-id="8d287-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="8d287-138">Ślad jest zapisywana za każdym razem, gdy wartość atrybutu zostanie osiągnięta.</span><span class="sxs-lookup"><span data-stu-id="8d287-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="8d287-139">Pierwszy ślad jest zapisywana jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="8d287-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d287-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d287-140">Example</span></span>  
 <span data-ttu-id="8d287-141">Poniższy przykład konfiguracji określa, że usługa ogranicza maksymalną liczbę współbieżnych wywołań do 2, a maksymalna liczba równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="8d287-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="8d287-142">Aby zapoznać się z szczegółowym przykładem uruchamiania tego przykładu, zobacz [ograniczanie przepustowości](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-142">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d287-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d287-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="8d287-144">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="8d287-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
