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
# <a name="systemcodedom-element"></a>\<element> system.codedom
Określa ustawienia konfiguracji kompilatora dla dostawców dostępnych języków.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
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
|[\<kompilatory>](compilers-element.md)|Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md)|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracyjne](../configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="net-framework-version-20"></a>.NET Framework w wersji 2.0  
 Element [ \<>system.codedom](system-codedom-element.md) zawiera ustawienia konfiguracji kompilatora dla dostawców języka zainstalowanych na komputerze oprócz domyślnych dostawców <xref:Microsoft.CSharp.CSharpCodeProvider> zainstalowanych z programem .NET Framework, takich jak <xref:Microsoft.VisualBasic.VBCodeProvider>i . [ \<Kompilatory>](compilers-element.md) element zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md) Każdy [ \<element>kompilatora](compiler-element.md) określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.  
  
 Deweloperzy i producenci kompilatorów mogą dodawać ustawienia konfiguracji do pliku <xref:System.CodeDom.Compiler.CodeDomProvider> konfiguracji komputera (Machine.config) dla nowej implementacji. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Metoda służy do programowego wyliczenia zarówno domyślnych dostawców języka, jak i dostawców języka zidentyfikowanych przez ustawienia konfiguracji kompilatora na komputerze.  
  
> [!NOTE]
> W .NET Framework w wersjach 1.0 i 1.1 domyślnych dostawców języka dostarczonych przez .NET Framework są identyfikowane w [ \<kompilatorach>](compilers-element.md) element. W .NET Framework w wersji 2.0 domyślnych dostawców języka nie są identyfikowane w [ \<kompilatorach>](compilers-element.md) element, ale mogą być wyliczone przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework wersje 1.0 i 1.1  
 Element [ \<>system.codedom](system-codedom-element.md) zawiera ustawienia konfiguracji kompilatora dla dostawców języków na komputerze. [ \<Kompilatory>](compilers-element.md) element zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md) Każdy [ \<element>kompilatora](compiler-element.md) określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.  
  
 Program .NET Framework definiuje początkowe ustawienia kompilatora w pliku konfiguracyjnym komputera (Machine.config). Deweloperzy i producenci kompilatorów mogą <xref:System.CodeDom.Compiler.CodeDomProvider> dodawać ustawienia konfiguracji dla nowej implementacji. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Metoda służy do programowego wyliczenia ustawień konfiguracji dostawcy języka i kompilatora na komputerze.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera i pliku konfiguracji aplikacji.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kompilatora i dostawcy języka](index.md)
- [\<element kompilatora>](compiler-element.md)
