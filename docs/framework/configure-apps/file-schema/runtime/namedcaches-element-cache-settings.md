---
title: <namedCaches>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153961"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="c9c1e-102">\<namedCaches>, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c9c1e-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="c9c1e-103">Określa kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="c9c1e-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Właściwość odwołuje się do kolekcji ustawień konfiguracji z co najmniej jednego `namedCaches` elementu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="c9c1e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9c1e-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c9c1e-106">Typ</span><span class="sxs-lookup"><span data-stu-id="c9c1e-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c1e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9c1e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c1e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c1e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9c1e-109">Attributes</span></span>  
  
|<span data-ttu-id="c9c1e-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9c1e-110">Attribute</span></span>|<span data-ttu-id="c9c1e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c9c1e-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="c9c1e-112">Wartość całkowita, która określa maksymalny dopuszczalny rozmiar (w megabajtach), do którego wystąpienie <xref:System.Runtime.Caching.MemoryCache> może się rozwijać.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c9c1e-113">Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne autozmiany rozmiarów <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="c9c1e-114">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="c9c1e-115">Wartość całkowita z zakresu od 0 do 100, która określa maksymalną wartość procentową fizycznie zainstalowanej pamięci komputera, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c9c1e-116">Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne autozmiany rozmiarów <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="c9c1e-117">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c9c1e-118">Ta wartość jest wprowadzana w formacie "gg: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="c9c1e-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9c1e-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9c1e-119">Child Elements</span></span>  
  
|<span data-ttu-id="c9c1e-120">Element</span><span class="sxs-lookup"><span data-stu-id="c9c1e-120">Element</span></span>|<span data-ttu-id="c9c1e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c9c1e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="c9c1e-122">Dodaje nazwaną pamięć podręczną do `namedCaches` kolekcji dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="c9c1e-123">Czyści `namedCaches` kolekcję dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="c9c1e-124">Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c1e-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9c1e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c1e-126">Element</span><span class="sxs-lookup"><span data-stu-id="c9c1e-126">Element</span></span>|<span data-ttu-id="c9c1e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="c9c1e-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="c9c1e-128">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="c9c1e-129">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="c9c1e-130">Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9c1e-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9c1e-131">Remarks</span></span>  
 <span data-ttu-id="c9c1e-132">Sekcja konfiguracja pamięci podręcznej pamięci w pliku Web. config może `add` zawierać `remove` `clear` atrybuty dla kolekcji, i `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="c9c1e-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="c9c1e-133">Każdy `namedCaches` wpis jest jednoznacznie identyfikowany przez `name` atrybut.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="c9c1e-134">Wystąpienia wpisów pamięci podręcznej pamięci można pobrać, odwołując się do informacji w plikach konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="c9c1e-135">Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="c9c1e-136">Domyślne wystąpienie pamięci podręcznej jest wystąpieniem zwracanym z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="c9c1e-137">Jeśli ustawisz atrybut name na "default", element używa domyślnego wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c1e-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9c1e-138">Example</span></span>  
 <span data-ttu-id="c9c1e-139">Poniższy przykład pokazuje, jak ustawić nazwę pamięci podręcznej na domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="c9c1e-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c9c1e-140">`cacheMemoryLimitMegabytes`Atrybut i `physicalMemoryPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c9c1e-141">Ustawienie tych atrybutów na zero oznacza, że używane są heurystyke autowymiarowania <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="c9c1e-142">Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9c1e-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9c1e-143">See also</span></span>

- [<span data-ttu-id="c9c1e-144">\<memoryCache>— Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c9c1e-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
