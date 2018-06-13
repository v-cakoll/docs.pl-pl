---
title: '&lt;Kompilator&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b033e26d64f23398a4da6842bb4688cc94627d68
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754496"
---
# <a name="ltcompilergt-element"></a>&lt;Kompilator&gt; — Element
Określa atrybuty kompilatora konfiguracji dostawcy języka.  
  
 \<Element konfiguracji >  
\<system.codedom Element>  
\<Element kompilatorów >  
\<Kompilator > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`compilerOptions`|Atrybut opcjonalny.<br /><br /> Określa dodatkowe argumenty kompilatora specyficzne dla kompilacji. Wartości `compilerOptions` atrybutu zwykle są wyświetlane w temacie opcje kompilatora dla kompilatora. W dokumentacji programu Visual Studio 2005 opcji dla kompilatora można znaleźć, wyszukując "Opcje kompilatora" w indeksie.|  
|`extension`|Atrybut wymagany.<br /><br /> Zawiera listę rozszerzeń nazw plików używane przez pliki źródłowe dla dostawcy języka oddzielonych średnikami. Na przykład ".cs".|  
|`language`|Atrybut wymagany.<br /><br /> Zawiera listę nazw języków obsługiwanych przez dostawcę języka oddzielonych średnikami. Na przykład "c# cs; csharp".|  
|`type`|Atrybut wymagany.<br /><br /> Określa nazwę typu dostawcy języka, w tym nazwę zestawu zawierającego implementację dostawcy. Nazwa typu musi spełniać wymagania zdefiniowane w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`warningLevel`|Atrybut opcjonalny.<br /><br /> Określa domyślny poziom ostrzeżeń kompilatora; Określa poziom, jaką dostawcy języka traktuje kompilacja ostrzeżenia jako błędy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<provideroption — > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Określa atrybuty wersji kompilatora dla dostawcy języka.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|[\<System.CodeDom — > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.|  
|[\<kompilatory > — Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej `<compiler>` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `<compiler>` element określa atrybuty kompilatora konfiguracji dostawcy języka. Dostawca rozszerza <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> klasy dla określonego języka; `<compiler>` element definiuje kompilatora i ustawienia generator kodu dla dostawcy języka.  
  
 .NET Framework definiuje ustawienia kompilatora początkowe w pliku konfiguracji komputera (Machine.config). Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider> implementacji. Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.  
  
 Elementy kompilatora w pliku konfiguracji sieci Web lub aplikacji można uzupełnić lub przesłonić ustawienia w pliku konfiguracji komputera. Jeśli więcej niż jedna implementacja dostawcy jest skonfigurowany dla tej samej nazwy języka lub samo rozszerzenie pliku, ostatni pasującej konfiguracji zastępuje wszelkie poprzednie dostawców skonfigurowanych dla tego rozszerzenia pliku lub nazwę języka.  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
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
 [Kompilator elementu dla kompilatory kompilacji (schemat ustawień programu ASP.NET)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))
