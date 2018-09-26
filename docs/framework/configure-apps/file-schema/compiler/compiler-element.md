---
title: '&lt;Kompilator&gt; — Element'
ms.date: 08/14/2018
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
ms.openlocfilehash: a26fc0bda341e85ca54f3dee4addd14e4164209c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071024"
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="8f15e-102">&lt;Kompilator&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-102">&lt;compiler&gt; Element</span></span>

<span data-ttu-id="8f15e-103">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="8f15e-104">\<Konfiguracja elementu > \<system.CodeDom — Element > \<kompilatory Element > \<kompilatora > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="8f15e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f15e-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f15e-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f15e-106">Attributes and Elements</span></span>

<span data-ttu-id="8f15e-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f15e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f15e-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f15e-108">Attributes</span></span>

|<span data-ttu-id="8f15e-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8f15e-109">Attribute</span></span>|<span data-ttu-id="8f15e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8f15e-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="8f15e-111">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f15e-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8f15e-112">Określa dodatkowe argumenty kompilatora specyficzne dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f15e-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="8f15e-113">Wartości `compilerOptions` atrybut zwykle są wymienione w temacie opcje kompilatora dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8f15e-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="8f15e-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8f15e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="8f15e-115">Zawiera rozdzieloną średnikami listę rozszerzeń nazw plików używane przez pliki źródłowe dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="8f15e-116">Na przykład ".cs".</span><span class="sxs-lookup"><span data-stu-id="8f15e-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="8f15e-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8f15e-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="8f15e-118">Zawiera rozdzieloną średnikami listę nazw języków obsługiwanych przez dostawcę języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="8f15e-119">Na przykład "c#; cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="8f15e-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="8f15e-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8f15e-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="8f15e-121">Określa nazwę typu dostawcy języka, łącznie z nazwą zestawu zawierającego implementację dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8f15e-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="8f15e-122">Nazwa typu musi spełniać wymagania zdefiniowane w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8f15e-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="8f15e-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f15e-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8f15e-124">Określa domyślny poziom ostrzeżeń kompilatora; Określa poziom, który dostawca języka traktuje jako błędy ostrzeżenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f15e-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8f15e-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f15e-125">Child Elements</span></span>

|<span data-ttu-id="8f15e-126">Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-126">Element</span></span>|<span data-ttu-id="8f15e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8f15e-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f15e-128">\<provideroption — > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="8f15e-129">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f15e-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f15e-130">Parent Elements</span></span>

|<span data-ttu-id="8f15e-131">Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-131">Element</span></span>|<span data-ttu-id="8f15e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="8f15e-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f15e-133">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="8f15e-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f15e-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="8f15e-135">\<System.CodeDom > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="8f15e-136">Określa ustawienia konfiguracyjne kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="8f15e-137">\<kompilatory > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="8f15e-138">Kontener dla elementów konfiguracji, kompilator; zawiera zero lub więcej `<compiler>` elementów.</span><span class="sxs-lookup"><span data-stu-id="8f15e-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f15e-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f15e-139">Remarks</span></span>

<span data-ttu-id="8f15e-140">Każdy `<compiler>` element określa atrybuty kompilatora konfiguracji dla dostawcy określonego języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="8f15e-141">Dostawca rozszerza <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> klasy dla określonego języka; `<compiler>` element definiuje kompilatora i ustawienia generator kodu dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="8f15e-142">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8f15e-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="8f15e-143">Deweloperom i dostawcom kompilatora umożliwia dodanie ustawienia konfiguracji dla nowego <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="8f15e-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="8f15e-144">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, można programowo wyliczyć języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8f15e-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="8f15e-145">Elementy kompilatora w pliku konfiguracji sieci Web lub aplikacji można uzupełnić lub przesłonić ustawienia w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="8f15e-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="8f15e-146">Jeśli więcej niż jedna implementacja dostawcy jest skonfigurowany dla tej samej nazwy języka lub to samo rozszerzenie pliku, ostatniej pasującej konfiguracji zastępuje wszystkie poprzednie dostawców skonfigurowanych dla tego rozszerzenia nazwy lub plik języka.</span><span class="sxs-lookup"><span data-stu-id="8f15e-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="8f15e-147">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8f15e-147">Configuration File</span></span>

<span data-ttu-id="8f15e-148">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f15e-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="8f15e-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f15e-149">Example</span></span>

<span data-ttu-id="8f15e-150">W poniższym przykładzie pokazano element kompilatora typowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="8f15e-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f15e-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f15e-151">See Also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="8f15e-152">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8f15e-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8f15e-153">\<kompilatory > Element</span><span class="sxs-lookup"><span data-stu-id="8f15e-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- <span data-ttu-id="8f15e-154">[Określanie w pełni kwalifikowanej nazwy typu]-(.. /.. /.. /.. /.. / docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)</span><span class="sxs-lookup"><span data-stu-id="8f15e-154">[Specifying Fully Qualified Type Names]-(../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)</span></span>
- <span data-ttu-id="8f15e-155">[Kompilator Element kompilatorów dla kompilacji (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8f15e-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
