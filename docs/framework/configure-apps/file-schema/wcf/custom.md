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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="0af5e-102">&lt;niestandardowe&gt;</span><span class="sxs-lookup"><span data-stu-id="0af5e-102">&lt;custom&gt;</span></span>
<span data-ttu-id="0af5e-103">Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="0af5e-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="0af5e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0af5e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0af5e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0af5e-105">\<bindings></span></span>  
<span data-ttu-id="0af5e-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="0af5e-106">\<netPeerBinding></span></span>  
<span data-ttu-id="0af5e-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0af5e-107">\<binding></span></span>  
<span data-ttu-id="0af5e-108">\<mechanizm rozpoznawania ></span><span class="sxs-lookup"><span data-stu-id="0af5e-108">\<resolver></span></span>  
<span data-ttu-id="0af5e-109">\<niestandardowe ></span><span class="sxs-lookup"><span data-stu-id="0af5e-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af5e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0af5e-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0af5e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0af5e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0af5e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0af5e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0af5e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0af5e-113">Attributes</span></span>  
  
|<span data-ttu-id="0af5e-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0af5e-114">Attribute</span></span>|<span data-ttu-id="0af5e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0af5e-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="0af5e-116">Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który jest hostem równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="0af5e-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="0af5e-117">Ciąg określający typ równorzędnej niestandardowej usługi rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="0af5e-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0af5e-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0af5e-118">Child Elements</span></span>  
  
|<span data-ttu-id="0af5e-119">Element</span><span class="sxs-lookup"><span data-stu-id="0af5e-119">Element</span></span>|<span data-ttu-id="0af5e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0af5e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0af5e-121">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="0af5e-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0af5e-122">Określa tożsamość mechanizmy rozpoznawania elementów równorzędnych niestandardowych skonfigurowanych z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="0af5e-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="0af5e-123">Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="0af5e-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="0af5e-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="0af5e-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="0af5e-125">Kolekcja dla wiadomości SOAP nagłówka adresu obsługiwane przez program rozpoznawania nazw dla równorzędnej niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0af5e-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0af5e-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0af5e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0af5e-127">Element</span><span class="sxs-lookup"><span data-stu-id="0af5e-127">Element</span></span>|<span data-ttu-id="0af5e-128">Opis</span><span class="sxs-lookup"><span data-stu-id="0af5e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0af5e-129">\<mechanizm rozpoznawania ></span><span class="sxs-lookup"><span data-stu-id="0af5e-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="0af5e-130">Program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego ID siatki do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.</span><span class="sxs-lookup"><span data-stu-id="0af5e-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af5e-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0af5e-131">Remarks</span></span>  
 <span data-ttu-id="0af5e-132">Ten element definiuje ustawienia podstawowe dla równorzędnej niestandardowej usługi rozpoznawania nazw, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę, a wszystkie ustawienia określone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0af5e-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="0af5e-133">Aby uzyskać więcej informacji na temat tworzenia niestandardowego programu rozpoznawania nazw, zobacz [Dodawanie niestandardowego programu rozpoznawania nazw dla aplikacji PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="0af5e-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af5e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0af5e-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="0af5e-135">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="0af5e-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="0af5e-136">Dodawanie do aplikacji PeerChannel niestandardowego programu rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="0af5e-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
