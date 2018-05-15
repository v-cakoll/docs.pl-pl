---
title: '&lt;memoryCache&gt; elementu (ustawienia pamięci podręcznej)'
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d0d741fd8193c7d874d70248cbd149f11163ed0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmemorycachegt-element-cache-settings"></a><span data-ttu-id="d2dc2-102">&lt;memoryCache&gt; elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="d2dc2-102">&lt;memoryCache&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="d2dc2-103">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="d2dc2-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Klasa definiuje [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) elementu, którego można użyć do skonfigurowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="d2dc2-105">Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasa może być używana w pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="d2dc2-106">Każdy `memoryCache` w pliku konfiguracji może zawierać ustawienia dla nazwane <xref:System.Runtime.Caching.MemoryCache> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="d2dc2-107">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d2dc2-107">\<configuration></span></span>  
<span data-ttu-id="d2dc2-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="d2dc2-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="d2dc2-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="d2dc2-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2dc2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2dc2-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="d2dc2-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d2dc2-111">Type</span></span>  
 <span data-ttu-id="d2dc2-112"><xref:System.Runtime.Caching.MemoryCache> Klasa.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2dc2-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2dc2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d2dc2-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2dc2-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2dc2-115">Attributes</span></span>  
  
|<span data-ttu-id="d2dc2-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2dc2-116">Attribute</span></span>|<span data-ttu-id="d2dc2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d2dc2-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="d2dc2-118">Maksymalny rozmiar pamięci, wyrażony w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektu odpowiednio do.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="d2dc2-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize klasy.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="d2dc2-120">Nazwa konfiguracji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="d2dc2-121">Procent pamięci fizycznej używanej przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="d2dc2-122">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize klasy.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="d2dc2-123">Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="d2dc2-124">Wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="d2dc2-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2dc2-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2dc2-125">Child Elements</span></span>  
  
|<span data-ttu-id="d2dc2-126">Element</span><span class="sxs-lookup"><span data-stu-id="d2dc2-126">Element</span></span>|<span data-ttu-id="d2dc2-127">Opis</span><span class="sxs-lookup"><span data-stu-id="d2dc2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2dc2-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="d2dc2-128">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="d2dc2-129">Zawiera kolekcję ustawień konfiguracji `namedCache` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2dc2-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2dc2-130">Parent Elements</span></span>  
  
|<span data-ttu-id="d2dc2-131">Element</span><span class="sxs-lookup"><span data-stu-id="d2dc2-131">Element</span></span>|<span data-ttu-id="d2dc2-132">Opis</span><span class="sxs-lookup"><span data-stu-id="d2dc2-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2dc2-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="d2dc2-133">\<system.runtime.caching></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="d2dc2-134">Zawiera typy, które pozwalają na wdrożenie buforowanie danych wyjściowych w aplikacjach, które są wbudowane w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2dc2-134">Contains types that let you implement output caching in applications that are built into the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2dc2-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2dc2-135">Remarks</span></span>  
 <span data-ttu-id="d2dc2-136"><xref:System.Runtime.Caching.MemoryCache> Konkretną implementację klasy abstrakcyjnej jest klasa <xref:System.Runtime.Caching.ObjectCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="d2dc2-137">Wystąpienia <xref:System.Runtime.Caching.MemoryCache> klasy można podać informacje o konfiguracji z pliki konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="d2dc2-138">[MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) sekcja konfiguracji zawiera `namedCaches` konfiguracji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-138">The [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="d2dc2-139">Po zainicjowaniu obiektu oparty na pamięci podręcznej po raz pierwszy próbuje odnaleźć `namedCaches` wpis, który odpowiada nazwie w parametr, który jest przekazywany do konstruktora pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="d2dc2-140">Jeśli `namedCaches` można odnaleźć wpisu, sondowania i informacji o zarządzaniu pamięci są pobierane z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="d2dc2-141">Proces inicjowania Określa, czy wszystkie pozycje konfiguracji zostały zastąpione, za pomocą opcjonalnych kolekcja par nazwa/wartość informacji o konfiguracji w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="d2dc2-142">Jeśli jeden z następujących wartości przekazywane w kolekcji par nazwa/wartość, te wartości zastąpić informacjami uzyskanymi z pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="d2dc2-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="d2dc2-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2dc2-143">Example</span></span>  
 <span data-ttu-id="d2dc2-144">Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiekt do domyślnej nazwy obiektu pamięci podręcznej przez ustawienie `name` atrybutu "default".</span><span class="sxs-lookup"><span data-stu-id="d2dc2-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="d2dc2-145">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryLimitPercentage` atrybutu zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="d2dc2-146">Ustawienia te atrybuty zero oznacza <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="d2dc2-147">Implementacja pamięci podręcznej należy porównać bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="d2dc2-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2dc2-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2dc2-148">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 [<span data-ttu-id="d2dc2-149">\<system.runtime.caching> Element (Cache Settings)</span><span class="sxs-lookup"><span data-stu-id="d2dc2-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [<span data-ttu-id="d2dc2-150">\<namedCaches > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="d2dc2-150">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
