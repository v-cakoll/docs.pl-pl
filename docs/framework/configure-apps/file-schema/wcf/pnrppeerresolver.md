---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="a2f35-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="a2f35-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="a2f35-103">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="a2f35-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="a2f35-104">Ten element jest opcjonalny, ponieważ usługa PNRP jest domyślny program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="a2f35-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="a2f35-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a2f35-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a2f35-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a2f35-106">\<bindings></span></span>  
<span data-ttu-id="a2f35-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a2f35-107">\<customBinding></span></span>  
<span data-ttu-id="a2f35-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a2f35-108">\<binding></span></span>  
<span data-ttu-id="a2f35-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="a2f35-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f35-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2f35-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f35-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2f35-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a2f35-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2f35-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f35-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2f35-113">Attributes</span></span>  
  
|<span data-ttu-id="a2f35-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2f35-114">Attribute</span></span>|<span data-ttu-id="a2f35-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a2f35-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2f35-116">Element resolverType</span><span class="sxs-lookup"><span data-stu-id="a2f35-116">resolverType</span></span>|<span data-ttu-id="a2f35-117">Ciąg, który określa mechanizm rozpoznawania do użycia.</span><span class="sxs-lookup"><span data-stu-id="a2f35-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="a2f35-118">Ten atrybut jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a2f35-118">This attribute is optional.</span></span> <span data-ttu-id="a2f35-119">Jeśli nie jest ustawiona lub jest ustawiona na pusty ciąg, jest używana usługa PNRP.</span><span class="sxs-lookup"><span data-stu-id="a2f35-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f35-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2f35-120">Child Elements</span></span>  
 <span data-ttu-id="a2f35-121">Brak</span><span class="sxs-lookup"><span data-stu-id="a2f35-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f35-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2f35-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f35-123">Element</span><span class="sxs-lookup"><span data-stu-id="a2f35-123">Element</span></span>|<span data-ttu-id="a2f35-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a2f35-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2f35-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a2f35-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a2f35-126">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a2f35-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2f35-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2f35-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2f35-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2f35-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a2f35-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a2f35-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a2f35-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a2f35-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a2f35-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a2f35-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a2f35-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a2f35-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a2f35-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a2f35-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
