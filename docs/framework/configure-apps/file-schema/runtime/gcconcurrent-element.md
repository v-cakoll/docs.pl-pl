---
title: <gcConcurrent> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 4897462e20b193496c44d26923d0d0e2a13f7dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116808"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="5157b-102">\<element > gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5157b-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="5157b-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="5157b-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="5157b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5157b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5157b-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5157b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5157b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent >**</span><span class="sxs-lookup"><span data-stu-id="5157b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcConcurrent>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="5157b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5157b-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5157b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5157b-108">Attributes and elements</span></span>

<span data-ttu-id="5157b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5157b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5157b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5157b-110">Attributes</span></span>

|<span data-ttu-id="5157b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5157b-111">Attribute</span></span>|<span data-ttu-id="5157b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5157b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5157b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5157b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5157b-114">Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="5157b-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="5157b-115">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="5157b-115">enabled attribute</span></span>

|<span data-ttu-id="5157b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5157b-116">Value</span></span>|<span data-ttu-id="5157b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5157b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5157b-118">Nie uruchamia współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5157b-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="5157b-119">Uruchamia odzyskiwanie pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="5157b-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="5157b-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5157b-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5157b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5157b-121">Child elements</span></span>

<span data-ttu-id="5157b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5157b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5157b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5157b-123">Parent elements</span></span>

|<span data-ttu-id="5157b-124">Element</span><span class="sxs-lookup"><span data-stu-id="5157b-124">Element</span></span>|<span data-ttu-id="5157b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5157b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5157b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5157b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5157b-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5157b-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5157b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5157b-128">Remarks</span></span>

<span data-ttu-id="5157b-129">Przed .NET Framework 4, wyrzucanie elementów bezużytecznych stacji roboczych obsługiwało współbieżne wyrzucanie elementów bezużytecznych, które przeprowadzono odzyskiwanie pamięci w tle w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="5157b-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="5157b-130">W .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych zostało zastąpione przez w tle GC, co również wykonuje wyrzucanie elementów bezużytecznych w tle w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="5157b-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="5157b-131">Począwszy od .NET Framework 4,5, zbieranie w tle stało się dostępne w wyrzucaniu elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="5157b-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="5157b-132">Element `<gcConcurrent>` określa, czy środowisko uruchomieniowe wykonuje współbieżne lub w tle wyrzucanie elementów bezużytecznych, jeśli jest dostępne, lub czy wykonuje wyrzucanie elementów bezużytecznych na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="5157b-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="5157b-133">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle</span><span class="sxs-lookup"><span data-stu-id="5157b-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="5157b-134">Począwszy od .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych jest zastępowane przez odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="5157b-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="5157b-135">Terminy *współbieżne* i *tła* są używane zamiennie w dokumentacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5157b-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="5157b-136">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle, użyj elementu `<gcConcurrent>`, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="5157b-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="5157b-137">Domyślnie środowisko uruchomieniowe używa współbieżnych lub w tle wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem opóźnień.</span><span class="sxs-lookup"><span data-stu-id="5157b-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="5157b-138">Jeśli aplikacja wymaga dużej interakcji z użytkownikiem, Włącz współbieżne wyrzucanie elementów bezużytecznych, aby zminimalizować czas wstrzymania aplikacji w celu wykonania odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="5157b-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="5157b-139">Jeśli ustawisz atrybut `enabled` elementu `<gcConcurrent>` do `false`, środowisko uruchomieniowe użyje niewspółbieżnego wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem przepływności.</span><span class="sxs-lookup"><span data-stu-id="5157b-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="5157b-140">Następujący plik konfiguracji wyłącza odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="5157b-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="5157b-141">Jeśli istnieje ustawienie `<gcConcurrentSetting>` w pliku konfiguracji komputera, definiuje wartość domyślną dla wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5157b-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="5157b-142">Ustawienie pliku konfiguracji komputera zastępuje ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5157b-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="5157b-143">Aby uzyskać więcej informacji na temat współbieżnych i wyrzucania elementów bezużytecznych w tle, zobacz sekcję [współbieżne odzyskiwanie](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) pamięci w artykule [podstawy odzyskiwania pamięci](../../../../standard/garbage-collection/fundamentals.md) .</span><span class="sxs-lookup"><span data-stu-id="5157b-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="5157b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="5157b-144">Example</span></span>

<span data-ttu-id="5157b-145">Poniższy przykład włącza współbieżne wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="5157b-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5157b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5157b-146">See also</span></span>

- [<span data-ttu-id="5157b-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5157b-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5157b-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5157b-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5157b-149">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="5157b-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
