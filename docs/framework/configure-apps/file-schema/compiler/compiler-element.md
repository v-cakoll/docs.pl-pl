---
title: '&lt;Kompilator&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b033e26d64f23398a4da6842bb4688cc94627d68
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754496"
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="070de-102">&lt;Kompilator&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="070de-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="070de-103">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="070de-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="070de-104">\<Element konfiguracji ></span><span class="sxs-lookup"><span data-stu-id="070de-104">\<configuration Element></span></span>  
<span data-ttu-id="070de-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="070de-105">\<system.codedom Element></span></span>  
<span data-ttu-id="070de-106">\<Element kompilatorów ></span><span class="sxs-lookup"><span data-stu-id="070de-106">\<compilers Element></span></span>  
<span data-ttu-id="070de-107">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070de-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="070de-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070de-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="070de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="070de-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="070de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070de-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="070de-111">Attributes</span></span>  
  
|<span data-ttu-id="070de-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="070de-112">Attribute</span></span>|<span data-ttu-id="070de-113">Opis</span><span class="sxs-lookup"><span data-stu-id="070de-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="070de-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="070de-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="070de-115">Określa dodatkowe argumenty kompilatora specyficzne dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="070de-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="070de-116">Wartości `compilerOptions` atrybutu zwykle są wyświetlane w temacie opcje kompilatora dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="070de-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="070de-117">W dokumentacji programu Visual Studio 2005 opcji dla kompilatora można znaleźć, wyszukując "Opcje kompilatora" w indeksie.</span><span class="sxs-lookup"><span data-stu-id="070de-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="070de-118">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="070de-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="070de-119">Zawiera listę rozszerzeń nazw plików używane przez pliki źródłowe dla dostawcy języka oddzielonych średnikami.</span><span class="sxs-lookup"><span data-stu-id="070de-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="070de-120">Na przykład ".cs".</span><span class="sxs-lookup"><span data-stu-id="070de-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="070de-121">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="070de-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="070de-122">Zawiera listę nazw języków obsługiwanych przez dostawcę języka oddzielonych średnikami.</span><span class="sxs-lookup"><span data-stu-id="070de-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="070de-123">Na przykład "c# cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="070de-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="070de-124">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="070de-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="070de-125">Określa nazwę typu dostawcy języka, w tym nazwę zestawu zawierającego implementację dostawcy.</span><span class="sxs-lookup"><span data-stu-id="070de-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="070de-126">Nazwa typu musi spełniać wymagania zdefiniowane w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="070de-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="070de-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="070de-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="070de-128">Określa domyślny poziom ostrzeżeń kompilatora; Określa poziom, jaką dostawcy języka traktuje kompilacja ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="070de-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070de-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="070de-129">Child Elements</span></span>  
  
|<span data-ttu-id="070de-130">Element</span><span class="sxs-lookup"><span data-stu-id="070de-130">Element</span></span>|<span data-ttu-id="070de-131">Opis</span><span class="sxs-lookup"><span data-stu-id="070de-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070de-132">\<provideroption — > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="070de-133">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="070de-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="070de-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="070de-134">Parent Elements</span></span>  
  
|<span data-ttu-id="070de-135">Element</span><span class="sxs-lookup"><span data-stu-id="070de-135">Element</span></span>|<span data-ttu-id="070de-136">Opis</span><span class="sxs-lookup"><span data-stu-id="070de-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070de-137">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="070de-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="070de-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="070de-139">\<System.CodeDom — > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="070de-140">Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="070de-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="070de-141">\<kompilatory > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="070de-142">Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej `<compiler>` elementów.</span><span class="sxs-lookup"><span data-stu-id="070de-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="070de-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="070de-143">Remarks</span></span>  
 <span data-ttu-id="070de-144">Każdy `<compiler>` element określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="070de-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="070de-145">Dostawca rozszerza <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> klasy dla określonego języka; `<compiler>` element definiuje kompilatora i ustawienia generator kodu dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="070de-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="070de-146">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="070de-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="070de-147">Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="070de-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="070de-148">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="070de-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="070de-149">Elementy kompilatora w pliku konfiguracji sieci Web lub aplikacji można uzupełnić lub przesłonić ustawienia w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="070de-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="070de-150">Jeśli więcej niż jedna implementacja dostawcy jest skonfigurowany dla tej samej nazwy języka lub samo rozszerzenie pliku, ostatni pasującej konfiguracji zastępuje wszelkie poprzednie dostawców skonfigurowanych dla tego rozszerzenia pliku lub nazwę języka.</span><span class="sxs-lookup"><span data-stu-id="070de-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="070de-151">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="070de-151">Configuration File</span></span>  
 <span data-ttu-id="070de-152">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="070de-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="070de-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="070de-153">Example</span></span>  
 <span data-ttu-id="070de-154">Poniższy przykład przedstawia element kompilatora typowych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="070de-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="070de-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="070de-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="070de-156">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="070de-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="070de-157">\<kompilatory > — Element</span><span class="sxs-lookup"><span data-stu-id="070de-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="070de-158">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="070de-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 <span data-ttu-id="070de-159">[Kompilator elementu dla kompilatory kompilacji (schemat ustawień programu ASP.NET)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="070de-159">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
