---
title: GCHeapCount, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283071"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="e0f57-102">\<element > GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e0f57-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="e0f57-103">Określa liczbę stert/wątków, które mają być używane do wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e0f57-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

<span data-ttu-id="e0f57-104">\<Konfiguracja > </span><span class="sxs-lookup"><span data-stu-id="e0f57-104">\<configuration></span></span>\
<span data-ttu-id="e0f57-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="e0f57-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="e0f57-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="e0f57-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount></span></span>

## <a name="syntax"></a><span data-ttu-id="e0f57-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0f57-107">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0f57-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e0f57-108">Attributes and elements</span></span>

<span data-ttu-id="e0f57-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e0f57-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0f57-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e0f57-110">Attributes</span></span>

|<span data-ttu-id="e0f57-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e0f57-111">Attribute</span></span>|<span data-ttu-id="e0f57-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e0f57-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e0f57-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e0f57-113">Required attribute.</span></span><br /><br /><span data-ttu-id="e0f57-114">Określa liczbę stert, która ma być używana do wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e0f57-114">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="e0f57-115">Rzeczywista liczba stert jest minimalnym określoną liczbą stert i liczbą procesorów, które mogą być używane przez proces.</span><span class="sxs-lookup"><span data-stu-id="e0f57-115">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="e0f57-116">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="e0f57-116">enabled attribute</span></span>

|<span data-ttu-id="e0f57-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="e0f57-117">Value</span></span>|<span data-ttu-id="e0f57-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e0f57-118">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="e0f57-119">Liczba stert, które mają być używane na potrzeby serwera GC.</span><span class="sxs-lookup"><span data-stu-id="e0f57-119">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e0f57-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e0f57-120">Child elements</span></span>

<span data-ttu-id="e0f57-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="e0f57-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0f57-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e0f57-122">Parent elements</span></span>

|<span data-ttu-id="e0f57-123">Element</span><span class="sxs-lookup"><span data-stu-id="e0f57-123">Element</span></span>|<span data-ttu-id="e0f57-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e0f57-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e0f57-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0f57-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e0f57-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e0f57-126">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0f57-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0f57-127">Remarks</span></span>

<span data-ttu-id="e0f57-128">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="e0f57-128">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="e0f57-129">Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapCount** , aby ograniczyć liczbę stert używanych przez aplikację dla serwera GC.</span><span class="sxs-lookup"><span data-stu-id="e0f57-129">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="e0f57-130">Ograniczenie liczby stert używanych na serwerze GC jest szczególnie przydatne w przypadku systemów, w których działa wiele wystąpień aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="e0f57-130">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="e0f57-131">**GCHeapCount** jest zazwyczaj używany wraz z dwiema innymi flagami:</span><span class="sxs-lookup"><span data-stu-id="e0f57-131">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="e0f57-132">[GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="e0f57-132">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="e0f57-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), która kontroluje koligację wątków/sterty GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="e0f57-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="e0f57-134">Jeśli ustawiono wartość **GCHeapCount** , **a GCNoAffinitize** jest wyłączona (ustawienie domyślne), istnieje koligacja między liczbami wątków i sterty *GC i* pierwszą *NN* procesorów.</span><span class="sxs-lookup"><span data-stu-id="e0f57-134">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="e0f57-135">Można użyć elementu **GCHeapAffinitizeMask** , aby określić, które procesory są używane przez sterty GC serwera procesu.</span><span class="sxs-lookup"><span data-stu-id="e0f57-135">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="e0f57-136">W przeciwnym razie, jeśli w systemie działa wiele procesów serwera, ich użycie procesora nastąpi.</span><span class="sxs-lookup"><span data-stu-id="e0f57-136">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="e0f57-137">Jeśli **GCHeapCount** jest ustawiony i **GCNoAffinitize** jest włączona, moduł zbierający elementy bezużyteczne ogranicza liczbę procesorów używanych przez serwer GC, ale nie KOLIGACJI stert i procesorów GC.</span><span class="sxs-lookup"><span data-stu-id="e0f57-137">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="e0f57-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0f57-138">Example</span></span>

<span data-ttu-id="e0f57-139">Poniższy przykład wskazuje, że aplikacja używa serwera GC z 10 stert/wątków.</span><span class="sxs-lookup"><span data-stu-id="e0f57-139">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="e0f57-140">Ponieważ nie chcesz, aby te sterty pokrywały się ze stertami z innych aplikacji uruchomionych w systemie, użyj **GCHeapAffinitizeMask** , aby określić, że proces ma używać procesorów od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="e0f57-140">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="e0f57-141">Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10.</span><span class="sxs-lookup"><span data-stu-id="e0f57-141">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e0f57-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0f57-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e0f57-143">GCNoAffinitize, element</span><span class="sxs-lookup"><span data-stu-id="e0f57-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="e0f57-144">GCHeapAffinitizeMask, element</span><span class="sxs-lookup"><span data-stu-id="e0f57-144">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="e0f57-145">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="e0f57-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="e0f57-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e0f57-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e0f57-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e0f57-147">Configuration File Schema</span></span>](../index.md)
