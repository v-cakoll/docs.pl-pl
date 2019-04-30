---
title: <relativeBindForResources>, element
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98914f57c24dc51625564e266157731ff173337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704573"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="9d9ec-102">\<relativeBindForResources> Element</span><span class="sxs-lookup"><span data-stu-id="9d9ec-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="9d9ec-103">Optymalizuje sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="9d9ec-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="9d9ec-104">\<configuration> Element</span></span>  
<span data-ttu-id="9d9ec-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="9d9ec-105">\<runtime> Element</span></span>  
<span data-ttu-id="9d9ec-106">\<relativeBindForResources> Element</span><span class="sxs-lookup"><span data-stu-id="9d9ec-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9ec-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d9ec-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d9ec-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d9ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d9ec-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d9ec-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d9ec-110">Attributes</span></span>  
  
|<span data-ttu-id="9d9ec-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9d9ec-111">Attribute</span></span>|<span data-ttu-id="9d9ec-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9d9ec-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9d9ec-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d9ec-114">Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9d9ec-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="9d9ec-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9d9ec-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="9d9ec-116">Value</span></span>|<span data-ttu-id="9d9ec-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9d9ec-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9d9ec-118">Środowisko wykonawcze nie optymalizuje sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="9d9ec-119">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="9d9ec-120">Środowisko uruchomieniowe optymalizuje sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d9ec-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d9ec-121">Child Elements</span></span>  
 <span data-ttu-id="9d9ec-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d9ec-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d9ec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d9ec-124">Element</span><span class="sxs-lookup"><span data-stu-id="9d9ec-124">Element</span></span>|<span data-ttu-id="9d9ec-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9d9ec-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d9ec-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9d9ec-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d9ec-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d9ec-128">Remarks</span></span>  
 <span data-ttu-id="9d9ec-129">Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="9d9ec-130">Oznacza to, że po sondy usługi Resource Manager dla konkretnej wersji zlokalizowanych zasobów, jego może Szukaj w globalnej pamięci podręcznej, poszukaj w folderze kodu aplikacji — zapytania bazowego, Instalator Windows specyficzne dla kultury zestawy satelickie i podnieść <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="9d9ec-131">`<relativeBindForResources>` Element optymalizuje sposób, w którym Menedżer zasobów sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="9d9ec-132">Go może poprawić wydajność podczas sondowania dla zasobów w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="9d9ec-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="9d9ec-133">Podczas wdrażania w tej samej lokalizacji co zestawu kodu w zestawie satelickim.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="9d9ec-134">Innymi słowy Jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej, zestawy satelickie należy także zainstalować istnieje.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="9d9ec-135">Jeśli zestaw kodu jest zainstalowana w bazie kodu aplikacji, zestawy satelickie musi również zainstalowany w folderze specyficzne dla kultury bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="9d9ec-136">Gdy Instalator Windows nie jest używana lub jest tylko rzadko używane do instalowania zestawów satelickich na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="9d9ec-137">Gdy kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="9d9ec-138">Ustawienie `enabled` atrybutu `<relativeBindForResources>` elementu `true` optymalizuje sondy usługi Resource Manager dla zestawów satelickich w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9d9ec-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="9d9ec-139">Lokalizacja zestawu kodu nadrzędnego używa do sondowania dla zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="9d9ec-140">Nie odpytuje Instalatora Windows dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="9d9ec-141">Zgłaszaj <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9d9ec-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9ec-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d9ec-142">See also</span></span>

- [<span data-ttu-id="9d9ec-143">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="9d9ec-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="9d9ec-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9d9ec-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9d9ec-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d9ec-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
