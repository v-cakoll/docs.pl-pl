---
title: "&lt;provideroption —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1f91b9fcd7ef9c9c616a7a41ced6be1cda365509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltprovideroptiongt-element"></a>&lt;provideroption —&gt; — Element
Określa atrybuty wersji kompilatora dla dostawcy języka.  
  
 \<Element konfiguracji >  
\<System.CodeDom — Element >  
\<Element kompilatorów >  
\<Kompilator > — Element  
\<provideroption — > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Atrybut wymagany.<br /><br /> Określa nazwę opcji; na przykład "CompilerVersion".|  
|`value`|Atrybut wymagany.<br /><br /> Określa wartość opcji; na przykład "v3.5".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.|  
|[\<System.CodeDom — > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.|  
|[\<kompilatory > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej `<compiler>` elementów.|  
|[\<Kompilator > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Określa atrybuty kompilatora konfiguracji dostawcy języka.|  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework w wersji 3.5, dostawców kodu kodu Document Object Model (CodeDOM) może obsługiwać opcji specyficznych dla dostawcy przy użyciu `<providerOption>` elementu.  
  
 .NET Framework 3.5 zawiera zaktualizowane zestawy .NET Framework 2.0 i udostępnia nowe zestawy w wersji 3.5, które zawiera nowe typy. Dostawcy kodu języka Microsoft C# i Visual Basic są zawarte w zestawach .NET Framework 2.0, ale zostały zaktualizowane do obsługi kompilatory w wersji 3.5. Domyślnie dostawców zaktualizowanego kodu wygenerować kod dla kompilatory w wersji 2.0. Można użyć `<providerOption>` element, aby zmienić docelową wersję kompilatora 3.5. Aby to zrobić, należy określić "CompilerVersion" `name` oraz "v3.5" dla atrybutu `value` atrybutu. Należy poprzedzić numer wersji, z małymi literami "v".  
  
 Możesz wprowadzić Specyfikacja wersji globalnej, dodając `<providerOption>` elementu .NET Framework 2.0 w pliku Machine.config lub głównym pliku Web.config. Po zaktualizowaniu domyślnej wersji kompilatora 3.5 w pliku Machine.config, można zmienić go do 2.0 na poszczególnych aplikacji, co przy użyciu `<providerOption>` elementu w pliku konfiguracyjnym aplikacji.  
  
 Implementacje dostawcy kodu codeDOM może przetwarzać niestandardowych opcji zapewniając konstruktora przyjmującego `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić tego dostawcę w wersji 3.5 C# kodu będzie używana.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<kompilatory > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Określanie w pełni kwalifikowanych nazw typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [Kompilator elementu dla kompilatory kompilacji (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
