---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153987"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="7fa61-102">\<memoryCache>, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="7fa61-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="7fa61-103">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="7fa61-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="7fa61-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement>Klasa definiuje element [elemencie MemoryCache](memorycache-element-cache-settings.md) , którego można użyć do skonfigurowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7fa61-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="7fa61-105">Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy może być używanych w pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fa61-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="7fa61-106">Każdy `memoryCache` element w pliku konfiguracji może zawierać ustawienia dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7fa61-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="7fa61-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fa61-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="7fa61-108">Typ</span><span class="sxs-lookup"><span data-stu-id="7fa61-108">Type</span></span>  
 <span data-ttu-id="7fa61-109"><xref:System.Runtime.Caching.MemoryCache>określonej.</span><span class="sxs-lookup"><span data-stu-id="7fa61-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fa61-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7fa61-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7fa61-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7fa61-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fa61-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7fa61-112">Attributes</span></span>  
  
|<span data-ttu-id="7fa61-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7fa61-113">Attribute</span></span>|<span data-ttu-id="7fa61-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7fa61-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="7fa61-115">Maksymalny rozmiar pamięci (w megabajtach), w którym <xref:System.Runtime.Caching.MemoryCache> można zwiększyć wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fa61-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="7fa61-116">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fa61-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="7fa61-117">Nazwa konfiguracji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7fa61-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="7fa61-118">Wartość procentowa pamięci fizycznej, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="7fa61-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="7fa61-119">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fa61-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="7fa61-120">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7fa61-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="7fa61-121">Wartość jest wprowadzana w formacie "gg: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="7fa61-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fa61-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7fa61-122">Child Elements</span></span>  
  
|<span data-ttu-id="7fa61-123">Element</span><span class="sxs-lookup"><span data-stu-id="7fa61-123">Element</span></span>|<span data-ttu-id="7fa61-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7fa61-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="7fa61-125">Zawiera kolekcję ustawień konfiguracji dla tego `namedCache` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7fa61-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fa61-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7fa61-126">Parent Elements</span></span>  
  
|<span data-ttu-id="7fa61-127">Element</span><span class="sxs-lookup"><span data-stu-id="7fa61-127">Element</span></span>|<span data-ttu-id="7fa61-128">Opis</span><span class="sxs-lookup"><span data-stu-id="7fa61-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="7fa61-129">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fa61-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="7fa61-130">Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fa61-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fa61-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fa61-131">Remarks</span></span>  
 <span data-ttu-id="7fa61-132"><xref:System.Runtime.Caching.MemoryCache>Klasa jest konkretną implementacją klasy abstrakcyjnej <xref:System.Runtime.Caching.ObjectCache> .</span><span class="sxs-lookup"><span data-stu-id="7fa61-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="7fa61-133">Wystąpienia <xref:System.Runtime.Caching.MemoryCache> klasy mogą być dostarczane z informacjami o konfiguracji z plików konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fa61-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="7fa61-134">Sekcja konfiguracja [elemencie MemoryCache](memorycache-element-cache-settings.md) zawiera `namedCaches` kolekcję konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7fa61-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="7fa61-135">Gdy obiekt pamięci podręcznej oparty na pamięci jest inicjowany, najpierw próbuje znaleźć `namedCaches` wpis pasujący do nazwy w parametrze, który jest przesyłany do konstruktora pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7fa61-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="7fa61-136">W przypadku `namedCaches` znalezienia wpisu informacje dotyczące sondowania i zarządzania pamięci są pobierane z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="7fa61-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="7fa61-137">Następnie proces inicjowania określa, czy wszystkie wpisy konfiguracji zostały zastąpione, przy użyciu opcjonalnej kolekcji par nazwa/wartość informacji o konfiguracji w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="7fa61-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="7fa61-138">W przypadku przekazania jednej z następujących wartości w kolekcji nazwa/wartość te wartości zastępują informacje uzyskane z pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="7fa61-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="7fa61-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fa61-139">Example</span></span>  
 <span data-ttu-id="7fa61-140">Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiektu na domyślną nazwę obiektu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="7fa61-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="7fa61-141">`cacheMemoryLimitMegabytes`Atrybut i `physicalMemoryLimitPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="7fa61-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="7fa61-142">Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fa61-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="7fa61-143">Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="7fa61-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fa61-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fa61-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="7fa61-145">\<system.runtime.caching>— Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="7fa61-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="7fa61-146">\<namedCaches>— Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="7fa61-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
