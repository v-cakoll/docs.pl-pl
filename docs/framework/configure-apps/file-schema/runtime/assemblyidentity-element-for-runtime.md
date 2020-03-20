---
title: <assemblyIdentity>, element dla <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154312"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="51da0-102">\<assemblyIdentity> Element dla \<> środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="51da0-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="51da0-103">Zawiera informacje identyfikujące o zestawie.</span><span class="sxs-lookup"><span data-stu-id="51da0-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="51da0-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="51da0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="51da0-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="51da0-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="51da0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="51da0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="51da0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="51da0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="51da0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span><span class="sxs-lookup"><span data-stu-id="51da0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51da0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="51da0-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51da0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="51da0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="51da0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="51da0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51da0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51da0-112">Attributes</span></span>  
  
|<span data-ttu-id="51da0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="51da0-113">Attribute</span></span>|<span data-ttu-id="51da0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="51da0-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="51da0-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="51da0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="51da0-116">Nazwa zestawu</span><span class="sxs-lookup"><span data-stu-id="51da0-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="51da0-117">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="51da0-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="51da0-118">Ciąg określający język i kraj/region zestawu.</span><span class="sxs-lookup"><span data-stu-id="51da0-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="51da0-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="51da0-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="51da0-120">Wartość szesnastkowa określająca silną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="51da0-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="51da0-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="51da0-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="51da0-122">Jedna z wartości "x86", "amd64", "msil" lub "ia64", określająca architekturę procesora dla zestawu zawierającego kod specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="51da0-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="51da0-123">W wartościach nie rozróżnia się wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="51da0-123">The values are not case-sensitive.</span></span> <span data-ttu-id="51da0-124">Jeśli atrybut jest przypisany do innych `<assemblyIdentity>` wartości, cały element jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="51da0-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="51da0-125">Zobacz: <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="51da0-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="51da0-126">ProcessorArchitecture Attribute processorArchitecture Attribute</span><span class="sxs-lookup"><span data-stu-id="51da0-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="51da0-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="51da0-127">Value</span></span>|<span data-ttu-id="51da0-128">Opis</span><span class="sxs-lookup"><span data-stu-id="51da0-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="51da0-129">Tylko architektura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="51da0-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="51da0-130">Tylko architektura Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="51da0-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="51da0-131">Neutralny w odniesieniu do procesora i bitów na słowo.</span><span class="sxs-lookup"><span data-stu-id="51da0-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="51da0-132">32-bitowy procesor x86, natywny lub w środowisku Windows w systemie Windows (WOW) na platformie 64-bitowej.</span><span class="sxs-lookup"><span data-stu-id="51da0-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51da0-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="51da0-133">Child Elements</span></span>  
 <span data-ttu-id="51da0-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="51da0-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51da0-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="51da0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="51da0-136">Element</span><span class="sxs-lookup"><span data-stu-id="51da0-136">Element</span></span>|<span data-ttu-id="51da0-137">Opis</span><span class="sxs-lookup"><span data-stu-id="51da0-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="51da0-138">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="51da0-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="51da0-139">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51da0-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="51da0-140">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="51da0-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="51da0-141">Użyj `<dependentAssembly>` jednego elementu dla każdego złożenia.</span><span class="sxs-lookup"><span data-stu-id="51da0-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="51da0-142">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="51da0-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51da0-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51da0-143">Remarks</span></span>  
 <span data-ttu-id="51da0-144">Każdy \*\* \<element>>\*\* musi mieć jeden \*\* \<zestawIdentykość>\*\* element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="51da0-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="51da0-145">Jeśli `processorArchitecture` atrybut jest obecny, `<assemblyIdentity>` element ma zastosowanie tylko do zestawu z odpowiednią architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="51da0-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="51da0-146">Jeśli `processorArchitecture` atrybut nie jest obecny, `<assemblyIdentity>` element można zastosować do zestawu z dowolnej architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="51da0-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="51da0-147">W poniższym przykładzie przedstawiono plik konfiguracji dla dwóch zestawów o tej samej nazwie, które są przeznaczone dla dwóch różnych architektur procesora i których wersje nie zostały zachowane w synchronizacji. Gdy aplikacja jest wykonywana na platformie `<assemblyIdentity>` x86, stosuje się pierwszy element, a drugi jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="51da0-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="51da0-148">Jeśli aplikacja jest wykonywana na platformie innej niż x86 lub ia64, oba są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="51da0-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="51da0-149">Jeśli plik konfiguracji `<assemblyIdentity>` zawiera element `processorArchitecture` bez atrybutu i nie zawiera elementu, który pasuje `processorArchitecture` do platformy, element bez atrybutu jest używany.</span><span class="sxs-lookup"><span data-stu-id="51da0-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51da0-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="51da0-150">Example</span></span>  
 <span data-ttu-id="51da0-151">W poniższym przykładzie pokazano, jak podać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="51da0-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51da0-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51da0-152">See also</span></span>

- [<span data-ttu-id="51da0-153">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="51da0-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="51da0-154">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="51da0-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="51da0-155">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="51da0-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
