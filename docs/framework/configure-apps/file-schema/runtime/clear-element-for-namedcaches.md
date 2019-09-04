---
title: <clear>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252757"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="598c4-102">\<clear> Element for \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="598c4-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="598c4-103">Czyści wszystkie `namedCache` wpisy `namedCaches` w kolekcji pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="598c4-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="598c4-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="598c4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="598c4-105">&nbsp;&nbsp;[ **\<System. Runtime. buforowanie >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="598c4-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="598c4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Elemencie MemoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="598c4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="598c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="598c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="598c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="598c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598c4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="598c4-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="598c4-110">Typ</span><span class="sxs-lookup"><span data-stu-id="598c4-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="598c4-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="598c4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="598c4-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="598c4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="598c4-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="598c4-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="598c4-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="598c4-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="598c4-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="598c4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="598c4-116">Element</span><span class="sxs-lookup"><span data-stu-id="598c4-116">Element</span></span>|<span data-ttu-id="598c4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="598c4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="598c4-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="598c4-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="598c4-119">Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="598c4-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="598c4-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="598c4-120">Remarks</span></span>  
 <span data-ttu-id="598c4-121">Element czyści wszystkie `namedCache` wpisy w kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej. `clear`</span><span class="sxs-lookup"><span data-stu-id="598c4-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="598c4-122">Można użyć `clear` elementu przed użyciem elementu, `add` aby dodać nowy nazwany wpis pamięci podręcznej w celu uzyskania pewności, że w kolekcji nie ma innych nazwanych pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="598c4-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598c4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="598c4-123">See also</span></span>

- [<span data-ttu-id="598c4-124">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="598c4-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
