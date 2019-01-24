---
title: '&lt;discoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5046d3342372960211942128372e9f62d98a2952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573088"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="8432a-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="8432a-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="8432a-103">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8432a-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="8432a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8432a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8432a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8432a-105">\<bindings></span></span>  
<span data-ttu-id="8432a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8432a-106">\<customBinding></span></span>  
<span data-ttu-id="8432a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8432a-107">\<binding></span></span>  
<span data-ttu-id="8432a-108">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="8432a-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8432a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8432a-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8432a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8432a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8432a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8432a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8432a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8432a-112">Attributes</span></span>  
  
|<span data-ttu-id="8432a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8432a-113">Attribute</span></span>|<span data-ttu-id="8432a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8432a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8432a-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="8432a-115">discoveryEndpoint</span></span>|<span data-ttu-id="8432a-116">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8432a-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8432a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8432a-117">Child Elements</span></span>  
  
|<span data-ttu-id="8432a-118">Element</span><span class="sxs-lookup"><span data-stu-id="8432a-118">Element</span></span>|<span data-ttu-id="8432a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8432a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8432a-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8432a-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="8432a-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="8432a-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="8432a-122">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="8432a-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8432a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8432a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8432a-124">Element</span><span class="sxs-lookup"><span data-stu-id="8432a-124">Element</span></span>|<span data-ttu-id="8432a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8432a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8432a-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8432a-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8432a-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8432a-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8432a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8432a-128">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
