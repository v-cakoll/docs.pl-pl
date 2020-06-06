---
title: GCHeapAffinitizeMask, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978383"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="a0e34-102">\<GCHeapAffinitizeMask>, element</span><span class="sxs-lookup"><span data-stu-id="a0e34-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="a0e34-103">Definiuje koligację między stertami GC i procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a0e34-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="a0e34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0e34-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0e34-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a0e34-105">Attributes and elements</span></span>

<span data-ttu-id="a0e34-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a0e34-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0e34-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a0e34-107">Attributes</span></span>

|<span data-ttu-id="a0e34-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a0e34-108">Attribute</span></span>|<span data-ttu-id="a0e34-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a0e34-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a0e34-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a0e34-110">Required attribute.</span></span><br /><br /><span data-ttu-id="a0e34-111">Określa koligację między stertami GC i procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a0e34-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="a0e34-112">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="a0e34-112">enabled attribute</span></span>

|<span data-ttu-id="a0e34-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a0e34-113">Value</span></span>|<span data-ttu-id="a0e34-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a0e34-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="a0e34-115">Wartość dziesiętna, która tworzy maskę bitowej definiującą koligację między sterty serwera GC a procesorami indywidualnymi.</span><span class="sxs-lookup"><span data-stu-id="a0e34-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="a0e34-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a0e34-116">Child elements</span></span>

<span data-ttu-id="a0e34-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a0e34-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0e34-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a0e34-118">Parent elements</span></span>

|<span data-ttu-id="a0e34-119">Element</span><span class="sxs-lookup"><span data-stu-id="a0e34-119">Element</span></span>|<span data-ttu-id="a0e34-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a0e34-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a0e34-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0e34-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a0e34-122">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a0e34-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0e34-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0e34-123">Remarks</span></span>

<span data-ttu-id="a0e34-124">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="a0e34-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="a0e34-125">Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapAffinitizeMask** do kontrolowania koligacji między stertami i procesorami serwera GC, gdy Liczba stert jest ograniczona przez element **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="a0e34-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="a0e34-126">**GCHeapAffinitizeMask** jest zazwyczaj używany wraz z dwiema innymi flagami:</span><span class="sxs-lookup"><span data-stu-id="a0e34-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="a0e34-127">[GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="a0e34-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="a0e34-128">`enabled`Atrybut elementu [GCNoAffinitize](gcnoaffinitize-element.md) musi być `false` (jego wartość domyślna) dla ustawienia **GCHeapAffinitizeMask** , które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="a0e34-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="a0e34-129">[GCHeapCount](gcheapcount-element.md), który ogranicza liczbę stert używany przez proces dla serwera GC.</span><span class="sxs-lookup"><span data-stu-id="a0e34-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="a0e34-130">Domyślnie istnieje jedna sterta dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="a0e34-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="a0e34-131">**nnnn** jest maską bitową wyrażoną jako wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a0e34-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="a0e34-132">Bit 0 z bajtem 0 reprezentuje procesor 0, bit 1 bajt 0 reprezentuje procesor 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="a0e34-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="a0e34-133">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a0e34-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="a0e34-134">Wartość 1023 to 0x3FF lub 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="a0e34-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="a0e34-135">Proces używa 10 procesorów, od 0 do procesor 9.</span><span class="sxs-lookup"><span data-stu-id="a0e34-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="a0e34-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0e34-136">Example</span></span>

<span data-ttu-id="a0e34-137">Poniższy przykład wskazuje, że aplikacja używa serwera GC z 10 stert/wątków.</span><span class="sxs-lookup"><span data-stu-id="a0e34-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="a0e34-138">Ponieważ nie chcesz, aby te sterty pokrywały się ze stertami z innych aplikacji uruchomionych w systemie, użyj **GCHeapAffinitizeMask** , aby określić, że proces ma używać procesorów od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="a0e34-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a0e34-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0e34-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a0e34-140">GCNoAffinitize, element</span><span class="sxs-lookup"><span data-stu-id="a0e34-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="a0e34-141">GCHeapCount, element</span><span class="sxs-lookup"><span data-stu-id="a0e34-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="a0e34-142">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="a0e34-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="a0e34-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a0e34-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a0e34-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a0e34-144">Configuration File Schema</span></span>](../index.md)
