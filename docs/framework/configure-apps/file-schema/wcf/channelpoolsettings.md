---
title: '&lt;ChannelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: e55d3a989ae35d6e29062337cc79114a204608bb
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149101"
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="fa728-102">&lt;ChannelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="fa728-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="fa728-103">Określa ustawienia puli kanału dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa728-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="fa728-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fa728-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fa728-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fa728-105">\<bindings></span></span>  
<span data-ttu-id="fa728-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fa728-106">\<customBinding></span></span>  
<span data-ttu-id="fa728-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fa728-107">\<binding></span></span>  
<span data-ttu-id="fa728-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa728-108">\<oneWay></span></span>  
<span data-ttu-id="fa728-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="fa728-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa728-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa728-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa728-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa728-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fa728-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa728-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa728-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa728-113">Attributes</span></span>  
  
|<span data-ttu-id="fa728-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fa728-114">Attribute</span></span>|<span data-ttu-id="fa728-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fa728-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="fa728-116">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="fa728-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="fa728-117">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="fa728-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="fa728-118">Element <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="fa728-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="fa728-119">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fa728-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="fa728-120">Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa728-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="fa728-121">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="fa728-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa728-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa728-122">Child Elements</span></span>  
 <span data-ttu-id="fa728-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa728-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa728-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa728-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fa728-125">Element</span><span class="sxs-lookup"><span data-stu-id="fa728-125">Element</span></span>|<span data-ttu-id="fa728-126">Opis</span><span class="sxs-lookup"><span data-stu-id="fa728-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa728-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa728-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="fa728-128">Umożliwia routing pakietów dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa728-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa728-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa728-129">Remarks</span></span>  
 <span data-ttu-id="fa728-130">Przydziały są używane jako mechanizm zasady zapobiegające zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="fa728-131">Mogą zapobiegać atakom typu odmowa usługi (DOS), które są złośliwe lub przypadkowe.</span><span class="sxs-lookup"><span data-stu-id="fa728-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="fa728-132">Podczas ustawiania przydziałów kanału w niestandardowym kanale, użyj tego elementu.</span><span class="sxs-lookup"><span data-stu-id="fa728-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="fa728-133">`ChannelPoolSettings` Określa trzy przydziały:</span><span class="sxs-lookup"><span data-stu-id="fa728-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="fa728-134">`idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które zależą od zajmowania zasobów przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="fa728-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="fa728-135">Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="fa728-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="fa728-136">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="fa728-137">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="fa728-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa728-138">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fa728-139">`leaseTimeout` Przydziału służy do integracji z modułami równoważenia obciążenia i zwiększając niezawodność.</span><span class="sxs-lookup"><span data-stu-id="fa728-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="fa728-140">Wartość domyślna jest oparta na zachowawcze alokacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="fa728-141">Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji.</span><span class="sxs-lookup"><span data-stu-id="fa728-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa728-142">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fa728-143">`maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej serwera i klienta i jest używana w celu zwiększenia niezawodności.</span><span class="sxs-lookup"><span data-stu-id="fa728-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="fa728-144">Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów, który nadaje się do środowiska deweloperskiego i scenariusze instalacji małych.</span><span class="sxs-lookup"><span data-stu-id="fa728-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa728-145">Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa728-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa728-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa728-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="fa728-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa728-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="fa728-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fa728-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fa728-149">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="fa728-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fa728-150">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="fa728-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fa728-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fa728-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
