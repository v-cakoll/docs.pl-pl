---
title: "&lt;relativebindforresources —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8409b1fe86776397ceb3db5b338fb8aaadef9cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="1a08a-102">&lt;relativebindforresources —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1a08a-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="1a08a-103">Optymalizuje sondy zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1a08a-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="1a08a-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="1a08a-104">\<configuration> Element</span></span>  
<span data-ttu-id="1a08a-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="1a08a-105">\<runtime> Element</span></span>  
<span data-ttu-id="1a08a-106">\<relativebindforresources — > — Element</span><span class="sxs-lookup"><span data-stu-id="1a08a-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a08a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a08a-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a08a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a08a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1a08a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a08a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a08a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a08a-110">Attributes</span></span>  
  
|<span data-ttu-id="1a08a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a08a-111">Attribute</span></span>|<span data-ttu-id="1a08a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1a08a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1a08a-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1a08a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a08a-114">Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondy zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1a08a-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1a08a-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1a08a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1a08a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1a08a-116">Value</span></span>|<span data-ttu-id="1a08a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1a08a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1a08a-118">Środowisko uruchomieniowe nie zoptymalizować badanie zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1a08a-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="1a08a-119">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="1a08a-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="1a08a-120">Środowisko uruchomieniowe optymalizuje sondy zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1a08a-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a08a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a08a-121">Child Elements</span></span>  
 <span data-ttu-id="1a08a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a08a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a08a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a08a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1a08a-124">Element</span><span class="sxs-lookup"><span data-stu-id="1a08a-124">Element</span></span>|<span data-ttu-id="1a08a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1a08a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a08a-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a08a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1a08a-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1a08a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a08a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a08a-128">Remarks</span></span>  
 <span data-ttu-id="1a08a-129">Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w [pakowanie i wdrażanie zasobów](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1a08a-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="1a08a-130">To oznacza, że podczas badania Menedżera zasobów dla określonej wersji zlokalizowanych zasobów, jego może Szukaj w globalnej pamięci podręcznej zestawów, poszukaj w folderze określonej kultury w podstawowej, zapytania kodu aplikacji Instalatora Windows zestawy satelickie i podnieść <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a08a-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="1a08a-131">`<relativeBindForResources>` Sposób, w którym Menedżer zasobów sondy zestawów satelickich optymalizuje elementu.</span><span class="sxs-lookup"><span data-stu-id="1a08a-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="1a08a-132">Go może poprawić wydajność podczas badania zasobów w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="1a08a-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="1a08a-133">Podczas wdrażania zestawu satelickiego w tej samej lokalizacji co zestaw kodu.</span><span class="sxs-lookup"><span data-stu-id="1a08a-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="1a08a-134">Innymi słowy Jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, zestawy satelickie należy także zainstalować istnieje.</span><span class="sxs-lookup"><span data-stu-id="1a08a-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="1a08a-135">Po zainstalowaniu zestawu kodu w kodzie aplikacji podstawowe zestawy satelickie należy także zainstalować w folderze określonej kultury w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="1a08a-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="1a08a-136">Gdy Instalator Windows nie jest używana lub jest rzadko używana dla instalacji zestawów satelickich na żądanie.</span><span class="sxs-lookup"><span data-stu-id="1a08a-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="1a08a-137">Jeśli kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a08a-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="1a08a-138">Ustawienie `enabled` atrybutu `<relativeBindForResources>` elementu `true` optymalizuje sondowania Menedżera zasobów dla zestawów satelickich w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1a08a-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="1a08a-139">Badanie dla zestawu satelickiego używa lokalizacji zestawu kod nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="1a08a-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="1a08a-140">Nie odpytuje Instalatora Windows zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1a08a-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="1a08a-141">Nie zgłaszał <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a08a-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a08a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a08a-142">See Also</span></span>  
 [<span data-ttu-id="1a08a-143">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="1a08a-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="1a08a-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1a08a-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1a08a-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1a08a-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
