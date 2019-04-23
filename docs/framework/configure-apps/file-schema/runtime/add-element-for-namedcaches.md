---
title: <add>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 9a7e370f9cce0e9ddf6dbe49984b7597e041eb84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094531"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="eefda-102">\<add> Element for \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="eefda-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="eefda-103">Dodaje `namedCache` wpis `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eefda-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="eefda-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="eefda-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="eefda-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="eefda-105">\<memoryCache></span></span>  
<span data-ttu-id="eefda-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="eefda-106">\<namedCaches></span></span>  
<span data-ttu-id="eefda-107">\<add></span><span class="sxs-lookup"><span data-stu-id="eefda-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefda-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eefda-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="eefda-109">Typ</span><span class="sxs-lookup"><span data-stu-id="eefda-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eefda-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eefda-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eefda-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eefda-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eefda-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eefda-112">Attributes</span></span>  
  
|<span data-ttu-id="eefda-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eefda-113">Attribute</span></span>|<span data-ttu-id="eefda-114">Opis</span><span class="sxs-lookup"><span data-stu-id="eefda-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="eefda-115">Wartość całkowitą, która określa maksymalny dozwolony rozmiar (w megabajtach), wystąpienie <xref:System.Runtime.Caching.MemoryCache> może zwiększyć się.</span><span class="sxs-lookup"><span data-stu-id="eefda-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="eefda-116">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru tej klasy.</span><span class="sxs-lookup"><span data-stu-id="eefda-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="eefda-117">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eefda-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="eefda-118">Wartość całkowitą pomiędzy 0 a 100 określającą maksymalną wartość procentową fizycznie zainstalowanym komputerze pamięci, które mogą być używane przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="eefda-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="eefda-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru tej klasy.</span><span class="sxs-lookup"><span data-stu-id="eefda-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="eefda-120">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eefda-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="eefda-121">Ta wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="eefda-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eefda-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eefda-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="eefda-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eefda-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eefda-124">Element</span><span class="sxs-lookup"><span data-stu-id="eefda-124">Element</span></span>|<span data-ttu-id="eefda-125">Opis</span><span class="sxs-lookup"><span data-stu-id="eefda-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eefda-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="eefda-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="eefda-127">Zawiera kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="eefda-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eefda-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eefda-128">Remarks</span></span>  
 <span data-ttu-id="eefda-129">`add` Elementu dodaje wpis do `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eefda-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="eefda-130">Możesz użyć [wyczyść](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element przed użyciem `add` elementu, aby mieć pewność, że nie istnieją żadne inne nazwane pamięci podręczne w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="eefda-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="eefda-131">Ten element może służyć w pliku machine.config i w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="eefda-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eefda-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="eefda-132">Example</span></span>  
 <span data-ttu-id="eefda-133">Poniższy przykład pokazuje jak zdefiniować ustawienia dla domyślnej `namedCache` wpis `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eefda-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eefda-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eefda-134">See also</span></span>

- [<span data-ttu-id="eefda-135">\<namedCaches >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="eefda-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
