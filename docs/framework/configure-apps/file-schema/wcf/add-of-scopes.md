---
title: '&lt;add&gt; w &lt;scopes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="e944a-102">&lt;add&gt; w &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="e944a-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="e944a-103">Dodaje niestandardowy zakres Uri, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="e944a-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="e944a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e944a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e944a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e944a-105">\<behaviors></span></span>  
<span data-ttu-id="e944a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e944a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e944a-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e944a-107">\<behavior></span></span>  
<span data-ttu-id="e944a-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="e944a-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="e944a-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="e944a-109">\<scopes></span></span>  
<span data-ttu-id="e944a-110">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="e944a-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e944a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e944a-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e944a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e944a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e944a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e944a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e944a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e944a-114">Attributes</span></span>  
  
|<span data-ttu-id="e944a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e944a-115">Attribute</span></span>|<span data-ttu-id="e944a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e944a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e944a-117">zakres</span><span class="sxs-lookup"><span data-stu-id="e944a-117">scope</span></span>|<span data-ttu-id="e944a-118">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="e944a-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e944a-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e944a-119">Child Elements</span></span>  
 <span data-ttu-id="e944a-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="e944a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e944a-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e944a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e944a-122">Element</span><span class="sxs-lookup"><span data-stu-id="e944a-122">Element</span></span>|<span data-ttu-id="e944a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e944a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e944a-124">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="e944a-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="e944a-125">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="e944a-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e944a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e944a-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
