---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 512a91bf25180606213eb9eb3b4f7c6a0cb4cbbf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366234"
---
# <a name="discoveryclient"></a><span data-ttu-id="d22bb-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="d22bb-101">\<discoveryClient></span></span>
<span data-ttu-id="d22bb-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d22bb-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="d22bb-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d22bb-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d22bb-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d22bb-104">\<bindings></span></span>  
<span data-ttu-id="d22bb-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d22bb-105">\<customBinding></span></span>  
<span data-ttu-id="d22bb-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d22bb-106">\<binding></span></span>  
<span data-ttu-id="d22bb-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="d22bb-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22bb-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d22bb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d22bb-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d22bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d22bb-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d22bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d22bb-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d22bb-111">Attributes</span></span>  
  
|<span data-ttu-id="d22bb-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d22bb-112">Attribute</span></span>|<span data-ttu-id="d22bb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d22bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d22bb-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="d22bb-114">discoveryEndpoint</span></span>|<span data-ttu-id="d22bb-115">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d22bb-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d22bb-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d22bb-116">Child Elements</span></span>  
  
|<span data-ttu-id="d22bb-117">Element</span><span class="sxs-lookup"><span data-stu-id="d22bb-117">Element</span></span>|<span data-ttu-id="d22bb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d22bb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d22bb-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d22bb-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d22bb-120">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="d22bb-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d22bb-121">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="d22bb-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d22bb-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d22bb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d22bb-123">Element</span><span class="sxs-lookup"><span data-stu-id="d22bb-123">Element</span></span>|<span data-ttu-id="d22bb-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d22bb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d22bb-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d22bb-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d22bb-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d22bb-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d22bb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d22bb-127">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
