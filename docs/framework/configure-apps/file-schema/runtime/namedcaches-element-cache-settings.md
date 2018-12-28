---
title: '&lt;namedCaches&gt; — Element (ustawienia pamięci podręcznej)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d6f741f4ecd3ea52dacc9f981024690a0031a533
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611090"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="618f0-102">&lt;namedCaches&gt; — Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="618f0-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="618f0-103">Określa kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="618f0-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="618f0-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Właściwości odwołuje się zestaw ustawień konfiguracji z co najmniej jeden `namedCaches` elementy pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="618f0-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="618f0-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="618f0-105">\<configuration></span></span>  
<span data-ttu-id="618f0-106">\< System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="618f0-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="618f0-107">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="618f0-107">\<memoryCache></span></span>  
<span data-ttu-id="618f0-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="618f0-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618f0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="618f0-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="618f0-110">Typ</span><span class="sxs-lookup"><span data-stu-id="618f0-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="618f0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="618f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="618f0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="618f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="618f0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="618f0-113">Attributes</span></span>  
  
|<span data-ttu-id="618f0-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="618f0-114">Attribute</span></span>|<span data-ttu-id="618f0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="618f0-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="618f0-116">Wartość całkowitą, która określa maksymalny dozwolony rozmiar w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> może zwiększyć się.</span><span class="sxs-lookup"><span data-stu-id="618f0-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="618f0-117">Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="618f0-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="618f0-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="618f0-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="618f0-119">Wartość całkowitą pomiędzy 0 a 100 określającą maksymalną wartość procentową fizycznie zainstalowanym komputerze pamięci, które mogą być używane przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="618f0-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="618f0-120">Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="618f0-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="618f0-121">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="618f0-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="618f0-122">Ta wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="618f0-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="618f0-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="618f0-123">Child Elements</span></span>  
  
|<span data-ttu-id="618f0-124">Element</span><span class="sxs-lookup"><span data-stu-id="618f0-124">Element</span></span>|<span data-ttu-id="618f0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="618f0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="618f0-126">\<add></span><span class="sxs-lookup"><span data-stu-id="618f0-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="618f0-127">Dodaje nazwaną pamięć podręczną do `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="618f0-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="618f0-128">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="618f0-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="618f0-129">Czyści `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="618f0-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="618f0-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="618f0-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="618f0-131">Usuwa wpis nazwaną pamięć podręczną z `namedCaches` kolekcji w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="618f0-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="618f0-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="618f0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="618f0-133">Element</span><span class="sxs-lookup"><span data-stu-id="618f0-133">Element</span></span>|<span data-ttu-id="618f0-134">Opis</span><span class="sxs-lookup"><span data-stu-id="618f0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="618f0-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="618f0-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="618f0-136">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="618f0-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="618f0-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="618f0-137">Remarks</span></span>  
 <span data-ttu-id="618f0-138">Sekcja konfiguracji pamięci podręcznej pamięci w pliku Web.config może zawierać `add`, `remove`, i `clear` atrybuty dla `namedCaches` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="618f0-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="618f0-139">Każdy `namedCaches` wpis jest unikatowo identyfikowana przez `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="618f0-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="618f0-140">Odwoływanie się do informacji w plikach konfiguracji aplikacji można pobrać wystąpień wpisy w pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="618f0-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="618f0-141">Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="618f0-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="618f0-142">Domyślne wystąpienie pamięci podręcznej jest wystąpieniem, który jest zwracany z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="618f0-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="618f0-143">Jeśli ustawiono atrybut name "domyślne", element używa domyślnego wystąpienia pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="618f0-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="618f0-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="618f0-144">Example</span></span>  
 <span data-ttu-id="618f0-145">Poniższy przykład pokazuje, jak ustawić nazwę pamięci podręcznej domyślną nazwę wpisu pamięci podręcznej, ustawiając `name` atrybutu "default".</span><span class="sxs-lookup"><span data-stu-id="618f0-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="618f0-146">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="618f0-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="618f0-147">Ustawienia te atrybuty zero oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane.</span><span class="sxs-lookup"><span data-stu-id="618f0-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="618f0-148">Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="618f0-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="618f0-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="618f0-149">See Also</span></span>  
- [<span data-ttu-id="618f0-150">\<memoryCache >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="618f0-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
