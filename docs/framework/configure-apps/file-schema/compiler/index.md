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
ms.openlocfilehash: ab8225d664b658789f7eb9e7830d5ec527ded94a
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084370"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="e0643-102">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="e0643-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="e0643-103">Kompilator i ustawienia dostawcy języka Określ elementy kompilatora konfiguracji dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="e0643-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="e0643-104">Każdy element konfiguracji kompilator określa kod nazwę typu dostawcy, parametry kompilatora obsługiwane nazwy języka i obsługiwane rozszerzenia plików.</span><span class="sxs-lookup"><span data-stu-id="e0643-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="e0643-105">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e0643-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e0643-106">Deweloperom i dostawcom kompilatora umożliwia dodanie ustawienia konfiguracji dla nowego <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="e0643-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e0643-107">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, można programowo wyliczyć języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e0643-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="e0643-108">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="e0643-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="e0643-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="e0643-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="e0643-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="e0643-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="e0643-111">\<compiler></span><span class="sxs-lookup"><span data-stu-id="e0643-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="e0643-112">Element</span><span class="sxs-lookup"><span data-stu-id="e0643-112">Element</span></span>|<span data-ttu-id="e0643-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e0643-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0643-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="e0643-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="e0643-115">Określa ustawienia konfiguracyjne kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="e0643-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="e0643-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="e0643-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="e0643-117">Kontener dla elementów konfiguracji, kompilator; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="e0643-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="e0643-118">\<compiler></span><span class="sxs-lookup"><span data-stu-id="e0643-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="e0643-119">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="e0643-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0643-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0643-120">Example</span></span>  
 <span data-ttu-id="e0643-121">W poniższym przykładzie pokazano element kompilatora typowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e0643-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0643-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0643-122">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e0643-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e0643-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e0643-124">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="e0643-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
