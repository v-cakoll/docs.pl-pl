---
title: '&lt;Klasa DiscoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 9aef599ebf8068a383fd093b126a6bde1670b291
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151401"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="365a6-102">&lt;Klasa DiscoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="365a6-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="365a6-103">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="365a6-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="365a6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="365a6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="365a6-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="365a6-105">\<bindings></span></span>  
<span data-ttu-id="365a6-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="365a6-106">\<customBinding></span></span>  
<span data-ttu-id="365a6-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="365a6-107">\<binding></span></span>  
<span data-ttu-id="365a6-108">\<Klasa discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="365a6-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365a6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="365a6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="365a6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="365a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="365a6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="365a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="365a6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="365a6-112">Attributes</span></span>  
  
|<span data-ttu-id="365a6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="365a6-113">Attribute</span></span>|<span data-ttu-id="365a6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="365a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="365a6-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="365a6-115">discoveryEndpoint</span></span>|<span data-ttu-id="365a6-116">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="365a6-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="365a6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="365a6-117">Child Elements</span></span>  
  
|<span data-ttu-id="365a6-118">Element</span><span class="sxs-lookup"><span data-stu-id="365a6-118">Element</span></span>|<span data-ttu-id="365a6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="365a6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365a6-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="365a6-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="365a6-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="365a6-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="365a6-122">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="365a6-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="365a6-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="365a6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="365a6-124">Element</span><span class="sxs-lookup"><span data-stu-id="365a6-124">Element</span></span>|<span data-ttu-id="365a6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="365a6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365a6-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="365a6-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="365a6-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="365a6-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="365a6-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="365a6-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
