---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 872084dabc5d345d10a39f0933ff2ef30ca40355
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584479"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="3a323-102">\<memoryCache >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="3a323-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="3a323-103">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a323-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="3a323-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Klasa definiuje [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element, który służy do konfigurowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3a323-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="3a323-105">Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy mogą być używane w jednej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a323-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="3a323-106">Każdy `memoryCache` elementu w pliku konfiguracji mogą zawierać ustawienia dla nazwane <xref:System.Runtime.Caching.MemoryCache> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3a323-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="3a323-107">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3a323-107">\<configuration></span></span>  
<span data-ttu-id="3a323-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3a323-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="3a323-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="3a323-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a323-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a323-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="3a323-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3a323-111">Type</span></span>  
 <span data-ttu-id="3a323-112"><xref:System.Runtime.Caching.MemoryCache> Klasa.</span><span class="sxs-lookup"><span data-stu-id="3a323-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a323-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a323-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3a323-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a323-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a323-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a323-115">Attributes</span></span>  
  
|<span data-ttu-id="3a323-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a323-116">Attribute</span></span>|<span data-ttu-id="3a323-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3a323-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="3a323-118">Maksymalny rozmiar pamięci, w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektów może zwiększyć się.</span><span class="sxs-lookup"><span data-stu-id="3a323-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="3a323-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a323-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="3a323-120">Nazwa konfiguracji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3a323-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="3a323-121">Procent pamięci fizycznej używanej przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="3a323-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="3a323-122">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a323-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="3a323-123">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3a323-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="3a323-124">Wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="3a323-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a323-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a323-125">Child Elements</span></span>  
  
|<span data-ttu-id="3a323-126">Element</span><span class="sxs-lookup"><span data-stu-id="3a323-126">Element</span></span>|<span data-ttu-id="3a323-127">Opis</span><span class="sxs-lookup"><span data-stu-id="3a323-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a323-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="3a323-128">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="3a323-129">Zawiera kolekcję ustawień konfiguracji `namedCache` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3a323-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a323-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a323-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3a323-131">Element</span><span class="sxs-lookup"><span data-stu-id="3a323-131">Element</span></span>|<span data-ttu-id="3a323-132">Opis</span><span class="sxs-lookup"><span data-stu-id="3a323-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a323-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3a323-133">\<system.runtime.caching></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="3a323-134">Zawiera typy, które pozwalają na implementowanie buforowania danych wyjściowych w aplikacjach, które są wbudowane w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a323-134">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a323-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a323-135">Remarks</span></span>  
 <span data-ttu-id="3a323-136"><xref:System.Runtime.Caching.MemoryCache> Klasa jest konkretną implementację abstrakcyjnej <xref:System.Runtime.Caching.ObjectCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a323-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="3a323-137">Wystąpienia elementu <xref:System.Runtime.Caching.MemoryCache> klasy mogą być dostarczane za pomocą informacji o konfiguracji z plików konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a323-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="3a323-138">[MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) sekcja konfiguracji zawiera `namedCaches` konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="3a323-138">The [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="3a323-139">Po zainicjowaniu obiektu pamięci podręcznej na podstawie pamięci najpierw podejmie próbę odnalezienia `namedCaches` wpis, który jest zgodna z nazwą parametru, który jest przekazywany do konstruktora pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="3a323-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="3a323-140">Jeśli `namedCaches` znajduje się wpis, sondowania i informacje o zarządzaniu pamięci są pobierane z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a323-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="3a323-141">Proces inicjowania Określa, czy wszystkie wpisy konfiguracji zostały zastąpione, za pomocą opcjonalnych kolekcję par nazwa/wartość informacji o konfiguracji w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="3a323-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="3a323-142">Jeśli jeden z następujących wartości są przekazywane w kolekcji par nazwa/wartość, te wartości zastąpić informacjami uzyskanymi z pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="3a323-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="3a323-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a323-143">Example</span></span>  
 <span data-ttu-id="3a323-144">Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiekt do domyślnej nazwy obiektu pamięci podręcznej, ustawiając `name` atrybutu "default".</span><span class="sxs-lookup"><span data-stu-id="3a323-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="3a323-145">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryLimitPercentage` atrybutu jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="3a323-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="3a323-146">Ustawienia te atrybuty zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="3a323-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="3a323-147">Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="3a323-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a323-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a323-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="3a323-149">\<system.runtime.caching> Element (Cache Settings)</span><span class="sxs-lookup"><span data-stu-id="3a323-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="3a323-150">\<namedCaches >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="3a323-150">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
