---
title: '&lt;zakresy&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b35696cbecb0badf397d6d48e7c97aae3d0232e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="81716-102">&lt;zakresy&gt;</span><span class="sxs-lookup"><span data-stu-id="81716-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="81716-103">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="81716-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="81716-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="81716-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81716-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="81716-105">\<behaviors></span></span>  
<span data-ttu-id="81716-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81716-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="81716-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="81716-107">\<behavior></span></span>  
<span data-ttu-id="81716-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="81716-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="81716-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="81716-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81716-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="81716-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81716-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="81716-111">Attributes and Elements</span></span>  
 <span data-ttu-id="81716-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81716-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81716-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="81716-113">Attributes</span></span>  
 <span data-ttu-id="81716-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="81716-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81716-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="81716-115">Child Elements</span></span>  
  
|<span data-ttu-id="81716-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="81716-116">Attribute</span></span>|<span data-ttu-id="81716-117">Opis</span><span class="sxs-lookup"><span data-stu-id="81716-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="81716-118">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="81716-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="81716-119">Dodaje zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="81716-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81716-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="81716-120">Parent Elements</span></span>  
  
|<span data-ttu-id="81716-121">Element</span><span class="sxs-lookup"><span data-stu-id="81716-121">Element</span></span>|<span data-ttu-id="81716-122">Opis</span><span class="sxs-lookup"><span data-stu-id="81716-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81716-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="81716-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="81716-124">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="81716-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81716-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81716-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
