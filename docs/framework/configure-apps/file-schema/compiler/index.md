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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088684"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="f88b2-102">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="f88b2-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="f88b2-103">Ustawienia kompilatora i dostawcy języka określają elementy konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="f88b2-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="f88b2-104">Każdy element konfiguracji kompilatora określa nazwę typu dostawcy kodu, parametry kompilatora, obsługiwane nazwy języków i obsługiwane rozszerzenia plików.</span><span class="sxs-lookup"><span data-stu-id="f88b2-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="f88b2-105">.NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f88b2-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="f88b2-106">Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="f88b2-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="f88b2-107">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f88b2-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="f88b2-108">Element</span><span class="sxs-lookup"><span data-stu-id="f88b2-108">Element</span></span>|<span data-ttu-id="f88b2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f88b2-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="f88b2-110">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="f88b2-110">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="f88b2-111">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [\<compiler>](compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="f88b2-111">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="f88b2-112">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="f88b2-112">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f88b2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f88b2-113">Example</span></span>  
 <span data-ttu-id="f88b2-114">Poniższy przykład ilustruje typowy element konfiguracji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f88b2-114">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f88b2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f88b2-115">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f88b2-116">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f88b2-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f88b2-117">\<compiler>Postaci</span><span class="sxs-lookup"><span data-stu-id="f88b2-117">\<compiler> Element</span></span>](compiler-element.md)
