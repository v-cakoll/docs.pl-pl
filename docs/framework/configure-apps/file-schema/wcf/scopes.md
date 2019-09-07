---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399928"
---
# <a name="scopes"></a><span data-ttu-id="37c36-101">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="37c36-101">\<scopes></span></span>
<span data-ttu-id="37c36-102">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="37c36-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="37c36-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37c36-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="37c36-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="37c36-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="37c36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="37c36-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="37c36-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="37c36-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zakresy >**</span><span class="sxs-lookup"><span data-stu-id="37c36-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c36-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="37c36-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c36-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37c36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="37c36-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37c36-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c36-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37c36-113">Attributes</span></span>  
 <span data-ttu-id="37c36-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="37c36-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37c36-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37c36-115">Child Elements</span></span>  
  
|<span data-ttu-id="37c36-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37c36-116">Attribute</span></span>|<span data-ttu-id="37c36-117">Opis</span><span class="sxs-lookup"><span data-stu-id="37c36-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="37c36-118">\<add></span><span class="sxs-lookup"><span data-stu-id="37c36-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="37c36-119">Dodaje informacje o zakresie dla punktu końcowego, którego można użyć w kryterium dopasowywania w celu znalezienia usług.</span><span class="sxs-lookup"><span data-stu-id="37c36-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37c36-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37c36-120">Parent Elements</span></span>  
  
|<span data-ttu-id="37c36-121">Element</span><span class="sxs-lookup"><span data-stu-id="37c36-121">Element</span></span>|<span data-ttu-id="37c36-122">Opis</span><span class="sxs-lookup"><span data-stu-id="37c36-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c36-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="37c36-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="37c36-124">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="37c36-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c36-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37c36-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
