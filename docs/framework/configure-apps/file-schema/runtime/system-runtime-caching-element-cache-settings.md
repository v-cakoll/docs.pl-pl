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
ms.openlocfilehash: e36e2ed96a0748a69f2bd9ee32432901f0bf0898
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252288"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="915ef-102">\<System. Runtime. cache >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="915ef-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="915ef-103">Zapewnia konfigurację dla domyślnej implementacji w pamięci <xref:System.Runtime.Caching.ObjectCache> `memoryCache` za pomocą wpisu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="915ef-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="915ef-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="915ef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="915ef-105">&nbsp;&nbsp; **\<System. Runtime. buforowanie >**</span><span class="sxs-lookup"><span data-stu-id="915ef-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915ef-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="915ef-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="915ef-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="915ef-107">Attributes and Elements</span></span>

<span data-ttu-id="915ef-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="915ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="915ef-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="915ef-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="915ef-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="915ef-110">Child Elements</span></span>

|<span data-ttu-id="915ef-111">Element</span><span class="sxs-lookup"><span data-stu-id="915ef-111">Element</span></span>|<span data-ttu-id="915ef-112">Opis</span><span class="sxs-lookup"><span data-stu-id="915ef-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="915ef-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="915ef-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="915ef-114">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="915ef-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="915ef-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="915ef-115">Parent Elements</span></span>  
  
|<span data-ttu-id="915ef-116">Element</span><span class="sxs-lookup"><span data-stu-id="915ef-116">Element</span></span>|<span data-ttu-id="915ef-117">Opis</span><span class="sxs-lookup"><span data-stu-id="915ef-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="915ef-118">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="915ef-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="915ef-119">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="915ef-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915ef-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="915ef-120">Remarks</span></span>

<span data-ttu-id="915ef-121">Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności `System.Web` od zestawu.</span><span class="sxs-lookup"><span data-stu-id="915ef-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="915ef-122">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="915ef-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="915ef-123">Funkcje i typy wyjściowej pamięci podręcznej w <xref:System.Runtime.Caching> przestrzeni nazw są nowe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="915ef-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="915ef-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="915ef-124">Example</span></span>

<span data-ttu-id="915ef-125">Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="915ef-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="915ef-126">W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="915ef-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="915ef-127">Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej `name` przez ustawienie atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="915ef-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="915ef-128">`cacheMemoryLimitMegabytes` Atrybut`physicalMemoryPercentage` i atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="915ef-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="915ef-129">Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="915ef-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="915ef-130">Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="915ef-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="915ef-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="915ef-131">See also</span></span>

- [<span data-ttu-id="915ef-132">\<Elemencie MemoryCache >, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="915ef-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
