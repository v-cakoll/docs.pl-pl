---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb977e05fa54b726b0cd584d287dc00c8ced995
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423251"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="711e6-102">\<System.Runtime.Caching >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="711e6-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="711e6-103">Udostępnia konfigurację dla domyślnej w pamięci <xref:System.Runtime.Caching.ObjectCache> wdrożenia za pośrednictwem `memoryCache` wpisu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="711e6-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="711e6-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="711e6-104">\<configuration></span></span>  
<span data-ttu-id="711e6-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="711e6-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711e6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="711e6-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="711e6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="711e6-107">Attributes and Elements</span></span>

<span data-ttu-id="711e6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="711e6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="711e6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="711e6-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="711e6-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="711e6-110">Child Elements</span></span>

|<span data-ttu-id="711e6-111">Element</span><span class="sxs-lookup"><span data-stu-id="711e6-111">Element</span></span>|<span data-ttu-id="711e6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="711e6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="711e6-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="711e6-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="711e6-114">Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="711e6-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="711e6-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="711e6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="711e6-116">Element</span><span class="sxs-lookup"><span data-stu-id="711e6-116">Element</span></span>|<span data-ttu-id="711e6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="711e6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="711e6-118">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="711e6-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="711e6-119">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="711e6-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="711e6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="711e6-120">Remarks</span></span>

<span data-ttu-id="711e6-121">Klasy w tej przestrzeni nazw zapewniają sposób na korzystanie z pamięci podręcznej urządzenia, podobnie jak w programie ASP.NET, ale bez zależności `System.Web` zestawu.</span><span class="sxs-lookup"><span data-stu-id="711e6-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="711e6-122">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="711e6-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="711e6-123">Zapisywanie funkcji i typów w pamięci podręcznej danych wyjściowych <xref:System.Runtime.Caching> przestrzeni nazw są nowością w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="711e6-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="711e6-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="711e6-124">Example</span></span>

<span data-ttu-id="711e6-125">Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="711e6-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="711e6-126">W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpis dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="711e6-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="711e6-127">Nazwę pamięci podręcznej jest ustawiona na domyślną nazwę wpisu pamięci podręcznej, ustawiając `name` atrybutu "Default".</span><span class="sxs-lookup"><span data-stu-id="711e6-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="711e6-128">`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="711e6-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="711e6-129">Ustawienia te atrybuty zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="711e6-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="711e6-130">Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="711e6-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="711e6-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="711e6-131">See also</span></span>

- [<span data-ttu-id="711e6-132">\<memoryCache >, Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="711e6-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
