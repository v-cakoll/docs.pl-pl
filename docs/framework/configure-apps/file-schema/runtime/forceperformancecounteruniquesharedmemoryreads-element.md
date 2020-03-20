---
title: <forcePerformanceCounterUniqueSharedMemoryReads>, element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154143"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="8d002-102">\<forcePerformanceCounterUniqueSharedMemoryCzyty> element</span><span class="sxs-lookup"><span data-stu-id="8d002-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="8d002-103">Określa, czy plik PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 w celu określenia, czy dane licznika wydajności mają być ładowane z pamięci współużytkowanej specyficznej dla kategorii, czy z pamięci globalnej.</span><span class="sxs-lookup"><span data-stu-id="8d002-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="8d002-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d002-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d002-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d002-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8d002-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemory Odczyty>**</span><span class="sxs-lookup"><span data-stu-id="8d002-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d002-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d002-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d002-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d002-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d002-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d002-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d002-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d002-110">Attributes</span></span>  
  
|<span data-ttu-id="8d002-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d002-111">Attribute</span></span>|<span data-ttu-id="8d002-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8d002-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8d002-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8d002-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8d002-114">Wskazuje, czy plik PerfCounter.dll używa ustawienia rejestru CategoryOptions w celu określenia, czy dane licznika wydajności mają być ładowane z pamięci współużytkowanej specyficznej dla kategorii, czy z pamięci globalnej.</span><span class="sxs-lookup"><span data-stu-id="8d002-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8d002-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="8d002-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8d002-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8d002-116">Value</span></span>|<span data-ttu-id="8d002-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8d002-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8d002-118">Plik PerfCounter.dll nie używa ustawienia rejestru CategoryOptions Jest to ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="8d002-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="8d002-119">Plik PerfCounter.dll używa ustawienia rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="8d002-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d002-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d002-120">Child Elements</span></span>  
 <span data-ttu-id="8d002-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="8d002-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d002-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d002-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8d002-123">Element</span><span class="sxs-lookup"><span data-stu-id="8d002-123">Element</span></span>|<span data-ttu-id="8d002-124">Opis</span><span class="sxs-lookup"><span data-stu-id="8d002-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8d002-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d002-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8d002-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8d002-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d002-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d002-127">Remarks</span></span>  
 <span data-ttu-id="8d002-128">W wersjach programu .NET Framework przed programem .NET Framework 4 załadowana wersja pliku PerfCounter.dll odpowiadała czasowi wykonawczemu, który został załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="8d002-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="8d002-129">Jeśli na komputerze zainstalowano zarówno program .NET Framework w wersji 1.1, jak i program .NET Framework 2.0, aplikacja .NET Framework 1.1 załadowałaby wersję pliku .NET Framework 1.1 pliku PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="8d002-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="8d002-130">Począwszy od programu .NET Framework 4, jest ładowana najnowsza zainstalowana wersja pliku PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="8d002-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="8d002-131">Oznacza to, że aplikacja .NET Framework 1.1 załaduje wersję programu .NET Framework 4 pliku PerfCounter.dll, jeśli na komputerze jest zainstalowana gra .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8d002-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="8d002-132">Począwszy od programu .NET Framework 4, podczas korzystania z liczników wydajności, PerfCounter.dll sprawdza wpis rejestru CategoryOptions dla każdego dostawcy, aby ustalić, czy powinien on odczytywać z pamięci współużytkowanej specyficznej dla kategorii lub globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="8d002-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="8d002-133">.NET Framework 1.1 PerfCounter.dll nie odczytuje tego wpisu rejestru, ponieważ nie jest świadomy pamięci współużytkowanej specyficznej dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="8d002-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="8d002-134">W celu zapewnienia zgodności z powrotem plik .NET Framework 4 PerfCounter.dll nie sprawdza wpisu rejestru CategoryOptions podczas uruchamiania w aplikacji .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="8d002-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="8d002-135">Po prostu używa globalnej pamięci współużytkowanej, podobnie jak .NET Framework 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="8d002-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="8d002-136">Można jednak poinstruować plik .NET Framework 4 PerfCounter.dll, aby `<forcePerformanceCounterUniqueSharedMemoryReads>` sprawdziły ustawienie rejestru, włączając ten element.</span><span class="sxs-lookup"><span data-stu-id="8d002-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d002-137">Włączenie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu nie gwarantuje, że będzie używana pamięć współdzielona dla danej kategorii.</span><span class="sxs-lookup"><span data-stu-id="8d002-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="8d002-138">Ustawienie włączone `true` powoduje tylko PerfCounter.dll do odwołania się do ustawienia rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="8d002-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="8d002-139">Domyślnym ustawieniem dla CategoryOptions jest użycie pamięci współużytkowanej specyficznej dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinna być używana globalna pamięć współdzielona.</span><span class="sxs-lookup"><span data-stu-id="8d002-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="8d002-140">Klucz rejestru zawierający ustawienie CategoryOptions to HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="8d002-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="8d002-141">Domyślnie CategoryOptions jest ustawiona na 3, co nakazuje PerfCounter.dll używać pamięci współużytkowanej specyficzne dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="8d002-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="8d002-142">Jeśli CategoryOptions jest ustawiona na 0, PerfCounter.dll używa globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="8d002-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="8d002-143">Dane wystąpienia będą ponownie używać tylko wtedy, gdy nazwa tworzonego wystąpienia jest identyczna z wystąpieniem, które jest ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="8d002-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="8d002-144">Wszystkie wersje będą mogły pisać do kategorii.</span><span class="sxs-lookup"><span data-stu-id="8d002-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="8d002-145">Jeśli CategoryOptions jest ustawiona na 1, używana jest globalna pamięć współdzielona, ale dane wystąpienia mogą być ponownie użyte, jeśli nazwa kategorii ma taką samą długość jak kategoria, która jest ponownie używana.</span><span class="sxs-lookup"><span data-stu-id="8d002-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="8d002-146">Ustawienia 0 i 1 mogą prowadzić do przecieków pamięci i zapełnienia pamięci licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="8d002-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d002-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d002-147">Example</span></span>  
 <span data-ttu-id="8d002-148">W poniższym przykładzie pokazano, jak określić, że PerfCounter.dll powinien odwoływać się do wpisu rejestru CategoryOptions, aby ustalić, czy należy używać pamięci współużytkowanej specyficznej dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="8d002-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d002-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d002-149">See also</span></span>

- [<span data-ttu-id="8d002-150">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8d002-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8d002-151">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8d002-151">Configuration File Schema</span></span>](../index.md)
