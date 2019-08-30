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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168917"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.  
  
[ **\<> konfiguracji**](../configuration-element.md)  
&nbsp;&nbsp; **\<> System. CodeDom**  
  
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
|[\<compilers>](compilers-element.md)|Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [ \<elementów > kompilatora](compiler-element.md) .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> konfiguracji](../configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="net-framework-version-20"></a>.NET Framework wersja 2,0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> [ ElementSystem.CodeDom>zawieraustawieniakonfiguracjikompilatoradladostawcówjęzykazainstalowanychnakomputerzeopróczdomyślnychdostawcówinstalowanychz\<](system-codedom-element.md) .NET Framework, takich jak i <xref:Microsoft.VisualBasic.VBCodeProvider>. Kompilator > element zawiera zero lub więcej [ \<elementów > kompilatora](compiler-element.md) . [ \<](compilers-element.md) Każdy element kompilatora > określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka. [ \<](compiler-element.md)  
  
 Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji do pliku konfiguracji komputera (Machine. config), aby uzyskać nową <xref:System.CodeDom.Compiler.CodeDomProvider> implementację. Użyj metody <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> , aby programowo wyliczyć zarówno domyślnych dostawców języka, jak i dostawców języka identyfikowanych przez ustawienia konfiguracji kompilatora na komputerze.  
  
> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1 dostawcy języka domyślnego dostarczone przez .NET Framework są identyfikowane w [ \<elemencie > kompilatory](compilers-element.md) . W .NET Framework w wersji 2,0 dostawcy języka domyślnego nie są identyfikowane w [ \<kompilatorach >](compilers-element.md) elementu, ale można je <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> wyliczyć przy użyciu metody.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework wersje 1,0 i 1,1  
 Element [System. CodeDom > zawiera ustawienia konfiguracji kompilatora dla dostawców języka na komputerze. \<](system-codedom-element.md) Kompilator > element zawiera zero lub więcej [ \<elementów > kompilatora](compiler-element.md) . [ \<](compilers-element.md) Każdy element kompilatora > określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka. [ \<](compiler-element.md)  
  
 .NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracji komputera (Machine. config). Deweloperzy i dostawcy kompilatora mogą dodać ustawienia konfiguracji dla nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji. Użyj metody <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> , aby programowo wyliczyć dostawcę języka i ustawienia konfiguracji kompilatora na komputerze.  
  
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
- [\<compiler> Element](compiler-element.md)
