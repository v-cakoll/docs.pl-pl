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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0a2309bb19b30f6927d5e9cd3047950936dff08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="29751-102">&lt;zakresy&gt;</span><span class="sxs-lookup"><span data-stu-id="29751-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="29751-103">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="29751-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="29751-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29751-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="29751-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="29751-105">\<behaviors></span></span>  
<span data-ttu-id="29751-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="29751-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="29751-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="29751-107">\<behavior></span></span>  
<span data-ttu-id="29751-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="29751-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="29751-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="29751-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29751-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="29751-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29751-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29751-111">Attributes and Elements</span></span>  
 <span data-ttu-id="29751-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29751-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29751-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29751-113">Attributes</span></span>  
 <span data-ttu-id="29751-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="29751-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29751-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29751-115">Child Elements</span></span>  
  
|<span data-ttu-id="29751-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="29751-116">Attribute</span></span>|<span data-ttu-id="29751-117">Opis</span><span class="sxs-lookup"><span data-stu-id="29751-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="29751-118">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="29751-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="29751-119">Dodaje zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="29751-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29751-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29751-120">Parent Elements</span></span>  
  
|<span data-ttu-id="29751-121">Element</span><span class="sxs-lookup"><span data-stu-id="29751-121">Element</span></span>|<span data-ttu-id="29751-122">Opis</span><span class="sxs-lookup"><span data-stu-id="29751-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29751-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="29751-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="29751-124">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="29751-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29751-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29751-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
