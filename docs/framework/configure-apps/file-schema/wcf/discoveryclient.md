---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128443"
---
# <a name="discoveryclient"></a><span data-ttu-id="d6775-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="d6775-101">\<discoveryClient></span></span>
<span data-ttu-id="d6775-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d6775-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="d6775-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6775-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d6775-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d6775-104">\<bindings></span></span>  
<span data-ttu-id="d6775-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d6775-105">\<customBinding></span></span>  
<span data-ttu-id="d6775-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d6775-106">\<binding></span></span>  
<span data-ttu-id="d6775-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="d6775-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6775-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6775-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6775-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d6775-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d6775-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d6775-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6775-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d6775-111">Attributes</span></span>  
  
|<span data-ttu-id="d6775-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d6775-112">Attribute</span></span>|<span data-ttu-id="d6775-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d6775-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6775-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="d6775-114">discoveryEndpoint</span></span>|<span data-ttu-id="d6775-115">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d6775-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6775-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d6775-116">Child Elements</span></span>  
  
|<span data-ttu-id="d6775-117">Element</span><span class="sxs-lookup"><span data-stu-id="d6775-117">Element</span></span>|<span data-ttu-id="d6775-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d6775-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6775-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d6775-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d6775-120">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="d6775-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d6775-121">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="d6775-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6775-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d6775-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d6775-123">Element</span><span class="sxs-lookup"><span data-stu-id="d6775-123">Element</span></span>|<span data-ttu-id="d6775-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d6775-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6775-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d6775-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d6775-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d6775-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6775-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6775-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
