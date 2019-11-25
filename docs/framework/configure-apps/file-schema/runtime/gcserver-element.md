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
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968948"
---
# <a name="gcserver-element"></a><span data-ttu-id="5d496-102">\<element > gcServer</span><span class="sxs-lookup"><span data-stu-id="5d496-102">\<gcServer> element</span></span>

<span data-ttu-id="5d496-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

<span data-ttu-id="5d496-104">[\<> konfiguracji](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d496-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="5d496-105">&nbsp;&nbsp;[\<środowiska uruchomieniowego >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d496-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="5d496-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer ></span><span class="sxs-lookup"><span data-stu-id="5d496-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer></span></span>

## <a name="syntax"></a><span data-ttu-id="5d496-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d496-107">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d496-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d496-108">Attributes and elements</span></span>

<span data-ttu-id="5d496-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d496-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d496-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d496-110">Attributes</span></span>

|<span data-ttu-id="5d496-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5d496-111">Attribute</span></span>|<span data-ttu-id="5d496-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5d496-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5d496-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5d496-113">Required attribute.</span></span><br /><br /><span data-ttu-id="5d496-114">Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-114">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="5d496-115">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="5d496-115">enabled attribute</span></span>

|<span data-ttu-id="5d496-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5d496-116">Value</span></span>|<span data-ttu-id="5d496-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5d496-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5d496-118">Nie uruchamia odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-118">Does not run server garbage collection.</span></span> <span data-ttu-id="5d496-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5d496-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="5d496-120">Uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-120">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5d496-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d496-121">Child elements</span></span>

<span data-ttu-id="5d496-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d496-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d496-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d496-123">Parent elements</span></span>

|<span data-ttu-id="5d496-124">Element</span><span class="sxs-lookup"><span data-stu-id="5d496-124">Element</span></span>|<span data-ttu-id="5d496-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5d496-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5d496-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d496-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5d496-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5d496-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d496-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d496-128">Remarks</span></span>

<span data-ttu-id="5d496-129">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy wyrzucania elementów bezużytecznych: odzyskiwanie pamięci stacji roboczej, które jest dostępne we wszystkich systemach i wyrzucanie elementów bezużytecznych serwera, które jest dostępne w systemach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="5d496-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="5d496-130">Użyj elementu **gcServer** , aby kontrolować typ wyrzucania elementów bezużytecznych wykonywanych przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5d496-130">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="5d496-131">Użyj właściwości <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>, aby określić, czy jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="5d496-132">W przypadku komputerów z jednym procesorem domyślna opcja wyrzucania elementów bezużytecznych stacji roboczej powinna być najszybszą opcją.</span><span class="sxs-lookup"><span data-stu-id="5d496-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="5d496-133">Stacja robocza lub serwer może być używana w przypadku komputerów dwuprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="5d496-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="5d496-134">Wyrzucanie elementów bezużytecznych serwera powinno być najszybszą opcją dla więcej niż dwóch procesorów.</span><span class="sxs-lookup"><span data-stu-id="5d496-134">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="5d496-135">Najczęściej systemy serwerów wieloprocesorowych wyłączą serwer GC i używają stacji roboczej GC zamiast tego, gdy wiele wystąpień aplikacji serwerowych działa na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5d496-135">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="5d496-136">Tego elementu można używać tylko w pliku konfiguracji aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="5d496-136">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="5d496-137">W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępne po włączeniu odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5d496-137">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="5d496-138">Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych serwera jest współbieżne.</span><span class="sxs-lookup"><span data-stu-id="5d496-138">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="5d496-139">Aby użyć niewspółbieżnego wyrzucania elementów bezużytecznych serwera, Ustaw element **gcServer** na `true` i [element gcConcurrent](gcconcurrent-element.md) , aby `false`.</span><span class="sxs-lookup"><span data-stu-id="5d496-139">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="5d496-140">Począwszy od .NET Framework 4.6.2 można również skonfigurować serwer GC przy użyciu następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5d496-140">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="5d496-141">[GCNoAffinitize](gcnoaffinitize-element.md), który określa, czy istnieje koligacja między stertą i procesorami serwera GC.</span><span class="sxs-lookup"><span data-stu-id="5d496-141">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="5d496-142">Domyślnie dla każdego procesora istnieje jedna sterta serwera GC.</span><span class="sxs-lookup"><span data-stu-id="5d496-142">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="5d496-143">[GCHeapCount](gcheapcount-element.md), który ogranicza liczbę sterty używanych przez proces.</span><span class="sxs-lookup"><span data-stu-id="5d496-143">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="5d496-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), który definiuje koligację między dostępnymi stertami GC serwera a indywidualnymi procesorami.</span><span class="sxs-lookup"><span data-stu-id="5d496-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="5d496-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d496-145">Example</span></span>

<span data-ttu-id="5d496-146">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera:</span><span class="sxs-lookup"><span data-stu-id="5d496-146">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5d496-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d496-147">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d496-148">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5d496-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d496-149">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5d496-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d496-150">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5d496-150">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
