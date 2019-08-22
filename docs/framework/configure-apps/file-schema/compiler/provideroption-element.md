---
title: <providerOption>, element
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 37f4d8c5eeacd82f8fc37179c478d026ca25f459
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664303"
---
# <a name="provideroption-element"></a>\<providerOption, element >
Określa atrybuty wersji kompilatora dla dostawcy języka.  
  
 \<> elementu konfiguracji  
\<system.codedom Element>  
\<Element kompilatorów >  
\<compiler> Element  
\<providerOption, element >  
  
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
|`value`|Atrybut wymagany.<br /><br /> Określa wartość dla opcji; na przykład "v 3.5".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> elementu konfiguracji](../configuration-element.md)|Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
|[\<Element System. CodeDom >](system-codedom-element.md)|Określa ustawienia konfiguracji kompilatora dla dostępnych dostawców języka.|  
|[\<kompilatory > element](compilers-element.md)|Kontener dla elementów konfiguracji kompilatora; zawiera zero lub więcej `<compiler>` elementów.|  
|[\<compiler> Element](compiler-element.md)|Określa atrybuty konfiguracji kompilatora dla dostawcy języka.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 3,5 Code Document Object Model (CodeDOM) dostawcy kodu mogą obsługiwać opcje specyficzne dla dostawcy za pomocą `<providerOption>` elementu.  
  
 .NET Framework 3,5 obejmuje zaktualizowane zestawy .NET Framework 2,0 i udostępnia 3,5 nowe zestawy, które zawierają nowe typy. Dostawcy kodu C# firmy Microsoft i Visual Basic są zawarti w zestawach .NET Framework 2,0, ale zostały zaktualizowane do obsługi kompilatorów w wersji 3,5. Domyślnie zaktualizowani dostawcy kodu generują kod dla kompilatorów w wersji 2,0. Możesz użyć elementu, `<providerOption>` aby zmienić docelową wersję kompilatora na 3,5. W tym celu należy określić wartość "CompilerVersion" dla `name` atrybutu i "v 3.5" `value` dla atrybutu. Należy poprzedzić numer wersji małą literą "v".  
  
 Można utworzyć globalną specyfikację wersji przez dodanie `<providerOption>` elementu do .NET Framework 2,0 Machine. config lub głównego pliku Web. config. Jeśli domyślna wersja kompilatora zostanie zaktualizowana do 3,5 w pliku Machine. config, można ją zmienić z powrotem na 2,0 dla poszczególnych aplikacji, korzystając z `<providerOption>` elementu w pliku konfiguracyjnym aplikacji.  
  
 Implementacje dostawcy kodu CodeDOM mogą przetwarzać niestandardowe opcje, dostarczając Konstruktor, który `providerOptions` przyjmuje parametr typu <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że należy użyć wersji C# 3,5 dostawcy kodu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schemat pliku konfiguracji](../index.md)
- [\<kompilatory > element](compilers-element.md)
- [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element kompilatora dla kompilatorów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
