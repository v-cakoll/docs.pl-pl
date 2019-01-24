---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 2a3e0de2bb5d2ed022f53aa5e498f338eaf56ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578604"
---
# <a name="ltresolvergt"></a><span data-ttu-id="4390d-102">&lt;resolver&gt;</span><span class="sxs-lookup"><span data-stu-id="4390d-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="4390d-103">Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego siatki identyfikator do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="4390d-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="4390d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4390d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4390d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4390d-105">\<bindings></span></span>  
<span data-ttu-id="4390d-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="4390d-106">\<netPeerBinding></span></span>  
<span data-ttu-id="4390d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4390d-107">\<binding></span></span>  
<span data-ttu-id="4390d-108">\<resolver></span><span class="sxs-lookup"><span data-stu-id="4390d-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4390d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4390d-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4390d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4390d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4390d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4390d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4390d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4390d-112">Attributes</span></span>  
  
|<span data-ttu-id="4390d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4390d-113">Attribute</span></span>|<span data-ttu-id="4390d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4390d-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4390d-115">Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw czy określone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4390d-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="4390d-116">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="4390d-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="4390d-117">Ciąg, który określa sposób odwołań są udostępniane między elementami równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="4390d-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="4390d-118">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="4390d-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4390d-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4390d-119">Child Elements</span></span>  
  
|<span data-ttu-id="4390d-120">Element</span><span class="sxs-lookup"><span data-stu-id="4390d-120">Element</span></span>|<span data-ttu-id="4390d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4390d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4390d-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="4390d-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="4390d-123">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="4390d-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4390d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4390d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4390d-125">Element</span><span class="sxs-lookup"><span data-stu-id="4390d-125">Element</span></span>|<span data-ttu-id="4390d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4390d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4390d-127">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4390d-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4390d-128">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4390d-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4390d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4390d-129">Remarks</span></span>  
 <span data-ttu-id="4390d-130">Rozpoznawania nazw równorzędnych to Usługa odnajdywania używana przez kanały równorzędnej można znaleźć elementu równorzędnego węzłów, które uczestniczą w siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="4390d-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="4390d-131">Służy również "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne z siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="4390d-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="4390d-132">Aby uzyskać więcej informacji na temat mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="4390d-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4390d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4390d-133">See also</span></span>
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="4390d-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="4390d-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="4390d-135">Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel</span><span class="sxs-lookup"><span data-stu-id="4390d-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
