---
title: GCHeapCount, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283071"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="b312c-102">\<GCHeapCount>, element</span><span class="sxs-lookup"><span data-stu-id="b312c-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="b312c-103">Określa liczbę stert/wątków, które mają być używane do wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="b312c-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="b312c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b312c-104">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b312c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b312c-105">Attributes and elements</span></span>

<span data-ttu-id="b312c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b312c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b312c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b312c-107">Attributes</span></span>

|<span data-ttu-id="b312c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b312c-108">Attribute</span></span>|<span data-ttu-id="b312c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b312c-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b312c-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b312c-110">Required attribute.</span></span><br /><br /><span data-ttu-id="b312c-111">Określa liczbę stert, która ma być używana do wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="b312c-111">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="b312c-112">Rzeczywista liczba stert jest minimalnym określoną liczbą stert i liczbą procesorów, które mogą być używane przez proces.</span><span class="sxs-lookup"><span data-stu-id="b312c-112">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="b312c-113">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="b312c-113">enabled attribute</span></span>

|<span data-ttu-id="b312c-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="b312c-114">Value</span></span>|<span data-ttu-id="b312c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b312c-115">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="b312c-116">Liczba stert, które mają być używane na potrzeby serwera GC.</span><span class="sxs-lookup"><span data-stu-id="b312c-116">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b312c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b312c-117">Child elements</span></span>

<span data-ttu-id="b312c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b312c-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b312c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b312c-119">Parent elements</span></span>

|<span data-ttu-id="b312c-120">Element</span><span class="sxs-lookup"><span data-stu-id="b312c-120">Element</span></span>|<span data-ttu-id="b312c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b312c-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b312c-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b312c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b312c-123">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b312c-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b312c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b312c-124">Remarks</span></span>

<span data-ttu-id="b312c-125">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora.</span><span class="sxs-lookup"><span data-stu-id="b312c-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="b312c-126">Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapCount** , aby ograniczyć liczbę stert używanych przez aplikację dla serwera GC.</span><span class="sxs-lookup"><span data-stu-id="b312c-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="b312c-127">Ograniczenie liczby stert używanych na serwerze GC jest szczególnie przydatne w przypadku systemów, w których działa wiele wystąpień aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="b312c-127">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="b312c-128">**GCHeapCount** jest zazwyczaj używany wraz z dwiema innymi flagami:</span><span class="sxs-lookup"><span data-stu-id="b312c-128">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="b312c-129">[GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="b312c-129">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="b312c-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), która kontroluje koligację wątków/sterty GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="b312c-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="b312c-131">Jeśli ustawiono wartość **GCHeapCount** , **a GCNoAffinitize** jest wyłączona (ustawienie domyślne), istnieje koligacja między liczbami wątków i sterty *GC i* pierwszą *NN* procesorów.</span><span class="sxs-lookup"><span data-stu-id="b312c-131">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="b312c-132">Można użyć elementu **GCHeapAffinitizeMask** , aby określić, które procesory są używane przez sterty GC serwera procesu.</span><span class="sxs-lookup"><span data-stu-id="b312c-132">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="b312c-133">W przeciwnym razie, jeśli w systemie działa wiele procesów serwera, ich użycie procesora nastąpi.</span><span class="sxs-lookup"><span data-stu-id="b312c-133">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="b312c-134">Jeśli **GCHeapCount** jest ustawiony i **GCNoAffinitize** jest włączona, moduł zbierający elementy bezużyteczne ogranicza liczbę procesorów używanych przez serwer GC, ale nie KOLIGACJI stert i procesorów GC.</span><span class="sxs-lookup"><span data-stu-id="b312c-134">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="b312c-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="b312c-135">Example</span></span>

<span data-ttu-id="b312c-136">Poniższy przykład wskazuje, że aplikacja używa serwera GC z 10 stert/wątków.</span><span class="sxs-lookup"><span data-stu-id="b312c-136">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="b312c-137">Ponieważ nie chcesz, aby te sterty pokrywały się ze stertami z innych aplikacji uruchomionych w systemie, użyj **GCHeapAffinitizeMask** , aby określić, że proces ma używać procesorów od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="b312c-137">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="b312c-138">Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10.</span><span class="sxs-lookup"><span data-stu-id="b312c-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b312c-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b312c-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b312c-140">GCNoAffinitize, element</span><span class="sxs-lookup"><span data-stu-id="b312c-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="b312c-141">GCHeapAffinitizeMask, element</span><span class="sxs-lookup"><span data-stu-id="b312c-141">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="b312c-142">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="b312c-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="b312c-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b312c-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b312c-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b312c-144">Configuration File Schema</span></span>](../index.md)
