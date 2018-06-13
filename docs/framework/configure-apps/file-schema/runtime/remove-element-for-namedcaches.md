---
title: '&lt;Usuń&gt; elementu &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6ffaea24910a6b8f4a120d6b72219bff592fab17
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745217"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="9acf8-102">&lt;Usuń&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="9acf8-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="9acf8-103">Usuwa wpis w pamięci podręcznej o nazwie z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9acf8-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="9acf8-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="9acf8-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="9acf8-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="9acf8-105">\<memoryCache></span></span>  
<span data-ttu-id="9acf8-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="9acf8-106">\<namedCaches></span></span>  
<span data-ttu-id="9acf8-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="9acf8-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acf8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9acf8-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9acf8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9acf8-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9acf8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9acf8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9acf8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9acf8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9acf8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9acf8-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="9acf8-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9acf8-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9acf8-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9acf8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9acf8-115">Element</span><span class="sxs-lookup"><span data-stu-id="9acf8-115">Element</span></span>|<span data-ttu-id="9acf8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9acf8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9acf8-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="9acf8-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="9acf8-118">Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9acf8-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9acf8-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9acf8-119">Remarks</span></span>  
 <span data-ttu-id="9acf8-120">`remove` Usuwa element `namedCache` wpisu z kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9acf8-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acf8-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9acf8-121">See Also</span></span>  
 [<span data-ttu-id="9acf8-122">\<namedCaches > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="9acf8-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
