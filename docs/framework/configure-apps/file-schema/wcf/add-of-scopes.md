---
title: <add> dla <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926627"
---
# <a name="add-of-scopes"></a><span data-ttu-id="97a59-102">\<Dodaj > \<zakresów ></span><span class="sxs-lookup"><span data-stu-id="97a59-102">\<add> of \<scopes></span></span>
<span data-ttu-id="97a59-103">Dodaje niestandardowy identyfikator URI zakresu, którego można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="97a59-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="97a59-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97a59-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="97a59-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="97a59-105">\<behaviors></span></span>  
<span data-ttu-id="97a59-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="97a59-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="97a59-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="97a59-107">\<behavior></span></span>  
<span data-ttu-id="97a59-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="97a59-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="97a59-109">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="97a59-109">\<scopes></span></span>  
<span data-ttu-id="97a59-110">\<add></span><span class="sxs-lookup"><span data-stu-id="97a59-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97a59-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="97a59-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97a59-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97a59-112">Attributes and Elements</span></span>  
 <span data-ttu-id="97a59-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97a59-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97a59-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97a59-114">Attributes</span></span>  
  
|<span data-ttu-id="97a59-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97a59-115">Attribute</span></span>|<span data-ttu-id="97a59-116">Opis</span><span class="sxs-lookup"><span data-stu-id="97a59-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97a59-117">zakres</span><span class="sxs-lookup"><span data-stu-id="97a59-117">scope</span></span>|<span data-ttu-id="97a59-118">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używany w kryterium dopasowywania do znajdowania usług.</span><span class="sxs-lookup"><span data-stu-id="97a59-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97a59-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97a59-119">Child Elements</span></span>  
 <span data-ttu-id="97a59-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="97a59-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97a59-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97a59-121">Parent Elements</span></span>  
  
|<span data-ttu-id="97a59-122">Element</span><span class="sxs-lookup"><span data-stu-id="97a59-122">Element</span></span>|<span data-ttu-id="97a59-123">Opis</span><span class="sxs-lookup"><span data-stu-id="97a59-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97a59-124">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="97a59-124">\<scopes></span></span>](scopes.md)|<span data-ttu-id="97a59-125">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="97a59-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97a59-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97a59-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
