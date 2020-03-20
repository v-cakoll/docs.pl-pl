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
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155417"
---
# <a name="compilers-element"></a>\<kompilatory> Element
Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej [ \<elementów kompilatora>.](compiler-element.md)  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<kompilatory>**

## <a name="syntax"></a>Składnia  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<element kompilatora>](compiler-element.md)|Określa atrybuty konfiguracji kompilatora dla dostawcy języka.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<element> konfiguracji](../configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|[\<element> system.codedom](system-codedom-element.md)|Określa ustawienia konfiguracji kompilatora dla dostawców dostępnych języków.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Kompilatory>](compilers-element.md) element zawiera ustawienia konfiguracji kompilatora dla dostawców języka na komputerze. Każdy [ \<element>kompilatora](compiler-element.md) określa atrybuty konfiguracji kompilatora dla określonego dostawcy języka.  
  
 Program .NET Framework definiuje początkowe ustawienia kompilatora i dostawcy języka w pliku konfiguracji komputera (Machine.config). Deweloperzy i producenci kompilatorów mogą <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> dodawać ustawienia konfiguracji dla nowej implementacji. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Metoda służy do programowego wyliczenia ustawień konfiguracji dostawcy języka i kompilatora na komputerze.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje typowy element konfiguracji kompilatora.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kompilatora i dostawcy języka](index.md)
- [\<element kompilatora>](compiler-element.md)
