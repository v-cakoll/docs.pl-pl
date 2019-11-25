---
title: GCNoAffinitize, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978376"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="c9040-102">\<element > GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c9040-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="c9040-103">Określa, czy koligacji wątki serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9040-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="c9040-104">\<Konfiguracja > </span><span class="sxs-lookup"><span data-stu-id="c9040-104">\<configuration></span></span>\
<span data-ttu-id="c9040-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="c9040-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="c9040-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="c9040-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="c9040-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9040-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9040-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9040-108">Attributes and elements</span></span>

<span data-ttu-id="c9040-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9040-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9040-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9040-110">Attributes</span></span>

|<span data-ttu-id="c9040-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9040-111">Attribute</span></span>|<span data-ttu-id="c9040-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c9040-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c9040-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c9040-113">Required attribute.</span></span><br /><br /><span data-ttu-id="c9040-114">Określa, czy wątki/sterty serwera GC są koligacją z procesorami dostępnymi na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c9040-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="c9040-115">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="c9040-115">enabled attribute</span></span>

|<span data-ttu-id="c9040-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c9040-116">Value</span></span>|<span data-ttu-id="c9040-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c9040-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c9040-118">Skoligacony Server GC wątki z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9040-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="c9040-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c9040-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="c9040-120">Nie koligacji wątków serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9040-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c9040-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9040-121">Child elements</span></span>

<span data-ttu-id="c9040-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="c9040-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9040-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9040-123">Parent elements</span></span>

|<span data-ttu-id="c9040-124">Element</span><span class="sxs-lookup"><span data-stu-id="c9040-124">Element</span></span>|<span data-ttu-id="c9040-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c9040-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c9040-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9040-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c9040-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c9040-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9040-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9040-128">Remarks</span></span>

<span data-ttu-id="c9040-129">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednimi procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9040-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="c9040-130">Każdy z dostępnych procesorów systemu ma własną stertę i wątek GC.</span><span class="sxs-lookup"><span data-stu-id="c9040-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="c9040-131">Jest to zazwyczaj preferowane ustawienie, ponieważ optymalizuje użycie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c9040-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="c9040-132">Rozpoczynając od .NET Framework 4.6.2, ustawiając atrybut `enabled` elementu **GCNoAffinitize** na `false`, można określić, że wątki i procesory serwera GC nie powinny być ściśle sprzężone.</span><span class="sxs-lookup"><span data-stu-id="c9040-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="c9040-133">Można określić **GCNoAffinitize** element konfiguracji, aby nie koligacji wątki serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9040-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="c9040-134">Można go również użyć wraz z elementem [GCHeapCount](gcheapcount-element.md) , aby kontrolować liczbę stert i wątków GC używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9040-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="c9040-135">Jeśli atrybut `enabled` elementu **GCNoAffinitize** jest `false` (jego wartość domyślna), można również użyć elementu [GCHeapCount](gcheapcount-element.md) w celu określenia liczby wątków i sterty GC, a także elementu [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) , aby określić procesory, do których są koligacje wątki i sterty GC.</span><span class="sxs-lookup"><span data-stu-id="c9040-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="c9040-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9040-136">Example</span></span>

<span data-ttu-id="c9040-137">W poniższym przykładzie nie są twarde koligacji Server GC wątki:</span><span class="sxs-lookup"><span data-stu-id="c9040-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="c9040-138">Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10:</span><span class="sxs-lookup"><span data-stu-id="c9040-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c9040-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9040-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c9040-140">GCHeapAffinitizeMask, element</span><span class="sxs-lookup"><span data-stu-id="c9040-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="c9040-141">GCHeapCount, element</span><span class="sxs-lookup"><span data-stu-id="c9040-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="c9040-142">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c9040-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="c9040-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c9040-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9040-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c9040-144">Configuration File Schema</span></span>](../index.md)
