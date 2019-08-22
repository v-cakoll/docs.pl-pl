---
title: <gcServer>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61b4076a72dbc17ffc800a1a8d37a22d1435e02b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663679"
---
# <a name="gcserver-element"></a><span data-ttu-id="e6c4e-102">\<gcServer, element ></span><span class="sxs-lookup"><span data-stu-id="e6c4e-102">\<gcServer> Element</span></span>
<span data-ttu-id="e6c4e-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="e6c4e-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e6c4e-104">\<configuration></span></span>  
<span data-ttu-id="e6c4e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e6c4e-105">\<runtime></span></span>  
<span data-ttu-id="e6c4e-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="e6c4e-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c4e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6c4e-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6c4e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6c4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6c4e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6c4e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6c4e-110">Attributes</span></span>  
  
|<span data-ttu-id="e6c4e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6c4e-111">Attribute</span></span>|<span data-ttu-id="e6c4e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e6c4e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e6c4e-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6c4e-114">Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e6c4e-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="e6c4e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e6c4e-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6c4e-116">Value</span></span>|<span data-ttu-id="e6c4e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e6c4e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e6c4e-118">Nie uruchamia odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-118">Does not run server garbage collection.</span></span> <span data-ttu-id="e6c4e-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e6c4e-120">Uruchamia odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6c4e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6c4e-121">Child Elements</span></span>  
 <span data-ttu-id="e6c4e-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6c4e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6c4e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e6c4e-124">Element</span><span class="sxs-lookup"><span data-stu-id="e6c4e-124">Element</span></span>|<span data-ttu-id="e6c4e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e6c4e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6c4e-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6c4e-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6c4e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6c4e-128">Remarks</span></span>  
 <span data-ttu-id="e6c4e-129">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy wyrzucania elementów bezużytecznych: odzyskiwanie pamięci stacji roboczej, które jest dostępne we wszystkich systemach i wyrzucanie elementów bezużytecznych serwera, które jest dostępne w systemach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="e6c4e-130">Za pomocą `<gcServer>` elementu można kontrolować typ wyrzucania elementów bezużytecznych wykonywanych przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="e6c4e-131">Użyj właściwości <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> , aby określić, czy jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="e6c4e-132">W przypadku komputerów z jednym procesorem domyślna opcja wyrzucania elementów bezużytecznych stacji roboczej powinna być najszybszą opcją.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="e6c4e-133">Stacja robocza lub serwer może być używana w przypadku komputerów dwuprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="e6c4e-134">Wyrzucanie elementów bezużytecznych serwera powinno być najszybszą opcją dla więcej niż dwóch procesorów.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="e6c4e-135">Tego elementu można używać tylko w pliku konfiguracji aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6c4e-136">W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępne po włączeniu odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="e6c4e-137">Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych serwera jest współbieżne.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="e6c4e-138">Aby użyć niewspółbieżnego wyrzucania elementów bezużytecznych serwera `true` , ustaw `<gcServer>` element na i [ \<gcConcurrent > elementu.](gcconcurrent-element.md) `false`</span><span class="sxs-lookup"><span data-stu-id="e6c4e-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c4e-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6c4e-139">Example</span></span>  
 <span data-ttu-id="e6c4e-140">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6c4e-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6c4e-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e6c4e-142">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e6c4e-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e6c4e-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e6c4e-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e6c4e-144">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="e6c4e-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
