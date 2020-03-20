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
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155404"
---
# <a name="provideroption-element"></a>\<ProviderOption> Element
Określa atrybuty wersji kompilatora dla dostawcy języka.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kompilatory>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kompilatora**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>dostawcyOpcja**

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
|[\<element> konfiguracji](../configuration-element.md)|Element główny w każdym pliku konfiguracyjnym używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
|[\<element> system.codedom](system-codedom-element.md)|Określa ustawienia konfiguracji kompilatora dla dostawców dostępnych języków.|  
|[\<kompilatory> Element](compilers-element.md)|Kontener dla elementów konfiguracji kompilatora; zawiera zero `<compiler>` lub więcej elementów.|  
|[\<element kompilatora>](compiler-element.md)|Określa atrybuty konfiguracji kompilatora dla dostawcy języka.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 3.5 dostawcy kodu modelu obiektu dokumentu (CodeDOM) `<providerOption>` mogą obsługiwać opcje specyficzne dla dostawcy przy użyciu tego elementu.  
  
 .NET Framework 3.5 zawiera zaktualizowane zestawy .NET Framework 2.0 i zawiera nowe zestawy w wersji 3.5, które zawierają nowe typy. Dostawcy kodu Microsoft C# i Visual Basic są zawarte w zestawach .NET Framework 2.0, ale zostały zaktualizowane do obsługi kompilatorów w wersji 3.5. Domyślnie zaktualizowane dostawców kodu generowania kodu dla kompilatorów w wersji 2.0. Można użyć `<providerOption>` elementu, aby zmienić wersję kompilatora docelowego do 3.5. Aby to zrobić, należy określić `name` "CompilerVersion" dla atrybutu i `value` "v3.5" dla atrybutu. Numer wersji należy poprzedzić wielkimi literami "v".  
  
 Specyfikację wersji można wprowadzić globalnie, dodając `<providerOption>` ten element do pliku .NET Framework 2.0 Machine.config lub root Web.config. Jeśli zaktualizujesz domyślną wersję kompilatora do wersji 3.5 w pliku Machine.config, można ją `<providerOption>` zmienić z powrotem na 2.0 dla aplikacji za pomocą elementu w pliku konfiguracyjnym aplikacji.  
  
 Implementatorzy dostawcy kodu CodeDOM mogą przetwarzać opcje `providerOptions` niestandardowe, <xref:System.Collections.Generic.IDictionary%602>zapewniając konstruktor, który przyjmuje parametr typu .  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że wersja 3.5 dostawcy kodu C# powinny być używane.  
  
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

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schemat pliku konfiguracji](../index.md)
- [\<kompilatory> Element](compilers-element.md)
- [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element kompilatora dla kompilatorów do kompilacji (ASP.NET Schemat ustawień)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
