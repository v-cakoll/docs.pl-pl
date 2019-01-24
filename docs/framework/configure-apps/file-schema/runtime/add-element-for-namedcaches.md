---
title: '&lt;Dodaj&gt; elementu &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fa11cea7e78a56c3f5cbfd9d0678e1ed671f6f3c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506046"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="17f33-102">&lt;Dodaj&gt; elementu &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="17f33-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="17f33-103">Dodaje `namedCache` wpis `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17f33-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="17f33-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="17f33-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="17f33-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="17f33-105">\<memoryCache></span></span>  
<span data-ttu-id="17f33-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="17f33-106">\<namedCaches></span></span>  
<span data-ttu-id="17f33-107">\<add></span><span class="sxs-lookup"><span data-stu-id="17f33-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f33-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="17f33-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="17f33-109">Typ</span><span class="sxs-lookup"><span data-stu-id="17f33-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17f33-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="17f33-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17f33-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="17f33-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17f33-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="17f33-112">Attributes</span></span>  
  
|<span data-ttu-id="17f33-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="17f33-113">Attribute</span></span>|<span data-ttu-id="17f33-114">Opis</span><span class="sxs-lookup"><span data-stu-id="17f33-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="17f33-115">Wartość całkowitą, która określa maksymalny dozwolony rozmiar (w megabajtach), wystąpienie <xref:System.Runtime.Caching.MemoryCache> może zwiększyć się.</span><span class="sxs-lookup"><span data-stu-id="17f33-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="17f33-116">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru tej klasy.</span><span class="sxs-lookup"><span data-stu-id="17f33-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="17f33-117">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17f33-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="17f33-118">Wartość całkowitą pomiędzy 0 a 100 określającą maksymalną wartość procentową fizycznie zainstalowanym komputerze pamięci, które mogą być używane przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="17f33-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="17f33-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru tej klasy.</span><span class="sxs-lookup"><span data-stu-id="17f33-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="17f33-120">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17f33-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="17f33-121">Ta wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="17f33-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17f33-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="17f33-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="17f33-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="17f33-123">Parent Elements</span></span>  
  
|<span data-ttu-id="17f33-124">Element</span><span class="sxs-lookup"><span data-stu-id="17f33-124">Element</span></span>|<span data-ttu-id="17f33-125">Opis</span><span class="sxs-lookup"><span data-stu-id="17f33-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17f33-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="17f33-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="17f33-127">Zawiera kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="17f33-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17f33-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17f33-128">Remarks</span></span>  
 <span data-ttu-id="17f33-129">`add` Elementu dodaje wpis do `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17f33-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="17f33-130">Możesz użyć [wyczyść](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element przed użyciem `add` elementu, aby mieć pewność, że nie istnieją żadne inne nazwane pamięci podręczne w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17f33-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="17f33-131">Ten element może służyć w pliku machine.config i w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="17f33-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f33-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="17f33-132">Example</span></span>  
 <span data-ttu-id="17f33-133">Poniższy przykład pokazuje jak zdefiniować ustawienia dla domyślnej `namedCache` wpis `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17f33-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17f33-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17f33-134">See also</span></span>
- [<span data-ttu-id="17f33-135">\<namedCaches >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="17f33-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
