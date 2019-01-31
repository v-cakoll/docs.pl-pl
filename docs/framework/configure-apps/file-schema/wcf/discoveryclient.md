---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 512a91bf25180606213eb9eb3b4f7c6a0cb4cbbf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284808"
---
# <a name="discoveryclient"></a><span data-ttu-id="12e0c-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="12e0c-101">\<discoveryClient></span></span>
<span data-ttu-id="12e0c-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12e0c-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="12e0c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12e0c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="12e0c-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="12e0c-104">\<bindings></span></span>  
<span data-ttu-id="12e0c-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="12e0c-105">\<customBinding></span></span>  
<span data-ttu-id="12e0c-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="12e0c-106">\<binding></span></span>  
<span data-ttu-id="12e0c-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="12e0c-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e0c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="12e0c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12e0c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12e0c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="12e0c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12e0c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12e0c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12e0c-111">Attributes</span></span>  
  
|<span data-ttu-id="12e0c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="12e0c-112">Attribute</span></span>|<span data-ttu-id="12e0c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="12e0c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12e0c-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="12e0c-114">discoveryEndpoint</span></span>|<span data-ttu-id="12e0c-115">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12e0c-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12e0c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12e0c-116">Child Elements</span></span>  
  
|<span data-ttu-id="12e0c-117">Element</span><span class="sxs-lookup"><span data-stu-id="12e0c-117">Element</span></span>|<span data-ttu-id="12e0c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="12e0c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12e0c-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="12e0c-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="12e0c-120">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="12e0c-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="12e0c-121">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="12e0c-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12e0c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12e0c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="12e0c-123">Element</span><span class="sxs-lookup"><span data-stu-id="12e0c-123">Element</span></span>|<span data-ttu-id="12e0c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="12e0c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12e0c-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="12e0c-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="12e0c-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="12e0c-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12e0c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12e0c-127">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
