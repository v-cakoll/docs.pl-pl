---
title: '&lt;gcserver —&gt; — Element'
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
ms.openlocfilehash: 8bfe0db3d6fcbdbbcfb90ff488ab19cdbfaab75e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216148"
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="0eb11-102">&lt;gcserver —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="0eb11-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="0eb11-103">Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="0eb11-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="0eb11-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0eb11-104">\<configuration></span></span>  
<span data-ttu-id="0eb11-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0eb11-105">\<runtime></span></span>  
<span data-ttu-id="0eb11-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="0eb11-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb11-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0eb11-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eb11-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0eb11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0eb11-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0eb11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eb11-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0eb11-110">Attributes</span></span>  
  
|<span data-ttu-id="0eb11-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0eb11-111">Attribute</span></span>|<span data-ttu-id="0eb11-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0eb11-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0eb11-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0eb11-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0eb11-114">Określa, czy środowisko uruchomieniowe jest uruchamiany serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0eb11-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="0eb11-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0eb11-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="0eb11-116">Value</span></span>|<span data-ttu-id="0eb11-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0eb11-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0eb11-118">Nie jest uruchamiany serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-118">Does not run server garbage collection.</span></span> <span data-ttu-id="0eb11-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="0eb11-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0eb11-120">Uruchamia serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eb11-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0eb11-121">Child Elements</span></span>  
 <span data-ttu-id="0eb11-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="0eb11-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eb11-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0eb11-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0eb11-124">Element</span><span class="sxs-lookup"><span data-stu-id="0eb11-124">Element</span></span>|<span data-ttu-id="0eb11-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0eb11-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0eb11-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0eb11-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0eb11-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eb11-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0eb11-128">Remarks</span></span>  
 <span data-ttu-id="0eb11-129">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy operacji wyrzucania elementów bezużytecznych: wyrzucanie elementów bezużytecznych, który jest dostępny we wszystkich systemach, i wyrzucanie elementów bezużytecznych serwera, który jest dostępny w systemach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="0eb11-130">Możesz użyć `<gcServer>` wykonuje element, aby kontrolować typ wyrzucania elementów bezużytecznych środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0eb11-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="0eb11-131">Użyj <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> właściwości w celu określenia, czy włączono serwer wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="0eb11-132">W przypadku komputerów z jednym procesorem wyrzucanie elementów bezużytecznych stacji roboczej domyślne powinny być najszybszą opcję.</span><span class="sxs-lookup"><span data-stu-id="0eb11-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="0eb11-133">Dwa procesory komputerów można stacji roboczej lub serwera.</span><span class="sxs-lookup"><span data-stu-id="0eb11-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="0eb11-134">Wyrzucanie elementów bezużytecznych serwera powinien być najszybszą opcję dla więcej niż dwóch procesorów.</span><span class="sxs-lookup"><span data-stu-id="0eb11-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="0eb11-135">Ten element może być używany tylko w pliku konfiguracyjnym aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="0eb11-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eb11-136">W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępna, gdy serwer wyrzucania elementów bezużytecznych jest włączona.</span><span class="sxs-lookup"><span data-stu-id="0eb11-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="0eb11-137">Począwszy od [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], serwer wyrzucania elementów bezużytecznych jest współbieżnych.</span><span class="sxs-lookup"><span data-stu-id="0eb11-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="0eb11-138">Aby użyć serwera niewspółbieżnym wyrzucaniem elementów bezużytecznych, ustaw `<gcServer>` elementu `true` i [ \<gcconcurrent — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do `false`.</span><span class="sxs-lookup"><span data-stu-id="0eb11-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eb11-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="0eb11-139">Example</span></span>  
 <span data-ttu-id="0eb11-140">Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="0eb11-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0eb11-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0eb11-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0eb11-142">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0eb11-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0eb11-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0eb11-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0eb11-144">Porady: wyłączanie współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="0eb11-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
