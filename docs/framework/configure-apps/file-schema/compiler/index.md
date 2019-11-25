---
title: Schemat ustawień kompilatora i dostawcy języka
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 5b1f9684ad26d4a03769af287fc8b0c0c7c4cc1a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088684"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="d05cb-102">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="d05cb-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="d05cb-103">Ustawienia kompilatora i dostawcy języka określają elementy konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="d05cb-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="d05cb-104">Każdy element konfiguracji kompilatora określa nazwę typu dostawcy kodu, parametry kompilatora, obsługiwane nazwy języków i obsługiwane rozszerzenia plików.</span><span class="sxs-lookup"><span data-stu-id="d05cb-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="d05cb-105">.NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d05cb-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="d05cb-106">Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej implementacji <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="d05cb-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="d05cb-107">Użyj metody <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>, aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d05cb-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
<span data-ttu-id="d05cb-108">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d05cb-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d05cb-109">&nbsp;&nbsp;[ **\<system. codedom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="d05cb-109">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="d05cb-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilatory**](compilers-element.md) ></span><span class="sxs-lookup"><span data-stu-id="d05cb-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="d05cb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[ **kompilator >** ](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="d05cb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>
  
|<span data-ttu-id="d05cb-112">Element</span><span class="sxs-lookup"><span data-stu-id="d05cb-112">Element</span></span>|<span data-ttu-id="d05cb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d05cb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d05cb-114">\<system. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="d05cb-114">\<system.codedom></span></span>](system-codedom-element.md)|<span data-ttu-id="d05cb-115">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="d05cb-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="d05cb-116">kompilatory \<</span><span class="sxs-lookup"><span data-stu-id="d05cb-116">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="d05cb-117">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej elementów [> kompilator\<](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d05cb-117">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="d05cb-118">> kompilator \<</span><span class="sxs-lookup"><span data-stu-id="d05cb-118">\<compiler></span></span>](compiler-element.md)|<span data-ttu-id="d05cb-119">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="d05cb-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d05cb-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d05cb-120">Example</span></span>  
 <span data-ttu-id="d05cb-121">Poniższy przykład ilustruje typowy element konfiguracji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d05cb-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""  
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d05cb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d05cb-122">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="d05cb-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d05cb-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d05cb-124">Element > kompilatora \<</span><span class="sxs-lookup"><span data-stu-id="d05cb-124">\<compiler> Element</span></span>](compiler-element.md)
