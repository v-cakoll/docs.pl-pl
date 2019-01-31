---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 35631cc4b120169e0cadb80c6beba26ab9eafd7a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283273"
---
# <a name="oneway"></a><span data-ttu-id="f0dea-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="f0dea-101">\<oneWay></span></span>
<span data-ttu-id="f0dea-102">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f0dea-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="f0dea-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f0dea-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f0dea-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f0dea-104">\<bindings></span></span>  
<span data-ttu-id="f0dea-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f0dea-105">\<customBinding></span></span>  
<span data-ttu-id="f0dea-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f0dea-106">\<binding></span></span>  
<span data-ttu-id="f0dea-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="f0dea-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0dea-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0dea-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0dea-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0dea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f0dea-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0dea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0dea-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0dea-111">Attributes</span></span>  
  
|<span data-ttu-id="f0dea-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f0dea-112">Attribute</span></span>|<span data-ttu-id="f0dea-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f0dea-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="f0dea-114">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="f0dea-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="f0dea-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f0dea-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="f0dea-116">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="f0dea-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0dea-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0dea-117">Child Elements</span></span>  
  
|<span data-ttu-id="f0dea-118">Element</span><span class="sxs-lookup"><span data-stu-id="f0dea-118">Element</span></span>|<span data-ttu-id="f0dea-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f0dea-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0dea-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="f0dea-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="f0dea-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału na kanał bieżący.</span><span class="sxs-lookup"><span data-stu-id="f0dea-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0dea-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0dea-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f0dea-123">Element</span><span class="sxs-lookup"><span data-stu-id="f0dea-123">Element</span></span>|<span data-ttu-id="f0dea-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f0dea-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0dea-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f0dea-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f0dea-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f0dea-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0dea-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0dea-127">Remarks</span></span>  
 <span data-ttu-id="f0dea-128">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersji jest wymagany, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="f0dea-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="f0dea-129">Użytkownik może utworzyć niestandardowego powiązania, które warstw tego powiązania za pośrednictwem obsługujących sesji lub "żądanie-odpowiedź" transportu ułatwiają pakietów obsługi routingu.</span><span class="sxs-lookup"><span data-stu-id="f0dea-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="f0dea-130">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej natywnych.</span><span class="sxs-lookup"><span data-stu-id="f0dea-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="f0dea-131">Kolejnych przekształceń można stosować w tej warstwie, takie jak złożone dwukierunkowego i niezawodną obsługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f0dea-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0dea-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0dea-132">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f0dea-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f0dea-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f0dea-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f0dea-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f0dea-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f0dea-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f0dea-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f0dea-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
