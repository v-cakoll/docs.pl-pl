---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704027"
---
# <a name="discoveryclient"></a><span data-ttu-id="3f6b6-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="3f6b6-101">\<discoveryClient></span></span>
<span data-ttu-id="3f6b6-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f6b6-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="3f6b6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3f6b6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3f6b6-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3f6b6-104">\<bindings></span></span>  
<span data-ttu-id="3f6b6-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3f6b6-105">\<customBinding></span></span>  
<span data-ttu-id="3f6b6-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3f6b6-106">\<binding></span></span>  
<span data-ttu-id="3f6b6-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="3f6b6-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6b6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f6b6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f6b6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f6b6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f6b6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f6b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f6b6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f6b6-111">Attributes</span></span>  
  
|<span data-ttu-id="3f6b6-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f6b6-112">Attribute</span></span>|<span data-ttu-id="3f6b6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3f6b6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f6b6-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="3f6b6-114">discoveryEndpoint</span></span>|<span data-ttu-id="3f6b6-115">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f6b6-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f6b6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f6b6-116">Child Elements</span></span>  
  
|<span data-ttu-id="3f6b6-117">Element</span><span class="sxs-lookup"><span data-stu-id="3f6b6-117">Element</span></span>|<span data-ttu-id="3f6b6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3f6b6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f6b6-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3f6b6-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="3f6b6-120">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="3f6b6-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="3f6b6-121">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="3f6b6-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f6b6-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f6b6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3f6b6-123">Element</span><span class="sxs-lookup"><span data-stu-id="3f6b6-123">Element</span></span>|<span data-ttu-id="3f6b6-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3f6b6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f6b6-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3f6b6-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3f6b6-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f6b6-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f6b6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f6b6-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
