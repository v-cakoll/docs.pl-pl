---
title: <relativeBindForResources>, element
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153909"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="a6013-102">\<relativeBindForResources> Element</span><span class="sxs-lookup"><span data-stu-id="a6013-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="a6013-103">Optymalizuje sondę dla zestawów satelitowych.</span><span class="sxs-lookup"><span data-stu-id="a6013-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="a6013-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6013-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6013-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6013-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a6013-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span><span class="sxs-lookup"><span data-stu-id="a6013-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6013-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6013-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6013-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6013-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6013-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6013-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6013-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6013-110">Attributes</span></span>  
  
|<span data-ttu-id="a6013-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6013-111">Attribute</span></span>|<span data-ttu-id="a6013-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a6013-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a6013-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a6013-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a6013-114">Określa, czy środowisko wykonawcze języka wspólnego optymalizuje sondę dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="a6013-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a6013-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="a6013-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a6013-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="a6013-116">Value</span></span>|<span data-ttu-id="a6013-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a6013-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a6013-118">Środowisko wykonawcze nie optymalizuje sondy dla zestawów satelitowych.</span><span class="sxs-lookup"><span data-stu-id="a6013-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="a6013-119">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="a6013-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="a6013-120">Środowisko wykonawcze optymalizuje sondę dla zestawów satelitowych.</span><span class="sxs-lookup"><span data-stu-id="a6013-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6013-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6013-121">Child Elements</span></span>  
 <span data-ttu-id="a6013-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6013-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6013-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6013-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a6013-124">Element</span><span class="sxs-lookup"><span data-stu-id="a6013-124">Element</span></span>|<span data-ttu-id="a6013-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a6013-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6013-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6013-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a6013-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a6013-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6013-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6013-128">Remarks</span></span>  
 <span data-ttu-id="a6013-129">Ogólnie rzecz biorąc, Menedżer zasobów sonduje zasoby, zgodnie z dokumentami w temacie [Pakowanie i wdrażanie zasobów.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a6013-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="a6013-130">Oznacza to, że gdy Menedżer zasobów sonduje dla określonej zlokalizowanej wersji zasobu, może wyglądać w globalnej pamięci podręcznej zestawów, szukać w folderze <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> specyficznym dla kultury w bazie kodu aplikacji, wysyłać zapytania instalatora Windows dla zestawów satelickich i podnosić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a6013-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="a6013-131">Element `<relativeBindForResources>` optymalizuje sposób, w jaki Resource Manager sondy dla zestawów satelitowych.</span><span class="sxs-lookup"><span data-stu-id="a6013-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="a6013-132">Może poprawić wydajność podczas sondowania zasobów w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="a6013-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="a6013-133">Gdy zestaw satelitów jest wdrażany w tej samej lokalizacji co zestaw kodu.</span><span class="sxs-lookup"><span data-stu-id="a6013-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="a6013-134">Innymi słowy, jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, zestawy satelickiego muszą być również zainstalowane tam.</span><span class="sxs-lookup"><span data-stu-id="a6013-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="a6013-135">Jeśli zestaw kodu jest zainstalowany w bazie kodu aplikacji, zestawy satelickiego muszą być również zainstalowane w folderze specyficznym dla kultury w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6013-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="a6013-136">Gdy Instalator Windows nie jest używany lub jest używany rzadko do instalacji na żądanie zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="a6013-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="a6013-137">Gdy kod aplikacji nie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> obsługuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a6013-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="a6013-138">Ustawienie `enabled` atrybutu elementu `<relativeBindForResources>` w `true` celu optymalizacji sondy Menedżera zasobów dla zestawów satelitowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a6013-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="a6013-139">Używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="a6013-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="a6013-140">Nie wysyła kwerendy Instalatora Windows dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="a6013-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="a6013-141">Nie podnosi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a6013-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6013-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6013-142">See also</span></span>

- [<span data-ttu-id="a6013-143">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="a6013-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="a6013-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a6013-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6013-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a6013-145">Configuration File Schema</span></span>](../index.md)
