---
title: <gcConcurrent>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674106"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="92dea-102">\<gcConcurrent> Element</span><span class="sxs-lookup"><span data-stu-id="92dea-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="92dea-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="92dea-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="92dea-104">\<Konfiguracja > \\</span><span class="sxs-lookup"><span data-stu-id="92dea-104">\<configuration>\\</span></span>
<span data-ttu-id="92dea-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="92dea-105">\<runtime>\\</span></span>
<span data-ttu-id="92dea-106">\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="92dea-106">\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="92dea-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="92dea-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92dea-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92dea-108">Attributes and elements</span></span>

<span data-ttu-id="92dea-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92dea-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="92dea-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92dea-110">Attributes</span></span>

|<span data-ttu-id="92dea-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92dea-111">Attribute</span></span>|<span data-ttu-id="92dea-112">Opis</span><span class="sxs-lookup"><span data-stu-id="92dea-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="92dea-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="92dea-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="92dea-114">Określa, czy środowisko uruchomieniowe jednocześnie uruchamia wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="92dea-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="92dea-115">enabled attribute</span></span>

|<span data-ttu-id="92dea-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="92dea-116">Value</span></span>|<span data-ttu-id="92dea-117">Opis</span><span class="sxs-lookup"><span data-stu-id="92dea-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="92dea-118">Nie równoczesne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="92dea-119">Uruchamia współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="92dea-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="92dea-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="92dea-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92dea-121">Child elements</span></span>

<span data-ttu-id="92dea-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="92dea-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92dea-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92dea-123">Parent elements</span></span>

|<span data-ttu-id="92dea-124">Element</span><span class="sxs-lookup"><span data-stu-id="92dea-124">Element</span></span>|<span data-ttu-id="92dea-125">Opis</span><span class="sxs-lookup"><span data-stu-id="92dea-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="92dea-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92dea-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="92dea-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="92dea-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dea-128">Remarks</span></span>

<span data-ttu-id="92dea-129">Przed .NET Framework 4 wyrzucanie elementów bezużytecznych obsługiwane współbieżne wyrzucanie elementów bezużytecznych, wykonywane wyrzucania elementów bezużytecznych w tle w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="92dea-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="92dea-130">W programie .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych została zastąpiona GC, który wykonuje wyrzucania elementów bezużytecznych w tle w oddzielnym wątku tła.</span><span class="sxs-lookup"><span data-stu-id="92dea-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="92dea-131">Począwszy od programu .NET Framework 4.5, zbieranie w tle stały się dostępne w serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="92dea-132">`<gcConcurrent>` Element kontroluje, czy środowisko uruchomieniowe wykonuje albo równolegle lub w tle wyrzucanie elementów bezużytecznych, jeśli jest dostępna lub czy wykonuje wyrzucanie elementów bezużytecznych na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="92dea-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="92dea-133">Aby wyłączyć wyrzucania elementów bezużytecznych w tle</span><span class="sxs-lookup"><span data-stu-id="92dea-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="92dea-134">Począwszy od programu .NET Framework 4, współbieżne wyrzucanie elementów bezużytecznych zastępuje wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="92dea-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="92dea-135">Warunki *współbieżnych* i *tła* są używane zamiennie w dokumentacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92dea-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="92dea-136">Aby wyłączyć wyrzucania elementów bezużytecznych w tle, należy użyć `<gcConcurrent>` elementu, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="92dea-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="92dea-137">Domyślnie używa środowiska uruchomieniowego współbieżnych oraz wyrzucania elementów bezużytecznych w tle, który jest zoptymalizowany pod kątem opóźnień.</span><span class="sxs-lookup"><span data-stu-id="92dea-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="92dea-138">Jeśli aplikacja obejmuje interakcji z użytkownikiem duże, należy pozostawić współbieżne wyrzucanie elementów bezużytecznych, włączone, aby zminimalizować czas wstrzymania aplikacji do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="92dea-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="92dea-139">Jeśli ustawisz `enabled` atrybutu `<gcConcurrent>` elementu `false`, środowisko wykonawcze używa niewspółbieżnym wyrzucaniem elementów bezużytecznych, zoptymalizowaną pod kątem przepływności.</span><span class="sxs-lookup"><span data-stu-id="92dea-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="92dea-140">Następujący plik konfiguracji wyłącza wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="92dea-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="92dea-141">W przypadku `<gcConcurrentSetting>` ustawienia w pliku konfiguracji komputera, określa wartość domyślną dla wszystkich aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92dea-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="92dea-142">Ustawienie pliku konfiguracji komputera zastępuje ustawienia pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92dea-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="92dea-143">Aby uzyskać więcej informacji na temat równolegle i wyrzucania elementów bezużytecznych w tle, zobacz [współbieżne wyrzucanie elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) sekcji [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="92dea-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="92dea-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="92dea-144">Example</span></span>

<span data-ttu-id="92dea-145">Poniższy przykład umożliwia współbieżne wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="92dea-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="92dea-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92dea-146">See also</span></span>

- [<span data-ttu-id="92dea-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="92dea-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="92dea-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="92dea-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="92dea-149">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="92dea-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
