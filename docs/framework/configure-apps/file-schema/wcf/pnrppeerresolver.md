---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783282"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="30e42-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="30e42-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="30e42-102">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="30e42-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="30e42-103">Ten element jest opcjonalny, ponieważ PNRP jest domyślny mechanizm rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="30e42-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="30e42-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30e42-104">\<system.serviceModel></span></span>  
<span data-ttu-id="30e42-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="30e42-105">\<bindings></span></span>  
<span data-ttu-id="30e42-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="30e42-106">\<customBinding></span></span>  
<span data-ttu-id="30e42-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="30e42-107">\<binding></span></span>  
<span data-ttu-id="30e42-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="30e42-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e42-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="30e42-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30e42-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30e42-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30e42-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30e42-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30e42-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30e42-112">Attributes</span></span>  
  
|<span data-ttu-id="30e42-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="30e42-113">Attribute</span></span>|<span data-ttu-id="30e42-114">Opis</span><span class="sxs-lookup"><span data-stu-id="30e42-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30e42-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="30e42-115">resolverType</span></span>|<span data-ttu-id="30e42-116">Ciąg, który określa rozpoznawania nazw ma być używany.</span><span class="sxs-lookup"><span data-stu-id="30e42-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="30e42-117">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="30e42-117">This attribute is optional.</span></span> <span data-ttu-id="30e42-118">Jeśli nie jest ustawiona lub jest ustawiony na pusty ciąg, jest używany protokół PNRP.</span><span class="sxs-lookup"><span data-stu-id="30e42-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30e42-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30e42-119">Child Elements</span></span>  
 <span data-ttu-id="30e42-120">Brak</span><span class="sxs-lookup"><span data-stu-id="30e42-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30e42-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30e42-121">Parent Elements</span></span>  
  
|<span data-ttu-id="30e42-122">Element</span><span class="sxs-lookup"><span data-stu-id="30e42-122">Element</span></span>|<span data-ttu-id="30e42-123">Opis</span><span class="sxs-lookup"><span data-stu-id="30e42-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30e42-124">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="30e42-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="30e42-125">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="30e42-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="30e42-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="30e42-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="30e42-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30e42-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="30e42-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="30e42-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="30e42-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="30e42-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30e42-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="30e42-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30e42-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="30e42-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="30e42-132">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="30e42-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
