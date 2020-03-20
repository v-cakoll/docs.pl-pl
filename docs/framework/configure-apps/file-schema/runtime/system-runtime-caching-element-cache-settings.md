---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153857"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="cb9a4-102">\<element> system.runtime.caching (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="cb9a4-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="cb9a4-103">Zapewnia konfigurację domyślnej <xref:System.Runtime.Caching.ObjectCache> implementacji `memoryCache` w pamięci za pośrednictwem wpisu w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="cb9a4-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb9a4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb9a4-105">&nbsp;&nbsp;**\<>system.runtime.caching**</span><span class="sxs-lookup"><span data-stu-id="cb9a4-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9a4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb9a4-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb9a4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cb9a4-107">Attributes and Elements</span></span>

<span data-ttu-id="cb9a4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb9a4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cb9a4-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="cb9a4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cb9a4-110">Child Elements</span></span>

|<span data-ttu-id="cb9a4-111">Element</span><span class="sxs-lookup"><span data-stu-id="cb9a4-111">Element</span></span>|<span data-ttu-id="cb9a4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cb9a4-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb9a4-113">\<>memoryCache</span><span class="sxs-lookup"><span data-stu-id="cb9a4-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="cb9a4-114">Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb9a4-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cb9a4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cb9a4-116">Element</span><span class="sxs-lookup"><span data-stu-id="cb9a4-116">Element</span></span>|<span data-ttu-id="cb9a4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="cb9a4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb9a4-118">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="cb9a4-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="cb9a4-119">Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb9a4-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb9a4-120">Remarks</span></span>

<span data-ttu-id="cb9a4-121">Klasy w tej przestrzeni nazw umożliwiają korzystanie z urządzeń buforowania, takich jak te w ASP.NET, ale bez zależności od `System.Web` zestawu.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="cb9a4-122">Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="cb9a4-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb9a4-123">Funkcje buforowania danych wyjściowych <xref:System.Runtime.Caching> i typy w obszarze nazw są nowe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb9a4-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb9a4-124">Example</span></span>

<span data-ttu-id="cb9a4-125">W poniższym przykładzie pokazano, jak skonfigurować <xref:System.Runtime.Caching.MemoryCache> pamięć podręczną, która jest oparta na klasie.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="cb9a4-126">W przykładzie pokazano, jak skonfigurować wystąpienie wpisu `namedCaches` dla pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="cb9a4-127">Nazwa pamięci podręcznej jest ustawiona na domyślną `name` nazwę wpisu pamięci podręcznej, ustawiając atrybut na "Domyślny".</span><span class="sxs-lookup"><span data-stu-id="cb9a4-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="cb9a4-128">Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryPercentage` atrybut są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="cb9a4-129">Ustawienie tych atrybutów na <xref:System.Runtime.Caching.MemoryCache> zero oznacza, że heurystyka automatycznego szesnasty są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="cb9a4-130">Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci z bezwzględnych i procentowych limitów pamięci co dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="cb9a4-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb9a4-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb9a4-131">See also</span></span>

- [<span data-ttu-id="cb9a4-132">\<MemoryCache> Element (ustawienia pamięci podręcznej)</span><span class="sxs-lookup"><span data-stu-id="cb9a4-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
