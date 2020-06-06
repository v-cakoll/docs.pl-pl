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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155391"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [\<compiler>](compiler-element.md) elementów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="net-framework-version-20"></a>.NET Framework wersja 2,0  
 [\<system.codedom>](system-codedom-element.md)Element zawiera ustawienia konfiguracji kompilatora dla dostawców języka zainstalowanych na komputerze oprócz domyślnych dostawców zainstalowanych z .NET Framework, takich jak <xref:Microsoft.CSharp.CSharpCodeProvider> i <xref:Microsoft.VisualBasic.VBCodeProvider> . [\<compilers>](compilers-element.md)Element zawiera zero lub więcej [\<compiler>](compiler-element.md) elementów. Każdy [\<compiler>](compiler-element.md) element określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.  
  
 Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji do pliku konfiguracji komputera (Machine. config), aby uzyskać nową <xref:System.CodeDom.Compiler.CodeDomProvider> implementację. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, aby programowo wyliczyć zarówno domyślnych dostawców języka, jak i dostawców języka identyfikowanych przez ustawienia konfiguracji kompilatora na komputerze.  
  
> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1 dostawcy języka domyślnego dostarczone przez .NET Framework są identyfikowane w [\<compilers>](compilers-element.md) elemencie. W .NET Framework w wersji 2,0 dostawcy języka domyślnego nie są identyfikowane w [\<compilers>](compilers-element.md) elemencie, ale można je wyliczyć przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework wersje 1,0 i 1,1  
 [\<system.codedom>](system-codedom-element.md)Element zawiera ustawienia konfiguracji kompilatora dla dostawców języka na komputerze. [\<compilers>](compilers-element.md)Element zawiera zero lub więcej [\<compiler>](compiler-element.md) elementów. Każdy [\<compiler>](compiler-element.md) element określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.  
  
 .NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracji komputera (Machine. config). Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody, aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje typową konfigurację kompilatora.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kompilatora i dostawcy języka](index.md)
- [\<compiler>Postaci](compiler-element.md)
