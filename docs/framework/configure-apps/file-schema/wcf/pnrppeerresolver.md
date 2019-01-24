---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: cefd46d7810149264f9c431a212da0f3f51f8186
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577649"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="c5fe2-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="c5fe2-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="c5fe2-103">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="c5fe2-104">Ten element jest opcjonalny, ponieważ PNRP jest domyślny mechanizm rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="c5fe2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5fe2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c5fe2-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c5fe2-106">\<bindings></span></span>  
<span data-ttu-id="c5fe2-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c5fe2-107">\<customBinding></span></span>  
<span data-ttu-id="c5fe2-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c5fe2-108">\<binding></span></span>  
<span data-ttu-id="c5fe2-109">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="c5fe2-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5fe2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5fe2-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5fe2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5fe2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c5fe2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5fe2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5fe2-113">Attributes</span></span>  
  
|<span data-ttu-id="c5fe2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5fe2-114">Attribute</span></span>|<span data-ttu-id="c5fe2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c5fe2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5fe2-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="c5fe2-116">resolverType</span></span>|<span data-ttu-id="c5fe2-117">Ciąg, który określa rozpoznawania nazw ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="c5fe2-118">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-118">This attribute is optional.</span></span> <span data-ttu-id="c5fe2-119">Jeśli nie jest ustawiona lub jest ustawiony na pusty ciąg, jest używany protokół PNRP.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5fe2-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5fe2-120">Child Elements</span></span>  
 <span data-ttu-id="c5fe2-121">Brak</span><span class="sxs-lookup"><span data-stu-id="c5fe2-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5fe2-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5fe2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c5fe2-123">Element</span><span class="sxs-lookup"><span data-stu-id="c5fe2-123">Element</span></span>|<span data-ttu-id="c5fe2-124">Opis</span><span class="sxs-lookup"><span data-stu-id="c5fe2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5fe2-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c5fe2-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c5fe2-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c5fe2-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5fe2-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5fe2-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="c5fe2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5fe2-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c5fe2-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c5fe2-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c5fe2-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c5fe2-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c5fe2-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c5fe2-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c5fe2-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c5fe2-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c5fe2-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="c5fe2-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
