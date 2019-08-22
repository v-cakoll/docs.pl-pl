---
title: <forcePerformanceCounterUniqueSharedMemoryReads>, element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96d38abad37f9460230164de784a1258e7e937a4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663722"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="d0283-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="d0283-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="d0283-103">Określa, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1,1, aby określić, czy ładować dane liczników wydajności z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.</span><span class="sxs-lookup"><span data-stu-id="d0283-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="d0283-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d0283-104">\<configuration></span></span>  
<span data-ttu-id="d0283-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="d0283-105">\<runtime></span></span>  
<span data-ttu-id="d0283-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="d0283-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0283-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0283-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0283-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0283-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d0283-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0283-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0283-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0283-110">Attributes</span></span>  
  
|<span data-ttu-id="d0283-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d0283-111">Attribute</span></span>|<span data-ttu-id="d0283-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d0283-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d0283-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d0283-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d0283-114">Wskazuje, czy funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions w celu ustalenia, czy dane liczników wydajności mają być ładowane z pamięci współdzielonej określonej dla kategorii, czy z pamięci globalnej.</span><span class="sxs-lookup"><span data-stu-id="d0283-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d0283-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d0283-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d0283-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="d0283-116">Value</span></span>|<span data-ttu-id="d0283-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d0283-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d0283-118">Funkcja kończąca PerfCounter. dll nie używa ustawienia rejestru CategoryOptions jest to ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="d0283-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="d0283-119">Funkcja kończąca PerfCounter. dll używa ustawienia rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="d0283-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0283-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0283-120">Child Elements</span></span>  
 <span data-ttu-id="d0283-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="d0283-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0283-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0283-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d0283-123">Element</span><span class="sxs-lookup"><span data-stu-id="d0283-123">Element</span></span>|<span data-ttu-id="d0283-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d0283-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d0283-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0283-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d0283-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d0283-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0283-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0283-127">Remarks</span></span>  
 <span data-ttu-id="d0283-128">W wersjach .NET Framework przed .NET Framework 4, wersja funkcja kończąca PerfCounter. dll, która została załadowana, odpowiada środowisko uruchomieniowe, które zostało załadowane w procesie.</span><span class="sxs-lookup"><span data-stu-id="d0283-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="d0283-129">Jeśli na komputerze zainstalowano zarówno .NET Framework w wersji 1,1, jak i .NET Framework 2,0, aplikacja .NET Framework 1,1 załaduje .NET Framework 1,1 wersji funkcja kończąca PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="d0283-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="d0283-130">Począwszy od .NET Framework 4, zostanie załadowana Najnowsza zainstalowana wersja funkcja kończąca PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="d0283-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="d0283-131">Oznacza to, że aplikacja .NET Framework 1,1 będzie ładować wersję programu funkcja kończąca PerfCounter. dll w wersji .NET Framework 4, jeśli na komputerze zainstalowano .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d0283-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="d0283-132">Począwszy od .NET Framework 4, podczas zużywania liczników wydajności, funkcja kończąca PerfCounter. dll sprawdza wpis rejestru CategoryOptions dla każdego dostawcy, aby określić, czy powinien on zostać odczytany z udostępnionej pamięci lub globalnej pamięci udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="d0283-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="d0283-133">.NET Framework 1,1 funkcja kończąca PerfCounter. dll nie odczytuje tego wpisu rejestru, ponieważ nie ma on informacji o pamięci współdzielonej określonej dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="d0283-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="d0283-134">W celu zapewnienia zgodności z poprzednimi wersjami .NET Framework 4 funkcja kończąca PerfCounter. dll nie sprawdza wpisu rejestru CategoryOptions w przypadku uruchamiania w aplikacji .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="d0283-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="d0283-135">Po prostu używa globalnej pamięci współdzielonej, podobnie jak .NET Framework 1,1 funkcja kończąca PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="d0283-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="d0283-136">Można jednak wydać polecenie .NET Framework 4 funkcja kończąca PerfCounter. dll, aby sprawdzić ustawienie rejestru przez włączenie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d0283-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0283-137">`<forcePerformanceCounterUniqueSharedMemoryReads>` Włączenie elementu nie gwarantuje, że zostanie użyta udostępniona pamięć określona w kategorii.</span><span class="sxs-lookup"><span data-stu-id="d0283-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="d0283-138">Ustawienie "Enabled `true` " powoduje tylko, że funkcja kończąca PerfCounter. dll odwołuje się do ustawienia rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="d0283-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="d0283-139">Ustawieniem domyślnym dla CategoryOptions jest użycie pamięci współużytkowanej określonej dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinna być używana globalna pamięć współdzielona.</span><span class="sxs-lookup"><span data-stu-id="d0283-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="d0283-140">Klucz rejestru zawierający ustawienie CategoryOptions jest HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\< CategoryName \Performance.\></span><span class="sxs-lookup"><span data-stu-id="d0283-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="d0283-141">Domyślnie CategoryOptions jest ustawiana na 3, która instruuje funkcja kończąca PerfCounter. dll, aby użyć udostępnionej pamięci określonej dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="d0283-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="d0283-142">Jeśli wartość CategoryOptions jest równa 0, funkcja kończąca PerfCounter. dll używa globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="d0283-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="d0283-143">Dane wystąpienia będą ponownie używane tylko wtedy, gdy nazwa tworzonego wystąpienia jest identyczna z ponownie używanym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="d0283-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="d0283-144">Wszystkie wersje będą mogły zapisywać w kategorii.</span><span class="sxs-lookup"><span data-stu-id="d0283-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="d0283-145">Jeśli CategoryOptions jest ustawiona na 1, używana jest globalna pamięć współdzielona, ale dane wystąpienia mogą być ponownie używane, jeśli nazwa kategorii ma taką samą długość jak kategoria używana ponownie.</span><span class="sxs-lookup"><span data-stu-id="d0283-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="d0283-146">Ustawienia 0 i 1 mogą prowadzić do przecieków pamięci i wypełniania pamięci licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="d0283-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0283-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0283-147">Example</span></span>  
 <span data-ttu-id="d0283-148">Poniższy przykład pokazuje, jak określić, że funkcja kończąca PerfCounter. dll powinna odwoływać się do wpisu rejestru CategoryOptions, aby określić, czy powinien on używać pamięci współdzielonej specyficznej dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="d0283-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0283-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0283-149">See also</span></span>

- [<span data-ttu-id="d0283-150">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d0283-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d0283-151">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d0283-151">Configuration File Schema</span></span>](../index.md)
