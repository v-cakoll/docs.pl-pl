---
title: '&lt;System.Runtime.Caching —&gt; — Element (ustawienia pamięci podręcznej)'
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 659a168f6c0bcb459bcfbdb247a9959c61c9c996
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750612"
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="4d82c-102">&lt;System.Runtime.Caching —&gt; — Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="4d82c-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="4d82c-103">Zapewnia konfigurację domyślną w pamięci <xref:System.Runtime.Caching.ObjectCache> wykonywania za pośrednictwem `memoryCache` wpis w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d82c-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="4d82c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4d82c-104">\<configuration></span></span>  
<span data-ttu-id="4d82c-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="4d82c-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d82c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d82c-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d82c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d82c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d82c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d82c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d82c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d82c-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="4d82c-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d82c-110">Child Elements</span></span>  
  
|<span data-ttu-id="4d82c-111">Element</span><span class="sxs-lookup"><span data-stu-id="4d82c-111">Element</span></span>|<span data-ttu-id="4d82c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4d82c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d82c-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="4d82c-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="4d82c-114">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="4d82c-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d82c-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d82c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4d82c-116">Element</span><span class="sxs-lookup"><span data-stu-id="4d82c-116">Element</span></span>|<span data-ttu-id="4d82c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4d82c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d82c-118">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4d82c-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="4d82c-119">Określa element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d82c-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d82c-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d82c-120">Remarks</span></span>  
 <span data-ttu-id="4d82c-121">Klasy w tej przestrzeni nazw umożliwiają używanie buforowania obiektów, podobnie jak w programie ASP.NET, ale bez zależności w `System.Web` zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d82c-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="4d82c-122">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4d82c-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d82c-123">Dane wyjściowe pamięci podręcznej funkcji i typów w <xref:System.Runtime.Caching> przestrzeni nazw są nowością w programie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d82c-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d82c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d82c-124">Example</span></span>  
 <span data-ttu-id="4d82c-125">Poniższy przykład przedstawia sposób skonfigurować pamięć podręczną, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="4d82c-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="4d82c-126">W przykładzie pokazano sposób konfigurowania wystąpienia `namedCaches` wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4d82c-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="4d82c-127">Nazwa pamięci podręcznej ma ustawioną domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu "default".</span><span class="sxs-lookup"><span data-stu-id="4d82c-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="4d82c-128">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="4d82c-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="4d82c-129">Ustawienia te atrybuty zero oznacza <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="4d82c-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="4d82c-130">Implementacja pamięci podręcznej należy porównać bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="4d82c-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d82c-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d82c-131">See Also</span></span>  
 [<span data-ttu-id="4d82c-132">\<memoryCache > elementu (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="4d82c-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
