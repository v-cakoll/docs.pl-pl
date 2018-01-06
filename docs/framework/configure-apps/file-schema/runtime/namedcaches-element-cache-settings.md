---
title: "&lt;namedCaches&gt; elementu (ustawienia pamięci podręcznej)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7c25f0039f75ba1c736cff946dbaaff9252dc93e
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="44948-102">&lt;namedCaches&gt; elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="44948-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="44948-103">Określa kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="44948-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="44948-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Właściwość odwołuje się zestaw ustawień konfiguracji z jednego lub kilku `namedCaches` elementów w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="44948-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="44948-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="44948-105">\<configuration></span></span>  
<span data-ttu-id="44948-106">\<System.Runtime.Caching — ></span><span class="sxs-lookup"><span data-stu-id="44948-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="44948-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="44948-107">\<memoryCache></span></span>  
<span data-ttu-id="44948-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="44948-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44948-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="44948-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="44948-110">Typ</span><span class="sxs-lookup"><span data-stu-id="44948-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44948-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44948-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44948-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44948-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44948-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44948-113">Attributes</span></span>  
  
|<span data-ttu-id="44948-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44948-114">Attribute</span></span>|<span data-ttu-id="44948-115">Opis</span><span class="sxs-lookup"><span data-stu-id="44948-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="44948-116">Wartość całkowita określająca maksymalny dozwolony rozmiar w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> odpowiednio do.</span><span class="sxs-lookup"><span data-stu-id="44948-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="44948-117">Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="44948-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="44948-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44948-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="44948-119">Wartość całkowitą pomiędzy 0 a 100 określająca maksymalny procent pamięci fizycznie zainstalowanym komputerze, który może być zużyte przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="44948-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="44948-120">Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="44948-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="44948-121">Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44948-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="44948-122">Ta wartość jest wprowadzana w formacie "Gg".</span><span class="sxs-lookup"><span data-stu-id="44948-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44948-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44948-123">Child Elements</span></span>  
  
|<span data-ttu-id="44948-124">Element</span><span class="sxs-lookup"><span data-stu-id="44948-124">Element</span></span>|<span data-ttu-id="44948-125">Opis</span><span class="sxs-lookup"><span data-stu-id="44948-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44948-126">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="44948-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="44948-127">Dodaje nazwany pamięci podręcznej, aby `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44948-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="44948-128">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="44948-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="44948-129">Czyści `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44948-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="44948-130">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="44948-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="44948-131">Usuwa wpis w pamięci podręcznej o nazwie z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44948-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44948-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44948-132">Parent Elements</span></span>  
  
|<span data-ttu-id="44948-133">Element</span><span class="sxs-lookup"><span data-stu-id="44948-133">Element</span></span>|<span data-ttu-id="44948-134">Opis</span><span class="sxs-lookup"><span data-stu-id="44948-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44948-135">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="44948-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="44948-136">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="44948-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44948-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44948-137">Remarks</span></span>  
 <span data-ttu-id="44948-138">Sekcja konfiguracji pamięci podręcznej pamięci w pliku Web.config może zawierać `add`, `remove`, i `clear` atrybutów `namedCaches` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="44948-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="44948-139">Każdy `namedCaches` wpis jest unikatowo identyfikowana przez `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="44948-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="44948-140">Za pomocą odwołań do informacji w plikach konfiguracji aplikacji można pobrać wystąpień wpisy w pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="44948-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="44948-141">Domyślnie tylko domyślnego wystąpienia pamięci podręcznej ma wpis w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="44948-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="44948-142">Domyślne wystąpienie pamięci podręcznej jest wystąpienia, która jest zwracana z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="44948-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="44948-143">Jeśli zostanie ustawiony atrybut name "default", element używa domyślnego wystąpienia pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="44948-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44948-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="44948-144">Example</span></span>  
 <span data-ttu-id="44948-145">Poniższy przykład przedstawia sposób ustawioną domyślną nazwę wpisu pamięci podręcznej nazwę pamięci podręcznej przez ustawienie `name` atrybutu "default".</span><span class="sxs-lookup"><span data-stu-id="44948-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="44948-146">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="44948-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="44948-147">Ustawienie tych atrybutów na zero oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane.</span><span class="sxs-lookup"><span data-stu-id="44948-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="44948-148">Implementacja pamięci podręcznej porównuje bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="44948-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44948-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44948-149">See Also</span></span>  
 [<span data-ttu-id="44948-150">\<memoryCache > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="44948-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
