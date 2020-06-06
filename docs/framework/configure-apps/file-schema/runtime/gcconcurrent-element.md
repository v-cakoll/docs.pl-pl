---
title: gcConcurrent, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102921"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="a6b66-102">\<gcConcurrent>, element</span><span class="sxs-lookup"><span data-stu-id="a6b66-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="a6b66-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="a6b66-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="a6b66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6b66-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6b66-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6b66-105">Attributes and elements</span></span>

<span data-ttu-id="a6b66-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6b66-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6b66-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6b66-107">Attributes</span></span>

|<span data-ttu-id="a6b66-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6b66-108">Attribute</span></span>|<span data-ttu-id="a6b66-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a6b66-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a6b66-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a6b66-110">Required attribute.</span></span><br /><br /><span data-ttu-id="a6b66-111">Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a6b66-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="a6b66-112">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="a6b66-112">enabled attribute</span></span>

|<span data-ttu-id="a6b66-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a6b66-113">Value</span></span>|<span data-ttu-id="a6b66-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a6b66-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a6b66-115">Nie uruchamia współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a6b66-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="a6b66-116">Uruchamia odzyskiwanie pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a6b66-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="a6b66-117">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a6b66-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a6b66-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6b66-118">Child elements</span></span>

<span data-ttu-id="a6b66-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6b66-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6b66-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6b66-120">Parent elements</span></span>

|<span data-ttu-id="a6b66-121">Element</span><span class="sxs-lookup"><span data-stu-id="a6b66-121">Element</span></span>|<span data-ttu-id="a6b66-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a6b66-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a6b66-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6b66-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a6b66-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a6b66-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6b66-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6b66-125">Remarks</span></span>

<span data-ttu-id="a6b66-126">Przed .NET Framework 4, wyrzucanie elementów bezużytecznych stacji roboczych obsługiwało współbieżne wyrzucanie elementów bezużytecznych, które przeprowadzono odzyskiwanie pamięci w tle w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="a6b66-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="a6b66-127">W .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych zostało zastąpione przez w tle GC, co również wykonuje odzyskiwanie pamięci w tle w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="a6b66-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="a6b66-128">Począwszy od .NET Framework 4,5, zbieranie w tle stało się dostępne w wyrzucaniu elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a6b66-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="a6b66-129">Element **gcConcurrent** określa, czy środowisko uruchomieniowe wykonuje współbieżne lub w tle odzyskiwanie pamięci, jeśli jest dostępne, lub czy wykonuje odzyskiwanie pamięci na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="a6b66-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="a6b66-130">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle</span><span class="sxs-lookup"><span data-stu-id="a6b66-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="a6b66-131">Począwszy od .NET Framework 4, współbieżne wyrzucanie elementów bezużytecznych jest zastępowane przez odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="a6b66-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="a6b66-132">Terminy *współbieżne* i *tła* są używane zamiennie w dokumentacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6b66-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="a6b66-133">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle, należy użyć elementu **gcConcurrent** , zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="a6b66-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="a6b66-134">Domyślnie środowisko uruchomieniowe używa współbieżnych lub w tle wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem opóźnień.</span><span class="sxs-lookup"><span data-stu-id="a6b66-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="a6b66-135">Jeśli aplikacja wymaga dużej interakcji z użytkownikiem, Włącz współbieżne wyrzucanie elementów bezużytecznych, aby zminimalizować czas wstrzymania aplikacji w celu wykonania odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a6b66-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="a6b66-136">Jeśli ustawisz `enabled` atrybut elementu **gcConcurrent** na `false` , środowisko uruchomieniowe używa niewspółbieżnego wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem przepływności.</span><span class="sxs-lookup"><span data-stu-id="a6b66-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="a6b66-137">Następujący plik konfiguracji wyłącza wyrzucanie elementów bezużytecznych w tle:</span><span class="sxs-lookup"><span data-stu-id="a6b66-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="a6b66-138">Jeśli istnieje ustawienie **gcConcurrentSetting** w pliku konfiguracji komputera, definiuje wartość domyślną dla wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6b66-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="a6b66-139">Ustawienie pliku konfiguracji komputera zastępuje ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6b66-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="a6b66-140">Aby uzyskać więcej informacji na temat współbieżnych i wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci w tle](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="a6b66-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="a6b66-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6b66-141">Example</span></span>

<span data-ttu-id="a6b66-142">Poniższy przykład włącza wyrzucanie elementów bezużytecznych w tle:</span><span class="sxs-lookup"><span data-stu-id="a6b66-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a6b66-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6b66-143">See also</span></span>

- [<span data-ttu-id="a6b66-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a6b66-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6b66-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a6b66-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a6b66-146">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="a6b66-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
