---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935183"
---
# <a name="scopes"></a><span data-ttu-id="766d8-101">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="766d8-101">\<scopes></span></span>
<span data-ttu-id="766d8-102">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="766d8-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="766d8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="766d8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="766d8-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="766d8-104">\<behaviors></span></span>  
<span data-ttu-id="766d8-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="766d8-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="766d8-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="766d8-106">\<behavior></span></span>  
<span data-ttu-id="766d8-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="766d8-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="766d8-108">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="766d8-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="766d8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="766d8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="766d8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="766d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="766d8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="766d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="766d8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="766d8-112">Attributes</span></span>  
 <span data-ttu-id="766d8-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="766d8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="766d8-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="766d8-114">Child Elements</span></span>  
  
|<span data-ttu-id="766d8-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="766d8-115">Attribute</span></span>|<span data-ttu-id="766d8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="766d8-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="766d8-117">\<add></span><span class="sxs-lookup"><span data-stu-id="766d8-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="766d8-118">Dodaje informacje o zakresie dla punktu końcowego, którego można użyć w kryterium dopasowywania w celu znalezienia usług.</span><span class="sxs-lookup"><span data-stu-id="766d8-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="766d8-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="766d8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="766d8-120">Element</span><span class="sxs-lookup"><span data-stu-id="766d8-120">Element</span></span>|<span data-ttu-id="766d8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="766d8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="766d8-122">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="766d8-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="766d8-123">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="766d8-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="766d8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="766d8-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
