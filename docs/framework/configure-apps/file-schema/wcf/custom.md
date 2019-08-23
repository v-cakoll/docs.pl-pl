---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925955"
---
# <a name="custom"></a><span data-ttu-id="be370-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="be370-101">\<custom></span></span>
<span data-ttu-id="be370-102">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="be370-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="be370-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="be370-103">\<system.serviceModel></span></span>  
<span data-ttu-id="be370-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="be370-104">\<bindings></span></span>  
<span data-ttu-id="be370-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="be370-105">\<netPeerBinding></span></span>  
<span data-ttu-id="be370-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="be370-106">\<binding></span></span>  
<span data-ttu-id="be370-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="be370-107">\<resolver></span></span>  
<span data-ttu-id="be370-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="be370-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be370-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="be370-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be370-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="be370-110">Attributes and Elements</span></span>  
 <span data-ttu-id="be370-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="be370-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be370-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="be370-112">Attributes</span></span>  
  
|<span data-ttu-id="be370-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="be370-113">Attribute</span></span>|<span data-ttu-id="be370-114">Opis</span><span class="sxs-lookup"><span data-stu-id="be370-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="be370-115">Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który hostuje niestandardową usługę rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="be370-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="be370-116">Ciąg określający typ niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="be370-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be370-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="be370-117">Child Elements</span></span>  
  
|<span data-ttu-id="be370-118">Element</span><span class="sxs-lookup"><span data-stu-id="be370-118">Element</span></span>|<span data-ttu-id="be370-119">Opis</span><span class="sxs-lookup"><span data-stu-id="be370-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be370-120">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="be370-120">\<identity></span></span>](identity.md)|<span data-ttu-id="be370-121">Określa tożsamość niestandardowych resolverów równorzędnych skonfigurowanych przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="be370-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="be370-122">Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="be370-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="be370-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="be370-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="be370-124">Kolekcja nagłówka adresu używana dla komunikatów SOAP obsłużonych przez niestandardowy program rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="be370-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be370-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="be370-125">Parent Elements</span></span>  
  
|<span data-ttu-id="be370-126">Element</span><span class="sxs-lookup"><span data-stu-id="be370-126">Element</span></span>|<span data-ttu-id="be370-127">Opis</span><span class="sxs-lookup"><span data-stu-id="be370-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be370-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="be370-128">\<resolver></span></span>](resolver.md)|<span data-ttu-id="be370-129">Równorzędny program rozpoznawania używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="be370-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be370-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be370-130">Remarks</span></span>  
 <span data-ttu-id="be370-131">Ten element definiuje podstawowe ustawienia dla niestandardowej usługi rozpoznawania elementów równorzędnych, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę i wszystkie określone ustawienia powiązań.</span><span class="sxs-lookup"><span data-stu-id="be370-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="be370-132">Aby uzyskać więcej informacji na temat tworzenia niestandardowego programu rozpoznawania nazw, zobacz [Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="be370-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be370-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be370-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="be370-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="be370-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="be370-135">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="be370-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
