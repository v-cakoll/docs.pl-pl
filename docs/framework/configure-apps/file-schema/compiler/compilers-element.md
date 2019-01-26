---
title: '&lt;kompilatory&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 7d9deda5e0ffeb95483eebbbb0a63831db08ac0b
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083369"
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="adcef-102">&lt;kompilatory&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="adcef-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="adcef-103">Kontener dla elementów konfiguracji, kompilator; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="adcef-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="adcef-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="adcef-104">\<configuration></span></span>  
<span data-ttu-id="adcef-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="adcef-105">\<system.codedom></span></span>  
<span data-ttu-id="adcef-106">\<compilers> Element</span><span class="sxs-lookup"><span data-stu-id="adcef-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcef-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="adcef-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adcef-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="adcef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adcef-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="adcef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adcef-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="adcef-110">Attributes</span></span>  
 <span data-ttu-id="adcef-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="adcef-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="adcef-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="adcef-112">Child Elements</span></span>  
  
|<span data-ttu-id="adcef-113">Element</span><span class="sxs-lookup"><span data-stu-id="adcef-113">Element</span></span>|<span data-ttu-id="adcef-114">Opis</span><span class="sxs-lookup"><span data-stu-id="adcef-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcef-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="adcef-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="adcef-116">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="adcef-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adcef-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="adcef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="adcef-118">Element</span><span class="sxs-lookup"><span data-stu-id="adcef-118">Element</span></span>|<span data-ttu-id="adcef-119">Opis</span><span class="sxs-lookup"><span data-stu-id="adcef-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcef-120">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="adcef-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="adcef-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adcef-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="adcef-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="adcef-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="adcef-123">Określa ustawienia konfiguracyjne kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="adcef-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adcef-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adcef-124">Remarks</span></span>  
 <span data-ttu-id="adcef-125">[ \<Kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze.</span><span class="sxs-lookup"><span data-stu-id="adcef-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="adcef-126">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dla dostawcy określonego języka.</span><span class="sxs-lookup"><span data-stu-id="adcef-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="adcef-127">.NET Framework definiuje kompilatora początkowej i ustawienia dostawcy języka w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="adcef-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="adcef-128">Deweloperom i dostawcom kompilatora umożliwia dodanie ustawienia konfiguracji dla nowego <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="adcef-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="adcef-129">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, można programowo wyliczyć języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="adcef-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="adcef-130">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="adcef-130">Configuration File</span></span>  
 <span data-ttu-id="adcef-131">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adcef-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adcef-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="adcef-132">Example</span></span>  
 <span data-ttu-id="adcef-133">W poniższym przykładzie pokazano element kompilatora typowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="adcef-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adcef-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adcef-134">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="adcef-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="adcef-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="adcef-136">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="adcef-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="adcef-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="adcef-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
