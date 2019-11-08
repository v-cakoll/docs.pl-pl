---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738742"
---
# <a name="resolver"></a><span data-ttu-id="4a132-101">> \<programu rozpoznawania</span><span class="sxs-lookup"><span data-stu-id="4a132-101">\<resolver></span></span>
<span data-ttu-id="4a132-102">Określa równorzędny program rozpoznawania, który jest używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="4a132-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="4a132-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4a132-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4a132-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="4a132-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4a132-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="4a132-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4a132-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetPeerTcpBinding**](netpeertcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="4a132-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="4a132-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="4a132-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4a132-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<rozpoznawania >**</span><span class="sxs-lookup"><span data-stu-id="4a132-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a132-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a132-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a132-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a132-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a132-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a132-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a132-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a132-112">Attributes</span></span>  
  
|<span data-ttu-id="4a132-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a132-113">Attribute</span></span>|<span data-ttu-id="4a132-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4a132-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4a132-115">Ciąg określający, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest zależne od protokołu PNRP, niestandardowym programem rozpoznawania nazw czy określane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4a132-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="4a132-116">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="4a132-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="4a132-117">Ciąg określający sposób, w jaki odwołania są współużytkowane przez elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="4a132-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="4a132-118">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="4a132-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a132-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a132-119">Child Elements</span></span>  
  
|<span data-ttu-id="4a132-120">Element</span><span class="sxs-lookup"><span data-stu-id="4a132-120">Element</span></span>|<span data-ttu-id="4a132-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4a132-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a132-122">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="4a132-122">\<headers></span></span>](headers.md)|<span data-ttu-id="4a132-123">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="4a132-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a132-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a132-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4a132-125">Element</span><span class="sxs-lookup"><span data-stu-id="4a132-125">Element</span></span>|<span data-ttu-id="4a132-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4a132-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a132-127">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="4a132-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="4a132-128">Definiuje wszystkie możliwości powiązań [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4a132-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a132-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a132-129">Remarks</span></span>  
 <span data-ttu-id="4a132-130">Program rozpoznawania nazw równorzędnych to usługa odnajdywania używana przez kanały równorzędne do znajdowania węzłów równorzędnych, które uczestniczą w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="4a132-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="4a132-131">Jest również używany do "Zarejestruj" węzeł z siatką równorzędną, mechanizm, za pomocą którego węzeł równorzędny jest znany i dostępny w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="4a132-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="4a132-132">Aby uzyskać więcej informacji na temat rozpoznawania elementów równorzędnych, zobacz [rozpoznawanie elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="4a132-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a132-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a132-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="4a132-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="4a132-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="4a132-135">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4a132-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
