---
title: <compiler> Element
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
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088053"
---
# <a name="compiler-element"></a><span data-ttu-id="20c10-102">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="20c10-102">\<compiler> Element</span></span>

<span data-ttu-id="20c10-103">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="20c10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20c10-104">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20c10-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20c10-105">Attributes and Elements</span></span>

<span data-ttu-id="20c10-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20c10-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20c10-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20c10-107">Attributes</span></span>

|<span data-ttu-id="20c10-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20c10-108">Attribute</span></span>|<span data-ttu-id="20c10-109">Opis</span><span class="sxs-lookup"><span data-stu-id="20c10-109">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="20c10-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20c10-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="20c10-111">Określa dodatkowe argumenty specyficzne dla kompilatora dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="20c10-111">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="20c10-112">Wartości `compilerOptions` atrybutu są zwykle wymienione w temacie Opcje kompilatora dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="20c10-112">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="20c10-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="20c10-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="20c10-114">Zawiera rozdzieloną średnikami listę rozszerzeń nazw plików używanych przez pliki źródłowe dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-114">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="20c10-115">Na przykład ". cs".</span><span class="sxs-lookup"><span data-stu-id="20c10-115">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="20c10-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="20c10-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="20c10-117">Zawiera rozdzieloną średnikami listę nazw języków obsługiwanych przez dostawcę języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-117">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="20c10-118">Na przykład "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="20c10-118">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="20c10-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="20c10-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="20c10-120">Określa nazwę typu dostawcy języka, łącznie z nazwą zestawu zawierającego implementację dostawcy.</span><span class="sxs-lookup"><span data-stu-id="20c10-120">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="20c10-121">Nazwa typu musi spełniać wymagania zdefiniowane w ramach [określania w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="20c10-121">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="20c10-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20c10-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="20c10-123">Określa domyślny poziom ostrzeżeń kompilatora; Określa poziom, na którym dostawca języka traktuje ostrzeżenia kompilacji jako błędy.</span><span class="sxs-lookup"><span data-stu-id="20c10-123">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="20c10-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20c10-124">Child Elements</span></span>

|<span data-ttu-id="20c10-125">Element</span><span class="sxs-lookup"><span data-stu-id="20c10-125">Element</span></span>|<span data-ttu-id="20c10-126">Opis</span><span class="sxs-lookup"><span data-stu-id="20c10-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20c10-127">\<providerOption>Postaci</span><span class="sxs-lookup"><span data-stu-id="20c10-127">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="20c10-128">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-128">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20c10-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20c10-129">Parent Elements</span></span>

|<span data-ttu-id="20c10-130">Element</span><span class="sxs-lookup"><span data-stu-id="20c10-130">Element</span></span>|<span data-ttu-id="20c10-131">Opis</span><span class="sxs-lookup"><span data-stu-id="20c10-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20c10-132">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="20c10-132">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="20c10-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20c10-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="20c10-134">\<system.codedom>Postaci</span><span class="sxs-lookup"><span data-stu-id="20c10-134">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="20c10-135">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-135">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="20c10-136">\<compilers>Postaci</span><span class="sxs-lookup"><span data-stu-id="20c10-136">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="20c10-137">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej `<compiler>` elementów.</span><span class="sxs-lookup"><span data-stu-id="20c10-137">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20c10-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20c10-138">Remarks</span></span>

<span data-ttu-id="20c10-139">Każdy `<compiler>` element określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-139">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="20c10-140">Dostawca rozszerza <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> klasę dla określonego języka; `<compiler>` element definiuje ustawienia kompilatora i generatora kodu dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="20c10-140">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="20c10-141">.NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="20c10-141">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="20c10-142">Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="20c10-142">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="20c10-143">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="20c10-143">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="20c10-144">Elementy kompilatora w pliku konfiguracyjnym aplikacji lub sieci Web mogą uzupełniać lub zastępować ustawienia w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="20c10-144">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="20c10-145">Jeśli skonfigurowano więcej niż jedną implementację dostawcy dla tej samej nazwy języka lub tego samego rozszerzenia pliku, Ostatnia zgodna konfiguracja zastępuje wszelkich wcześniej skonfigurowanych dostawców dla tej nazwy języka lub rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="20c10-145">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="20c10-146">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="20c10-146">Configuration File</span></span>

<span data-ttu-id="20c10-147">Ten element może być używany w pliku konfiguracji komputera i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20c10-147">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="20c10-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="20c10-148">Example</span></span>

<span data-ttu-id="20c10-149">Poniższy przykład ilustruje typowy element konfiguracji kompilatora:</span><span class="sxs-lookup"><span data-stu-id="20c10-149">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="20c10-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20c10-150">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="20c10-151">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="20c10-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="20c10-152">\<compilers>Postaci</span><span class="sxs-lookup"><span data-stu-id="20c10-152">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="20c10-153">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="20c10-153">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="20c10-154">[Element kompilatora dla kompilatorów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20c10-154">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
