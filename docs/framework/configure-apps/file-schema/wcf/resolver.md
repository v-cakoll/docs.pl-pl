---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 39dcb868bd3ff25451509616e1dac7d41f94cfa1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075882"
---
# <a name="resolver"></a><span data-ttu-id="e22ab-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e22ab-101">\<resolver></span></span>
<span data-ttu-id="e22ab-102">Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego siatki identyfikator do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="e22ab-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="e22ab-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e22ab-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e22ab-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e22ab-104">\<bindings></span></span>  
<span data-ttu-id="e22ab-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="e22ab-105">\<netPeerBinding></span></span>  
<span data-ttu-id="e22ab-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e22ab-106">\<binding></span></span>  
<span data-ttu-id="e22ab-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e22ab-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e22ab-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e22ab-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e22ab-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e22ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e22ab-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e22ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e22ab-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e22ab-111">Attributes</span></span>  
  
|<span data-ttu-id="e22ab-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e22ab-112">Attribute</span></span>|<span data-ttu-id="e22ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e22ab-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="e22ab-114">Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw czy określone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e22ab-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="e22ab-115">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="e22ab-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="e22ab-116">Ciąg, który określa sposób odwołań są udostępniane między elementami równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="e22ab-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="e22ab-117">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="e22ab-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e22ab-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e22ab-118">Child Elements</span></span>  
  
|<span data-ttu-id="e22ab-119">Element</span><span class="sxs-lookup"><span data-stu-id="e22ab-119">Element</span></span>|<span data-ttu-id="e22ab-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e22ab-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e22ab-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="e22ab-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="e22ab-122">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="e22ab-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e22ab-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e22ab-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e22ab-124">Element</span><span class="sxs-lookup"><span data-stu-id="e22ab-124">Element</span></span>|<span data-ttu-id="e22ab-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e22ab-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e22ab-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e22ab-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e22ab-127">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e22ab-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e22ab-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e22ab-128">Remarks</span></span>  
 <span data-ttu-id="e22ab-129">Rozpoznawania nazw równorzędnych to Usługa odnajdywania używana przez kanały równorzędnej można znaleźć elementu równorzędnego węzłów, które uczestniczą w siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e22ab-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="e22ab-130">Służy również "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne z siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e22ab-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="e22ab-131">Aby uzyskać więcej informacji na temat mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="e22ab-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22ab-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e22ab-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="e22ab-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="e22ab-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="e22ab-134">Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel</span><span class="sxs-lookup"><span data-stu-id="e22ab-134">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
