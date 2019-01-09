---
title: '&lt;OneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 5f3d534ee98100347acaa485e60a3c74f82ee0b9
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150581"
---
# <a name="ltonewaygt"></a><span data-ttu-id="f179e-102">&lt;OneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="f179e-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="f179e-103">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f179e-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="f179e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f179e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f179e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f179e-105">\<bindings></span></span>  
<span data-ttu-id="f179e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f179e-106">\<customBinding></span></span>  
<span data-ttu-id="f179e-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f179e-107">\<binding></span></span>  
<span data-ttu-id="f179e-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="f179e-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f179e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f179e-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f179e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f179e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f179e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f179e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f179e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f179e-112">Attributes</span></span>  
  
|<span data-ttu-id="f179e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f179e-113">Attribute</span></span>|<span data-ttu-id="f179e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f179e-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="f179e-115">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="f179e-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="f179e-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f179e-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="f179e-117">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="f179e-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f179e-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f179e-118">Child Elements</span></span>  
  
|<span data-ttu-id="f179e-119">Element</span><span class="sxs-lookup"><span data-stu-id="f179e-119">Element</span></span>|<span data-ttu-id="f179e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f179e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f179e-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="f179e-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="f179e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału na kanał bieżący.</span><span class="sxs-lookup"><span data-stu-id="f179e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f179e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f179e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f179e-124">Element</span><span class="sxs-lookup"><span data-stu-id="f179e-124">Element</span></span>|<span data-ttu-id="f179e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f179e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f179e-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f179e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f179e-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f179e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f179e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f179e-128">Remarks</span></span>  
 <span data-ttu-id="f179e-129">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersji jest wymagany, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="f179e-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="f179e-130">Użytkownik może utworzyć niestandardowego powiązania, które warstw tego powiązania za pośrednictwem obsługujących sesji lub "żądanie-odpowiedź" transportu ułatwiają pakietów obsługi routingu.</span><span class="sxs-lookup"><span data-stu-id="f179e-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="f179e-131">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej natywnych.</span><span class="sxs-lookup"><span data-stu-id="f179e-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="f179e-132">Kolejnych przekształceń można stosować w tej warstwie, takie jak złożone dwukierunkowego i niezawodną obsługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f179e-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f179e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f179e-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f179e-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f179e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f179e-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f179e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f179e-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f179e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f179e-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f179e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
