---
title: '&lt;oneWay&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be70abe745879b5d6f6e8cdde802a6403f90174b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="06eef-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="06eef-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="06eef-103">Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="06eef-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="06eef-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="06eef-104">\<system.serviceModel></span></span>  
<span data-ttu-id="06eef-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="06eef-105">\<bindings></span></span>  
<span data-ttu-id="06eef-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="06eef-106">\<customBinding></span></span>  
<span data-ttu-id="06eef-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="06eef-107">\<binding></span></span>  
<span data-ttu-id="06eef-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="06eef-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06eef-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="06eef-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06eef-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06eef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06eef-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06eef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06eef-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06eef-112">Attributes</span></span>  
  
|<span data-ttu-id="06eef-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="06eef-113">Attribute</span></span>|<span data-ttu-id="06eef-114">Opis</span><span class="sxs-lookup"><span data-stu-id="06eef-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="06eef-115">Wartość logiczna określająca, czy jest włączony pakiet routingu.</span><span class="sxs-lookup"><span data-stu-id="06eef-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="06eef-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="06eef-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="06eef-117">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.</span><span class="sxs-lookup"><span data-stu-id="06eef-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06eef-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06eef-118">Child Elements</span></span>  
  
|<span data-ttu-id="06eef-119">Element</span><span class="sxs-lookup"><span data-stu-id="06eef-119">Element</span></span>|<span data-ttu-id="06eef-120">Opis</span><span class="sxs-lookup"><span data-stu-id="06eef-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06eef-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="06eef-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="06eef-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału dla bieżącego kanału.</span><span class="sxs-lookup"><span data-stu-id="06eef-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06eef-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06eef-123">Parent Elements</span></span>  
  
|<span data-ttu-id="06eef-124">Element</span><span class="sxs-lookup"><span data-stu-id="06eef-124">Element</span></span>|<span data-ttu-id="06eef-125">Opis</span><span class="sxs-lookup"><span data-stu-id="06eef-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06eef-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="06eef-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="06eef-127">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="06eef-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06eef-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06eef-128">Remarks</span></span>  
 <span data-ttu-id="06eef-129">Aby włączyć routing pakietów, warstwy jednokierunkowe konwersja jest wymagana, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="06eef-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="06eef-130">Użytkownik może utworzyć niestandardowego powiązania, który warstwy tego powiązania za pośrednictwem sesji aware lub żądanie odpowiedź transportu była pakietów routingu.</span><span class="sxs-lookup"><span data-stu-id="06eef-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="06eef-131">Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej macierzystego.</span><span class="sxs-lookup"><span data-stu-id="06eef-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="06eef-132">Przekształcenia więcej można zastosować za pośrednictwem tej warstwy, takie jak złożone dupleksu i niezawodna obsługa komunikatów.</span><span class="sxs-lookup"><span data-stu-id="06eef-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06eef-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06eef-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="06eef-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="06eef-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="06eef-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="06eef-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="06eef-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="06eef-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="06eef-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="06eef-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
