---
title: <namedCaches>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153961"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="c4749-102">\<namedCaches> Element (Ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c4749-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="c4749-103">Określa zbiór ustawień konfiguracji dla <xref:System.Runtime.Caching.MemoryCache> nazwanych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c4749-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="c4749-104">Właściwość <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> odwołuje się do kolekcji ustawień `namedCaches` konfiguracji z jednego lub więcej elementów pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4749-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="c4749-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4749-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4749-106">&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4749-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="c4749-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4749-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="c4749-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nazwaneCaches>**</span><span class="sxs-lookup"><span data-stu-id="c4749-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4749-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4749-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c4749-110">Typ</span><span class="sxs-lookup"><span data-stu-id="c4749-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4749-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c4749-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c4749-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c4749-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4749-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c4749-113">Attributes</span></span>  
  
|<span data-ttu-id="c4749-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c4749-114">Attribute</span></span>|<span data-ttu-id="c4749-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c4749-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="c4749-116">Wartość całkowita określająca maksymalny dopuszczalny rozmiar w megabajtach, <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c4749-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c4749-117">Wartość domyślna to 0, co oznacza, że heurystyka automatycznego <xref:System.Runtime.Caching.MemoryCache> rozmiaru klasy jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c4749-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="c4749-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="c4749-119">Wartość całkowita z przedziału od 0 do 100, która określa maksymalny procent fizycznie zainstalowanej pamięci komputera, która może być zużywana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="c4749-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c4749-120">Wartość domyślna to 0, co oznacza, że heurystyka automatycznego <xref:System.Runtime.Caching.MemoryCache> rozmiaru klasy jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c4749-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="c4749-121">Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c4749-122">Ta wartość jest wprowadzana w formacie "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="c4749-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4749-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c4749-123">Child Elements</span></span>  
  
|<span data-ttu-id="c4749-124">Element</span><span class="sxs-lookup"><span data-stu-id="c4749-124">Element</span></span>|<span data-ttu-id="c4749-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c4749-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4749-126">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="c4749-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="c4749-127">Dodaje nazwaną pamięć `namedCaches` podręczną do kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="c4749-128">\<wyraźne></span><span class="sxs-lookup"><span data-stu-id="c4749-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="c4749-129">Czyści `namedCaches` kolekcję dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="c4749-130">\<usuń></span><span class="sxs-lookup"><span data-stu-id="c4749-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="c4749-131">Usuwa wpis nazwanej pamięci `namedCaches` podręcznej z kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4749-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c4749-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c4749-133">Element</span><span class="sxs-lookup"><span data-stu-id="c4749-133">Element</span></span>|<span data-ttu-id="c4749-134">Opis</span><span class="sxs-lookup"><span data-stu-id="c4749-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4749-135">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="c4749-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="c4749-136">Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4749-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="c4749-137">\<>memoryCache</span><span class="sxs-lookup"><span data-stu-id="c4749-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="c4749-138">Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie.</span><span class="sxs-lookup"><span data-stu-id="c4749-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="c4749-139">\<>system.runtime.caching</span><span class="sxs-lookup"><span data-stu-id="c4749-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="c4749-140">Zawiera typy, które umożliwiają implementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4749-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4749-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4749-141">Remarks</span></span>  
 <span data-ttu-id="c4749-142">Sekcja konfiguracji pamięci podręcznej pliku Web.config `remove`może `clear` zawierać `add` `namedCaches` i atrybuty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c4749-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="c4749-143">Każdy `namedCaches` wpis jest jednoznacznie `name` identyfikowany przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="c4749-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="c4749-144">Można pobrać wystąpienia wpisów pamięci podręcznej, odwołując się do informacji w plikach konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4749-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="c4749-145">Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="c4749-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="c4749-146">Domyślne wystąpienie pamięci podręcznej jest <xref:System.Runtime.Caching.MemoryCache.Default%2A> wystąpienie, które jest zwracane z właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4749-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="c4749-147">Jeśli ustawisz atrybut name na "default", element używa domyślnego wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c4749-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4749-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4749-148">Example</span></span>  
 <span data-ttu-id="c4749-149">W poniższym przykładzie pokazano, jak ustawić nazwę pamięci podręcznej `name` na domyślną nazwę wpisu pamięci podręcznej, ustawiając atrybut na "domyślny".</span><span class="sxs-lookup"><span data-stu-id="c4749-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c4749-150">Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="c4749-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c4749-151">Ustawienie tych atrybutów na zero oznacza, że używane <xref:System.Runtime.Caching.MemoryCache> są heurystyki autosizing klasy.</span><span class="sxs-lookup"><span data-stu-id="c4749-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="c4749-152">Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="c4749-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4749-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4749-153">See also</span></span>

- [<span data-ttu-id="c4749-154">\<MemoryCache> Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c4749-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
