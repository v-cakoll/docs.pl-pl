---
title: '&lt;oneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: c909bce5b54976a215a59ca8fd9f097f574acd80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600300"
---
# <a name="ltonewaygt"></a><span data-ttu-id="09dd5-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="09dd5-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="09dd5-103">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="09dd5-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="09dd5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09dd5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="09dd5-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="09dd5-105">\<bindings></span></span>  
<span data-ttu-id="09dd5-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="09dd5-106">\<customBinding></span></span>  
<span data-ttu-id="09dd5-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="09dd5-107">\<binding></span></span>  
<span data-ttu-id="09dd5-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="09dd5-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09dd5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="09dd5-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09dd5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09dd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09dd5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="09dd5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09dd5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09dd5-112">Attributes</span></span>  
  
|<span data-ttu-id="09dd5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="09dd5-113">Attribute</span></span>|<span data-ttu-id="09dd5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="09dd5-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="09dd5-115">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="09dd5-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="09dd5-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="09dd5-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="09dd5-117">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="09dd5-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09dd5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09dd5-118">Child Elements</span></span>  
  
|<span data-ttu-id="09dd5-119">Element</span><span class="sxs-lookup"><span data-stu-id="09dd5-119">Element</span></span>|<span data-ttu-id="09dd5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="09dd5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09dd5-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="09dd5-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="09dd5-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału na kanał bieżący.</span><span class="sxs-lookup"><span data-stu-id="09dd5-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09dd5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09dd5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="09dd5-124">Element</span><span class="sxs-lookup"><span data-stu-id="09dd5-124">Element</span></span>|<span data-ttu-id="09dd5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="09dd5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09dd5-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="09dd5-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="09dd5-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="09dd5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09dd5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09dd5-128">Remarks</span></span>  
 <span data-ttu-id="09dd5-129">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersji jest wymagany, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="09dd5-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="09dd5-130">Użytkownik może utworzyć niestandardowego powiązania, które warstw tego powiązania za pośrednictwem obsługujących sesji lub "żądanie-odpowiedź" transportu ułatwiają pakietów obsługi routingu.</span><span class="sxs-lookup"><span data-stu-id="09dd5-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="09dd5-131">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej natywnych.</span><span class="sxs-lookup"><span data-stu-id="09dd5-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="09dd5-132">Kolejnych przekształceń można stosować w tej warstwie, takie jak złożone dwukierunkowego i niezawodną obsługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="09dd5-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09dd5-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09dd5-133">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="09dd5-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="09dd5-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="09dd5-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="09dd5-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="09dd5-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="09dd5-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="09dd5-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="09dd5-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
