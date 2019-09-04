---
title: <add>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252890"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="a366b-102">\<add> Element for \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="a366b-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="a366b-103">`namedCache` Dodaje wpis`namedCaches` do kolekcji dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="a366b-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="a366b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a366b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a366b-105">&nbsp;&nbsp;[ **\<System. Runtime. buforowanie >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a366b-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="a366b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Elemencie MemoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a366b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="a366b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a366b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="a366b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="a366b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a366b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a366b-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="a366b-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a366b-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a366b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a366b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a366b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a366b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a366b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a366b-113">Attributes</span></span>  
  
|<span data-ttu-id="a366b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a366b-114">Attribute</span></span>|<span data-ttu-id="a366b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a366b-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="a366b-116">Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach), do którego wystąpienie <xref:System.Runtime.Caching.MemoryCache> może się rozwijać.</span><span class="sxs-lookup"><span data-stu-id="a366b-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="a366b-117">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autowymiarowania klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a366b-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="a366b-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a366b-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="a366b-119">Wartość całkowita z zakresu od 0 do 100, która określa maksymalną wartość procentową fizycznie zainstalowanej pamięci komputera, która może być używana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="a366b-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="a366b-120">Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autowymiarowania klasy są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a366b-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="a366b-121">Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a366b-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="a366b-122">Ta wartość jest wprowadzana w formacie "gg: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="a366b-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a366b-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a366b-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="a366b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a366b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a366b-125">Element</span><span class="sxs-lookup"><span data-stu-id="a366b-125">Element</span></span>|<span data-ttu-id="a366b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a366b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a366b-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="a366b-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="a366b-128">Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a366b-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a366b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a366b-129">Remarks</span></span>  
 <span data-ttu-id="a366b-130">Element dodaje wpis `namedCaches` do kolekcji dla pamięci podręcznej pamięci. `add`</span><span class="sxs-lookup"><span data-stu-id="a366b-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="a366b-131">Można użyć elementu [Clear](clear-element-for-namedcaches.md) przed użyciem `add` elementu, aby mieć pewność, że w kolekcji nie ma innych nazwanych pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="a366b-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="a366b-132">Ten element może być używany w pliku Machine. config i w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="a366b-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a366b-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="a366b-133">Example</span></span>  
 <span data-ttu-id="a366b-134">Poniższy przykład pokazuje, jak zdefiniować ustawienia domyślnego `namedCache` wpisu `namedCaches` do kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a366b-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a366b-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a366b-135">See also</span></span>

- [<span data-ttu-id="a366b-136">\<namedCaches >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="a366b-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
