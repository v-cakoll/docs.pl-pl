---
title: "&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0819141b2135a2de99a2801a1888f7b0e1cd19fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="40500-102">&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="40500-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="40500-103">Czyści wszystkie `namedCache` wpisów w `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40500-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="40500-104">\<System.Runtime.Caching — ></span><span class="sxs-lookup"><span data-stu-id="40500-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="40500-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="40500-105">\<memoryCache></span></span>  
<span data-ttu-id="40500-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="40500-106">\<namedCaches></span></span>  
<span data-ttu-id="40500-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="40500-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40500-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="40500-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="40500-109">Typ</span><span class="sxs-lookup"><span data-stu-id="40500-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40500-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="40500-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40500-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="40500-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40500-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="40500-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="40500-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="40500-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="40500-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="40500-114">Parent Elements</span></span>  
  
|<span data-ttu-id="40500-115">Element</span><span class="sxs-lookup"><span data-stu-id="40500-115">Element</span></span>|<span data-ttu-id="40500-116">Opis</span><span class="sxs-lookup"><span data-stu-id="40500-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40500-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="40500-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="40500-118">Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="40500-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40500-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40500-119">Remarks</span></span>  
 <span data-ttu-id="40500-120">`clear` Element czyści wszystkie `namedCache` wpisów w kolekcji nazwanych pamięci podręcznej w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40500-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="40500-121">Można użyć `clear` element przed użyciem `add` element, aby dodać nowy wpis pamięci podręcznej o nazwie, aby mieć pewność, nie ma żadnych innych o nazwie pamięci podręcznych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="40500-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40500-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40500-122">See Also</span></span>  
 [<span data-ttu-id="40500-123">\<namedCaches > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="40500-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
