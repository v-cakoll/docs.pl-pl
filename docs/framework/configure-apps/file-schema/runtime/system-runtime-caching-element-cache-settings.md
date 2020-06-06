---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153857"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="cdf4f-102">\<system.runtime.caching>, element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="cdf4f-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="cdf4f-103">Zapewnia konfigurację dla domyślnej implementacji w pamięci <xref:System.Runtime.Caching.ObjectCache> za pomocą `memoryCache` wpisu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="cdf4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdf4f-104">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf4f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cdf4f-105">Attributes and Elements</span></span>

<span data-ttu-id="cdf4f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdf4f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cdf4f-107">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="cdf4f-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cdf4f-108">Child Elements</span></span>

|<span data-ttu-id="cdf4f-109">Element</span><span class="sxs-lookup"><span data-stu-id="cdf4f-109">Element</span></span>|<span data-ttu-id="cdf4f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cdf4f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="cdf4f-111">Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-111">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdf4f-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cdf4f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="cdf4f-113">Element</span><span class="sxs-lookup"><span data-stu-id="cdf4f-113">Element</span></span>|<span data-ttu-id="cdf4f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cdf4f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="cdf4f-115">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-115">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf4f-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdf4f-116">Remarks</span></span>

<span data-ttu-id="cdf4f-117">Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności od `System.Web` zestawu.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-117">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="cdf4f-118">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="cdf4f-118">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdf4f-119">Funkcje i typy wyjściowej pamięci podręcznej w <xref:System.Runtime.Caching> przestrzeni nazw są nowe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-119">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf4f-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdf4f-120">Example</span></span>

<span data-ttu-id="cdf4f-121">Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na <xref:System.Runtime.Caching.MemoryCache> klasie.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-121">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="cdf4f-122">W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-122">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="cdf4f-123">Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".</span><span class="sxs-lookup"><span data-stu-id="cdf4f-123">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="cdf4f-124">`cacheMemoryLimitMegabytes`Atrybut i `physicalMemoryPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-124">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="cdf4f-125">Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-125">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="cdf4f-126">Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="cdf4f-126">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdf4f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdf4f-127">See also</span></span>

- [<span data-ttu-id="cdf4f-128">\<memoryCache>— Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="cdf4f-128">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
