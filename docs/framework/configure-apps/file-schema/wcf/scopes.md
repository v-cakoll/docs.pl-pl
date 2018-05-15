---
title: '&lt;Zakresy&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7e2dda0d0def4d1f90bf1b4dbf54f18983355222
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltscopesgt"></a><span data-ttu-id="732f3-102">&lt;Zakresy&gt;</span><span class="sxs-lookup"><span data-stu-id="732f3-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="732f3-103">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="732f3-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="732f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="732f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="732f3-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="732f3-105">\<behaviors></span></span>  
<span data-ttu-id="732f3-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="732f3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="732f3-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="732f3-107">\<behavior></span></span>  
<span data-ttu-id="732f3-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="732f3-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="732f3-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="732f3-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="732f3-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="732f3-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="732f3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="732f3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="732f3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="732f3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="732f3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="732f3-113">Attributes</span></span>  
 <span data-ttu-id="732f3-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="732f3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="732f3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="732f3-115">Child Elements</span></span>  
  
|<span data-ttu-id="732f3-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="732f3-116">Attribute</span></span>|<span data-ttu-id="732f3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="732f3-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="732f3-118">\<add></span><span class="sxs-lookup"><span data-stu-id="732f3-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="732f3-119">Dodaje zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="732f3-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="732f3-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="732f3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="732f3-121">Element</span><span class="sxs-lookup"><span data-stu-id="732f3-121">Element</span></span>|<span data-ttu-id="732f3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="732f3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="732f3-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="732f3-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="732f3-124">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="732f3-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="732f3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="732f3-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
