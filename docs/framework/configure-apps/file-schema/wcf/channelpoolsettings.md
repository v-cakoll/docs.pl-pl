---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919558"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="192e1-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="192e1-101">\<channelPoolSettings></span></span>
<span data-ttu-id="192e1-102">Określa ustawienia puli kanałów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="192e1-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="192e1-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="192e1-103">\<system.serviceModel></span></span>  
<span data-ttu-id="192e1-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="192e1-104">\<bindings></span></span>  
<span data-ttu-id="192e1-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="192e1-105">\<customBinding></span></span>  
<span data-ttu-id="192e1-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="192e1-106">\<binding></span></span>  
<span data-ttu-id="192e1-107">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="192e1-107">\<oneWay></span></span>  
<span data-ttu-id="192e1-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="192e1-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="192e1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="192e1-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="192e1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="192e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="192e1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="192e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="192e1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="192e1-112">Attributes</span></span>  
  
|<span data-ttu-id="192e1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="192e1-113">Attribute</span></span>|<span data-ttu-id="192e1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="192e1-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="192e1-115">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności kanałów w puli przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="192e1-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="192e1-116">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="192e1-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="192e1-117">A <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy jest zwracany do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="192e1-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="192e1-118">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="192e1-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="192e1-119">Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="192e1-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="192e1-120">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="192e1-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="192e1-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="192e1-121">Child Elements</span></span>  
 <span data-ttu-id="192e1-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="192e1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="192e1-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="192e1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="192e1-124">Element</span><span class="sxs-lookup"><span data-stu-id="192e1-124">Element</span></span>|<span data-ttu-id="192e1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="192e1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="192e1-126">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="192e1-126">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="192e1-127">Włącza routing pakietów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="192e1-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192e1-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="192e1-128">Remarks</span></span>  
 <span data-ttu-id="192e1-129">Przydziały są używane jako mechanizm zasad, aby zapobiec zużyciu nadmiernych zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="192e1-130">Uniemożliwiają one ataki typu "odmowa usługi" (DOS), które są złośliwe lub niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="192e1-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="192e1-131">Użyj tego elementu, gdy ustawiasz limity przydziału kanałów w niestandardowym kanale.</span><span class="sxs-lookup"><span data-stu-id="192e1-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="192e1-132">`ChannelPoolSettings`określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="192e1-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="192e1-133">`idleTimeout` Przydział służy do zapobiegania atakom typu "odmowa usługi" (DOS) na serwerze, który polega na rozdzieleniu zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="192e1-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="192e1-134">Ustawienie poprawnej wartości na kliencie może zwiększyć niezawodność połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="192e1-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="192e1-135">Wartość domyślna jest oparta na nieumiarkowanie niedostatecznej alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="192e1-136">Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="192e1-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="192e1-137">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="192e1-138">`leaseTimeout` Przydział służy do integracji z usługami równoważenia obciążenia i zwiększania niezawodności.</span><span class="sxs-lookup"><span data-stu-id="192e1-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="192e1-139">Wartość domyślna jest określana na podstawie ostrożnej alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="192e1-140">Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="192e1-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="192e1-141">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="192e1-142">Limity `maxOutboundChannelsPerEndpoint` przydziału są ustawiane w pamięci podręcznej zarówno na serwerze, jak i na kliencie i są używane w celu zwiększenia niezawodności.</span><span class="sxs-lookup"><span data-stu-id="192e1-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="192e1-143">Wartość domyślna jest oparta na niewielkiej ilości alokacji zasobów, która jest odpowiednia dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="192e1-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="192e1-144">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="192e1-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192e1-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="192e1-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="192e1-146">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="192e1-146">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="192e1-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="192e1-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="192e1-148">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="192e1-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="192e1-149">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="192e1-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="192e1-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="192e1-150">\<customBinding></span></span>](custombinding.md)
