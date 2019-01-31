---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f98c358cc9891e9d7223d280fc8e50c19aad9759
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260657"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="b3a9b-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="b3a9b-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="b3a9b-102">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="b3a9b-103">Ten element jest opcjonalny, ponieważ PNRP jest domyślny mechanizm rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="b3a9b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b3a9b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b3a9b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b3a9b-105">\<bindings></span></span>  
<span data-ttu-id="b3a9b-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b3a9b-106">\<customBinding></span></span>  
<span data-ttu-id="b3a9b-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b3a9b-107">\<binding></span></span>  
<span data-ttu-id="b3a9b-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="b3a9b-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a9b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3a9b-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3a9b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3a9b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b3a9b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3a9b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3a9b-112">Attributes</span></span>  
  
|<span data-ttu-id="b3a9b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3a9b-113">Attribute</span></span>|<span data-ttu-id="b3a9b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b3a9b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3a9b-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="b3a9b-115">resolverType</span></span>|<span data-ttu-id="b3a9b-116">Ciąg, który określa rozpoznawania nazw ma być używany.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="b3a9b-117">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-117">This attribute is optional.</span></span> <span data-ttu-id="b3a9b-118">Jeśli nie jest ustawiona lub jest ustawiony na pusty ciąg, jest używany protokół PNRP.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3a9b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3a9b-119">Child Elements</span></span>  
 <span data-ttu-id="b3a9b-120">Brak</span><span class="sxs-lookup"><span data-stu-id="b3a9b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3a9b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3a9b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b3a9b-122">Element</span><span class="sxs-lookup"><span data-stu-id="b3a9b-122">Element</span></span>|<span data-ttu-id="b3a9b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b3a9b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3a9b-124">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b3a9b-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b3a9b-125">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b3a9b-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3a9b-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3a9b-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b3a9b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3a9b-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b3a9b-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b3a9b-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b3a9b-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b3a9b-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b3a9b-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b3a9b-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b3a9b-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b3a9b-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="b3a9b-132">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b3a9b-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
