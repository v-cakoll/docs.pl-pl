---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 70f7452a22ae08d6eccd7d3644bdc8df45087ae0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423187"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="1e035-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="1e035-101">\<channelPoolSettings></span></span>
<span data-ttu-id="1e035-102">Określa ustawienia puli kanału dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e035-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="1e035-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1e035-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1e035-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1e035-104">\<bindings></span></span>  
<span data-ttu-id="1e035-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1e035-105">\<customBinding></span></span>  
<span data-ttu-id="1e035-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1e035-106">\<binding></span></span>  
<span data-ttu-id="1e035-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="1e035-107">\<oneWay></span></span>  
<span data-ttu-id="1e035-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="1e035-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e035-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e035-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e035-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1e035-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1e035-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1e035-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e035-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1e035-112">Attributes</span></span>  
  
|<span data-ttu-id="1e035-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1e035-113">Attribute</span></span>|<span data-ttu-id="1e035-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1e035-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="1e035-115">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="1e035-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="1e035-116">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="1e035-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="1e035-117">Element <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="1e035-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="1e035-118">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1e035-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="1e035-119">Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1e035-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="1e035-120">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="1e035-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e035-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1e035-121">Child Elements</span></span>  
 <span data-ttu-id="1e035-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="1e035-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e035-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1e035-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1e035-124">Element</span><span class="sxs-lookup"><span data-stu-id="1e035-124">Element</span></span>|<span data-ttu-id="1e035-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1e035-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e035-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="1e035-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="1e035-127">Umożliwia routing pakietów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1e035-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e035-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e035-128">Remarks</span></span>  
 <span data-ttu-id="1e035-129">Przydziały są używane jako mechanizm zasady zapobiegające zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="1e035-130">Mogą zapobiegać atakom typu odmowa usługi (DOS), które są złośliwe lub przypadkowe.</span><span class="sxs-lookup"><span data-stu-id="1e035-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="1e035-131">Podczas ustawiania przydziałów kanału w niestandardowym kanale, użyj tego elementu.</span><span class="sxs-lookup"><span data-stu-id="1e035-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="1e035-132">`ChannelPoolSettings` Określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="1e035-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="1e035-133">`idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które zależą od zajmowania zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="1e035-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="1e035-134">Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="1e035-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="1e035-135">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="1e035-136">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="1e035-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="1e035-137">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="1e035-138">`leaseTimeout` Przydziału służy do integracji z modułami równoważenia obciążenia i zwiększając niezawodność.</span><span class="sxs-lookup"><span data-stu-id="1e035-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="1e035-139">Wartość domyślna jest oparta na zachowawcze alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="1e035-140">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="1e035-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="1e035-141">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="1e035-142">`maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej serwera i klienta i jest używana w celu zwiększenia niezawodności.</span><span class="sxs-lookup"><span data-stu-id="1e035-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="1e035-143">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów, który nadaje się do środowiska deweloperskiego i scenariusze instalacji małych.</span><span class="sxs-lookup"><span data-stu-id="1e035-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="1e035-144">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e035-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e035-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e035-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1e035-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="1e035-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="1e035-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1e035-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1e035-148">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1e035-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1e035-149">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1e035-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1e035-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1e035-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
