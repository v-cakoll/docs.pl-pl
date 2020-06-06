---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738742"
---
# \<resolver>
<span data-ttu-id="b28a8-101">Określa równorzędny program rozpoznawania, który jest używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="b28a8-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="b28a8-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="b28a8-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b28a8-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b28a8-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b28a8-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b28a8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b28a8-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b28a8-105">Attributes</span></span>  
  
|<span data-ttu-id="b28a8-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b28a8-106">Attribute</span></span>|<span data-ttu-id="b28a8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b28a8-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="b28a8-108">Ciąg określający, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest zależne od protokołu PNRP, niestandardowym programem rozpoznawania nazw czy określane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="b28a8-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="b28a8-109">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .</span><span class="sxs-lookup"><span data-stu-id="b28a8-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="b28a8-110">Ciąg określający sposób, w jaki odwołania są współużytkowane przez elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="b28a8-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="b28a8-111">Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .</span><span class="sxs-lookup"><span data-stu-id="b28a8-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b28a8-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b28a8-112">Child Elements</span></span>  
  
|<span data-ttu-id="b28a8-113">Element</span><span class="sxs-lookup"><span data-stu-id="b28a8-113">Element</span></span>|<span data-ttu-id="b28a8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b28a8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="b28a8-115">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b28a8-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b28a8-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b28a8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b28a8-117">Element</span><span class="sxs-lookup"><span data-stu-id="b28a8-117">Element</span></span>|<span data-ttu-id="b28a8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b28a8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="b28a8-119">Definiuje wszystkie możliwości powiązań [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b28a8-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b28a8-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b28a8-120">Remarks</span></span>  
 <span data-ttu-id="b28a8-121">Program rozpoznawania nazw równorzędnych to usługa odnajdywania używana przez kanały równorzędne do znajdowania węzłów równorzędnych, które uczestniczą w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="b28a8-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="b28a8-122">Jest również używany do "Zarejestruj" węzeł z siatką równorzędną, mechanizm, za pomocą którego węzeł równorzędny jest znany i dostępny w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="b28a8-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="b28a8-123">Aby uzyskać więcej informacji na temat rozpoznawania elementów równorzędnych, zobacz [rozpoznawanie elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="b28a8-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28a8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b28a8-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="b28a8-125">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b28a8-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="b28a8-126">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b28a8-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
