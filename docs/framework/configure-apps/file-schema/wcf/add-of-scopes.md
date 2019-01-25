---
title: '&lt;add&gt; w &lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 961fb3e388e3ae756bd7511ea6c65df6dd2a1486
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705576"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="09af1-102">&lt;add&gt; w &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="09af1-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="09af1-103">Dodaje niestandardowy zakres Uri, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="09af1-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="09af1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="09af1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="09af1-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="09af1-105">\<behaviors></span></span>  
<span data-ttu-id="09af1-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="09af1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="09af1-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="09af1-107">\<behavior></span></span>  
<span data-ttu-id="09af1-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="09af1-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="09af1-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="09af1-109">\<scopes></span></span>  
<span data-ttu-id="09af1-110">\<add></span><span class="sxs-lookup"><span data-stu-id="09af1-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09af1-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="09af1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09af1-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09af1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="09af1-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="09af1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09af1-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09af1-114">Attributes</span></span>  
  
|<span data-ttu-id="09af1-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="09af1-115">Attribute</span></span>|<span data-ttu-id="09af1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="09af1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09af1-117">zakres</span><span class="sxs-lookup"><span data-stu-id="09af1-117">scope</span></span>|<span data-ttu-id="09af1-118">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być użyty w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="09af1-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09af1-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09af1-119">Child Elements</span></span>  
 <span data-ttu-id="09af1-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="09af1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09af1-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09af1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="09af1-122">Element</span><span class="sxs-lookup"><span data-stu-id="09af1-122">Element</span></span>|<span data-ttu-id="09af1-123">Opis</span><span class="sxs-lookup"><span data-stu-id="09af1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09af1-124">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="09af1-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="09af1-125">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="09af1-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09af1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09af1-126">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
