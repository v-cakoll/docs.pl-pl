---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 18359e871feed17a11006d0b2998907faf25c158
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106590"
---
# <a name="custom"></a><span data-ttu-id="7d596-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="7d596-101">\<custom></span></span>
<span data-ttu-id="7d596-102">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="7d596-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="7d596-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d596-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7d596-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7d596-104">\<bindings></span></span>  
<span data-ttu-id="7d596-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="7d596-105">\<netPeerBinding></span></span>  
<span data-ttu-id="7d596-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7d596-106">\<binding></span></span>  
<span data-ttu-id="7d596-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="7d596-107">\<resolver></span></span>  
<span data-ttu-id="7d596-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="7d596-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d596-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d596-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d596-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d596-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d596-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d596-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d596-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d596-112">Attributes</span></span>  
  
|<span data-ttu-id="7d596-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d596-113">Attribute</span></span>|<span data-ttu-id="7d596-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d596-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="7d596-115">Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który jest hostem równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="7d596-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="7d596-116">Ciąg, który określa typ równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="7d596-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d596-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d596-117">Child Elements</span></span>  
  
|<span data-ttu-id="7d596-118">Element</span><span class="sxs-lookup"><span data-stu-id="7d596-118">Element</span></span>|<span data-ttu-id="7d596-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7d596-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d596-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="7d596-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7d596-121">Określa tożsamość mechanizmy rozpoznawania elementów równorzędnych niestandardowe skonfigurowane z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="7d596-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="7d596-122">Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="7d596-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="7d596-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="7d596-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="7d596-124">Kolekcja nagłówka adres używany dla wiadomości protokołu SOAP, obsługiwane przez program rozpoznawania nazw dla równorzędnej niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="7d596-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d596-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d596-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7d596-126">Element</span><span class="sxs-lookup"><span data-stu-id="7d596-126">Element</span></span>|<span data-ttu-id="7d596-127">Opis</span><span class="sxs-lookup"><span data-stu-id="7d596-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d596-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="7d596-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="7d596-129">Program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego siatki identyfikator do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="7d596-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d596-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d596-130">Remarks</span></span>  
 <span data-ttu-id="7d596-131">Ten element definiuje ustawienia podstawowe dla równorzędnej niestandardowej usługi rozpoznawania nazw, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę, a także ustawienia określonego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7d596-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="7d596-132">Aby uzyskać więcej informacji na temat tworzenia niestandardowego mechanizmu, zobacz [Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7d596-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d596-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d596-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="7d596-134">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="7d596-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="7d596-135">[Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7d596-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
