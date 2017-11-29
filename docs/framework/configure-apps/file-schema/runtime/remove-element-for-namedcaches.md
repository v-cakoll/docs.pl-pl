---
title: "&lt;Usuń&gt; elementu &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6170b59e87948225708c9e697cba1542d756d2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="0ccdb-102">&lt;Usuń&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="0ccdb-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="0ccdb-103">Usuwa wpis w pamięci podręcznej o nazwie z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0ccdb-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="0ccdb-104">\<System.Runtime.Caching — ></span><span class="sxs-lookup"><span data-stu-id="0ccdb-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="0ccdb-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="0ccdb-105">\<memoryCache></span></span>  
<span data-ttu-id="0ccdb-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0ccdb-106">\<namedCaches></span></span>  
<span data-ttu-id="0ccdb-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="0ccdb-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccdb-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ccdb-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="0ccdb-109">Typ</span><span class="sxs-lookup"><span data-stu-id="0ccdb-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ccdb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0ccdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0ccdb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0ccdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ccdb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ccdb-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="0ccdb-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0ccdb-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="0ccdb-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0ccdb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0ccdb-115">Element</span><span class="sxs-lookup"><span data-stu-id="0ccdb-115">Element</span></span>|<span data-ttu-id="0ccdb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0ccdb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ccdb-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0ccdb-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="0ccdb-118">Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0ccdb-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ccdb-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ccdb-119">Remarks</span></span>  
 <span data-ttu-id="0ccdb-120">`remove` Usuwa element `namedCache` wpisu z kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0ccdb-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccdb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ccdb-121">See Also</span></span>  
 [<span data-ttu-id="0ccdb-122">\<namedCaches > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="0ccdb-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
