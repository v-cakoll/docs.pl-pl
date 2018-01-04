---
title: '&lt;niestandardowe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bcab1e8361448abfe14db8ac38a924c656b9065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="b77ab-102">&lt;niestandardowe&gt;</span><span class="sxs-lookup"><span data-stu-id="b77ab-102">&lt;custom&gt;</span></span>
<span data-ttu-id="b77ab-103">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="b77ab-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="b77ab-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b77ab-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b77ab-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b77ab-105">\<bindings></span></span>  
<span data-ttu-id="b77ab-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="b77ab-106">\<netPeerBinding></span></span>  
<span data-ttu-id="b77ab-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b77ab-107">\<binding></span></span>  
<span data-ttu-id="b77ab-108">\<mechanizm rozpoznawania ></span><span class="sxs-lookup"><span data-stu-id="b77ab-108">\<resolver></span></span>  
<span data-ttu-id="b77ab-109">\<niestandardowe ></span><span class="sxs-lookup"><span data-stu-id="b77ab-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77ab-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b77ab-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b77ab-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b77ab-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b77ab-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b77ab-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b77ab-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b77ab-113">Attributes</span></span>  
  
|<span data-ttu-id="b77ab-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b77ab-114">Attribute</span></span>|<span data-ttu-id="b77ab-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b77ab-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="b77ab-116">Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który jest hostem równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="b77ab-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="b77ab-117">Ciąg określający typ równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="b77ab-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b77ab-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b77ab-118">Child Elements</span></span>  
  
|<span data-ttu-id="b77ab-119">Element</span><span class="sxs-lookup"><span data-stu-id="b77ab-119">Element</span></span>|<span data-ttu-id="b77ab-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b77ab-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b77ab-121">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="b77ab-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b77ab-122">Określa tożsamość mechanizmy rozpoznawania elementów równorzędnych niestandardowych skonfigurowanych z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="b77ab-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="b77ab-123">Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="b77ab-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="b77ab-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="b77ab-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b77ab-125">Kolekcja dla wiadomości SOAP nagłówka adresu obsługiwane przez program rozpoznawania nazw dla równorzędnej niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="b77ab-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b77ab-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b77ab-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b77ab-127">Element</span><span class="sxs-lookup"><span data-stu-id="b77ab-127">Element</span></span>|<span data-ttu-id="b77ab-128">Opis</span><span class="sxs-lookup"><span data-stu-id="b77ab-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b77ab-129">\<mechanizm rozpoznawania ></span><span class="sxs-lookup"><span data-stu-id="b77ab-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="b77ab-130">Program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego ID siatki do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="b77ab-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b77ab-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b77ab-131">Remarks</span></span>  
 <span data-ttu-id="b77ab-132">Ten element definiuje ustawienia podstawowe dla równorzędnej niestandardowej usługi rozpoznawania nazw, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę, a wszystkie ustawienia określone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="b77ab-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="b77ab-133">Aby uzyskać więcej informacji na temat tworzenia niestandardowego programu rozpoznawania nazw, zobacz [Dodawanie niestandardowego programu rozpoznawania nazw dla aplikacji PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="b77ab-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77ab-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b77ab-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="b77ab-135">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b77ab-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="b77ab-136">Dodawanie do aplikacji PeerChannel niestandardowego programu rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="b77ab-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
