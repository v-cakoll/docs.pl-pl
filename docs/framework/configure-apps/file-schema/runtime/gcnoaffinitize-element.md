---
title: GCNoAffinitize, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004741"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="9922f-102">\<GCNoAffinitize>, element</span><span class="sxs-lookup"><span data-stu-id="9922f-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="9922f-103">Określa, czy koligacji wątki serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="9922f-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="9922f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9922f-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9922f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9922f-105">Attributes and elements</span></span>

<span data-ttu-id="9922f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9922f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9922f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9922f-107">Attributes</span></span>

|<span data-ttu-id="9922f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9922f-108">Attribute</span></span>|<span data-ttu-id="9922f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9922f-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9922f-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9922f-110">Required attribute.</span></span><br /><br /><span data-ttu-id="9922f-111">Określa, czy wątki/sterty serwera GC są koligacją z procesorami dostępnymi na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9922f-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="9922f-112">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="9922f-112">enabled attribute</span></span>

|<span data-ttu-id="9922f-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="9922f-113">Value</span></span>|<span data-ttu-id="9922f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9922f-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="9922f-115">Skoligacony Server GC wątki z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="9922f-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="9922f-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="9922f-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="9922f-117">Nie koligacji wątków serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="9922f-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9922f-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9922f-118">Child elements</span></span>

<span data-ttu-id="9922f-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="9922f-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9922f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9922f-120">Parent elements</span></span>

|<span data-ttu-id="9922f-121">Element</span><span class="sxs-lookup"><span data-stu-id="9922f-121">Element</span></span>|<span data-ttu-id="9922f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9922f-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9922f-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9922f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9922f-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9922f-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9922f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9922f-125">Remarks</span></span>

<span data-ttu-id="9922f-126">Domyślnie wątki serwera GC są trudne do koligacji z odpowiednimi procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="9922f-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="9922f-127">Każdy z dostępnych procesorów systemu ma własną stertę i wątek GC.</span><span class="sxs-lookup"><span data-stu-id="9922f-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="9922f-128">Jest to zazwyczaj preferowane ustawienie, ponieważ optymalizuje użycie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9922f-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="9922f-129">Rozpoczynając od .NET Framework 4.6.2, ustawiając atrybut **GCNoAffinitize** elementu `enabled` na `true` , można określić, że wątki i procesory serwera GC nie powinny być ściśle sprzężone.</span><span class="sxs-lookup"><span data-stu-id="9922f-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="9922f-130">Można określić **GCNoAffinitize** element konfiguracji, aby nie koligacji wątki serwera GC z procesorami CPU.</span><span class="sxs-lookup"><span data-stu-id="9922f-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="9922f-131">Można go również użyć wraz z elementem [GCHeapCount](gcheapcount-element.md) , aby kontrolować liczbę stert i wątków GC używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9922f-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="9922f-132">Jeśli `enabled` atrybut elementu **GCNoAffinitize** jest `false` (jego wartość domyślna), można również użyć elementu [GCHeapCount](gcheapcount-element.md) , aby określić liczbę wątków i sterty GC, wraz z elementem [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) , aby określić procesory, do których są koligacje wątki i sterty GC.</span><span class="sxs-lookup"><span data-stu-id="9922f-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="9922f-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9922f-133">Example</span></span>

<span data-ttu-id="9922f-134">W poniższym przykładzie nie są twarde koligacji Server GC wątki:</span><span class="sxs-lookup"><span data-stu-id="9922f-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="9922f-135">Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10:</span><span class="sxs-lookup"><span data-stu-id="9922f-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9922f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9922f-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9922f-137">GCHeapAffinitizeMask, element</span><span class="sxs-lookup"><span data-stu-id="9922f-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="9922f-138">GCHeapCount, element</span><span class="sxs-lookup"><span data-stu-id="9922f-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="9922f-139">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="9922f-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="9922f-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9922f-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9922f-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9922f-141">Configuration File Schema</span></span>](../index.md)
