---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: bfda2b9d7b3aa5219a3e4c344347d3b10419a7bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102417"
---
# <a name="oneway"></a><span data-ttu-id="fc5b0-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="fc5b0-101">\<oneWay></span></span>
<span data-ttu-id="fc5b0-102">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="fc5b0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fc5b0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="fc5b0-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fc5b0-104">\<bindings></span></span>  
<span data-ttu-id="fc5b0-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fc5b0-105">\<customBinding></span></span>  
<span data-ttu-id="fc5b0-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fc5b0-106">\<binding></span></span>  
<span data-ttu-id="fc5b0-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="fc5b0-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5b0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc5b0-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc5b0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc5b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc5b0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc5b0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc5b0-111">Attributes</span></span>  
  
|<span data-ttu-id="fc5b0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fc5b0-112">Attribute</span></span>|<span data-ttu-id="fc5b0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fc5b0-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="fc5b0-114">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="fc5b0-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="fc5b0-116">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc5b0-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc5b0-117">Child Elements</span></span>  
  
|<span data-ttu-id="fc5b0-118">Element</span><span class="sxs-lookup"><span data-stu-id="fc5b0-118">Element</span></span>|<span data-ttu-id="fc5b0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fc5b0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc5b0-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="fc5b0-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="fc5b0-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału na kanał bieżący.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc5b0-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc5b0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fc5b0-123">Element</span><span class="sxs-lookup"><span data-stu-id="fc5b0-123">Element</span></span>|<span data-ttu-id="fc5b0-124">Opis</span><span class="sxs-lookup"><span data-stu-id="fc5b0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc5b0-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fc5b0-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fc5b0-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc5b0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc5b0-127">Remarks</span></span>  
 <span data-ttu-id="fc5b0-128">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersji jest wymagany, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="fc5b0-129">Użytkownik może utworzyć niestandardowego powiązania, które warstw tego powiązania za pośrednictwem obsługujących sesji lub "żądanie-odpowiedź" transportu ułatwiają pakietów obsługi routingu.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="fc5b0-130">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej natywnych.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="fc5b0-131">Kolejnych przekształceń można stosować w tej warstwie, takie jak złożone dwukierunkowego i niezawodną obsługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5b0-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc5b0-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fc5b0-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fc5b0-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fc5b0-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="fc5b0-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fc5b0-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="fc5b0-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fc5b0-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fc5b0-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
