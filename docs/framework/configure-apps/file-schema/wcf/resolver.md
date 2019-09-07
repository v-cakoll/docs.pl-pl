---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: fb974492dee6b2a4244cedc06e3f5e40334dd02a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399980"
---
# <a name="resolver"></a><span data-ttu-id="6b194-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="6b194-101">\<resolver></span></span>
<span data-ttu-id="6b194-102">Określa równorzędny program rozpoznawania, który jest używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="6b194-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="6b194-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b194-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b194-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b194-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b194-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6b194-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6b194-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6b194-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="6b194-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="6b194-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6b194-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> mechanizmu rozwiązywania konfliktów**</span><span class="sxs-lookup"><span data-stu-id="6b194-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b194-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b194-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b194-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b194-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b194-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b194-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b194-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b194-112">Attributes</span></span>  
  
|<span data-ttu-id="6b194-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6b194-113">Attribute</span></span>|<span data-ttu-id="6b194-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6b194-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6b194-115">Ciąg określający, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest zależne od protokołu PNRP, niestandardowym programem rozpoznawania nazw czy określane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="6b194-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="6b194-116">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="6b194-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="6b194-117">Ciąg określający sposób, w jaki odwołania są współużytkowane przez elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="6b194-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="6b194-118">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="6b194-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b194-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b194-119">Child Elements</span></span>  
  
|<span data-ttu-id="6b194-120">Element</span><span class="sxs-lookup"><span data-stu-id="6b194-120">Element</span></span>|<span data-ttu-id="6b194-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6b194-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b194-122">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="6b194-122">\<headers></span></span>](headers.md)|<span data-ttu-id="6b194-123">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="6b194-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b194-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b194-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6b194-125">Element</span><span class="sxs-lookup"><span data-stu-id="6b194-125">Element</span></span>|<span data-ttu-id="6b194-126">Opis</span><span class="sxs-lookup"><span data-stu-id="6b194-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b194-127">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6b194-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="6b194-128">Definiuje wszystkie możliwości [ \<powiązań NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6b194-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b194-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b194-129">Remarks</span></span>  
 <span data-ttu-id="6b194-130">Program rozpoznawania nazw równorzędnych to usługa odnajdywania używana przez kanały równorzędne do znajdowania węzłów równorzędnych, które uczestniczą w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="6b194-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="6b194-131">Jest również używany do "Zarejestruj" węzeł z siatką równorzędną, mechanizm, za pomocą którego węzeł równorzędny jest znany i dostępny w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="6b194-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="6b194-132">Aby uzyskać więcej informacji na temat rozpoznawania elementów równorzędnych, zobacz [rozpoznawanie elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="6b194-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b194-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b194-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="6b194-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="6b194-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="6b194-135">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6b194-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
