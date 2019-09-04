---
title: <remove>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252338"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="d4fc6-102">\<remove> Element for \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="d4fc6-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="d4fc6-103">Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d4fc6-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="d4fc6-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4fc6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4fc6-105">&nbsp;&nbsp;[ **\<System. Runtime. buforowanie >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d4fc6-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="d4fc6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Elemencie MemoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d4fc6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="d4fc6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d4fc6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="d4fc6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="d4fc6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fc6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4fc6-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="d4fc6-110">Typ</span><span class="sxs-lookup"><span data-stu-id="d4fc6-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4fc6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4fc6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4fc6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4fc6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4fc6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4fc6-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="d4fc6-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4fc6-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="d4fc6-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4fc6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d4fc6-116">Element</span><span class="sxs-lookup"><span data-stu-id="d4fc6-116">Element</span></span>|<span data-ttu-id="d4fc6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d4fc6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4fc6-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="d4fc6-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="d4fc6-119">Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d4fc6-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4fc6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4fc6-120">Remarks</span></span>  
 <span data-ttu-id="d4fc6-121">`remove` Element`namedCache` usuwa wpis z kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d4fc6-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fc6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4fc6-122">See also</span></span>

- [<span data-ttu-id="d4fc6-123">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="d4fc6-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
