---
title: '&lt;Usuń&gt; elementu &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7e183a624b95e207d34697c906cc3f278c967ae9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499786"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="37bd5-102">&lt;Usuń&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="37bd5-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="37bd5-103">Usuwa wpis nazwaną pamięć podręczną z `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="37bd5-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="37bd5-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="37bd5-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="37bd5-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="37bd5-105">\<memoryCache></span></span>  
<span data-ttu-id="37bd5-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="37bd5-106">\<namedCaches></span></span>  
<span data-ttu-id="37bd5-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="37bd5-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37bd5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="37bd5-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="37bd5-109">Typ</span><span class="sxs-lookup"><span data-stu-id="37bd5-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37bd5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37bd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37bd5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37bd5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37bd5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37bd5-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="37bd5-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37bd5-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="37bd5-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37bd5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="37bd5-115">Element</span><span class="sxs-lookup"><span data-stu-id="37bd5-115">Element</span></span>|<span data-ttu-id="37bd5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="37bd5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37bd5-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="37bd5-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="37bd5-118">Zawiera kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="37bd5-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37bd5-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37bd5-119">Remarks</span></span>  
 <span data-ttu-id="37bd5-120">`remove` Usuwa element `namedCache` wpis z kolekcji nazwaną pamięć podręczną dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="37bd5-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bd5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37bd5-121">See also</span></span>
- [<span data-ttu-id="37bd5-122">\<namedCaches >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="37bd5-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
