---
title: <remove>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252338"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="c3929-102">\<remove>, element dla \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="c3929-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="c3929-103">Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c3929-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="c3929-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3929-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c3929-105">Typ</span><span class="sxs-lookup"><span data-stu-id="c3929-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3929-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3929-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c3929-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c3929-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3929-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3929-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="c3929-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3929-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c3929-110">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3929-110">Parent Elements</span></span>  
  
|<span data-ttu-id="c3929-111">Element</span><span class="sxs-lookup"><span data-stu-id="c3929-111">Element</span></span>|<span data-ttu-id="c3929-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c3929-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="c3929-113">Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c3929-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3929-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3929-114">Remarks</span></span>  
 <span data-ttu-id="c3929-115">`remove`Element usuwa `namedCache` wpis z kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c3929-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3929-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3929-116">See also</span></span>

- [<span data-ttu-id="c3929-117">\<namedCaches>— Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c3929-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
