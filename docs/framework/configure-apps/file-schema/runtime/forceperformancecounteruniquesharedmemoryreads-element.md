---
title: '&lt;forceperformancecounteruniquesharedmemoryreads —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a><span data-ttu-id="267b0-102">&lt;forceperformancecounteruniquesharedmemoryreads —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="267b0-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; Element</span></span>
<span data-ttu-id="267b0-103">Określa, czy PerfCounter.dll używa ustawienia rejestru CategoryOptions w aplikacji .NET Framework w wersji 1.1 do określenia, czy ładowanie danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub pamięci globalnej.</span><span class="sxs-lookup"><span data-stu-id="267b0-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="267b0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="267b0-104">\<configuration></span></span>  
<span data-ttu-id="267b0-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="267b0-105">\<runtime></span></span>  
<span data-ttu-id="267b0-106">\<forceperformancecounteruniquesharedmemoryreads — ></span><span class="sxs-lookup"><span data-stu-id="267b0-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267b0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="267b0-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="267b0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="267b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="267b0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="267b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="267b0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="267b0-110">Attributes</span></span>  
  
|<span data-ttu-id="267b0-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="267b0-111">Attribute</span></span>|<span data-ttu-id="267b0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="267b0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="267b0-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="267b0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="267b0-114">Wskazuje, czy PerfCounter.dll używa CategoryOptions ustawienie rejestru w celu określenia, czy ładowanie danych licznika wydajności z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="267b0-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="267b0-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="267b0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="267b0-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="267b0-116">Value</span></span>|<span data-ttu-id="267b0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="267b0-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="267b0-118">PerfCounter.dll nie używa CategoryOptions rejestru to ustawienie jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="267b0-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="267b0-119">PerfCounter.dll użyj ustawienia rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="267b0-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="267b0-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="267b0-120">Child Elements</span></span>  
 <span data-ttu-id="267b0-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="267b0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="267b0-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="267b0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="267b0-123">Element</span><span class="sxs-lookup"><span data-stu-id="267b0-123">Element</span></span>|<span data-ttu-id="267b0-124">Opis</span><span class="sxs-lookup"><span data-stu-id="267b0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="267b0-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="267b0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="267b0-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="267b0-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="267b0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="267b0-127">Remarks</span></span>  
 <span data-ttu-id="267b0-128">W wersjach programu .NET Framework, przed [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], uzgodnić wersji PerfCounter.dll, która została załadowana do środowiska wykonawczego, który został załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="267b0-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="267b0-129">Jeśli komputer ma zarówno programu .NET Framework w wersji 1.1 i [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] zainstalowany, aplikacji .NET Framework 1.1 czy ładowanie wersji .NET Framework 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="267b0-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="267b0-130">Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], najnowsza wersja zainstalowanego PerfCounter.dll został załadowany.</span><span class="sxs-lookup"><span data-stu-id="267b0-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="267b0-131">Oznacza to, że załaduje aplikacji .NET Framework 1.1 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] wersji PerfCounter.dll Jeśli [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="267b0-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="267b0-132">Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], gdy korzystanie z liczników wydajności, PerfCounter.dll sprawdza CategoryOptions wpisu rejestru dla każdego dostawcy określić, czy odczytywane z pamięci współużytkowanej specyficznego dla kategorii lub globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="267b0-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="267b0-133">.NET Framework 1.1 PerfCounter.dll nie odczytać tego wpisu rejestru, ponieważ nie został powiadomiony o pamięci współużytkowanej specyficznego dla kategorii; zawsze odczytuje z globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="267b0-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="267b0-134">W celu zapewnienia zgodności z poprzednimi wersjami [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll nie sprawdza wpis rejestru CategoryOptions podczas uruchamiania aplikacji .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="267b0-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="267b0-135">Po prostu używa globalnej pamięci współdzielonej, podobnie jak PerfCounter.dll 1.1 programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="267b0-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="267b0-136">Jednak możesz wydać [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll, aby sprawdzić ustawienie rejestru, należy włączyć `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="267b0-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="267b0-137">Włączanie `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu nie gwarantuje użytą pamięci współużytkowanej specyficznego dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="267b0-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="267b0-138">Aby włączyć ustawienie `true` tylko powoduje PerfCounter.dll do odwołania na ustawienie rejestru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="267b0-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="267b0-139">Ustawieniem domyślnym dla CategoryOptions jest użycie pamięci współużytkowanej specyficznego dla kategorii; można jednak zmienić CategoryOptions, aby wskazać, że powinny być używane globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="267b0-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="267b0-140">Klucz rejestru, która zawiera ustawienie CategoryOptions jest HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="267b0-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="267b0-141">Domyślnie CategoryOptions wynosi 3, który powoduje, że PerfCounter.dll do użycia pamięci współużytkowanej specyficznego dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="267b0-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="267b0-142">Jeśli CategoryOptions jest ustawiona na 0, PerfCounter.dll korzysta z globalnej pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="267b0-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="267b0-143">Dane wystąpienia zostanie ono użyte ponownie tylko wtedy, gdy nazwa wystąpienia, tworzony jest identyczny z wystąpieniem używane ponownie.</span><span class="sxs-lookup"><span data-stu-id="267b0-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="267b0-144">Wszystkie wersje będzie można zapisywać do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="267b0-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="267b0-145">Jeśli CategoryOptions jest ustawiona na 1, jest używany w globalnej pamięci współdzielonej, ale dane wystąpienia mogą być ponownie używane, jeśli nazwa kategorii jest taką samą długość jak kategoria używane ponownie.</span><span class="sxs-lookup"><span data-stu-id="267b0-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="267b0-146">Ustawienia wartości 0 i 1 może prowadzić do przecieki pamięci i wypełnianie zapasowej pamięci liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="267b0-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="267b0-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="267b0-147">Example</span></span>  
 <span data-ttu-id="267b0-148">Poniższy przykład przedstawia sposób określania, czy PerfCounter.dll powinien odwoływać się wpis rejestru CategoryOptions, aby określić, czy należy używać pamięci współużytkowanej specyficznego dla kategorii.</span><span class="sxs-lookup"><span data-stu-id="267b0-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="267b0-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="267b0-149">See Also</span></span>  
 [<span data-ttu-id="267b0-150">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="267b0-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="267b0-151">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="267b0-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
