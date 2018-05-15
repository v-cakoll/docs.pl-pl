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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: beb38c00c7055d8edfff6f574ec454902e3a9b14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="7c256-102">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="7c256-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="7c256-103">Ustawienia dostawcy języka i kompilatora dla dostawców dostępny język należy określić elementy kompilatora konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c256-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="7c256-104">Każdy element konfiguracji kompilatora określa kod nazwę typu dostawcy, parametry kompilatora obsługiwane nazwy języka i obsługiwane rozszerzeń plików.</span><span class="sxs-lookup"><span data-stu-id="7c256-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="7c256-105">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7c256-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="7c256-106">Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="7c256-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="7c256-107">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7c256-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="7c256-108">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="7c256-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="7c256-109">\<System.CodeDom — ></span><span class="sxs-lookup"><span data-stu-id="7c256-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="7c256-110">\<kompilatory ></span><span class="sxs-lookup"><span data-stu-id="7c256-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="7c256-111">\<Kompilator ></span><span class="sxs-lookup"><span data-stu-id="7c256-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="7c256-112">Element</span><span class="sxs-lookup"><span data-stu-id="7c256-112">Element</span></span>|<span data-ttu-id="7c256-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7c256-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c256-114">\<System.CodeDom — ></span><span class="sxs-lookup"><span data-stu-id="7c256-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="7c256-115">Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="7c256-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="7c256-116">\<kompilatory ></span><span class="sxs-lookup"><span data-stu-id="7c256-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="7c256-117">Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="7c256-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="7c256-118">\<Kompilator ></span><span class="sxs-lookup"><span data-stu-id="7c256-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="7c256-119">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="7c256-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7c256-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c256-120">Example</span></span>  
 <span data-ttu-id="7c256-121">Poniższy przykład przedstawia element kompilatora typowych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c256-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c256-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c256-122">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="7c256-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c256-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7c256-124">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="7c256-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
