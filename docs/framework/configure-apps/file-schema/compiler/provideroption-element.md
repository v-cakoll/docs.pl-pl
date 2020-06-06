---
title: <providerOption> Element
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155404"
---
# <a name="provideroption-element"></a><span data-ttu-id="58072-102">\<providerOption> Element</span><span class="sxs-lookup"><span data-stu-id="58072-102">\<providerOption> Element</span></span>
<span data-ttu-id="58072-103">Określa atrybuty wersji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="58072-103">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="58072-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58072-104">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58072-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="58072-105">Attributes and Elements</span></span>  
 <span data-ttu-id="58072-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="58072-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58072-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="58072-107">Attributes</span></span>  
  
|<span data-ttu-id="58072-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="58072-108">Attribute</span></span>|<span data-ttu-id="58072-109">Opis</span><span class="sxs-lookup"><span data-stu-id="58072-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="58072-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="58072-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="58072-111">Określa nazwę opcji; na przykład "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="58072-111">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="58072-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="58072-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="58072-113">Określa wartość dla opcji; na przykład "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="58072-113">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58072-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="58072-114">Child Elements</span></span>  
 <span data-ttu-id="58072-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="58072-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58072-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="58072-116">Parent Elements</span></span>  
  
|<span data-ttu-id="58072-117">Element</span><span class="sxs-lookup"><span data-stu-id="58072-117">Element</span></span>|<span data-ttu-id="58072-118">Opis</span><span class="sxs-lookup"><span data-stu-id="58072-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58072-119">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="58072-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="58072-120">Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58072-120">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="58072-121">\<system.codedom>Postaci</span><span class="sxs-lookup"><span data-stu-id="58072-121">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="58072-122">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="58072-122">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="58072-123">\<compilers>Postaci</span><span class="sxs-lookup"><span data-stu-id="58072-123">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="58072-124">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej `<compiler>` elementów.</span><span class="sxs-lookup"><span data-stu-id="58072-124">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="58072-125">\<compiler>Postaci</span><span class="sxs-lookup"><span data-stu-id="58072-125">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="58072-126">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="58072-126">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58072-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58072-127">Remarks</span></span>  
 <span data-ttu-id="58072-128">W .NET Framework w wersji 3,5 Code Document Object Model (CodeDOM) dostawcy kodu mogą obsługiwać opcje specyficzne dla dostawcy za pomocą `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="58072-128">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="58072-129">.NET Framework 3,5 obejmuje zaktualizowane zestawy .NET Framework 2,0 i udostępnia 3,5 nowe zestawy, które zawierają nowe typy.</span><span class="sxs-lookup"><span data-stu-id="58072-129">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="58072-130">Dostawcy kodów programu Microsoft C# i Visual Basic są zainstalowani w zestawach .NET Framework 2,0, ale zostały zaktualizowane do obsługi kompilatorów w wersji 3,5.</span><span class="sxs-lookup"><span data-stu-id="58072-130">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="58072-131">Domyślnie zaktualizowani dostawcy kodu generują kod dla kompilatorów w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="58072-131">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="58072-132">Możesz użyć elementu, `<providerOption>` Aby zmienić docelową wersję kompilatora na 3,5.</span><span class="sxs-lookup"><span data-stu-id="58072-132">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="58072-133">W tym celu należy określić wartość "CompilerVersion" dla `name` atrybutu i "v 3.5" dla `value` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="58072-133">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="58072-134">Należy poprzedzić numer wersji małą literą "v".</span><span class="sxs-lookup"><span data-stu-id="58072-134">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="58072-135">Można utworzyć globalną specyfikację wersji przez dodanie `<providerOption>` elementu do .NET Framework 2,0 Machine. config lub głównego pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="58072-135">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="58072-136">Jeśli domyślna wersja kompilatora zostanie zaktualizowana do 3,5 w pliku Machine. config, można ją zmienić z powrotem na 2,0 dla poszczególnych aplikacji, korzystając z `<providerOption>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58072-136">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="58072-137">Implementacje dostawcy kodu CodeDOM mogą przetwarzać niestandardowe opcje, dostarczając Konstruktor, który przyjmuje `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="58072-137">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58072-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="58072-138">Example</span></span>  
 <span data-ttu-id="58072-139">W poniższym przykładzie pokazano, jak określić, że należy użyć wersji 3,5 dostawcy kodu C#.</span><span class="sxs-lookup"><span data-stu-id="58072-139">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58072-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58072-140">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="58072-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="58072-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="58072-142">\<compilers>Postaci</span><span class="sxs-lookup"><span data-stu-id="58072-142">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="58072-143">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="58072-143">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="58072-144">[Element kompilatora dla kompilatorów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58072-144">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
