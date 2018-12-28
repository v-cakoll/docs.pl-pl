---
title: '&lt;gcconcurrent —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa802ab9d1025bd130a6265b50050284aae0150
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612390"
---
# <a name="ltgcconcurrentgt-element"></a><span data-ttu-id="bb235-102">&lt;gcconcurrent —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="bb235-102">&lt;gcConcurrent&gt; Element</span></span>
<span data-ttu-id="bb235-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="bb235-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>  
  
 <span data-ttu-id="bb235-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bb235-104">\<configuration></span></span>  
<span data-ttu-id="bb235-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="bb235-105">\<runtime></span></span>  
<span data-ttu-id="bb235-106">\<gcconcurrent — ></span><span class="sxs-lookup"><span data-stu-id="bb235-106">\<gcConcurrent></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb235-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb235-107">Syntax</span></span>  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb235-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bb235-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bb235-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bb235-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb235-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bb235-110">Attributes</span></span>  
  
|<span data-ttu-id="bb235-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bb235-111">Attribute</span></span>|<span data-ttu-id="bb235-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bb235-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bb235-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="bb235-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb235-114">Określa, czy środowisko uruchomieniowe jednocześnie uruchamia wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bb235-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="bb235-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bb235-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="bb235-116">Value</span></span>|<span data-ttu-id="bb235-117">Opis</span><span class="sxs-lookup"><span data-stu-id="bb235-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bb235-118">Nie równoczesne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-118">Does not run garbage collection concurrently.</span></span>|  
|`true`|<span data-ttu-id="bb235-119">Uruchamia współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="bb235-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="bb235-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb235-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bb235-121">Child Elements</span></span>  
 <span data-ttu-id="bb235-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bb235-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb235-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bb235-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb235-124">Element</span><span class="sxs-lookup"><span data-stu-id="bb235-124">Element</span></span>|<span data-ttu-id="bb235-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bb235-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb235-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb235-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bb235-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb235-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb235-128">Remarks</span></span>  
 <span data-ttu-id="bb235-129">Przed .NET Framework 4 wyrzucanie elementów bezużytecznych obsługiwane współbieżne wyrzucanie elementów bezużytecznych, wykonywane wyrzucania elementów bezużytecznych w tle w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="bb235-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="bb235-130">W programie .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych została zastąpiona GC, który wykonuje wyrzucania elementów bezużytecznych w tle w oddzielnym wątku tła.</span><span class="sxs-lookup"><span data-stu-id="bb235-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="bb235-131">Począwszy od programu .NET Framework 4.5, zbieranie w tle stały się dostępne w serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="bb235-132">`<gcConcurrent>` Element kontroluje, czy środowisko uruchomieniowe wykonuje albo równolegle lub w tle wyrzucanie elementów bezużytecznych, jeśli jest dostępna lub czy wykonuje wyrzucanie elementów bezużytecznych na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="bb235-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it is available, or whether it performs garbage collection in the foreground.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bb235-133">Począwszy od programu .NET Framework 4, współbieżne wyrzucanie elementów bezużytecznych zastępuje wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="bb235-133">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="bb235-134">Warunki *współbieżnych* i *tła* są używane zamiennie w dokumentacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb235-134">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="bb235-135">Aby wyłączyć wyrzucania elementów bezużytecznych w tle, należy użyć `<gcConcurrent>` elementu, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="bb235-135">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>  
  
 <span data-ttu-id="bb235-136">Domyślnie używa środowiska uruchomieniowego współbieżnych oraz wyrzucania elementów bezużytecznych w tle, który jest zoptymalizowany pod kątem opóźnień.</span><span class="sxs-lookup"><span data-stu-id="bb235-136">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="bb235-137">Jeśli aplikacja obejmuje interakcji z użytkownikiem duże, należy pozostawić współbieżne wyrzucanie elementów bezużytecznych, włączone, aby zminimalizować czas wstrzymania aplikacji do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-137">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="bb235-138">Jeśli ustawisz `enabled` atrybutu `<gcConcurrent>` elementu `false`, środowisko wykonawcze używa niewspółbieżnym wyrzucaniem elementów bezużytecznych, zoptymalizowaną pod kątem przepływności.</span><span class="sxs-lookup"><span data-stu-id="bb235-138">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="bb235-139">Następujący plik konfiguracji wyłącza wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="bb235-139">The following configuration file disables background garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="bb235-140">W przypadku `<gcConcurrentSetting>` ustawienia w pliku konfiguracji komputera, określa wartość domyślną dla wszystkich aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb235-140">If there is a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="bb235-141">Ustawienie pliku konfiguracji komputera zastępuje ustawienia pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb235-141">The machine configuration file setting overrides the application configuration file setting.</span></span>  
  
 <span data-ttu-id="bb235-142">Aby uzyskać więcej informacji na temat równolegle i wyrzucania elementów bezużytecznych w tle, zobacz sekcję "współbieżne wyrzucanie elementów bezużytecznych" w [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../../docs/standard/garbage-collection/fundamentals.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bb235-142">For more information on concurrent and background garbage collection, see the "Concurrent garbage collection" section in the [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb235-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb235-143">Example</span></span>  
 <span data-ttu-id="bb235-144">Poniższy przykład umożliwia współbieżne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb235-144">The following example enables concurrent garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb235-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb235-145">See Also</span></span>  
- [<span data-ttu-id="bb235-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bb235-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="bb235-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bb235-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="bb235-148">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="bb235-148">Fundamentals of Garbage Collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md)
