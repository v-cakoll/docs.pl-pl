---
title: <system.codedom>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155391"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="6b866-102">\<element> system.codedom</span><span class="sxs-lookup"><span data-stu-id="6b866-102">\<system.codedom> Element</span></span>
<span data-ttu-id="6b866-103">Określa ustawienia konfiguracji kompilatora dla dostawców dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="6b866-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="6b866-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="6b866-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6b866-105">&nbsp;&nbsp;**\<system.codedom>**</span><span class="sxs-lookup"><span data-stu-id="6b866-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b866-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b866-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b866-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b866-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6b866-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b866-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b866-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b866-109">Attributes</span></span>  
 <span data-ttu-id="6b866-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="6b866-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b866-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b866-111">Child Elements</span></span>  
  
|<span data-ttu-id="6b866-112">Element</span><span class="sxs-lookup"><span data-stu-id="6b866-112">Element</span></span>|<span data-ttu-id="6b866-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6b866-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b866-114">\<kompilatory></span><span class="sxs-lookup"><span data-stu-id="6b866-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="6b866-115">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b866-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b866-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b866-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6b866-117">Element</span><span class="sxs-lookup"><span data-stu-id="6b866-117">Element</span></span>|<span data-ttu-id="6b866-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6b866-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b866-119">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="6b866-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="6b866-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b866-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b866-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b866-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="6b866-122">.NET Framework w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="6b866-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="6b866-123">Element [ \<>system.codedom](system-codedom-element.md) zawiera ustawienia konfiguracji kompilatora dla dostawców języka zainstalowanych na komputerze oprócz domyślnych dostawców <xref:Microsoft.CSharp.CSharpCodeProvider> zainstalowanych z programem .NET Framework, takich jak <xref:Microsoft.VisualBasic.VBCodeProvider>i .</span><span class="sxs-lookup"><span data-stu-id="6b866-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="6b866-124">[ \<Kompilatory>](compilers-element.md) element zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b866-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="6b866-125">Każdy [ \<element>kompilatora](compiler-element.md) określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="6b866-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6b866-126">Deweloperzy i producenci kompilatorów mogą dodawać ustawienia konfiguracji do pliku <xref:System.CodeDom.Compiler.CodeDomProvider> konfiguracji komputera (Machine.config) dla nowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="6b866-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6b866-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Metoda służy do programowego wyliczenia zarówno domyślnych dostawców języka, jak i dostawców języka zidentyfikowanych przez ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b866-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b866-128">W .NET Framework w wersjach 1.0 i 1.1 domyślnych dostawców języka dostarczonych przez .NET Framework są identyfikowane w [ \<kompilatorach>](compilers-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="6b866-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="6b866-129">W .NET Framework w wersji 2.0 domyślnych dostawców języka nie są identyfikowane w [ \<kompilatorach>](compilers-element.md) element, ale mogą być wyliczone przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6b866-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="6b866-130">.NET Framework wersje 1.0 i 1.1</span><span class="sxs-lookup"><span data-stu-id="6b866-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="6b866-131">Element [ \<>system.codedom](system-codedom-element.md) zawiera ustawienia konfiguracji kompilatora dla dostawców języków na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b866-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="6b866-132">[ \<Kompilatory>](compilers-element.md) element zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b866-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="6b866-133">Każdy [ \<element>kompilatora](compiler-element.md) określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="6b866-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6b866-134">Program .NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6b866-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6b866-135">Deweloperzy i producenci kompilatorów mogą <xref:System.CodeDom.Compiler.CodeDomProvider> dodawać ustawienia konfiguracji dla nowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="6b866-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6b866-136"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Metoda służy do programowego wyliczenia ustawień konfiguracji dostawcy języka i kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b866-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6b866-137">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b866-137">Configuration File</span></span>  
 <span data-ttu-id="6b866-138">Ten element może być używany w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b866-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b866-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b866-139">Example</span></span>  
 <span data-ttu-id="6b866-140">Poniższy przykład ilustruje typową konfigurację kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6b866-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b866-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b866-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6b866-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b866-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6b866-143">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="6b866-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b866-144">\<element kompilatora></span><span class="sxs-lookup"><span data-stu-id="6b866-144">\<compiler> Element</span></span>](compiler-element.md)
