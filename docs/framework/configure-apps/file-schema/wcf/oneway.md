---
title: '&lt;oneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f9a5631501b3879463606f526485314efd5eff2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltonewaygt"></a><span data-ttu-id="23d92-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="23d92-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="23d92-103">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="23d92-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="23d92-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23d92-104">\<system.serviceModel></span></span>  
<span data-ttu-id="23d92-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="23d92-105">\<bindings></span></span>  
<span data-ttu-id="23d92-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="23d92-106">\<customBinding></span></span>  
<span data-ttu-id="23d92-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="23d92-107">\<binding></span></span>  
<span data-ttu-id="23d92-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="23d92-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d92-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="23d92-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23d92-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23d92-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23d92-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23d92-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23d92-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23d92-112">Attributes</span></span>  
  
|<span data-ttu-id="23d92-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23d92-113">Attribute</span></span>|<span data-ttu-id="23d92-114">Opis</span><span class="sxs-lookup"><span data-stu-id="23d92-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="23d92-115">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="23d92-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="23d92-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="23d92-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="23d92-117">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="23d92-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23d92-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23d92-118">Child Elements</span></span>  
  
|<span data-ttu-id="23d92-119">Element</span><span class="sxs-lookup"><span data-stu-id="23d92-119">Element</span></span>|<span data-ttu-id="23d92-120">Opis</span><span class="sxs-lookup"><span data-stu-id="23d92-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d92-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="23d92-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="23d92-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału dla bieżącego kanału.</span><span class="sxs-lookup"><span data-stu-id="23d92-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23d92-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23d92-123">Parent Elements</span></span>  
  
|<span data-ttu-id="23d92-124">Element</span><span class="sxs-lookup"><span data-stu-id="23d92-124">Element</span></span>|<span data-ttu-id="23d92-125">Opis</span><span class="sxs-lookup"><span data-stu-id="23d92-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d92-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="23d92-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="23d92-127">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="23d92-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d92-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23d92-128">Remarks</span></span>  
 <span data-ttu-id="23d92-129">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersja jest wymagana, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="23d92-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="23d92-130">Użytkownik może utworzyć niestandardowego powiązania, który warstwy tego powiązania za pośrednictwem sesji aware lub żądanie odpowiedź transportu była pakietów routingu.</span><span class="sxs-lookup"><span data-stu-id="23d92-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="23d92-131">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej macierzystego.</span><span class="sxs-lookup"><span data-stu-id="23d92-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="23d92-132">Przekształcenia więcej można zastosować za pośrednictwem tej warstwy, takie jak złożone dupleksu i niezawodna obsługa komunikatów.</span><span class="sxs-lookup"><span data-stu-id="23d92-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d92-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23d92-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="23d92-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="23d92-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="23d92-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="23d92-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="23d92-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="23d92-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="23d92-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="23d92-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
