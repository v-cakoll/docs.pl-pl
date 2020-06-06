---
title: gcServer, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968948"
---
# <a name="gcserver-element"></a><span data-ttu-id="4f215-102">\<gcServer>, element</span><span class="sxs-lookup"><span data-stu-id="4f215-102">\<gcServer> element</span></span>

<span data-ttu-id="4f215-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="4f215-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f215-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f215-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4f215-105">Attributes and elements</span></span>

<span data-ttu-id="4f215-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4f215-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f215-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4f215-107">Attributes</span></span>

|<span data-ttu-id="4f215-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4f215-108">Attribute</span></span>|<span data-ttu-id="4f215-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4f215-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="4f215-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4f215-110">Required attribute.</span></span><br /><br /><span data-ttu-id="4f215-111">Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="4f215-112">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="4f215-112">enabled attribute</span></span>

|<span data-ttu-id="4f215-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="4f215-113">Value</span></span>|<span data-ttu-id="4f215-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4f215-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="4f215-115">Nie uruchamia odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-115">Does not run server garbage collection.</span></span> <span data-ttu-id="4f215-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="4f215-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="4f215-117">Uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4f215-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4f215-118">Child elements</span></span>

<span data-ttu-id="4f215-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="4f215-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4f215-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4f215-120">Parent elements</span></span>

|<span data-ttu-id="4f215-121">Element</span><span class="sxs-lookup"><span data-stu-id="4f215-121">Element</span></span>|<span data-ttu-id="4f215-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4f215-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4f215-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f215-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="4f215-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4f215-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f215-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f215-125">Remarks</span></span>

<span data-ttu-id="4f215-126">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy wyrzucania elementów bezużytecznych: odzyskiwanie pamięci stacji roboczej, które jest dostępne we wszystkich systemach i wyrzucanie elementów bezużytecznych serwera, które jest dostępne w systemach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="4f215-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="4f215-127">Użyj elementu **gcServer** , aby kontrolować typ wyrzucania elementów bezużytecznych wykonywanych przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4f215-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="4f215-128">Użyj <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> właściwości, aby określić, czy jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="4f215-129">W przypadku komputerów z jednym procesorem domyślna opcja wyrzucania elementów bezużytecznych stacji roboczej powinna być najszybszą opcją.</span><span class="sxs-lookup"><span data-stu-id="4f215-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="4f215-130">Stacja robocza lub serwer może być używana w przypadku komputerów dwuprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="4f215-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="4f215-131">Wyrzucanie elementów bezużytecznych serwera powinno być najszybszą opcją dla więcej niż dwóch procesorów.</span><span class="sxs-lookup"><span data-stu-id="4f215-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="4f215-132">Najczęściej systemy serwerów wieloprocesorowych wyłączą serwer GC i używają stacji roboczej GC zamiast tego, gdy wiele wystąpień aplikacji serwerowych działa na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4f215-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="4f215-133">Tego elementu można używać tylko w pliku konfiguracji aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="4f215-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="4f215-134">W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępne po włączeniu odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="4f215-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="4f215-135">Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych serwera jest współbieżne.</span><span class="sxs-lookup"><span data-stu-id="4f215-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="4f215-136">Aby użyć niewspółbieżnego wyrzucania elementów bezużytecznych serwera, Ustaw element **gcServer** na `true` i [element gcConcurrent](gcconcurrent-element.md) na wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="4f215-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="4f215-137">Począwszy od .NET Framework 4.6.2 można również skonfigurować serwer GC przy użyciu następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="4f215-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="4f215-138">[GCNoAffinitize](gcnoaffinitize-element.md), który określa, czy istnieje koligacja między stertą i procesorami serwera GC.</span><span class="sxs-lookup"><span data-stu-id="4f215-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="4f215-139">Domyślnie dla każdego procesora istnieje jedna sterta serwera GC.</span><span class="sxs-lookup"><span data-stu-id="4f215-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="4f215-140">[GCHeapCount](gcheapcount-element.md), który ogranicza liczbę sterty używanych przez proces.</span><span class="sxs-lookup"><span data-stu-id="4f215-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="4f215-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), który definiuje koligację między dostępnymi stertami GC serwera a indywidualnymi procesorami.</span><span class="sxs-lookup"><span data-stu-id="4f215-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="4f215-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f215-142">Example</span></span>

<span data-ttu-id="4f215-143">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera:</span><span class="sxs-lookup"><span data-stu-id="4f215-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4f215-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f215-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f215-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4f215-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4f215-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4f215-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4f215-147">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="4f215-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
