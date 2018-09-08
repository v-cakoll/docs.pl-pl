---
title: '&lt;Program rozpoznawania nazw&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 48b6b6ca315f7ab63a8f7a64b97167fa04fe1e4e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133769"
---
# <a name="ltresolvergt"></a><span data-ttu-id="2bea9-102">&lt;Program rozpoznawania nazw&gt;</span><span class="sxs-lookup"><span data-stu-id="2bea9-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="2bea9-103">Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego siatki identyfikator do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="2bea9-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="2bea9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2bea9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2bea9-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2bea9-105">\<bindings></span></span>  
<span data-ttu-id="2bea9-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="2bea9-106">\<netPeerBinding></span></span>  
<span data-ttu-id="2bea9-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2bea9-107">\<binding></span></span>  
<span data-ttu-id="2bea9-108">\<Program rozpoznawania nazw ></span><span class="sxs-lookup"><span data-stu-id="2bea9-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bea9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bea9-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bea9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2bea9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2bea9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2bea9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bea9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2bea9-112">Attributes</span></span>  
  
|<span data-ttu-id="2bea9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2bea9-113">Attribute</span></span>|<span data-ttu-id="2bea9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2bea9-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="2bea9-115">Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw czy określone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2bea9-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="2bea9-116">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="2bea9-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="2bea9-117">Ciąg, który określa sposób odwołań są udostępniane między elementami równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="2bea9-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="2bea9-118">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="2bea9-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bea9-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2bea9-119">Child Elements</span></span>  
  
|<span data-ttu-id="2bea9-120">Element</span><span class="sxs-lookup"><span data-stu-id="2bea9-120">Element</span></span>|<span data-ttu-id="2bea9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2bea9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bea9-122">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="2bea9-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="2bea9-123">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="2bea9-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bea9-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2bea9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2bea9-125">Element</span><span class="sxs-lookup"><span data-stu-id="2bea9-125">Element</span></span>|<span data-ttu-id="2bea9-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2bea9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bea9-127">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2bea9-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2bea9-128">Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2bea9-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bea9-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2bea9-129">Remarks</span></span>  
 <span data-ttu-id="2bea9-130">Rozpoznawania nazw równorzędnych to Usługa odnajdywania używana przez kanały równorzędnej można znaleźć elementu równorzędnego węzłów, które uczestniczą w siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="2bea9-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="2bea9-131">Służy również "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne z siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="2bea9-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="2bea9-132">Aby uzyskać więcej informacji na temat mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="2bea9-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bea9-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bea9-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="2bea9-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="2bea9-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="2bea9-135">Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel</span><span class="sxs-lookup"><span data-stu-id="2bea9-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
