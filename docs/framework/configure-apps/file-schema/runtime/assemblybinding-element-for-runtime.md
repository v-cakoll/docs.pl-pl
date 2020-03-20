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
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154325"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="b452d-102">\<element> w \<czasie wykonywania></span><span class="sxs-lookup"><span data-stu-id="b452d-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="b452d-103">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="b452d-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
<span data-ttu-id="b452d-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b452d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b452d-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b452d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b452d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>montażowy**</span><span class="sxs-lookup"><span data-stu-id="b452d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b452d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b452d-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b452d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b452d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b452d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b452d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b452d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b452d-110">Attributes</span></span>  
  
|<span data-ttu-id="b452d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b452d-111">Attribute</span></span>|<span data-ttu-id="b452d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b452d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b452d-113">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="b452d-113">**xmlns**</span></span>|<span data-ttu-id="b452d-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b452d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b452d-115">Określa obszar nazw XML wymagany dla powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b452d-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="b452d-116">Użyj ciągu "urn:schemas-microsoft-com:asm.v1" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="b452d-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="b452d-117">**Appliesto**</span><span class="sxs-lookup"><span data-stu-id="b452d-117">**appliesTo**</span></span>|<span data-ttu-id="b452d-118">Określa wersję środowiska uruchomieniowego, do na które ma zastosowanie przekierowanie zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b452d-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="b452d-119">Ten atrybut opcjonalny używa numeru wersji programu .NET Framework, aby wskazać, jakiej wersji dotyczy.</span><span class="sxs-lookup"><span data-stu-id="b452d-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="b452d-120">Jeśli nie **appliesTo** atrybut jest określony, \*\* \<assemblyBinding>\*\* element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b452d-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="b452d-121">Atrybut **appliesTo** został wprowadzony w wersji .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="b452d-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="b452d-122">Oznacza to, \*\* \<\*\* że wszystkie elementy>wiązania zestawu są stosowane podczas korzystania z programu .NET Framework w wersji 1.0, nawet jeśli atrybut **appliesTo** jest określony.</span><span class="sxs-lookup"><span data-stu-id="b452d-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b452d-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b452d-123">Child Elements</span></span>  
  
|<span data-ttu-id="b452d-124">Element</span><span class="sxs-lookup"><span data-stu-id="b452d-124">Element</span></span>|<span data-ttu-id="b452d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b452d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b452d-126">\<></span><span class="sxs-lookup"><span data-stu-id="b452d-126">\<dependentAssembly></span></span>](dependentassembly-element.md)|<span data-ttu-id="b452d-127">Hermetyzuje zasady wiązania i lokalizację zestawu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="b452d-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="b452d-128">Użyj jednego \*\* \<zależnegoAsześci>\*\* znacznik dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b452d-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="b452d-129">\<sondowanie></span><span class="sxs-lookup"><span data-stu-id="b452d-129">\<probing></span></span>](probing-element.md)|<span data-ttu-id="b452d-130">Określa podkatalogi wyszukiwania środowiska uruchomieniowego języka wspólnego podczas ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="b452d-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="b452d-131">\<wydawcaPolicja></span><span class="sxs-lookup"><span data-stu-id="b452d-131">\<publisherPolicy></span></span>](publisherpolicy-element.md)|<span data-ttu-id="b452d-132">Określa, czy środowisko wykonawcze stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b452d-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="b452d-133">\<kwalifikacje></span><span class="sxs-lookup"><span data-stu-id="b452d-133">\<qualifyAssembly></span></span>](qualifyassembly-element.md)|<span data-ttu-id="b452d-134">Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy używana jest nazwa częściowa.</span><span class="sxs-lookup"><span data-stu-id="b452d-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b452d-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b452d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b452d-136">Element</span><span class="sxs-lookup"><span data-stu-id="b452d-136">Element</span></span>|<span data-ttu-id="b452d-137">Opis</span><span class="sxs-lookup"><span data-stu-id="b452d-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b452d-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b452d-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b452d-139">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b452d-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b452d-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="b452d-140">Example</span></span>  
 <span data-ttu-id="b452d-141">W poniższym przykładzie pokazano, jak przekierować jedną wersję zestawu do innej i podać bazę kodu.</span><span class="sxs-lookup"><span data-stu-id="b452d-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="b452d-142">W poniższym przykładzie pokazano, jak użyć **atrybutu appliesTo,** aby przekierować powiązanie zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b452d-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b452d-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b452d-143">See also</span></span>

- [<span data-ttu-id="b452d-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b452d-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b452d-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b452d-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b452d-146">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="b452d-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
