---
title: <system.codedom> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674802"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="43a85-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="43a85-102">\<system.codedom> Element</span></span>
<span data-ttu-id="43a85-103">Określa ustawienia konfiguracyjne kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="43a85-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="43a85-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="43a85-104">\<configuration> Element</span></span>  
<span data-ttu-id="43a85-105">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="43a85-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a85-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="43a85-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43a85-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43a85-107">Attributes and Elements</span></span>  
 <span data-ttu-id="43a85-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43a85-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43a85-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43a85-109">Attributes</span></span>  
 <span data-ttu-id="43a85-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="43a85-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43a85-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43a85-111">Child Elements</span></span>  
  
|<span data-ttu-id="43a85-112">Element</span><span class="sxs-lookup"><span data-stu-id="43a85-112">Element</span></span>|<span data-ttu-id="43a85-113">Opis</span><span class="sxs-lookup"><span data-stu-id="43a85-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a85-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="43a85-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="43a85-115">Kontener dla elementów konfiguracji, kompilator; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="43a85-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43a85-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43a85-116">Parent Elements</span></span>  
  
|<span data-ttu-id="43a85-117">Element</span><span class="sxs-lookup"><span data-stu-id="43a85-117">Element</span></span>|<span data-ttu-id="43a85-118">Opis</span><span class="sxs-lookup"><span data-stu-id="43a85-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a85-119">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="43a85-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="43a85-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43a85-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43a85-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43a85-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="43a85-122">.NET framework w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="43a85-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="43a85-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dla dostawców język zainstalowany na komputerze oprócz domyślnych dostawców, które są instalowane z .NET Framework, takich jak <xref:Microsoft.CSharp.CSharpCodeProvider> i <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="43a85-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="43a85-124">[ \<Kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="43a85-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="43a85-125">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dla dostawcy określonego języka.</span><span class="sxs-lookup"><span data-stu-id="43a85-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="43a85-126">Deweloperom i dostawcom kompilatora można dodać ustawień konfiguracji do pliku konfiguracji komputera (Machine.config) nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="43a85-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="43a85-127">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodę, aby programowo wyliczyć dostawców języka domyślnego i dostawcy języka identyfikowane za pomocą ustawienia kompilatora konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43a85-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43a85-128">W .NET Framework w wersji 1.0 i 1.1, domyślny język dostawców dostarczanych przez .NET Framework są identyfikowane w [ \<kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="43a85-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="43a85-129">W .NET Framework w wersji 2.0 dostawcy języka domyślnego nie są oznaczone w [ \<kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mogą być wyliczane przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="43a85-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="43a85-130">.NET framework w wersji 1.0 i 1.1</span><span class="sxs-lookup"><span data-stu-id="43a85-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="43a85-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43a85-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="43a85-132">[ \<Kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="43a85-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="43a85-133">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dla dostawcy określonego języka.</span><span class="sxs-lookup"><span data-stu-id="43a85-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="43a85-134">.NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="43a85-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="43a85-135">Deweloperom i dostawcom kompilatora umożliwia dodanie ustawienia konfiguracji dla nowego <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji.</span><span class="sxs-lookup"><span data-stu-id="43a85-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="43a85-136">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, można programowo wyliczyć języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43a85-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="43a85-137">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43a85-137">Configuration File</span></span>  
 <span data-ttu-id="43a85-138">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43a85-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43a85-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="43a85-139">Example</span></span>  
 <span data-ttu-id="43a85-140">W poniższym przykładzie pokazano konfigurację kompilatora typowy.</span><span class="sxs-lookup"><span data-stu-id="43a85-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43a85-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43a85-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="43a85-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43a85-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="43a85-143">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="43a85-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="43a85-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="43a85-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
