---
title: <namedCaches>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252462"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="93e6f-102">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="93e6f-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="93e6f-103">Określa kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="93e6f-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="93e6f-104">Właściwość odwołuje się do kolekcji ustawień konfiguracji z co najmniej jednego `namedCaches` elementu pliku konfiguracji. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A></span><span class="sxs-lookup"><span data-stu-id="93e6f-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="93e6f-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93e6f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93e6f-106">&nbsp;&nbsp;[ **\<System. Runtime. buforowanie >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="93e6f-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="93e6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Elemencie MemoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="93e6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="93e6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedCaches >**</span><span class="sxs-lookup"><span data-stu-id="93e6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93e6f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="93e6f-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="93e6f-110">Typ</span><span class="sxs-lookup"><span data-stu-id="93e6f-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93e6f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93e6f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="93e6f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="93e6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93e6f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93e6f-113">Attributes</span></span>  
  
|<span data-ttu-id="93e6f-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="93e6f-114">Attribute</span></span>|<span data-ttu-id="93e6f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="93e6f-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="93e6f-116">Wartość całkowita, która określa maksymalny dopuszczalny rozmiar (w megabajtach), do którego wystąpienie <xref:System.Runtime.Caching.MemoryCache> może się rozwijać.</span><span class="sxs-lookup"><span data-stu-id="93e6f-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="93e6f-117">Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne <xref:System.Runtime.Caching.MemoryCache> autozmiany rozmiarów klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="93e6f-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="93e6f-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="93e6f-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="93e6f-119">Wartość całkowita z zakresu od 0 do 100, która określa maksymalną wartość procentową fizycznie zainstalowanej pamięci komputera, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="93e6f-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="93e6f-120">Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne <xref:System.Runtime.Caching.MemoryCache> autozmiany rozmiarów klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="93e6f-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="93e6f-121">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="93e6f-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="93e6f-122">Ta wartość jest wprowadzana w formacie "gg: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="93e6f-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93e6f-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93e6f-123">Child Elements</span></span>  
  
|<span data-ttu-id="93e6f-124">Element</span><span class="sxs-lookup"><span data-stu-id="93e6f-124">Element</span></span>|<span data-ttu-id="93e6f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="93e6f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93e6f-126">\<add></span><span class="sxs-lookup"><span data-stu-id="93e6f-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="93e6f-127">Dodaje nazwaną pamięć podręczną `namedCaches` do kolekcji dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="93e6f-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="93e6f-128">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="93e6f-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="93e6f-129">`namedCaches` Czyści kolekcję dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="93e6f-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="93e6f-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="93e6f-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="93e6f-131">Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="93e6f-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93e6f-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93e6f-132">Parent Elements</span></span>  
  
|<span data-ttu-id="93e6f-133">Element</span><span class="sxs-lookup"><span data-stu-id="93e6f-133">Element</span></span>|<span data-ttu-id="93e6f-134">Opis</span><span class="sxs-lookup"><span data-stu-id="93e6f-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93e6f-135">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="93e6f-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="93e6f-136">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93e6f-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="93e6f-137">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="93e6f-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="93e6f-138">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="93e6f-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="93e6f-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="93e6f-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="93e6f-140">Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93e6f-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93e6f-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93e6f-141">Remarks</span></span>  
 <span data-ttu-id="93e6f-142">Sekcja konfiguracja pamięci podręcznej pamięci w pliku Web. config może `add`zawierać `remove`atrybuty dla `clear` `namedCaches` kolekcji, i.</span><span class="sxs-lookup"><span data-stu-id="93e6f-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="93e6f-143">Każdy `namedCaches` wpis jest jednoznacznie identyfikowany `name` przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="93e6f-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="93e6f-144">Wystąpienia wpisów pamięci podręcznej pamięci można pobrać, odwołując się do informacji w plikach konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93e6f-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="93e6f-145">Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="93e6f-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="93e6f-146">Domyślne wystąpienie pamięci podręcznej jest wystąpieniem zwracanym z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="93e6f-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="93e6f-147">Jeśli ustawisz atrybut name na "default", element używa domyślnego wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="93e6f-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93e6f-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="93e6f-148">Example</span></span>  
 <span data-ttu-id="93e6f-149">Poniższy przykład pokazuje, jak ustawić nazwę pamięci podręcznej na domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="93e6f-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="93e6f-150">`cacheMemoryLimitMegabytes` Atrybut`physicalMemoryPercentage` i atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="93e6f-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="93e6f-151">Ustawienie tych atrybutów na zero oznacza, że używane są heurystyke <xref:System.Runtime.Caching.MemoryCache> autowymiarowania klasy.</span><span class="sxs-lookup"><span data-stu-id="93e6f-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="93e6f-152">Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="93e6f-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93e6f-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93e6f-153">See also</span></span>

- [<span data-ttu-id="93e6f-154">\<Elemencie MemoryCache >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="93e6f-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
