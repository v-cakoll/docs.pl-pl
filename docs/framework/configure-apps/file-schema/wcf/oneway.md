---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932943"
---
# <a name="oneway"></a><span data-ttu-id="bef88-101">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="bef88-101">\<oneWay></span></span>
<span data-ttu-id="bef88-102">Umożliwia routing pakietów i stosowanie jednokierunkowych metod dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bef88-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="bef88-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bef88-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bef88-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="bef88-104">\<bindings></span></span>  
<span data-ttu-id="bef88-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bef88-105">\<customBinding></span></span>  
<span data-ttu-id="bef88-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="bef88-106">\<binding></span></span>  
<span data-ttu-id="bef88-107">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="bef88-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef88-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bef88-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef88-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bef88-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bef88-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bef88-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef88-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bef88-111">Attributes</span></span>  
  
|<span data-ttu-id="bef88-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bef88-112">Attribute</span></span>|<span data-ttu-id="bef88-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bef88-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="bef88-114">Wartość logiczna określająca, czy jest włączona funkcja routingu pakietów.</span><span class="sxs-lookup"><span data-stu-id="bef88-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="bef88-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="bef88-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="bef88-116">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="bef88-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bef88-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bef88-117">Child Elements</span></span>  
  
|<span data-ttu-id="bef88-118">Element</span><span class="sxs-lookup"><span data-stu-id="bef88-118">Element</span></span>|<span data-ttu-id="bef88-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bef88-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bef88-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="bef88-120">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="bef88-121"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> Obiekt, który zawiera właściwości puli kanałów dla bieżącego kanału.</span><span class="sxs-lookup"><span data-stu-id="bef88-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bef88-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bef88-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bef88-123">Element</span><span class="sxs-lookup"><span data-stu-id="bef88-123">Element</span></span>|<span data-ttu-id="bef88-124">Opis</span><span class="sxs-lookup"><span data-stu-id="bef88-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bef88-125">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="bef88-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bef88-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bef88-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef88-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bef88-127">Remarks</span></span>  
 <span data-ttu-id="bef88-128">Aby włączyć routing pakietów, wymagana jest jednokierunkowa warstwa konwersji, która zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="bef88-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="bef88-129">Użytkownik może utworzyć niestandardowe powiązanie, które tworzy warstwy tego powiązania przez transport obsługujący sesję lub żądanie-odpowiedź, aby umożliwić jej Routing.</span><span class="sxs-lookup"><span data-stu-id="bef88-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="bef88-130">Ten element jest również przydatny, gdy chcesz uwidocznić jednokierunkowe metody w bardziej natywny sposób.</span><span class="sxs-lookup"><span data-stu-id="bef88-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="bef88-131">Więcej przekształceń można zastosować do tej warstwy, na przykład złożonego dupleksu i niezawodnej obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bef88-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef88-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bef88-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bef88-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bef88-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bef88-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="bef88-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bef88-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bef88-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bef88-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bef88-136">\<customBinding></span></span>](custombinding.md)
