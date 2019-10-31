---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115508"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="c4f26-102">\<element System. Runtime. cache > (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c4f26-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="c4f26-103">Zapewnia konfigurację dla domyślnej implementacji <xref:System.Runtime.Caching.ObjectCache> w pamięci za pomocą wpisu `memoryCache` w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4f26-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="c4f26-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c4f26-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4f26-105">&nbsp;&nbsp; **\<system. Runtime. buforowanie >**</span><span class="sxs-lookup"><span data-stu-id="c4f26-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f26-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4f26-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4f26-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c4f26-107">Attributes and Elements</span></span>

<span data-ttu-id="c4f26-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c4f26-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4f26-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c4f26-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="c4f26-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c4f26-110">Child Elements</span></span>

|<span data-ttu-id="c4f26-111">Element</span><span class="sxs-lookup"><span data-stu-id="c4f26-111">Element</span></span>|<span data-ttu-id="c4f26-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c4f26-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4f26-113">\<elemencie MemoryCache ></span><span class="sxs-lookup"><span data-stu-id="c4f26-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="c4f26-114">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na klasie <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="c4f26-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4f26-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c4f26-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c4f26-116">Element</span><span class="sxs-lookup"><span data-stu-id="c4f26-116">Element</span></span>|<span data-ttu-id="c4f26-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c4f26-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4f26-118">> konfiguracji \<</span><span class="sxs-lookup"><span data-stu-id="c4f26-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="c4f26-119">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4f26-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4f26-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4f26-120">Remarks</span></span>

<span data-ttu-id="c4f26-121">Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności w zestawie `System.Web`.</span><span class="sxs-lookup"><span data-stu-id="c4f26-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="c4f26-122">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c4f26-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4f26-123">Funkcje i typy wyjściowej pamięci podręcznej w przestrzeni nazw <xref:System.Runtime.Caching> są nowe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c4f26-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4f26-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4f26-124">Example</span></span>

<span data-ttu-id="c4f26-125">Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na klasie <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="c4f26-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="c4f26-126">W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c4f26-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="c4f26-127">Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej, ustawiając atrybut `name` na "default".</span><span class="sxs-lookup"><span data-stu-id="c4f26-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="c4f26-128">Atrybut `cacheMemoryLimitMegabytes` i atrybut `physicalMemoryPercentage` są ustawione na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="c4f26-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c4f26-129">Ustawienie tych atrybutów na zero oznacza, że domyślnie są używane algorytmy heurystyczne <xref:System.Runtime.Caching.MemoryCache> autodopasowywania.</span><span class="sxs-lookup"><span data-stu-id="c4f26-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="c4f26-130">Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="c4f26-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4f26-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4f26-131">See also</span></span>

- [<span data-ttu-id="c4f26-132">\<element > elemencie MemoryCache (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="c4f26-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
