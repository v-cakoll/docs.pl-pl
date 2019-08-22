---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663618"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="3ec5e-102">\<Elemencie MemoryCache >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="3ec5e-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="3ec5e-103">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="3ec5e-104">Klasa definiuje element elemencie MemoryCache, którego można użyć do skonfigurowania pamięci podręcznej. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement></span><span class="sxs-lookup"><span data-stu-id="3ec5e-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="3ec5e-105">Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy może być używanych w pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="3ec5e-106">Każdy `memoryCache` element w pliku konfiguracji może zawierać ustawienia dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="3ec5e-107">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3ec5e-107">\<configuration></span></span>  
<span data-ttu-id="3ec5e-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3ec5e-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="3ec5e-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="3ec5e-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec5e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ec5e-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="3ec5e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3ec5e-111">Type</span></span>  
 <span data-ttu-id="3ec5e-112"><xref:System.Runtime.Caching.MemoryCache>określonej.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ec5e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ec5e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3ec5e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ec5e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ec5e-115">Attributes</span></span>  
  
|<span data-ttu-id="3ec5e-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ec5e-116">Attribute</span></span>|<span data-ttu-id="3ec5e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3ec5e-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="3ec5e-118">Maksymalny rozmiar pamięci (w megabajtach), w którym można zwiększyć wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="3ec5e-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="3ec5e-120">Nazwa konfiguracji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="3ec5e-121">Wartość procentowa pamięci fizycznej, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="3ec5e-122">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="3ec5e-123">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="3ec5e-124">Wartość jest wprowadzana w formacie "gg: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="3ec5e-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ec5e-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ec5e-125">Child Elements</span></span>  
  
|<span data-ttu-id="3ec5e-126">Element</span><span class="sxs-lookup"><span data-stu-id="3ec5e-126">Element</span></span>|<span data-ttu-id="3ec5e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="3ec5e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ec5e-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="3ec5e-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="3ec5e-129">Zawiera kolekcję ustawień konfiguracji dla tego `namedCache` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ec5e-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ec5e-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3ec5e-131">Element</span><span class="sxs-lookup"><span data-stu-id="3ec5e-131">Element</span></span>|<span data-ttu-id="3ec5e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="3ec5e-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ec5e-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3ec5e-133">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="3ec5e-134">Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-134">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ec5e-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ec5e-135">Remarks</span></span>  
 <span data-ttu-id="3ec5e-136">Klasa jest konkretną implementacją klasy abstrakcyjnej <xref:System.Runtime.Caching.ObjectCache>. <xref:System.Runtime.Caching.MemoryCache></span><span class="sxs-lookup"><span data-stu-id="3ec5e-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="3ec5e-137"><xref:System.Runtime.Caching.MemoryCache> Wystąpienia klasy mogą być dostarczane z informacjami o konfiguracji z plików konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="3ec5e-138">Sekcja konfiguracja [elemencie MemoryCache](memorycache-element-cache-settings.md) zawiera `namedCaches` kolekcję konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-138">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="3ec5e-139">Gdy obiekt pamięci podręcznej oparty na pamięci jest inicjowany, najpierw próbuje `namedCaches` znaleźć wpis pasujący do nazwy w parametrze, który jest przesyłany do konstruktora pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="3ec5e-140">W przypadku znalezienia wpisu informacje dotyczące sondowania i zarządzania pamięci są pobierane z pliku konfiguracyjnego. `namedCaches`</span><span class="sxs-lookup"><span data-stu-id="3ec5e-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="3ec5e-141">Następnie proces inicjowania określa, czy wszystkie wpisy konfiguracji zostały zastąpione, przy użyciu opcjonalnej kolekcji par nazwa/wartość informacji o konfiguracji w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="3ec5e-142">W przypadku przekazania jednej z następujących wartości w kolekcji nazwa/wartość te wartości zastępują informacje uzyskane z pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="3ec5e-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="3ec5e-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ec5e-143">Example</span></span>  
 <span data-ttu-id="3ec5e-144">Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiektu na domyślną nazwę obiektu pamięci podręcznej przez `name` ustawienie atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="3ec5e-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="3ec5e-145">`cacheMemoryLimitMegabytes` Atrybut`physicalMemoryLimitPercentage` i atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="3ec5e-146">Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="3ec5e-147">Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="3ec5e-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ec5e-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ec5e-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="3ec5e-149">\<system.runtime.caching> Element (Cache Settings)</span><span class="sxs-lookup"><span data-stu-id="3ec5e-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="3ec5e-150">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="3ec5e-150">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
