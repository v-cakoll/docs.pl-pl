---
title: <assemblyBinding>, element dla <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ec54eeb8adee90031057dadc4549cb73527be1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663897"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="ce14e-102">\<zestawbinding > element dla \<> środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ce14e-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="ce14e-103">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="ce14e-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="ce14e-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce14e-104">\<configuration></span></span>  
<span data-ttu-id="ce14e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="ce14e-105">\<runtime></span></span>  
<span data-ttu-id="ce14e-106">\<> zestawubinding</span><span class="sxs-lookup"><span data-stu-id="ce14e-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce14e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce14e-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce14e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce14e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce14e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce14e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce14e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce14e-110">Attributes</span></span>  
  
|<span data-ttu-id="ce14e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ce14e-111">Attribute</span></span>|<span data-ttu-id="ce14e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ce14e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce14e-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="ce14e-113">**xmlns**</span></span>|<span data-ttu-id="ce14e-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ce14e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce14e-115">Określa przestrzeń nazw XML wymaganą dla powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce14e-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="ce14e-116">Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="ce14e-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="ce14e-117">**Zignorowan**</span><span class="sxs-lookup"><span data-stu-id="ce14e-117">**appliesTo**</span></span>|<span data-ttu-id="ce14e-118">Określa wersję środowiska uruchomieniowego, do której odnosi się przekierowanie zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce14e-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="ce14e-119">Ten opcjonalny atrybut używa numeru wersji .NET Framework, aby wskazać, której wersji dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ce14e-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="ce14e-120">Jeśli nie **appliesTo** atrybut jest określony, **\<assemblyBinding>** element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce14e-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="ce14e-121">Atrybut **AppliesTo** został wprowadzony w .NET Framework w wersji 1,1; jest on ignorowany przez .NET Framework w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="ce14e-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="ce14e-122">Oznacza to, że wszystkie **\<assemblyBinding>** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.</span><span class="sxs-lookup"><span data-stu-id="ce14e-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce14e-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce14e-123">Child Elements</span></span>  
  
|<span data-ttu-id="ce14e-124">Element</span><span class="sxs-lookup"><span data-stu-id="ce14e-124">Element</span></span>|<span data-ttu-id="ce14e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ce14e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce14e-126">\<> dependentAssembly</span><span class="sxs-lookup"><span data-stu-id="ce14e-126">\<dependentAssembly></span></span>](dependentassembly-element.md)|<span data-ttu-id="ce14e-127">Hermetyzuje zasady powiązań i lokalizację zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce14e-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="ce14e-128">Użyj jednego  **\<elementu dependentAssembly >** znacznika dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce14e-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="ce14e-129">\<> sondowania</span><span class="sxs-lookup"><span data-stu-id="ce14e-129">\<probing></span></span>](probing-element.md)|<span data-ttu-id="ce14e-130">Określa podkatalogi przeszukiwania środowiska uruchomieniowego języka wspólnego podczas ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="ce14e-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="ce14e-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="ce14e-131">\<publisherPolicy></span></span>](publisherpolicy-element.md)|<span data-ttu-id="ce14e-132">Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ce14e-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="ce14e-133">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="ce14e-133">\<qualifyAssembly></span></span>](qualifyassembly-element.md)|<span data-ttu-id="ce14e-134">Określa pełną nazwę zestawu, który ma być dynamicznie ładowany, gdy zostanie użyta nazwa częściowa.</span><span class="sxs-lookup"><span data-stu-id="ce14e-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce14e-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce14e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="ce14e-136">Element</span><span class="sxs-lookup"><span data-stu-id="ce14e-136">Element</span></span>|<span data-ttu-id="ce14e-137">Opis</span><span class="sxs-lookup"><span data-stu-id="ce14e-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce14e-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce14e-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce14e-139">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ce14e-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce14e-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce14e-140">Example</span></span>  
 <span data-ttu-id="ce14e-141">Poniższy przykład pokazuje, jak przekierować jedną wersję zestawu do innej i podać bazę kodu.</span><span class="sxs-lookup"><span data-stu-id="ce14e-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ce14e-142">Poniższy przykład pokazuje, jak używać atrybutu **AppliesTo** do przekierowywania powiązań zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce14e-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce14e-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce14e-143">See also</span></span>

- [<span data-ttu-id="ce14e-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ce14e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce14e-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce14e-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ce14e-146">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="ce14e-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
