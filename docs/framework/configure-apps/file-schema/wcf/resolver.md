---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934217"
---
# <a name="resolver"></a><span data-ttu-id="354e5-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="354e5-101">\<resolver></span></span>
<span data-ttu-id="354e5-102">Określa równorzędny program rozpoznawania, który jest używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="354e5-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="354e5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="354e5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="354e5-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="354e5-104">\<bindings></span></span>  
<span data-ttu-id="354e5-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="354e5-105">\<netPeerBinding></span></span>  
<span data-ttu-id="354e5-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="354e5-106">\<binding></span></span>  
<span data-ttu-id="354e5-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="354e5-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354e5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="354e5-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="354e5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="354e5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="354e5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="354e5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="354e5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="354e5-111">Attributes</span></span>  
  
|<span data-ttu-id="354e5-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="354e5-112">Attribute</span></span>|<span data-ttu-id="354e5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="354e5-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="354e5-114">Ciąg określający, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest zależne od protokołu PNRP, niestandardowym programem rozpoznawania nazw czy określane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="354e5-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="354e5-115">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="354e5-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="354e5-116">Ciąg określający sposób, w jaki odwołania są współużytkowane przez elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="354e5-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="354e5-117">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="354e5-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="354e5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="354e5-118">Child Elements</span></span>  
  
|<span data-ttu-id="354e5-119">Element</span><span class="sxs-lookup"><span data-stu-id="354e5-119">Element</span></span>|<span data-ttu-id="354e5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="354e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="354e5-121">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="354e5-121">\<headers></span></span>](headers.md)|<span data-ttu-id="354e5-122">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="354e5-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="354e5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="354e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="354e5-124">Element</span><span class="sxs-lookup"><span data-stu-id="354e5-124">Element</span></span>|<span data-ttu-id="354e5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="354e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="354e5-126">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="354e5-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="354e5-127">Definiuje wszystkie możliwości [ \<powiązań NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="354e5-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="354e5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="354e5-128">Remarks</span></span>  
 <span data-ttu-id="354e5-129">Program rozpoznawania nazw równorzędnych to usługa odnajdywania używana przez kanały równorzędne do znajdowania węzłów równorzędnych, które uczestniczą w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="354e5-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="354e5-130">Jest również używany do "Zarejestruj" węzeł z siatką równorzędną, mechanizm, za pomocą którego węzeł równorzędny jest znany i dostępny w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="354e5-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="354e5-131">Aby uzyskać więcej informacji na temat rozpoznawania elementów równorzędnych, zobacz [rozpoznawanie elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="354e5-131">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354e5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="354e5-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="354e5-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="354e5-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="354e5-134">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="354e5-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
