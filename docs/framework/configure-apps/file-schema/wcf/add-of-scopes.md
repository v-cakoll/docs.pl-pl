---
title: <add> dla <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398309"
---
# <a name="add-of-scopes"></a><span data-ttu-id="b97fb-102">\<add> dla \<scopes></span><span class="sxs-lookup"><span data-stu-id="b97fb-102">\<add> of \<scopes></span></span>
<span data-ttu-id="b97fb-103">Dodaje niestandardowy identyfikator URI zakresu, którego można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="b97fb-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b97fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b97fb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b97fb-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b97fb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b97fb-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b97fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b97fb-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b97fb-107">Attributes</span></span>  
  
|<span data-ttu-id="b97fb-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b97fb-108">Attribute</span></span>|<span data-ttu-id="b97fb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b97fb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b97fb-110">scope</span><span class="sxs-lookup"><span data-stu-id="b97fb-110">scope</span></span>|<span data-ttu-id="b97fb-111">Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używany w kryterium dopasowywania do znajdowania usług.</span><span class="sxs-lookup"><span data-stu-id="b97fb-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b97fb-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b97fb-112">Child Elements</span></span>  
 <span data-ttu-id="b97fb-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="b97fb-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b97fb-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b97fb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b97fb-115">Element</span><span class="sxs-lookup"><span data-stu-id="b97fb-115">Element</span></span>|<span data-ttu-id="b97fb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b97fb-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="b97fb-117">Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.</span><span class="sxs-lookup"><span data-stu-id="b97fb-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b97fb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b97fb-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
