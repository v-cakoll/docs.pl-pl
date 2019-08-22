---
title: <clear>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658862"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="aad13-102">\<clear> Element for \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aad13-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="aad13-103">Czyści wszystkie `namedCache` wpisy `namedCaches` w kolekcji pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="aad13-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="aad13-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="aad13-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="aad13-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="aad13-105">\<memoryCache></span></span>  
<span data-ttu-id="aad13-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aad13-106">\<namedCaches></span></span>  
<span data-ttu-id="aad13-107">\<add></span><span class="sxs-lookup"><span data-stu-id="aad13-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad13-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="aad13-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="aad13-109">Typ</span><span class="sxs-lookup"><span data-stu-id="aad13-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aad13-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aad13-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aad13-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aad13-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aad13-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aad13-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="aad13-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aad13-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="aad13-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aad13-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aad13-115">Element</span><span class="sxs-lookup"><span data-stu-id="aad13-115">Element</span></span>|<span data-ttu-id="aad13-116">Opis</span><span class="sxs-lookup"><span data-stu-id="aad13-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aad13-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aad13-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="aad13-118">Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="aad13-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aad13-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aad13-119">Remarks</span></span>  
 <span data-ttu-id="aad13-120">Element czyści wszystkie `namedCache` wpisy w kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej. `clear`</span><span class="sxs-lookup"><span data-stu-id="aad13-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="aad13-121">Można użyć `clear` elementu przed użyciem elementu, `add` aby dodać nowy nazwany wpis pamięci podręcznej w celu uzyskania pewności, że w kolekcji nie ma innych nazwanych pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="aad13-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad13-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aad13-122">See also</span></span>

- [<span data-ttu-id="aad13-123">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="aad13-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
