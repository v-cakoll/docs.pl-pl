---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: eee6382c578648866045fd9b283454d9e0e76fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275031"
---
# <a name="scopes"></a><span data-ttu-id="8d765-101">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="8d765-101">\<scopes></span></span>
<span data-ttu-id="8d765-102">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="8d765-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="8d765-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8d765-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d765-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="8d765-104">\<behaviors></span></span>  
<span data-ttu-id="8d765-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8d765-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="8d765-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="8d765-106">\<behavior></span></span>  
<span data-ttu-id="8d765-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="8d765-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="8d765-108">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="8d765-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d765-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d765-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d765-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d765-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d765-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d765-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d765-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d765-112">Attributes</span></span>  
 <span data-ttu-id="8d765-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="8d765-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d765-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d765-114">Child Elements</span></span>  
  
|<span data-ttu-id="8d765-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d765-115">Attribute</span></span>|<span data-ttu-id="8d765-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8d765-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8d765-117">\<add></span><span class="sxs-lookup"><span data-stu-id="8d765-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="8d765-118">Dodaje zakres informacji dla punktu końcowego, który może służyć w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="8d765-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d765-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d765-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d765-120">Element</span><span class="sxs-lookup"><span data-stu-id="8d765-120">Element</span></span>|<span data-ttu-id="8d765-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8d765-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d765-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="8d765-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="8d765-123">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="8d765-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d765-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d765-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
