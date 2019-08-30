---
title: <compilers>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 5232c5bd2d4fad8104d156bfa86141ceb7f0dd93
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167689"
---
# <a name="compilers-element"></a><span data-ttu-id="cac12-102">\<kompilatory > element</span><span class="sxs-lookup"><span data-stu-id="cac12-102">\<compilers> Element</span></span>
<span data-ttu-id="cac12-103">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [ \<elementów > kompilatora](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="cac12-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
[<span data-ttu-id="cac12-104"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="cac12-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cac12-105">&nbsp;&nbsp;[ **\<> System. CodeDom**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac12-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="cac12-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kompilatory >**</span><span class="sxs-lookup"><span data-stu-id="cac12-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac12-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cac12-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cac12-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cac12-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cac12-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cac12-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cac12-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cac12-110">Attributes</span></span>  
 <span data-ttu-id="cac12-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="cac12-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cac12-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cac12-112">Child Elements</span></span>  
  
|<span data-ttu-id="cac12-113">Element</span><span class="sxs-lookup"><span data-stu-id="cac12-113">Element</span></span>|<span data-ttu-id="cac12-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cac12-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cac12-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="cac12-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="cac12-116">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="cac12-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cac12-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cac12-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cac12-118">Element</span><span class="sxs-lookup"><span data-stu-id="cac12-118">Element</span></span>|<span data-ttu-id="cac12-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cac12-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cac12-120">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cac12-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="cac12-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cac12-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="cac12-122">\<Element System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="cac12-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="cac12-123">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="cac12-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cac12-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cac12-124">Remarks</span></span>  
 <span data-ttu-id="cac12-125">Kompilator > element zawiera ustawienia konfiguracji kompilatora dla dostawców języka na komputerze. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac12-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="cac12-126">Każdy element kompilatora > określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka. [ \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="cac12-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="cac12-127">.NET Framework definiuje początkowe ustawienia kompilatora i dostawcy języka w pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="cac12-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="cac12-128">Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="cac12-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="cac12-129">Użyj metody <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> , aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cac12-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cac12-130">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cac12-130">Configuration File</span></span>  
 <span data-ttu-id="cac12-131">Ten element może być używany w pliku konfiguracji komputera i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cac12-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac12-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="cac12-132">Example</span></span>  
 <span data-ttu-id="cac12-133">Poniższy przykład ilustruje typowy element konfiguracji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="cac12-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cac12-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cac12-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="cac12-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cac12-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cac12-136">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="cac12-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cac12-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="cac12-137">\<compiler> Element</span></span>](compiler-element.md)
