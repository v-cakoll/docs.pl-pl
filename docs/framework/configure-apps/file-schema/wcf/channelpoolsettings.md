---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398158"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="f1754-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="f1754-101">\<channelPoolSettings></span></span>
<span data-ttu-id="f1754-102">Określa ustawienia puli kanałów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1754-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
<span data-ttu-id="f1754-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1754-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f1754-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f1754-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f1754-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f1754-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f1754-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f1754-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f1754-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="f1754-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f1754-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> oneWay**](oneway.md)</span><span class="sxs-lookup"><span data-stu-id="f1754-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)</span></span>\
<span data-ttu-id="f1754-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<channelPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="f1754-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1754-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1754-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1754-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1754-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f1754-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1754-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1754-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1754-113">Attributes</span></span>  
  
|<span data-ttu-id="f1754-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1754-114">Attribute</span></span>|<span data-ttu-id="f1754-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f1754-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="f1754-116">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności kanałów w puli przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="f1754-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="f1754-117">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="f1754-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="f1754-118">A <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy jest zwracany do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="f1754-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="f1754-119">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f1754-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="f1754-120">Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f1754-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="f1754-121">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="f1754-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1754-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1754-122">Child Elements</span></span>  
 <span data-ttu-id="f1754-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="f1754-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1754-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1754-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f1754-125">Element</span><span class="sxs-lookup"><span data-stu-id="f1754-125">Element</span></span>|<span data-ttu-id="f1754-126">Opis</span><span class="sxs-lookup"><span data-stu-id="f1754-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1754-127">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="f1754-127">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="f1754-128">Włącza routing pakietów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1754-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1754-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1754-129">Remarks</span></span>  
 <span data-ttu-id="f1754-130">Przydziały są używane jako mechanizm zasad, aby zapobiec zużyciu nadmiernych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="f1754-131">Uniemożliwiają one ataki typu "odmowa usługi" (DOS), które są złośliwe lub niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="f1754-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="f1754-132">Użyj tego elementu, gdy ustawiasz limity przydziału kanałów w niestandardowym kanale.</span><span class="sxs-lookup"><span data-stu-id="f1754-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="f1754-133">`ChannelPoolSettings`określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="f1754-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="f1754-134">`idleTimeout` Przydział służy do zapobiegania atakom typu "odmowa usługi" (DOS) na serwerze, który polega na rozdzieleniu zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="f1754-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="f1754-135">Ustawienie poprawnej wartości na kliencie może zwiększyć niezawodność połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="f1754-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="f1754-136">Wartość domyślna jest oparta na nieumiarkowanie niedostatecznej alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="f1754-137">Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="f1754-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f1754-138">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f1754-139">`leaseTimeout` Przydział służy do integracji z usługami równoważenia obciążenia i zwiększania niezawodności.</span><span class="sxs-lookup"><span data-stu-id="f1754-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="f1754-140">Wartość domyślna jest określana na podstawie ostrożnej alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="f1754-141">Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="f1754-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f1754-142">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f1754-143">Limity `maxOutboundChannelsPerEndpoint` przydziału są ustawiane w pamięci podręcznej zarówno na serwerze, jak i na kliencie i są używane w celu zwiększenia niezawodności.</span><span class="sxs-lookup"><span data-stu-id="f1754-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="f1754-144">Wartość domyślna jest oparta na niewielkiej ilości alokacji zasobów, która jest odpowiednia dla środowiska programistycznego i małych scenariuszy instalacji.</span><span class="sxs-lookup"><span data-stu-id="f1754-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f1754-145">Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1754-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1754-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1754-146">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f1754-147">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="f1754-147">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="f1754-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f1754-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f1754-149">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f1754-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f1754-150">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f1754-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f1754-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f1754-151">\<customBinding></span></span>](custombinding.md)
