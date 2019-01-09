---
title: '&lt;Zakresy&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7afab700c2d9eb91ffe57bfefaf5864782a0af5f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145331"
---
# <a name="ltscopesgt"></a><span data-ttu-id="d919d-102">&lt;Zakresy&gt;</span><span class="sxs-lookup"><span data-stu-id="d919d-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="d919d-103">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="d919d-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="d919d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d919d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d919d-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d919d-105">\<behaviors></span></span>  
<span data-ttu-id="d919d-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d919d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d919d-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d919d-107">\<behavior></span></span>  
<span data-ttu-id="d919d-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d919d-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="d919d-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="d919d-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d919d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d919d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d919d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d919d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d919d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d919d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d919d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d919d-113">Attributes</span></span>  
 <span data-ttu-id="d919d-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d919d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d919d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d919d-115">Child Elements</span></span>  
  
|<span data-ttu-id="d919d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d919d-116">Attribute</span></span>|<span data-ttu-id="d919d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d919d-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d919d-118">\<add></span><span class="sxs-lookup"><span data-stu-id="d919d-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="d919d-119">Dodaje zakres informacji dla punktu końcowego, który może służyć w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="d919d-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d919d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d919d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d919d-121">Element</span><span class="sxs-lookup"><span data-stu-id="d919d-121">Element</span></span>|<span data-ttu-id="d919d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d919d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d919d-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d919d-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="d919d-124">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="d919d-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d919d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d919d-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
