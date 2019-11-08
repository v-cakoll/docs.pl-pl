---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738791"
---
# <a name="oneway"></a><span data-ttu-id="11ae2-101">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="11ae2-101">\<oneWay></span></span>
<span data-ttu-id="11ae2-102">Umożliwia routing pakietów i stosowanie jednokierunkowych metod dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="11ae2-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="11ae2-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="11ae2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="11ae2-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="11ae2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="11ae2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="11ae2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="11ae2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="11ae2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="11ae2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="11ae2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="11ae2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oneWay >**</span><span class="sxs-lookup"><span data-stu-id="11ae2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ae2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="11ae2-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11ae2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11ae2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11ae2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11ae2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11ae2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11ae2-112">Attributes</span></span>  
  
|<span data-ttu-id="11ae2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="11ae2-113">Attribute</span></span>|<span data-ttu-id="11ae2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="11ae2-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="11ae2-115">Wartość logiczna określająca, czy jest włączona funkcja routingu pakietów.</span><span class="sxs-lookup"><span data-stu-id="11ae2-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="11ae2-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="11ae2-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="11ae2-117">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="11ae2-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11ae2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11ae2-118">Child Elements</span></span>  
  
|<span data-ttu-id="11ae2-119">Element</span><span class="sxs-lookup"><span data-stu-id="11ae2-119">Element</span></span>|<span data-ttu-id="11ae2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="11ae2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11ae2-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="11ae2-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="11ae2-122">Obiekt <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>, który zawiera właściwości puli kanałów dla bieżącego kanału.</span><span class="sxs-lookup"><span data-stu-id="11ae2-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11ae2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11ae2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="11ae2-124">Element</span><span class="sxs-lookup"><span data-stu-id="11ae2-124">Element</span></span>|<span data-ttu-id="11ae2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="11ae2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11ae2-126">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="11ae2-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="11ae2-127">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="11ae2-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11ae2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11ae2-128">Remarks</span></span>  
 <span data-ttu-id="11ae2-129">Aby włączyć routing pakietów, wymagana jest jednokierunkowa warstwa konwersji, która zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="11ae2-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="11ae2-130">Użytkownik może utworzyć niestandardowe powiązanie, które tworzy warstwy tego powiązania przez transport obsługujący sesję lub żądanie-odpowiedź, aby umożliwić jej Routing.</span><span class="sxs-lookup"><span data-stu-id="11ae2-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="11ae2-131">Ten element jest również przydatny, gdy chcesz uwidocznić jednokierunkowe metody w bardziej natywny sposób.</span><span class="sxs-lookup"><span data-stu-id="11ae2-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="11ae2-132">Więcej przekształceń można zastosować do tej warstwy, na przykład złożonego dupleksu i niezawodnej obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="11ae2-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ae2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11ae2-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="11ae2-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="11ae2-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="11ae2-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="11ae2-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="11ae2-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="11ae2-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="11ae2-137">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="11ae2-137">\<customBinding></span></span>](custombinding.md)
