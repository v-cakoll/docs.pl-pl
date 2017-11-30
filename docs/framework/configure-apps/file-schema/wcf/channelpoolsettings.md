---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="9c126-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="9c126-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="9c126-103">Określa ustawienia puli kanału dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9c126-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="9c126-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9c126-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9c126-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9c126-105">\<bindings></span></span>  
<span data-ttu-id="9c126-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9c126-106">\<customBinding></span></span>  
<span data-ttu-id="9c126-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9c126-107">\<binding></span></span>  
<span data-ttu-id="9c126-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="9c126-108">\<oneWay></span></span>  
<span data-ttu-id="9c126-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="9c126-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c126-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c126-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c126-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c126-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9c126-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c126-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c126-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c126-113">Attributes</span></span>  
  
|<span data-ttu-id="9c126-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9c126-114">Attribute</span></span>|<span data-ttu-id="9c126-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9c126-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="9c126-116">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="9c126-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="9c126-117">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="9c126-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="9c126-118">A <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="9c126-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="9c126-119">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9c126-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="9c126-120">Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9c126-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="9c126-121">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="9c126-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c126-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c126-122">Child Elements</span></span>  
 <span data-ttu-id="9c126-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c126-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c126-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c126-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9c126-125">Element</span><span class="sxs-lookup"><span data-stu-id="9c126-125">Element</span></span>|<span data-ttu-id="9c126-126">Opis</span><span class="sxs-lookup"><span data-stu-id="9c126-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c126-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="9c126-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="9c126-128">Włącza pakiet rutingu dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9c126-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c126-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c126-129">Remarks</span></span>  
 <span data-ttu-id="9c126-130">Przydziały są używane jako mechanizm zasad zapobiegających zużycie zasobów nadmierne.</span><span class="sxs-lookup"><span data-stu-id="9c126-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="9c126-131">Zapobiegają one przez ataków typu odmowa usługi (DOS), które są złośliwe lub przypadkowe.</span><span class="sxs-lookup"><span data-stu-id="9c126-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="9c126-132">Użyj tego elementu, ustawiając przydziały kanału w niestandardowym kanale.</span><span class="sxs-lookup"><span data-stu-id="9c126-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="9c126-133">`ChannelPoolSettings`Określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="9c126-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="9c126-134">`idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które są oparte na zajmowania zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="9c126-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="9c126-135">Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywać połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="9c126-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="9c126-136">Wartość domyślna jest oparta na konserwatywnie niewielkie alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c126-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="9c126-137">Jest ona odpowiednia dla Środowisko deweloperskie i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="9c126-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9c126-138">Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c126-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="9c126-139">`leaseTimeout` Przydziału służy do integracji z usługą równoważenia obciążenia i poprawa niezawodności.</span><span class="sxs-lookup"><span data-stu-id="9c126-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="9c126-140">Wartość domyślna jest oparta na zachowawcze alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c126-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="9c126-141">Jest ona odpowiednia dla Środowisko deweloperskie i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="9c126-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9c126-142">Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c126-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="9c126-143">`maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej na serwerze i kliencie i jest używany do poprawy niezawodności.</span><span class="sxs-lookup"><span data-stu-id="9c126-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="9c126-144">Wartość domyślna jest oparta na konserwatywnie niewielkie alokacji zasobów, które jest odpowiednie dla środowiska programowania i scenariusze instalacji małych.</span><span class="sxs-lookup"><span data-stu-id="9c126-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9c126-145">Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c126-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c126-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c126-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9c126-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="9c126-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="9c126-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9c126-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9c126-149">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9c126-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9c126-150">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9c126-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9c126-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9c126-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
