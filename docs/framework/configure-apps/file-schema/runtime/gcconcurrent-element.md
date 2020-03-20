---
title: gcCzłonek koncurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400044"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="e5968-102">\<gcWliczna> element</span><span class="sxs-lookup"><span data-stu-id="e5968-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="e5968-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="e5968-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="e5968-104">[\<>konfiguracyjne](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5968-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="e5968-105">&nbsp;&nbsp;[\<>czasu wykonywania](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5968-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="e5968-106">&nbsp;&nbsp;&nbsp;&nbsp;\<> gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e5968-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="e5968-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5968-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5968-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5968-108">Attributes and elements</span></span>

<span data-ttu-id="e5968-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5968-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5968-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5968-110">Attributes</span></span>

|<span data-ttu-id="e5968-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5968-111">Attribute</span></span>|<span data-ttu-id="e5968-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e5968-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e5968-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e5968-113">Required attribute.</span></span><br /><br /><span data-ttu-id="e5968-114">Określa, czy środowisko uruchomieniowe uruchamia wyrzucanie elementów bezużytecznych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e5968-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="e5968-115">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="e5968-115">enabled attribute</span></span>

|<span data-ttu-id="e5968-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="e5968-116">Value</span></span>|<span data-ttu-id="e5968-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e5968-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e5968-118">Nie uruchamia wyrzucania elementów bezużytecznych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e5968-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="e5968-119">Uruchamia wyrzucania elementów bezużytecznych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e5968-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="e5968-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="e5968-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e5968-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5968-121">Child elements</span></span>

<span data-ttu-id="e5968-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="e5968-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5968-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5968-123">Parent elements</span></span>

|<span data-ttu-id="e5968-124">Element</span><span class="sxs-lookup"><span data-stu-id="e5968-124">Element</span></span>|<span data-ttu-id="e5968-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e5968-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e5968-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5968-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e5968-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e5968-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5968-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5968-128">Remarks</span></span>

<span data-ttu-id="e5968-129">Przed .NET Framework 4, wyrzucania elementów bezużytecznych stacji roboczej obsługiwane równoczesnych wyrzucania elementów bezużytecznych, który wykonywane wyrzucania elementów bezużytecznych w tle w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="e5968-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="e5968-130">W programie .NET Framework 4 równoczesnych wyrzucania elementów bezużytecznych został zastąpiony przez gc tła, który wykonuje również wyrzucania elementów bezużytecznych w tle w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="e5968-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="e5968-131">Począwszy od programu .NET Framework 4.5, zbieranie w tle stało się dostępne w wyrzucaniu elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e5968-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="e5968-132">**GcConcurrent** element kontroluje, czy środowisko wykonawcze wykonuje równoczesnych lub w tle wyrzucania elementów bezużytecznych, jeśli jest dostępny lub czy wykonuje wyrzucania elementów bezużytecznych na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="e5968-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="e5968-133">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle</span><span class="sxs-lookup"><span data-stu-id="e5968-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="e5968-134">Począwszy od programu .NET Framework 4, równoczesnych wyrzucania elementów bezużytecznych jest zastępowany przez wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="e5968-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="e5968-135">Terminy *równoczesnych* i *tła* są używane zamiennie w dokumentacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5968-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="e5968-136">Aby wyłączyć wyrzucanie elementów bezużytecznych w tle, należy użyć **gcConcurrent** element, jak omówiono w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="e5968-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="e5968-137">Domyślnie środowisko wykonawcze używa równoczesnych lub w tle wyrzucania elementów bezużytecznych, który jest zoptymalizowany pod kątem opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="e5968-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="e5968-138">Jeśli aplikacja obejmuje intensywnej interakcji użytkownika, pozostawić równoczesnych wyrzucania elementów bezużytecznych włączone, aby zminimalizować czas wstrzymania aplikacji do wykonywania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e5968-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="e5968-139">Jeśli ustawisz `enabled` atrybut **gcConcurrent** element `false`do , środowisko wykonawcze używa niebieżne wyrzucania elementów bezużytecznych, który jest zoptymalizowany pod kątem przepływności.</span><span class="sxs-lookup"><span data-stu-id="e5968-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="e5968-140">Następujący plik konfiguracyjny wyłącza wyrzucanie elementów bezużytecznych w tle:</span><span class="sxs-lookup"><span data-stu-id="e5968-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="e5968-141">Jeśli w pliku konfiguracji komputera znajduje się ustawienie **gcConcurrentSetting,** definiuje wartość domyślną dla wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5968-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="e5968-142">Ustawienie pliku konfiguracji komputera zastępuje ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5968-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="e5968-143">Aby uzyskać więcej informacji na temat równoczesnych i tła wyrzucania elementów bezużytecznych, zobacz [równoczesnych wyrzucania elementów](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) [bezużytecznych, Tło wyrzucania elementów bezużytecznych stacji roboczej](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)i [części wyrzucania elementów bezużytecznych serwera w](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sekcji Podstawy [wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="e5968-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="e5968-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5968-144">Example</span></span>

<span data-ttu-id="e5968-145">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych w tle:</span><span class="sxs-lookup"><span data-stu-id="e5968-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e5968-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5968-146">See also</span></span>

- [<span data-ttu-id="e5968-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e5968-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5968-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e5968-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e5968-149">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="e5968-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
