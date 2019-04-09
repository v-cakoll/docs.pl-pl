---
title: x:TypeArguments — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 1d1b10b4da1263843bdce5447f0716569c7700e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085808"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments — dyrektywa
Przebiegi, ograniczając wpisz argumenty ogólne do konstruktora typu ogólnego.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`object`|Deklaracja elementu obiektu typu XAML, która jest wspierana przez CLR typu ogólnego. Jeśli `object` odwołuje się do typu XAML, który nie pochodzi z domyślna przestrzeń nazw XAML, `object` wymaga prefiksu, aby wskazać, przestrzeń nazw XAML gdzie `object` istnieje.|  
|`typeString`|Ciąg, który deklaruje co najmniej jeden XAML wpisz nazwy użytkowników jako ciągi, które dostarcza argumentów typu dla typu ogólnego środowiska CLR. Informacje o dodatkowych składni, zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 W większości przypadków i typy XAML, które są używane jako element informacji w `typeString` są poprzedzone ciągiem. Typowe typy CLR ograniczenia ogólne (na przykład <xref:System.Int32> i <xref:System.String>) pochodzą z biblioteki klas bazowych CLR. Te biblioteki nie są zmapowane do typowych domyślnych właściwa dla struktury XAML w przestrzeni nazw i dlatego wymagają mapowania prefiks do użycia XAML.  
  
 Można określić więcej niż jedną nazwę typu XAML przy użyciu ogranicznika przecinkami.  
  
 Użycie typów ogólnych, ograniczenia ogólne, same argumenty typu zagnieżdżonego ograniczenia mogą być zawarte w nawiasy ().  
  
 Należy pamiętać, że ta definicja `x:TypeArguments` jest przeznaczony dla usług programu .NET Framework XAML i przy użyciu środowiska CLR. Definicja poziomu języka znajdują się w [ \[MS-XAML\] sekcji 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Przykłady użycia  
 W poniższych przykładach założono, że następujące definicje przestrzeń nazw XAML są deklarowane:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Lista\<ciąg >  
 `<scg:List x:TypeArguments="sys:String" ...>` Tworzy nową <xref:System.Collections.Generic.List%601> z <xref:System.String> argument typu.  
  
### <a name="dictionarystringstring"></a>Słownik\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Tworzy nową <xref:System.Collections.Generic.Dictionary%602> przy użyciu dwóch <xref:System.String> argumentów typu.  
  
### <a name="queuekeyvaluepairstringstring"></a>Kolejka < KeyValuePair\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Tworzy nową <xref:System.Collections.Generic.Queue%601> zawierający ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami typu Ograniczenie wewnętrzne <xref:System.String> i <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Wartości XAML 2006 i środowisku WPF XAML ogólnego użycia  
 Użycie XAML 2006 i XAML, która jest używana dla aplikacji WPF, obowiązują następujące ograniczenia dla `x:TypeArguments` i użycia typu ogólnego z XAML w ogólne:  
  
-   Tylko element główny plik XAML może obsługiwać ogólnego użycia XAML, który odwołuje się do typu ogólnego.  
  
-   Element główny musi być mapowane z co najmniej jeden typ argumentu typu ogólnego. Może to być na przykład <xref:System.Windows.Navigation.PageFunction%601>. Funkcje strony są podstawowy scenariusz obsługi ogólnego użycia XAML w WPF.  
  
-   Element główny element XAML obiektu dla ogólnej musi również zadeklarować klasy częściowej przy użyciu `x:Class`. Ta zasada obowiązuje, nawet w przypadku definiowania WPF Akcja kompilacji.  
  
-   `x:TypeArguments` Nie można odwołać zagnieżdżonych ograniczenia ogólne.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 lub XAML 2006 bez WPF 3.0 lub WPF 3.5 zależności  
 W przypadku usług .NET Framework XAML XAML 2006 lub XAML 2009 ograniczenia związane z WPF ogólnego użycia XAML są złagodzone. Można utworzyć wystąpienia elementu obiekt rodzajowy, w dowolnym miejscu w znaczniku XAML, który zapasowy typ systemu i obiekt modelu mogą obsługiwać.  
  
 Jeśli używasz XAML 2009 zamiast mapowania środowiska CLR typy uzyskać typy XAML dla wspólnych elementów podstawowych języka podstawowe, możesz użyć [typy wbudowane dla wspólnych elementów podstawowych języka XAML](built-in-types-for-common-xaml-language-primitives.md) jako elementy informacji w programie `typeString`. Na przykład, można zadeklarować następujące (przestrzeń nazw XAML języka XAML dla XAML 2009 jest mapowania prefiksów, które nie są wyświetlane, ale x):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 Na platformie WPF i przeznaczonych dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć XAML 2009 — funkcje wraz z `x:TypeArguments` , ale tylko w przypadku luźne XAML (XAML, która nie jest kompilowana do znaczników). XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009. Jeśli potrzebujesz do znaczników kompilacji XAML, musi działać w ramach ograniczenia, o których wspomniano w sekcji "XAML 2006 i WPF ogólny XAML użycia".  
  
## <a name="see-also"></a>Zobacz także

- [x:Class — dyrektywa](x-class-directive.md)
- [x:Type — Rozszerzenie znaczników](x-type-markup-extension.md)
- [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](built-in-types-for-common-xaml-language-primitives.md)
- [Typy ogólne w XAML](generics-in-xaml.md)
