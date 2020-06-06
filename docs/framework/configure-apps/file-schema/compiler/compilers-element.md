---
title: <compilers> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155417"
---
# <a name="compilers-element"></a><span data-ttu-id="320be-102">\<compilers> Element</span><span class="sxs-lookup"><span data-stu-id="320be-102">\<compilers> Element</span></span>
<span data-ttu-id="320be-103">Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [\<compiler>](compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="320be-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="320be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="320be-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="320be-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="320be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="320be-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="320be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="320be-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="320be-107">Attributes</span></span>  
 <span data-ttu-id="320be-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="320be-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="320be-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="320be-109">Child Elements</span></span>  
  
|<span data-ttu-id="320be-110">Element</span><span class="sxs-lookup"><span data-stu-id="320be-110">Element</span></span>|<span data-ttu-id="320be-111">Opis</span><span class="sxs-lookup"><span data-stu-id="320be-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="320be-112">\<compiler>Postaci</span><span class="sxs-lookup"><span data-stu-id="320be-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="320be-113">Określa atrybuty konfiguracji kompilatora dla dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="320be-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="320be-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="320be-114">Parent Elements</span></span>  
  
|<span data-ttu-id="320be-115">Element</span><span class="sxs-lookup"><span data-stu-id="320be-115">Element</span></span>|<span data-ttu-id="320be-116">Opis</span><span class="sxs-lookup"><span data-stu-id="320be-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="320be-117">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="320be-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="320be-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="320be-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="320be-119">\<system.codedom>Postaci</span><span class="sxs-lookup"><span data-stu-id="320be-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="320be-120">Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="320be-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="320be-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="320be-121">Remarks</span></span>  
 <span data-ttu-id="320be-122">[\<compilers>](compilers-element.md)Element zawiera ustawienia konfiguracji kompilatora dla dostawców języka na komputerze.</span><span class="sxs-lookup"><span data-stu-id="320be-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="320be-123">Każdy [\<compiler>](compiler-element.md) element określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="320be-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="320be-124">.NET Framework definiuje początkowe ustawienia kompilatora i dostawcy języka w pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="320be-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="320be-125">Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="320be-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="320be-126">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="320be-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="320be-127">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="320be-127">Configuration File</span></span>  
 <span data-ttu-id="320be-128">Ten element może być używany w pliku konfiguracji komputera i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="320be-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="320be-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="320be-129">Example</span></span>  
 <span data-ttu-id="320be-130">Poniższy przykład ilustruje typowy element konfiguracji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="320be-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="320be-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="320be-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="320be-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="320be-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="320be-133">Schemat ustawień kompilatora i dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="320be-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="320be-134">\<compiler>Postaci</span><span class="sxs-lookup"><span data-stu-id="320be-134">\<compiler> Element</span></span>](compiler-element.md)
