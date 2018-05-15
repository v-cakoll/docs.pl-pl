---
title: '&lt;add&gt; w &lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: a889100da4723a1f5e8f84ca88ea426ccaa2e77f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="1d569-102">&lt;add&gt; w &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="1d569-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="1d569-103">Dodaje niestandardowy zakres Uri, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="1d569-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="1d569-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d569-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d569-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1d569-105">\<behaviors></span></span>  
<span data-ttu-id="1d569-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d569-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1d569-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1d569-107">\<behavior></span></span>  
<span data-ttu-id="1d569-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1d569-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="1d569-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="1d569-109">\<scopes></span></span>  
<span data-ttu-id="1d569-110">\<add></span><span class="sxs-lookup"><span data-stu-id="1d569-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d569-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d569-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d569-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d569-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1d569-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d569-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d569-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d569-114">Attributes</span></span>  
  
|<span data-ttu-id="1d569-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d569-115">Attribute</span></span>|<span data-ttu-id="1d569-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1d569-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d569-117">zakres</span><span class="sxs-lookup"><span data-stu-id="1d569-117">scope</span></span>|<span data-ttu-id="1d569-118">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="1d569-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d569-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d569-119">Child Elements</span></span>  
 <span data-ttu-id="1d569-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d569-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d569-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d569-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1d569-122">Element</span><span class="sxs-lookup"><span data-stu-id="1d569-122">Element</span></span>|<span data-ttu-id="1d569-123">Opis</span><span class="sxs-lookup"><span data-stu-id="1d569-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d569-124">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="1d569-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="1d569-125">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="1d569-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d569-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d569-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
