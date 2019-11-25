---
title: GCHeapAffinitizeMask, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978383"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="a9c84-102">\<element > GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="a9c84-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="a9c84-103">Definiuje koligację między stertami GC i procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a9c84-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="a9c84-104">\<Konfiguracja > </span><span class="sxs-lookup"><span data-stu-id="a9c84-104">\<configuration></span></span>\
<span data-ttu-id="a9c84-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="a9c84-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="a9c84-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="a9c84-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="a9c84-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9c84-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9c84-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9c84-108">Attributes and elements</span></span>

<span data-ttu-id="a9c84-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a9c84-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9c84-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9c84-110">Attributes</span></span>

|<span data-ttu-id="a9c84-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a9c84-111">Attribute</span></span>|<span data-ttu-id="a9c84-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a9c84-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a9c84-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9c84-113">Required attribute.</span></span><br /><br /><span data-ttu-id="a9c84-114">Określa koligację między stertami GC i procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a9c84-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="a9c84-115">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="a9c84-115">enabled attribute</span></span>

|<span data-ttu-id="a9c84-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="a9c84-116">Value</span></span>|<span data-ttu-id="a9c84-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a9c84-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="a9c84-118">Wartość dziesiętna, która tworzy maskę bitowej definiującą koligację między sterty serwera GC a procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a9c84-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="a9c84-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9c84-119">Child elements</span></span>

<span data-ttu-id="a9c84-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9c84-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9c84-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9c84-121">Parent elements</span></span>

|<span data-ttu-id="a9c84-122">Element</span><span class="sxs-lookup"><span data-stu-id="a9c84-122">Element</span></span>|<span data-ttu-id="a9c84-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a9c84-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a9c84-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9c84-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a9c84-125">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a9c84-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9c84-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9c84-126">Remarks</span></span>

<span data-ttu-id="a9c84-127">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="a9c84-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="a9c84-128">Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapAffinitizeMask** do kontrolowania koligacji między stertami i procesorami serwera GC, gdy Liczba stert jest ograniczona przez element **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="a9c84-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="a9c84-129">**GCHeapAffinitizeMask** jest zazwyczaj używany wraz z dwiema innymi flagami:</span><span class="sxs-lookup"><span data-stu-id="a9c84-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="a9c84-130">[GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="a9c84-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="a9c84-131">Atrybut `enabled` elementu [GCNoAffinitize](gcnoaffinitize-element.md) musi być `false` (jego wartość domyślna) dla ustawienia **GCHeapAffinitizeMask** , które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="a9c84-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="a9c84-132">[GCHeapCount](gcheapcount-element.md), który ogranicza liczbę stert używany przez proces dla serwera GC.</span><span class="sxs-lookup"><span data-stu-id="a9c84-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="a9c84-133">Domyślnie istnieje jedna sterta dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="a9c84-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="a9c84-134">**nnnn** jest maską bitową wyrażoną jako wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a9c84-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="a9c84-135">Bit 0 z bajtem 0 reprezentuje procesor 0, bit 1 bajt 0 reprezentuje procesor 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="a9c84-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="a9c84-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a9c84-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="a9c84-137">Wartość 1023 to 0x3FF lub 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="a9c84-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="a9c84-138">Proces używa 10 procesorów, od 0 do procesor 9.</span><span class="sxs-lookup"><span data-stu-id="a9c84-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="a9c84-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9c84-139">Example</span></span>

<span data-ttu-id="a9c84-140">Poniższy przykład wskazuje, że aplikacja używa serwera GC z 10 stert/wątków.</span><span class="sxs-lookup"><span data-stu-id="a9c84-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="a9c84-141">Ponieważ nie chcesz, aby te sterty pokrywały się ze stertami z innych aplikacji uruchomionych w systemie, użyj **GCHeapAffinitizeMask** , aby określić, że proces ma używać procesorów od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="a9c84-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a9c84-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9c84-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a9c84-143">GCNoAffinitize, element</span><span class="sxs-lookup"><span data-stu-id="a9c84-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="a9c84-144">GCHeapCount, element</span><span class="sxs-lookup"><span data-stu-id="a9c84-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="a9c84-145">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="a9c84-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="a9c84-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a9c84-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a9c84-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9c84-147">Configuration File Schema</span></span>](../index.md)
