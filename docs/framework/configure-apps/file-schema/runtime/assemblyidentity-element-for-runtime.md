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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154312"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="d08dc-102">\<assemblyIdentity>, element dla \<runtime></span><span class="sxs-lookup"><span data-stu-id="d08dc-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="d08dc-103">Zawiera informacje identyfikacyjne zestawu.</span><span class="sxs-lookup"><span data-stu-id="d08dc-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="d08dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d08dc-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d08dc-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d08dc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d08dc-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d08dc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d08dc-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d08dc-107">Attributes</span></span>  
  
|<span data-ttu-id="d08dc-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d08dc-108">Attribute</span></span>|<span data-ttu-id="d08dc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d08dc-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d08dc-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d08dc-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d08dc-111">Nazwa zestawu</span><span class="sxs-lookup"><span data-stu-id="d08dc-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="d08dc-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d08dc-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d08dc-113">Ciąg określający język i kraj/region zestawu.</span><span class="sxs-lookup"><span data-stu-id="d08dc-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="d08dc-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d08dc-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d08dc-115">Wartość szesnastkowa, która określa silną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="d08dc-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="d08dc-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d08dc-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d08dc-117">Jedna z wartości "x86", "amd64", "MSIL" lub "ia64", określająca architekturę procesora dla zestawu, który zawiera kod specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="d08dc-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="d08dc-118">W wartościach nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d08dc-118">The values are not case-sensitive.</span></span> <span data-ttu-id="d08dc-119">Jeśli atrybut jest przypisany dowolną inną wartość, cały `<assemblyIdentity>` element jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="d08dc-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="d08dc-120">Zobacz: <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="d08dc-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="d08dc-121">processorArchitecture — atrybut</span><span class="sxs-lookup"><span data-stu-id="d08dc-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="d08dc-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="d08dc-122">Value</span></span>|<span data-ttu-id="d08dc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d08dc-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="d08dc-124">Tylko architektura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="d08dc-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="d08dc-125">Tylko architektura procesorów Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="d08dc-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="d08dc-126">Neutralna w odniesieniu do procesora i bitów na słowo.</span><span class="sxs-lookup"><span data-stu-id="d08dc-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="d08dc-127">32-bitowy procesor x86 — natywny lub w środowisku Windows on Windows (WOW) na platformie 64-bitowej.</span><span class="sxs-lookup"><span data-stu-id="d08dc-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d08dc-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d08dc-128">Child Elements</span></span>  
 <span data-ttu-id="d08dc-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="d08dc-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d08dc-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d08dc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="d08dc-131">Element</span><span class="sxs-lookup"><span data-stu-id="d08dc-131">Element</span></span>|<span data-ttu-id="d08dc-132">Opis</span><span class="sxs-lookup"><span data-stu-id="d08dc-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="d08dc-133">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="d08dc-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="d08dc-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d08dc-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="d08dc-135">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d08dc-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="d08dc-136">Użyj jednego `<dependentAssembly>` elementu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d08dc-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="d08dc-137">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d08dc-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08dc-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d08dc-138">Remarks</span></span>  
 <span data-ttu-id="d08dc-139">Każdy **\<dependentAssembly>** element musi mieć jeden **\<assemblyIdentity>** element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="d08dc-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="d08dc-140">Jeśli `processorArchitecture` atrybut jest obecny, `<assemblyIdentity>` element ma zastosowanie tylko do zestawu z odpowiednią architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="d08dc-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="d08dc-141">Jeśli `processorArchitecture` atrybut nie istnieje, `<assemblyIdentity>` element może być stosowany do zestawu z dowolną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="d08dc-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="d08dc-142">W poniższym przykładzie przedstawiono plik konfiguracyjny dla dwóch zestawów o tej samej nazwie, który jest przeznaczony dla dwóch różnych architektur procesora, a których wersje nie zostały zachowane w synchronizacji. Gdy aplikacja jest wykonywana na platformie x86, stosuje się pierwszy `<assemblyIdentity>` element, a drugi jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="d08dc-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="d08dc-143">Jeśli aplikacja jest uruchamiana na platformie innej niż x86 lub ia64, obie te wartości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d08dc-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="d08dc-144">Jeśli plik konfiguracji zawiera element bez `<assemblyIdentity>` `processorArchitecture` atrybutu i nie zawiera elementu, który jest zgodny z platformą, element bez `processorArchitecture` atrybutu jest używany.</span><span class="sxs-lookup"><span data-stu-id="d08dc-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d08dc-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="d08dc-145">Example</span></span>  
 <span data-ttu-id="d08dc-146">Poniższy przykład pokazuje, jak podać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="d08dc-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d08dc-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d08dc-147">See also</span></span>

- [<span data-ttu-id="d08dc-148">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d08dc-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d08dc-149">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d08dc-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d08dc-150">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="d08dc-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
