---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933802"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="7a616-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="7a616-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="7a616-102">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="7a616-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="7a616-103">Ten element jest opcjonalny, ponieważ protokół PNRP jest domyślnym programem rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="7a616-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="7a616-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7a616-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7a616-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="7a616-105">\<bindings></span></span>  
<span data-ttu-id="7a616-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7a616-106">\<customBinding></span></span>  
<span data-ttu-id="7a616-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7a616-107">\<binding></span></span>  
<span data-ttu-id="7a616-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="7a616-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a616-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a616-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a616-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a616-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7a616-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a616-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a616-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a616-112">Attributes</span></span>  
  
|<span data-ttu-id="7a616-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a616-113">Attribute</span></span>|<span data-ttu-id="7a616-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7a616-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a616-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="7a616-115">resolverType</span></span>|<span data-ttu-id="7a616-116">Ciąg określający, który mechanizm rozwiązywania konfliktów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="7a616-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="7a616-117">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7a616-117">This attribute is optional.</span></span> <span data-ttu-id="7a616-118">Jeśli nie jest ustawiona, lub jeśli jest ustawiona na pusty ciąg, używany jest protokół PNRP.</span><span class="sxs-lookup"><span data-stu-id="7a616-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a616-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a616-119">Child Elements</span></span>  
 <span data-ttu-id="7a616-120">Brak</span><span class="sxs-lookup"><span data-stu-id="7a616-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a616-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a616-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7a616-122">Element</span><span class="sxs-lookup"><span data-stu-id="7a616-122">Element</span></span>|<span data-ttu-id="7a616-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7a616-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a616-124">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7a616-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7a616-125">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a616-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a616-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a616-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="7a616-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a616-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7a616-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7a616-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a616-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="7a616-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7a616-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7a616-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7a616-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7a616-131">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="7a616-132">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="7a616-132">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
