---
title: "&lt;kompilatory&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: deb9f99253c4cf523c8fe5052b1f30823e5e9944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilersgt-element"></a>&lt;kompilatory&gt; — Element
Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.  
  
 \<Konfiguracja >  
\<System.CodeDom — >  
\<kompilatory > — Element  
  
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
|[\<Kompilator > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Określa atrybuty kompilatora konfiguracji dostawcy języka.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|[\<System.CodeDom — > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze. Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.  
  
 .NET Framework definiuje ustawienia dostawcy języka i kompilatora początkowej w pliku konfiguracji komputera (Machine.config). Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementacji. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia element kompilatora typowych konfiguracji.  
  
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
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schemat ustawień kompilatora i dostawcy języka](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<Kompilator > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
