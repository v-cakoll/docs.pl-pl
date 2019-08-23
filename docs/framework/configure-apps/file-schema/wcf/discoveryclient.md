---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919275"
---
# <a name="discoveryclient"></a><span data-ttu-id="6cf54-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="6cf54-101">\<discoveryClient></span></span>
<span data-ttu-id="6cf54-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6cf54-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="6cf54-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6cf54-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6cf54-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="6cf54-104">\<bindings></span></span>  
<span data-ttu-id="6cf54-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6cf54-105">\<customBinding></span></span>  
<span data-ttu-id="6cf54-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6cf54-106">\<binding></span></span>  
<span data-ttu-id="6cf54-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="6cf54-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf54-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cf54-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cf54-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6cf54-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6cf54-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6cf54-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cf54-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6cf54-111">Attributes</span></span>  
  
|<span data-ttu-id="6cf54-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6cf54-112">Attribute</span></span>|<span data-ttu-id="6cf54-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6cf54-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cf54-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="6cf54-114">discoveryEndpoint</span></span>|<span data-ttu-id="6cf54-115">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6cf54-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cf54-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6cf54-116">Child Elements</span></span>  
  
|<span data-ttu-id="6cf54-117">Element</span><span class="sxs-lookup"><span data-stu-id="6cf54-117">Element</span></span>|<span data-ttu-id="6cf54-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6cf54-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cf54-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="6cf54-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="6cf54-120">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="6cf54-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6cf54-121">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="6cf54-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cf54-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6cf54-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6cf54-123">Element</span><span class="sxs-lookup"><span data-stu-id="6cf54-123">Element</span></span>|<span data-ttu-id="6cf54-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6cf54-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cf54-125">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6cf54-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="6cf54-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6cf54-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cf54-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cf54-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
