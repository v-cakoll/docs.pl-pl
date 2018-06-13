---
title: '&lt;Program rozpoznawania nazw&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749026"
---
# <a name="ltresolvergt"></a><span data-ttu-id="a5d89-102">&lt;Program rozpoznawania nazw&gt;</span><span class="sxs-lookup"><span data-stu-id="a5d89-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="a5d89-103">Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego ID siatki do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="a5d89-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="a5d89-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a5d89-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a5d89-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a5d89-105">\<bindings></span></span>  
<span data-ttu-id="a5d89-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="a5d89-106">\<netPeerBinding></span></span>  
<span data-ttu-id="a5d89-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a5d89-107">\<binding></span></span>  
<span data-ttu-id="a5d89-108">\<mechanizm rozpoznawania ></span><span class="sxs-lookup"><span data-stu-id="a5d89-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d89-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5d89-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5d89-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5d89-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5d89-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5d89-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5d89-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5d89-112">Attributes</span></span>  
  
|<span data-ttu-id="a5d89-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5d89-113">Attribute</span></span>|<span data-ttu-id="a5d89-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5d89-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="a5d89-115">Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw, czy określone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a5d89-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="a5d89-116">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="a5d89-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="a5d89-117">Ciąg, który określa sposób według którego odwołania są współużytkowane przez elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="a5d89-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="a5d89-118">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="a5d89-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5d89-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5d89-119">Child Elements</span></span>  
  
|<span data-ttu-id="a5d89-120">Element</span><span class="sxs-lookup"><span data-stu-id="a5d89-120">Element</span></span>|<span data-ttu-id="a5d89-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a5d89-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5d89-122">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="a5d89-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="a5d89-123">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="a5d89-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5d89-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5d89-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a5d89-125">Element</span><span class="sxs-lookup"><span data-stu-id="a5d89-125">Element</span></span>|<span data-ttu-id="a5d89-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a5d89-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5d89-127">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a5d89-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a5d89-128">Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a5d89-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5d89-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5d89-129">Remarks</span></span>  
 <span data-ttu-id="a5d89-130">Nazwa elementu równorzędnego program rozpoznawania nazw odnajdywania usługa jest używana przez kanałów elementów równorzędnych można znaleźć elementu równorzędnego węzłów, które uczestniczą w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="a5d89-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="a5d89-131">Służy również do "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="a5d89-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="a5d89-132">Aby uzyskać więcej informacji dotyczących mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="a5d89-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d89-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5d89-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="a5d89-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a5d89-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="a5d89-135">Dodawanie do aplikacji PeerChannel niestandardowego programu rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="a5d89-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
