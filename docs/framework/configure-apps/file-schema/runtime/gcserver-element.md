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
ms.openlocfilehash: 5df7ab070cc0a40f4e2f3d0545c5bc40ccb07f4d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378033"
---
# <a name="gcserver-element"></a><span data-ttu-id="19a3a-102">\<gcServer> Element</span><span class="sxs-lookup"><span data-stu-id="19a3a-102">\<gcServer> Element</span></span>
<span data-ttu-id="19a3a-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="19a3a-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="19a3a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="19a3a-104">\<configuration></span></span>  
<span data-ttu-id="19a3a-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="19a3a-105">\<runtime></span></span>  
<span data-ttu-id="19a3a-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="19a3a-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a3a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="19a3a-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19a3a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="19a3a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="19a3a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19a3a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19a3a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19a3a-110">Attributes</span></span>  
  
|<span data-ttu-id="19a3a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="19a3a-111">Attribute</span></span>|<span data-ttu-id="19a3a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="19a3a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="19a3a-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="19a3a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="19a3a-114">Określa, czy środowisko uruchomieniowe jest uruchamiany serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="19a3a-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="19a3a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="19a3a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="19a3a-116">Value</span></span>|<span data-ttu-id="19a3a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="19a3a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="19a3a-118">Nie jest uruchamiany serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-118">Does not run server garbage collection.</span></span> <span data-ttu-id="19a3a-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="19a3a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="19a3a-120">Uruchamia serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19a3a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="19a3a-121">Child Elements</span></span>  
 <span data-ttu-id="19a3a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="19a3a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19a3a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="19a3a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="19a3a-124">Element</span><span class="sxs-lookup"><span data-stu-id="19a3a-124">Element</span></span>|<span data-ttu-id="19a3a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="19a3a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="19a3a-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19a3a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="19a3a-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19a3a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19a3a-128">Remarks</span></span>  
 <span data-ttu-id="19a3a-129">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy operacji wyrzucania elementów bezużytecznych: wyrzucanie elementów bezużytecznych, który jest dostępny we wszystkich systemach, i wyrzucanie elementów bezużytecznych serwera, który jest dostępny w systemach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="19a3a-130">Możesz użyć `<gcServer>` wykonuje element, aby kontrolować typ wyrzucania elementów bezużytecznych środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="19a3a-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="19a3a-131">Użyj <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> właściwości w celu określenia, czy włączono serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="19a3a-132">W przypadku komputerów z jednym procesorem wyrzucanie elementów bezużytecznych stacji roboczej domyślne powinny być najszybszą opcję.</span><span class="sxs-lookup"><span data-stu-id="19a3a-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="19a3a-133">Dwa procesory komputerów można stacji roboczej lub serwera.</span><span class="sxs-lookup"><span data-stu-id="19a3a-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="19a3a-134">Wyrzucanie elementów bezużytecznych serwera powinien być najszybszą opcję dla więcej niż dwóch procesorów.</span><span class="sxs-lookup"><span data-stu-id="19a3a-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="19a3a-135">Ten element może być używany tylko w pliku konfiguracyjnym aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="19a3a-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19a3a-136">W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępna, gdy serwer wyrzucania elementów bezużytecznych jest włączona.</span><span class="sxs-lookup"><span data-stu-id="19a3a-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="19a3a-137">Począwszy od programu .NET Framework 4.5, wyrzucanie elementów bezużytecznych serwera jest współbieżnych.</span><span class="sxs-lookup"><span data-stu-id="19a3a-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="19a3a-138">Aby użyć serwera niewspółbieżnym wyrzucaniem elementów bezużytecznych, ustaw `<gcServer>` elementu `true` i [ \<gcconcurrent — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do `false`.</span><span class="sxs-lookup"><span data-stu-id="19a3a-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a3a-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="19a3a-139">Example</span></span>  
 <span data-ttu-id="19a3a-140">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="19a3a-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19a3a-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19a3a-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="19a3a-142">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="19a3a-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="19a3a-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="19a3a-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="19a3a-144">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="19a3a-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
