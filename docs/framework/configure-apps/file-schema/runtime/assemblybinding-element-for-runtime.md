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
ms.openlocfilehash: eec77d4dd42a7b95d1e2cd0e353e2e54746676b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704885"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="3f866-102">\<assemblybinding — >, Element dla \<runtime ></span><span class="sxs-lookup"><span data-stu-id="3f866-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="3f866-103">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="3f866-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="3f866-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3f866-104">\<configuration></span></span>  
<span data-ttu-id="3f866-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="3f866-105">\<runtime></span></span>  
<span data-ttu-id="3f866-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="3f866-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f866-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f866-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f866-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f866-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3f866-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f866-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f866-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f866-110">Attributes</span></span>  
  
|<span data-ttu-id="3f866-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f866-111">Attribute</span></span>|<span data-ttu-id="3f866-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3f866-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f866-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="3f866-113">**xmlns**</span></span>|<span data-ttu-id="3f866-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3f866-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f866-115">Określa przestrzeń nazw XML wymagane w celu tworzenia powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="3f866-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="3f866-116">Użyj ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="3f866-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="3f866-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="3f866-117">**appliesTo**</span></span>|<span data-ttu-id="3f866-118">Określa wersję środowiska uruchomieniowego, dotyczy przekierowania zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f866-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="3f866-119">Ten atrybut opcjonalny używa numeru wersji .NET Framework, aby wskazać dla której wersji dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f866-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="3f866-120">Jeśli nie **appliesTo** atrybut jest określony,  **\<assemblyBinding >** element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f866-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="3f866-121">**AppliesTo** atrybut wprowadzono w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="3f866-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="3f866-122">Oznacza to, że wszystkie  **\<assemblyBinding >** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.</span><span class="sxs-lookup"><span data-stu-id="3f866-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f866-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f866-123">Child Elements</span></span>  
  
|<span data-ttu-id="3f866-124">Element</span><span class="sxs-lookup"><span data-stu-id="3f866-124">Element</span></span>|<span data-ttu-id="3f866-125">Opis</span><span class="sxs-lookup"><span data-stu-id="3f866-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f866-126">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="3f866-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="3f866-127">Hermetyzuje powiązania zasad oraz lokalizację zestawu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f866-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="3f866-128">Użyj jednej  **\<dependentAssembly >** tag dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f866-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="3f866-129">\<sondowanie ></span><span class="sxs-lookup"><span data-stu-id="3f866-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="3f866-130">Określa podkatalogi podczas ładowania zestawów środowiska uruchomieniowego języka wspólnego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="3f866-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="3f866-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="3f866-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="3f866-132">Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="3f866-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="3f866-133">\<qualifyassembly — ></span><span class="sxs-lookup"><span data-stu-id="3f866-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="3f866-134">Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.</span><span class="sxs-lookup"><span data-stu-id="3f866-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f866-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f866-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3f866-136">Element</span><span class="sxs-lookup"><span data-stu-id="3f866-136">Element</span></span>|<span data-ttu-id="3f866-137">Opis</span><span class="sxs-lookup"><span data-stu-id="3f866-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3f866-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f866-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3f866-139">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3f866-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f866-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f866-140">Example</span></span>  
 <span data-ttu-id="3f866-141">Poniższy przykład przedstawia sposób przekierowywania wersji zestawu do drugiego i podaj bazę kodu.</span><span class="sxs-lookup"><span data-stu-id="3f866-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="3f866-142">Poniższy przykład pokazuje, jak używać **appliesTo** atrybutu, aby przekierować powiązanie zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f866-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f866-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f866-143">See also</span></span>

- [<span data-ttu-id="3f866-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3f866-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3f866-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3f866-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="3f866-146">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="3f866-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
