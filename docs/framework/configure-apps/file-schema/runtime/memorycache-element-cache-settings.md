---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153987"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="f31f1-102">\<MemoryCache> Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="f31f1-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="f31f1-103">Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie.</span><span class="sxs-lookup"><span data-stu-id="f31f1-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="f31f1-104">Klasa <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> definiuje [memoryCache](memorycache-element-cache-settings.md) element, który służy do konfigurowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f31f1-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="f31f1-105">Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy może służyć w jednej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f31f1-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="f31f1-106">Każdy `memoryCache` element w pliku konfiguracji może <xref:System.Runtime.Caching.MemoryCache> zawierać ustawienia dla nazwanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f31f1-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="f31f1-107">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f31f1-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f31f1-108">&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f31f1-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="f31f1-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<>memoryCache**</span><span class="sxs-lookup"><span data-stu-id="f31f1-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f31f1-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f31f1-110">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="f31f1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f31f1-111">Type</span></span>  
 <span data-ttu-id="f31f1-112"><xref:System.Runtime.Caching.MemoryCache>Klasa.</span><span class="sxs-lookup"><span data-stu-id="f31f1-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f31f1-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f31f1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f31f1-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f31f1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f31f1-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f31f1-115">Attributes</span></span>  
  
|<span data-ttu-id="f31f1-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f31f1-116">Attribute</span></span>|<span data-ttu-id="f31f1-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f31f1-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="f31f1-118">Maksymalny rozmiar pamięci w megabajtach, <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f31f1-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="f31f1-119">Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że heurystyka autosize klasy jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f31f1-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="f31f1-120">Nazwa konfiguracji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f31f1-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="f31f1-121">Procent pamięci fizycznej, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="f31f1-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="f31f1-122">Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że heurystyka autosize klasy jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f31f1-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="f31f1-123">Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f31f1-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="f31f1-124">Wartość jest wprowadzana w formacie "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="f31f1-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f31f1-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f31f1-125">Child Elements</span></span>  
  
|<span data-ttu-id="f31f1-126">Element</span><span class="sxs-lookup"><span data-stu-id="f31f1-126">Element</span></span>|<span data-ttu-id="f31f1-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f31f1-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f31f1-128">\<nazwaneCaches></span><span class="sxs-lookup"><span data-stu-id="f31f1-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="f31f1-129">Zawiera kolekcję ustawień konfiguracji `namedCache` dla wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f31f1-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f31f1-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f31f1-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f31f1-131">Element</span><span class="sxs-lookup"><span data-stu-id="f31f1-131">Element</span></span>|<span data-ttu-id="f31f1-132">Opis</span><span class="sxs-lookup"><span data-stu-id="f31f1-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f31f1-133">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="f31f1-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="f31f1-134">Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f31f1-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="f31f1-135">\<>system.runtime.caching</span><span class="sxs-lookup"><span data-stu-id="f31f1-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="f31f1-136">Zawiera typy, które umożliwiają implementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f31f1-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f31f1-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f31f1-137">Remarks</span></span>  
 <span data-ttu-id="f31f1-138">Klasa <xref:System.Runtime.Caching.MemoryCache> jest konkretną implementacją <xref:System.Runtime.Caching.ObjectCache> klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="f31f1-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="f31f1-139">Wystąpienia <xref:System.Runtime.Caching.MemoryCache> klasy mogą być dostarczane z informacjami o konfiguracji z plików konfiguracyjnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f31f1-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="f31f1-140">Sekcja konfiguracji [memoryCache](memorycache-element-cache-settings.md) `namedCaches` zawiera kolekcję konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f31f1-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="f31f1-141">Po zainicjowaniu obiektu pamięci podręcznej, najpierw próbuje `namedCaches` znaleźć wpis, który pasuje do nazwy w parametrze, który jest przekazywany do konstruktora pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f31f1-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="f31f1-142">Jeśli `namedCaches` zostanie znaleziony wpis, informacje o sondowaniu i zarządzaniu pamięcią są pobierane z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f31f1-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="f31f1-143">Proces inicjowania następnie określa, czy wszystkie wpisy konfiguracji zostały zastąpione przy użyciu opcjonalnej kolekcji par nazw/wartości informacji o konfiguracji w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="f31f1-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="f31f1-144">Jeśli przekażesz jedną z następujących wartości w kolekcji pary nazwa/wartość, te wartości zastępują informacje uzyskane z pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f31f1-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="f31f1-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="f31f1-145">Example</span></span>  
 <span data-ttu-id="f31f1-146">W poniższym przykładzie pokazano, <xref:System.Runtime.Caching.MemoryCache> jak ustawić nazwę obiektu na `name` domyślną nazwę obiektu pamięci podręcznej, ustawiając atrybut na "Domyślny".</span><span class="sxs-lookup"><span data-stu-id="f31f1-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="f31f1-147">Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryLimitPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="f31f1-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="f31f1-148">Ustawienie tych atrybutów na <xref:System.Runtime.Caching.MemoryCache> zero oznacza, że heurystyka automatycznego szesnasty są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f31f1-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="f31f1-149">Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci z bezwzględnych i procentowych limitów pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="f31f1-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f31f1-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f31f1-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="f31f1-151">\<element> system.runtime.caching (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="f31f1-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="f31f1-152">\<namedCaches> Element (Ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="f31f1-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
