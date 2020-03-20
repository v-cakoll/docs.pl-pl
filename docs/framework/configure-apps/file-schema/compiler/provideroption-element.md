---
title: <providerOption>, element
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155404"
---
# <a name="provideroption-element"></a><span data-ttu-id="999f7-102">\<ProviderOption> Element</span><span class="sxs-lookup"><span data-stu-id="999f7-102">\<providerOption> Element</span></span>
<span data-ttu-id="999f7-103">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="999f7-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="999f7-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="999f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="999f7-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="999f7-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="999f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kompilatory>**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="999f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="999f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kompilatora**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="999f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="999f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>dostawcyOpcja**</span><span class="sxs-lookup"><span data-stu-id="999f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="999f7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="999f7-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="999f7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="999f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="999f7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="999f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="999f7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="999f7-112">Attributes</span></span>  
  
|<span data-ttu-id="999f7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="999f7-113">Attribute</span></span>|<span data-ttu-id="999f7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="999f7-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="999f7-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="999f7-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="999f7-116">Określa nazwę opcji; na przykład "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="999f7-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="999f7-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="999f7-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="999f7-118">Określa wartość opcji; na przykład "v3.5".</span><span class="sxs-lookup"><span data-stu-id="999f7-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="999f7-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="999f7-119">Child Elements</span></span>  
 <span data-ttu-id="999f7-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="999f7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="999f7-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="999f7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="999f7-122">Element</span><span class="sxs-lookup"><span data-stu-id="999f7-122">Element</span></span>|<span data-ttu-id="999f7-123">Opis</span><span class="sxs-lookup"><span data-stu-id="999f7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="999f7-124">\<element> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="999f7-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="999f7-125">Element główny w każdym pliku konfiguracyjnym używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="999f7-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="999f7-126">\<element> system.codedom</span><span class="sxs-lookup"><span data-stu-id="999f7-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="999f7-127">Określa ustawienia konfiguracji kompilatora dla dostawców dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="999f7-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="999f7-128">\<kompilatory> Element</span><span class="sxs-lookup"><span data-stu-id="999f7-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="999f7-129">Kontener dla elementów konfiguracji kompilatora; zawiera zero `<compiler>` lub więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="999f7-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="999f7-130">\<element kompilatora></span><span class="sxs-lookup"><span data-stu-id="999f7-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="999f7-131">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="999f7-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="999f7-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="999f7-132">Remarks</span></span>  
 <span data-ttu-id="999f7-133">W .NET Framework w wersji 3.5 dostawcy kodu modelu obiektu dokumentu (CodeDOM) `<providerOption>` mogą obsługiwać opcje specyficzne dla dostawcy przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="999f7-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="999f7-134">.NET Framework 3.5 zawiera zaktualizowane zestawy .NET Framework 2.0 i zawiera nowe zestawy w wersji 3.5, które zawierają nowe typy.</span><span class="sxs-lookup"><span data-stu-id="999f7-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="999f7-135">Dostawcy kodu Microsoft C# i Visual Basic są zawarte w zestawach .NET Framework 2.0, ale zostały zaktualizowane do obsługi kompilatorów w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="999f7-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="999f7-136">Domyślnie zaktualizowane dostawców kodu generowania kodu dla kompilatorów w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="999f7-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="999f7-137">Można użyć `<providerOption>` elementu, aby zmienić wersję kompilatora docelowego do 3.5.</span><span class="sxs-lookup"><span data-stu-id="999f7-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="999f7-138">Aby to zrobić, należy określić `name` "CompilerVersion" dla atrybutu i `value` "v3.5" dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="999f7-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="999f7-139">Numer wersji należy poprzedzić wielkimi literami "v".</span><span class="sxs-lookup"><span data-stu-id="999f7-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="999f7-140">Specyfikację wersji można wprowadzić globalnie, dodając `<providerOption>` ten element do pliku .NET Framework 2.0 Machine.config lub root Web.config.</span><span class="sxs-lookup"><span data-stu-id="999f7-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="999f7-141">Jeśli zaktualizujesz domyślną wersję kompilatora do wersji 3.5 w pliku Machine.config, można ją `<providerOption>` zmienić z powrotem na 2.0 dla aplikacji za pomocą elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="999f7-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="999f7-142">Implementatorzy dostawcy kodu CodeDOM mogą przetwarzać opcje `providerOptions` niestandardowe, <xref:System.Collections.Generic.IDictionary%602>zapewniając konstruktor, który przyjmuje parametr typu .</span><span class="sxs-lookup"><span data-stu-id="999f7-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="999f7-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="999f7-143">Example</span></span>  
 <span data-ttu-id="999f7-144">W poniższym przykładzie pokazano, jak określić, że wersja 3.5 dostawcy kodu C# powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="999f7-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="999f7-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="999f7-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="999f7-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="999f7-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="999f7-147">\<kompilatory> Element</span><span class="sxs-lookup"><span data-stu-id="999f7-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="999f7-148">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="999f7-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="999f7-149">[Element kompilatora dla kompilatorów do kompilacji (ASP.NET Schemat ustawień)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="999f7-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
