---
title: "&lt;System.CodeDom —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8b223ab6ab742c5b7d3b3d2f5640e99835afe268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemcodedomgt-element"></a>&lt;System.CodeDom —&gt; — Element
Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.  
  
 \<Konfiguracja > — Element  
\<System.CodeDom — > — Element  
  
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
|[\<kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="net-framework-version-20"></a>.NET framework w wersji 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dla dostawców język zainstalowany na komputerze, oprócz domyślnych dostawców, które są instalowane z programu .NET Framework, takich jak <xref:Microsoft.CSharp.CSharpCodeProvider> i <xref:Microsoft.VisualBasic.VBCodeProvider>. [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów. Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.  
  
 Deweloperom i dostawcom kompilatora można dodać ustawienia konfiguracji do pliku konfiguracji komputera (Machine.config) nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody programowo wyliczyć dostawców język domyślny i dostawcy języka identyfikowana na podstawie ustawienia kompilatora konfiguracji na komputerze.  
  
> [!NOTE]
>  W wersji systemu .NET Framework 1.0 i 1.1, domyślny język dostawców dostarczanych przez program .NET Framework są identyfikowane w [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu. W programie .NET Framework w wersji 2.0, dostawcy języków domyślne nie zostaną rozpoznane w [ \<kompilatory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mogą być wyliczane przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> — metoda.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework w wersji 1.0, 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze. [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów. Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.  
  
 .NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config). Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładową konfigurację typowe kompilatora.  
  
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
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schemat ustawień dostawcy języka i kompilatora](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<Kompilator > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
