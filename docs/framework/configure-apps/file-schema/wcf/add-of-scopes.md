---
title: <add> dla <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187087"
---
# <a name="add-of-scopes"></a><span data-ttu-id="6799b-102">\<Dodaj > z \<zakresy ></span><span class="sxs-lookup"><span data-stu-id="6799b-102">\<add> of \<scopes></span></span>
<span data-ttu-id="6799b-103">Dodaje niestandardowy zakres Uri, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="6799b-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="6799b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6799b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6799b-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="6799b-105">\<behaviors></span></span>  
<span data-ttu-id="6799b-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6799b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6799b-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="6799b-107">\<behavior></span></span>  
<span data-ttu-id="6799b-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="6799b-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="6799b-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="6799b-109">\<scopes></span></span>  
<span data-ttu-id="6799b-110">\<add></span><span class="sxs-lookup"><span data-stu-id="6799b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6799b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="6799b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6799b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6799b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6799b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6799b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6799b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6799b-114">Attributes</span></span>  
  
|<span data-ttu-id="6799b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6799b-115">Attribute</span></span>|<span data-ttu-id="6799b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6799b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6799b-117">zakres</span><span class="sxs-lookup"><span data-stu-id="6799b-117">scope</span></span>|<span data-ttu-id="6799b-118">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być użyty w dopasowaniu kryteriów dla znajdowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="6799b-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6799b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6799b-119">Child Elements</span></span>  
 <span data-ttu-id="6799b-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="6799b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6799b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6799b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6799b-122">Element</span><span class="sxs-lookup"><span data-stu-id="6799b-122">Element</span></span>|<span data-ttu-id="6799b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6799b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6799b-124">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="6799b-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="6799b-125">Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="6799b-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6799b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6799b-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
