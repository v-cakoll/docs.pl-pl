---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f0874d38c3432f066d1bec5cc84f53e1f3730180
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="42b5b-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="42b5b-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="42b5b-103">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="42b5b-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="42b5b-104">Ten element jest opcjonalny, ponieważ usługa PNRP jest domyślny program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="42b5b-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="42b5b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="42b5b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="42b5b-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="42b5b-106">\<bindings></span></span>  
<span data-ttu-id="42b5b-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="42b5b-107">\<customBinding></span></span>  
<span data-ttu-id="42b5b-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="42b5b-108">\<binding></span></span>  
<span data-ttu-id="42b5b-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="42b5b-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b5b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="42b5b-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42b5b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="42b5b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="42b5b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="42b5b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42b5b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42b5b-113">Attributes</span></span>  
  
|<span data-ttu-id="42b5b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="42b5b-114">Attribute</span></span>|<span data-ttu-id="42b5b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="42b5b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42b5b-116">Element resolverType</span><span class="sxs-lookup"><span data-stu-id="42b5b-116">resolverType</span></span>|<span data-ttu-id="42b5b-117">Ciąg, który określa mechanizm rozpoznawania do użycia.</span><span class="sxs-lookup"><span data-stu-id="42b5b-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="42b5b-118">Ten atrybut jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="42b5b-118">This attribute is optional.</span></span> <span data-ttu-id="42b5b-119">Jeśli nie jest ustawiona lub jest ustawiona na pusty ciąg, jest używana usługa PNRP.</span><span class="sxs-lookup"><span data-stu-id="42b5b-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42b5b-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="42b5b-120">Child Elements</span></span>  
 <span data-ttu-id="42b5b-121">Brak</span><span class="sxs-lookup"><span data-stu-id="42b5b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42b5b-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42b5b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="42b5b-123">Element</span><span class="sxs-lookup"><span data-stu-id="42b5b-123">Element</span></span>|<span data-ttu-id="42b5b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="42b5b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42b5b-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="42b5b-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="42b5b-126">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="42b5b-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42b5b-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="42b5b-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="42b5b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42b5b-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="42b5b-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="42b5b-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42b5b-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="42b5b-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="42b5b-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="42b5b-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="42b5b-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="42b5b-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="42b5b-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="42b5b-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
