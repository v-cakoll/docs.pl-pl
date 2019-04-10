---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213080"
---
# <a name="scopes"></a><span data-ttu-id="d02bd-101">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="d02bd-101">\<scopes></span></span>
<span data-ttu-id="d02bd-102">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="d02bd-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="d02bd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d02bd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d02bd-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d02bd-104">\<behaviors></span></span>  
<span data-ttu-id="d02bd-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d02bd-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="d02bd-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d02bd-106">\<behavior></span></span>  
<span data-ttu-id="d02bd-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="d02bd-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="d02bd-108">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="d02bd-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d02bd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d02bd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d02bd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d02bd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d02bd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d02bd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d02bd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d02bd-112">Attributes</span></span>  
 <span data-ttu-id="d02bd-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="d02bd-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d02bd-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d02bd-114">Child Elements</span></span>  
  
|<span data-ttu-id="d02bd-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d02bd-115">Attribute</span></span>|<span data-ttu-id="d02bd-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d02bd-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d02bd-117">\<add></span><span class="sxs-lookup"><span data-stu-id="d02bd-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="d02bd-118">Dodaje zakres informacji dla punktu końcowego, który może służyć w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="d02bd-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d02bd-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d02bd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d02bd-120">Element</span><span class="sxs-lookup"><span data-stu-id="d02bd-120">Element</span></span>|<span data-ttu-id="d02bd-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d02bd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d02bd-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="d02bd-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="d02bd-123">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="d02bd-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d02bd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d02bd-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
