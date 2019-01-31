---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd6cf74560694e7e16103c624b33a4c590ce5d50
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266926"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="9cb11-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="9cb11-101">\<channelPoolSettings></span></span>
<span data-ttu-id="9cb11-102">Określa ustawienia puli kanału dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9cb11-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="9cb11-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9cb11-103">\<system.serviceModel></span></span>  
<span data-ttu-id="9cb11-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9cb11-104">\<bindings></span></span>  
<span data-ttu-id="9cb11-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9cb11-105">\<customBinding></span></span>  
<span data-ttu-id="9cb11-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9cb11-106">\<binding></span></span>  
<span data-ttu-id="9cb11-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9cb11-107">\<oneWay></span></span>  
<span data-ttu-id="9cb11-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="9cb11-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb11-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cb11-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cb11-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9cb11-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9cb11-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9cb11-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cb11-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9cb11-112">Attributes</span></span>  
  
|<span data-ttu-id="9cb11-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9cb11-113">Attribute</span></span>|<span data-ttu-id="9cb11-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9cb11-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="9cb11-115">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="9cb11-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="9cb11-116">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="9cb11-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="9cb11-117">Element <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="9cb11-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="9cb11-118">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9cb11-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="9cb11-119">Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9cb11-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="9cb11-120">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="9cb11-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cb11-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9cb11-121">Child Elements</span></span>  
 <span data-ttu-id="9cb11-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="9cb11-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cb11-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9cb11-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9cb11-124">Element</span><span class="sxs-lookup"><span data-stu-id="9cb11-124">Element</span></span>|<span data-ttu-id="9cb11-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9cb11-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cb11-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9cb11-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="9cb11-127">Umożliwia routing pakietów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9cb11-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb11-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cb11-128">Remarks</span></span>  
 <span data-ttu-id="9cb11-129">Przydziały są używane jako mechanizm zasady zapobiegające zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="9cb11-130">Mogą zapobiegać atakom typu odmowa usługi (DOS), które są złośliwe lub przypadkowe.</span><span class="sxs-lookup"><span data-stu-id="9cb11-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="9cb11-131">Podczas ustawiania przydziałów kanału w niestandardowym kanale, użyj tego elementu.</span><span class="sxs-lookup"><span data-stu-id="9cb11-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="9cb11-132">`ChannelPoolSettings` Określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="9cb11-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="9cb11-133">`idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które zależą od zajmowania zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="9cb11-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="9cb11-134">Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="9cb11-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="9cb11-135">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="9cb11-136">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="9cb11-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9cb11-137">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="9cb11-138">`leaseTimeout` Przydziału służy do integracji z modułami równoważenia obciążenia i zwiększając niezawodność.</span><span class="sxs-lookup"><span data-stu-id="9cb11-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="9cb11-139">Wartość domyślna jest oparta na zachowawcze alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="9cb11-140">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="9cb11-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9cb11-141">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="9cb11-142">`maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej serwera i klienta i jest używana w celu zwiększenia niezawodności.</span><span class="sxs-lookup"><span data-stu-id="9cb11-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="9cb11-143">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów, który nadaje się do środowiska deweloperskiego i scenariusze instalacji małych.</span><span class="sxs-lookup"><span data-stu-id="9cb11-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="9cb11-144">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cb11-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb11-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cb11-145">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9cb11-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="9cb11-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="9cb11-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9cb11-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9cb11-148">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9cb11-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9cb11-149">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9cb11-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9cb11-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9cb11-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
