---
title: '&lt;System.CodeDom —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5939fa31a2f87348922d4586e3e7b7b52066fb09
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744229"
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="36258-102">&lt;System.CodeDom —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="36258-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="36258-103">Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="36258-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="36258-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="36258-104">\<configuration> Element</span></span>  
<span data-ttu-id="36258-105">\<System.CodeDom — > — Element</span><span class="sxs-lookup"><span data-stu-id="36258-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36258-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="36258-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36258-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="36258-107">Attributes and Elements</span></span>  
 <span data-ttu-id="36258-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="36258-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36258-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="36258-109">Attributes</span></span>  
 <span data-ttu-id="36258-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="36258-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36258-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="36258-111">Child Elements</span></span>  
  
|<span data-ttu-id="36258-112">Element</span><span class="sxs-lookup"><span data-stu-id="36258-112">Element</span></span>|<span data-ttu-id="36258-113">Opis</span><span class="sxs-lookup"><span data-stu-id="36258-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36258-114">\<kompilatory ></span><span class="sxs-lookup"><span data-stu-id="36258-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="36258-115">Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="36258-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36258-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="36258-116">Parent Elements</span></span>  
  
|<span data-ttu-id="36258-117">Element</span><span class="sxs-lookup"><span data-stu-id="36258-117">Element</span></span>|<span data-ttu-id="36258-118">Opis</span><span class="sxs-lookup"><span data-stu-id="36258-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36258-119">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="36258-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="36258-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36258-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36258-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36258-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="36258-122">.NET framework w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="36258-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="36258-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dla dostawców język zainstalowany na komputerze, oprócz domyślnych dostawców, które są instalowane z programu .NET Framework, takich jak <xref:Microsoft.CSharp.CSharpCodeProvider> i <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="36258-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="36258-124">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="36258-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="36258-125">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="36258-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="36258-126">Deweloperom i dostawcom kompilatora można dodać ustawienia konfiguracji do pliku konfiguracji komputera (Machine.config) nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="36258-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="36258-127">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody programowo wyliczyć dostawców język domyślny i dostawcy języka identyfikowana na podstawie ustawienia kompilatora konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="36258-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36258-128">W wersji systemu .NET Framework 1.0 i 1.1, domyślny język dostawców dostarczanych przez program .NET Framework są identyfikowane w [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="36258-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="36258-129">W programie .NET Framework w wersji 2.0, dostawcy języków domyślne nie zostaną rozpoznane w [ \<kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mogą być wyliczane przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="36258-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="36258-130">.NET framework w wersji 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="36258-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="36258-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze.</span><span class="sxs-lookup"><span data-stu-id="36258-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="36258-132">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="36258-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="36258-133">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="36258-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="36258-134">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="36258-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="36258-135">Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="36258-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="36258-136">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="36258-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="36258-137">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="36258-137">Configuration File</span></span>  
 <span data-ttu-id="36258-138">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36258-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36258-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="36258-139">Example</span></span>  
 <span data-ttu-id="36258-140">Poniżej przedstawiono przykładową konfigurację typowe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="36258-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36258-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36258-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="36258-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="36258-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="36258-143">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="36258-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="36258-144">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="36258-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
