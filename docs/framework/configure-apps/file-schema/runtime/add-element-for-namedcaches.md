---
title: <add>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154508"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="107d0-102">\<dodaj element> dla \<nazwanychcach></span><span class="sxs-lookup"><span data-stu-id="107d0-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="107d0-103">Dodaje `namedCache` wpis do `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="107d0-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="107d0-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="107d0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="107d0-105">&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="107d0-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="107d0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="107d0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="107d0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nazwaneCaches>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="107d0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="107d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="107d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107d0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="107d0-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="107d0-110">Typ</span><span class="sxs-lookup"><span data-stu-id="107d0-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="107d0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="107d0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="107d0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="107d0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="107d0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="107d0-113">Attributes</span></span>  
  
|<span data-ttu-id="107d0-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="107d0-114">Attribute</span></span>|<span data-ttu-id="107d0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="107d0-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="107d0-116">Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach), <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="107d0-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="107d0-117">Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że klasy autosizing heurystyki są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="107d0-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="107d0-118">Nazwa pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="107d0-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="107d0-119">Wartość całkowita z przedziału od 0 do 100, która określa maksymalny procent fizycznie zainstalowanej pamięci komputera, która może być zużywana przez pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="107d0-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="107d0-120">Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że klasy autosizing heurystyki są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="107d0-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="107d0-121">Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="107d0-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="107d0-122">Ta wartość jest wprowadzana w formacie "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="107d0-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="107d0-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="107d0-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="107d0-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="107d0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="107d0-125">Element</span><span class="sxs-lookup"><span data-stu-id="107d0-125">Element</span></span>|<span data-ttu-id="107d0-126">Opis</span><span class="sxs-lookup"><span data-stu-id="107d0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="107d0-127">\<nazwaneCaches></span><span class="sxs-lookup"><span data-stu-id="107d0-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="107d0-128">Zawiera kolekcję ustawień konfiguracji <xref:System.Runtime.Caching.MemoryCache> dla nazwanych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="107d0-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107d0-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="107d0-129">Remarks</span></span>  
 <span data-ttu-id="107d0-130">Element `add` dodaje wpis do `namedCaches` kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="107d0-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="107d0-131">Można użyć [clear](clear-element-for-namedcaches.md) element przed `add` użyciem elementu, aby mieć pewność, że nie ma żadnych innych nazwanych pamięci podręcznych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="107d0-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="107d0-132">Ten element może być używany w pliku machine.config i w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="107d0-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="107d0-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="107d0-133">Example</span></span>  
 <span data-ttu-id="107d0-134">W poniższym przykładzie pokazano, `namedCache` jak zdefiniować ustawienia domyślnego wpisu `namedCaches` do kolekcji dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="107d0-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="107d0-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="107d0-135">See also</span></span>

- [<span data-ttu-id="107d0-136">\<namedCaches> Element (Ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="107d0-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
