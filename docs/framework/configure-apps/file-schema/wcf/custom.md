---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400464"
---
# <a name="custom"></a><span data-ttu-id="e2aaa-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="e2aaa-101">\<custom></span></span>
<span data-ttu-id="e2aaa-102">Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="e2aaa-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2aaa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2aaa-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e2aaa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e2aaa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e2aaa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e2aaa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e2aaa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="e2aaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="e2aaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e2aaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> mechanizmu rozwiązywania konfliktów**](resolver.md)</span><span class="sxs-lookup"><span data-stu-id="e2aaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)</span></span>\
<span data-ttu-id="e2aaa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> niestandardowe**</span><span class="sxs-lookup"><span data-stu-id="e2aaa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2aaa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2aaa-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2aaa-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e2aaa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2aaa-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2aaa-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2aaa-113">Attributes</span></span>  
  
|<span data-ttu-id="e2aaa-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e2aaa-114">Attribute</span></span>|<span data-ttu-id="e2aaa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e2aaa-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="e2aaa-116">Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który hostuje niestandardową usługę rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="e2aaa-117">Ciąg określający typ niestandardowej usługi rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2aaa-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2aaa-118">Child Elements</span></span>  
  
|<span data-ttu-id="e2aaa-119">Element</span><span class="sxs-lookup"><span data-stu-id="e2aaa-119">Element</span></span>|<span data-ttu-id="e2aaa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e2aaa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2aaa-121">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="e2aaa-121">\<identity></span></span>](identity.md)|<span data-ttu-id="e2aaa-122">Określa tożsamość niestandardowych resolverów równorzędnych skonfigurowanych przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="e2aaa-123">Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="e2aaa-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="e2aaa-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="e2aaa-125">Kolekcja nagłówka adresu używana dla komunikatów SOAP obsłużonych przez niestandardowy program rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2aaa-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2aaa-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e2aaa-127">Element</span><span class="sxs-lookup"><span data-stu-id="e2aaa-127">Element</span></span>|<span data-ttu-id="e2aaa-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e2aaa-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2aaa-129">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e2aaa-129">\<resolver></span></span>](resolver.md)|<span data-ttu-id="e2aaa-130">Równorzędny program rozpoznawania używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2aaa-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2aaa-131">Remarks</span></span>  
 <span data-ttu-id="e2aaa-132">Ten element definiuje podstawowe ustawienia dla niestandardowej usługi rozpoznawania elementów równorzędnych, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę i wszystkie określone ustawienia powiązań.</span><span class="sxs-lookup"><span data-stu-id="e2aaa-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="e2aaa-133">Aby uzyskać więcej informacji na temat tworzenia niestandardowego programu rozpoznawania nazw, zobacz [Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e2aaa-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2aaa-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2aaa-134">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="e2aaa-135">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="e2aaa-135">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="e2aaa-136">[Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e2aaa-136">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
