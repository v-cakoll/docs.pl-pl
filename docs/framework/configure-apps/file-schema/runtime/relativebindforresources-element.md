---
title: <relativeBindForResources> Element
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115799"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="dee10-102">\<element > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="dee10-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="dee10-103">Optymalizuje sondę dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="dee10-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="dee10-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dee10-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="dee10-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="dee10-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources >**</span><span class="sxs-lookup"><span data-stu-id="dee10-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee10-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dee10-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dee10-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dee10-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dee10-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dee10-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dee10-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dee10-110">Attributes</span></span>  
  
|<span data-ttu-id="dee10-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dee10-111">Attribute</span></span>|<span data-ttu-id="dee10-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dee10-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dee10-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="dee10-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="dee10-114">Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondę dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dee10-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="dee10-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="dee10-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="dee10-116">Value</span></span>|<span data-ttu-id="dee10-117">Opis</span><span class="sxs-lookup"><span data-stu-id="dee10-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="dee10-118">Środowisko uruchomieniowe nie optymalizuje sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="dee10-119">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="dee10-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="dee10-120">Środowisko uruchomieniowe optymalizuje sondę dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dee10-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dee10-121">Child Elements</span></span>  
 <span data-ttu-id="dee10-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="dee10-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dee10-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dee10-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dee10-124">Element</span><span class="sxs-lookup"><span data-stu-id="dee10-124">Element</span></span>|<span data-ttu-id="dee10-125">Opis</span><span class="sxs-lookup"><span data-stu-id="dee10-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dee10-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dee10-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dee10-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="dee10-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee10-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dee10-128">Remarks</span></span>  
 <span data-ttu-id="dee10-129">Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w temacie [pakowanie i wdrażanie zasobów](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="dee10-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="dee10-130">Oznacza to, że podczas Menedżer zasobów sond dla konkretnej zlokalizowanej wersji zasobu może on wyglądać w globalnej pamięci podręcznej zestawów, wyszukać w folderze specyficznym dla kultury w bazie kodu aplikacji, Instalator Windows zapytań dla zestawów satelickich i podnieść zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dee10-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="dee10-131">Element `<relativeBindForResources>` optymalizuje sposób, w jaki Menedżer zasobów sondy dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="dee10-132">Może zwiększyć wydajność podczas sondowania zasobów w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="dee10-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="dee10-133">Gdy zestaw satelicki zostanie wdrożony w tej samej lokalizacji co zestaw kodu.</span><span class="sxs-lookup"><span data-stu-id="dee10-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="dee10-134">Innymi słowy, jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, należy również zainstalować w tym miejscu zestawy satelickie.</span><span class="sxs-lookup"><span data-stu-id="dee10-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="dee10-135">Jeśli zestaw kodu jest zainstalowany w bazie kodu aplikacji, zestawy satelickie muszą być również zainstalowane w folderze specyficznym dla kultury w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="dee10-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="dee10-136">Gdy Instalator Windows nie jest używany lub jest używany rzadko w przypadku instalacji zestawów satelitarnych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="dee10-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="dee10-137">Gdy kod aplikacji nie obsługuje zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dee10-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="dee10-138">Ustawienie atrybutu `enabled` elementu `<relativeBindForResources>`, aby `true` zoptymalizować sondę Menedżer zasobów dla zestawów satelitarnych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dee10-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="dee10-139">Używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="dee10-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="dee10-140">Nie bada Instalator Windows dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dee10-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="dee10-141">Nie zgłasza zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dee10-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee10-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dee10-142">See also</span></span>

- [<span data-ttu-id="dee10-143">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="dee10-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="dee10-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="dee10-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dee10-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dee10-145">Configuration File Schema</span></span>](../index.md)
