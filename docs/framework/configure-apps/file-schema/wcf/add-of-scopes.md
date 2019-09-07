---
title: <add> dla <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398309"
---
# <a name="add-of-scopes"></a><span data-ttu-id="34b4c-102">\<Dodaj > \<zakresów ></span><span class="sxs-lookup"><span data-stu-id="34b4c-102">\<add> of \<scopes></span></span>
<span data-ttu-id="34b4c-103">Dodaje niestandardowy identyfikator URI zakresu, którego można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="34b4c-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="34b4c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34b4c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="34b4c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="34b4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="34b4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="34b4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="34b4c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zakresy >** ](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="34b4c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="34b4c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="34b4c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b4c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="34b4c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34b4c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34b4c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="34b4c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34b4c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34b4c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34b4c-115">Attributes</span></span>  
  
|<span data-ttu-id="34b4c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34b4c-116">Attribute</span></span>|<span data-ttu-id="34b4c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="34b4c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34b4c-118">zakres</span><span class="sxs-lookup"><span data-stu-id="34b4c-118">scope</span></span>|<span data-ttu-id="34b4c-119">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używany w kryterium dopasowywania do znajdowania usług.</span><span class="sxs-lookup"><span data-stu-id="34b4c-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34b4c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34b4c-120">Child Elements</span></span>  
 <span data-ttu-id="34b4c-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="34b4c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34b4c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34b4c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="34b4c-123">Element</span><span class="sxs-lookup"><span data-stu-id="34b4c-123">Element</span></span>|<span data-ttu-id="34b4c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="34b4c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34b4c-125">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="34b4c-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="34b4c-126">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="34b4c-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34b4c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34b4c-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
