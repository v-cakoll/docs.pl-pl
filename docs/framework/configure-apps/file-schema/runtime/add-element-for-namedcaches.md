---
title: '&lt;Dodaj&gt; elementu &lt;namedCaches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0baafcb53bf79a25618dad56c2dcf1412e48624b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="ac556-102">&lt;Dodaj&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="ac556-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="ac556-103">Dodaje `namedCache` wpisu `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac556-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="ac556-104">\<System.Runtime.Caching — ></span><span class="sxs-lookup"><span data-stu-id="ac556-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="ac556-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="ac556-105">\<memoryCache></span></span>  
<span data-ttu-id="ac556-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="ac556-106">\<namedCaches></span></span>  
<span data-ttu-id="ac556-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="ac556-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac556-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac556-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ac556-109">Typ</span><span class="sxs-lookup"><span data-stu-id="ac556-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac556-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac556-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac556-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac556-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac556-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac556-112">Attributes</span></span>  
  
|<span data-ttu-id="ac556-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ac556-113">Attribute</span></span>|<span data-ttu-id="ac556-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ac556-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="ac556-115">Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach) który wystąpienia <xref:System.Runtime.Caching.MemoryCache> odpowiednio do.</span><span class="sxs-lookup"><span data-stu-id="ac556-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="ac556-116">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru klasy.</span><span class="sxs-lookup"><span data-stu-id="ac556-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="ac556-117">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac556-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="ac556-118">Wartość całkowitą pomiędzy 0 a 100 określająca maksymalny procent pamięci fizycznie zainstalowanym komputerze, który może być zużyte przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="ac556-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="ac556-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru klasy.</span><span class="sxs-lookup"><span data-stu-id="ac556-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="ac556-120">Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac556-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="ac556-121">Ta wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="ac556-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac556-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac556-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ac556-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac556-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ac556-124">Element</span><span class="sxs-lookup"><span data-stu-id="ac556-124">Element</span></span>|<span data-ttu-id="ac556-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ac556-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac556-126">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="ac556-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="ac556-127">Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ac556-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac556-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac556-128">Remarks</span></span>  
 <span data-ttu-id="ac556-129">`add` Element dodaje wpis do `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac556-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="ac556-130">Można użyć [wyczyść](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element przed użyciem `add` elementu, aby mieć pewność, że nie ma żadnych innych o nazwie pamięci podręcznych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ac556-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="ac556-131">Ten element może być użyty w pliku machine.config i w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="ac556-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac556-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac556-132">Example</span></span>  
 <span data-ttu-id="ac556-133">Poniższy przykład przedstawia sposób zdefiniować ustawienia domyślne `namedCache` wpisu `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac556-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac556-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac556-134">See Also</span></span>  
 [<span data-ttu-id="ac556-135">\<namedCaches > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="ac556-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
