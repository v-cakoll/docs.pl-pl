---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399928"
---
# \<scopes>
<span data-ttu-id="45f99-101">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="45f99-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="45f99-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="45f99-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45f99-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45f99-103">Attributes and Elements</span></span>  
 <span data-ttu-id="45f99-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45f99-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45f99-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45f99-105">Attributes</span></span>  
 <span data-ttu-id="45f99-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="45f99-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45f99-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45f99-107">Child Elements</span></span>  
  
|<span data-ttu-id="45f99-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="45f99-108">Attribute</span></span>|<span data-ttu-id="45f99-109">Opis</span><span class="sxs-lookup"><span data-stu-id="45f99-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="45f99-110">Dodaje informacje o zakresie dla punktu końcowego, którego można użyć w kryterium dopasowywania w celu znalezienia usług.</span><span class="sxs-lookup"><span data-stu-id="45f99-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45f99-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45f99-111">Parent Elements</span></span>  
  
|<span data-ttu-id="45f99-112">Element</span><span class="sxs-lookup"><span data-stu-id="45f99-112">Element</span></span>|<span data-ttu-id="45f99-113">Opis</span><span class="sxs-lookup"><span data-stu-id="45f99-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="45f99-114">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="45f99-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45f99-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45f99-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
