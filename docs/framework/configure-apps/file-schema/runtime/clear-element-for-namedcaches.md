---
title: '&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: dd521e3afa7584cadb28829028a5ecfd1cb55a92
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612306"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="ed466-102">&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="ed466-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="ed466-103">Czyści wszystkie `namedCache` wpisów w `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ed466-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="ed466-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="ed466-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="ed466-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="ed466-105">\<memoryCache></span></span>  
<span data-ttu-id="ed466-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="ed466-106">\<namedCaches></span></span>  
<span data-ttu-id="ed466-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ed466-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed466-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed466-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ed466-109">Typ</span><span class="sxs-lookup"><span data-stu-id="ed466-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed466-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ed466-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ed466-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ed466-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed466-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ed466-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="ed466-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed466-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ed466-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ed466-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ed466-115">Element</span><span class="sxs-lookup"><span data-stu-id="ed466-115">Element</span></span>|<span data-ttu-id="ed466-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ed466-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed466-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="ed466-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="ed466-118">Zawiera kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ed466-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed466-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed466-119">Remarks</span></span>  
 <span data-ttu-id="ed466-120">`clear` Element czyści wszystkie `namedCache` wpisów w kolekcji nazwaną pamięć podręczną dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ed466-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="ed466-121">Możesz użyć `clear` element przed użyciem `add` elementu, aby dodać nowy wpis nazwaną pamięć podręczną, aby mieć pewność, istnieją żadne inne nazwane pamięci podręczne w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ed466-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed466-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed466-122">See Also</span></span>  
- [<span data-ttu-id="ed466-123">\<namedCaches >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="ed466-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
