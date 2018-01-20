---
title: "&lt;provideroption —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="9cd2f-102">&lt;provideroption —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="9cd2f-103">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="9cd2f-104">\<Element konfiguracji ></span><span class="sxs-lookup"><span data-stu-id="9cd2f-104">\<configuration Element></span></span>  
<span data-ttu-id="9cd2f-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="9cd2f-105">\<system.codedom Element></span></span>  
<span data-ttu-id="9cd2f-106">\<Element kompilatorów ></span><span class="sxs-lookup"><span data-stu-id="9cd2f-106">\<compilers Element></span></span>  
<span data-ttu-id="9cd2f-107">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-107">\<compiler> Element</span></span>  
<span data-ttu-id="9cd2f-108">\<provideroption — > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cd2f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cd2f-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cd2f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9cd2f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9cd2f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cd2f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9cd2f-112">Attributes</span></span>  
  
|<span data-ttu-id="9cd2f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9cd2f-113">Attribute</span></span>|<span data-ttu-id="9cd2f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9cd2f-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9cd2f-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="9cd2f-116">Określa nazwę opcji; na przykład "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="9cd2f-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="9cd2f-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="9cd2f-118">Określa wartość opcji; na przykład "v3.5".</span><span class="sxs-lookup"><span data-stu-id="9cd2f-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cd2f-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9cd2f-119">Child Elements</span></span>  
 <span data-ttu-id="9cd2f-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cd2f-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9cd2f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9cd2f-122">Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-122">Element</span></span>|<span data-ttu-id="9cd2f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9cd2f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cd2f-124">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9cd2f-125">Element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="9cd2f-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="9cd2f-127">Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="9cd2f-128">\<kompilatory > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="9cd2f-129">Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej `<compiler>` elementów.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="9cd2f-130">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="9cd2f-131">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cd2f-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cd2f-132">Remarks</span></span>  
 <span data-ttu-id="9cd2f-133">W programie .NET Framework w wersji 3.5, dostawców kodu kodu Document Object Model (CodeDOM) może obsługiwać opcji specyficznych dla dostawcy przy użyciu `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="9cd2f-134">.NET Framework 3.5 zawiera zaktualizowane zestawy .NET Framework 2.0 i udostępnia nowe zestawy w wersji 3.5, które zawiera nowe typy.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="9cd2f-135">Dostawcy kodu języka Microsoft C# i Visual Basic są zawarte w zestawach .NET Framework 2.0, ale zostały zaktualizowane do obsługi kompilatory w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="9cd2f-136">Domyślnie dostawców zaktualizowanego kodu wygenerować kod dla kompilatory w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="9cd2f-137">Można użyć `<providerOption>` element, aby zmienić docelową wersję kompilatora 3.5.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="9cd2f-138">Aby to zrobić, należy określić "CompilerVersion" `name` oraz "v3.5" dla atrybutu `value` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="9cd2f-139">Należy poprzedzić numer wersji, z małymi literami "v".</span><span class="sxs-lookup"><span data-stu-id="9cd2f-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="9cd2f-140">Możesz wprowadzić Specyfikacja wersji globalnej, dodając `<providerOption>` elementu .NET Framework 2.0 w pliku Machine.config lub głównym pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="9cd2f-141">Po zaktualizowaniu domyślnej wersji kompilatora 3.5 w pliku Machine.config, można zmienić go do 2.0 na poszczególnych aplikacji, co przy użyciu `<providerOption>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="9cd2f-142">Implementacje dostawcy kodu codeDOM może przetwarzać niestandardowych opcji zapewniając konstruktora przyjmującego `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd2f-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cd2f-143">Example</span></span>  
 <span data-ttu-id="9cd2f-144">W poniższym przykładzie pokazano, jak określić tego dostawcę w wersji 3.5 C# kodu będzie używana.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cd2f-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cd2f-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="9cd2f-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9cd2f-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9cd2f-147">\<kompilatory > — Element</span><span class="sxs-lookup"><span data-stu-id="9cd2f-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="9cd2f-148">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="9cd2f-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="9cd2f-149">Kompilator elementu dla kompilatory kompilacji (schemat ustawień programu ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="9cd2f-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
