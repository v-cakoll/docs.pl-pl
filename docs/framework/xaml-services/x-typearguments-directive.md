---
title: "x:TypeArguments — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: "18"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a63a8080c71ad026664e2e14fc1762fcdd4bdb36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xtypearguments-directive"></a>x:TypeArguments — dyrektywa
Przekazuje ograniczający wpisz argumenty ogólne do konstruktora typu ogólnego.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`object`|Deklaracja elementu obiektu typu XAML, który nie jest obsługiwana przez CLR typu ogólnego. Jeśli `object` odwołuje się do typu XAML, który nie pochodzi z domyślnej przestrzeni nazw XAML, `object` wymaga prefiksu przestrzeni nazw XAML wskazująca, gdzie `object` istnieje.|  
|`typeString`|Ciąg, który deklaruje co najmniej jeden XAML wpisz nazwy jako ciąg, który dostarcza argumentów typu dla typu ogólnego środowiska CLR. Zobacz uwagi dla uwagi dodatkowe składni.|  
  
## <a name="remarks"></a>Uwagi  
 W większości przypadków typów XAML, które są używane jako element informacji w `typeString` są poprzedzane w postaci ciągu. Typowe typy CLR ograniczenia ogólne (na przykład <xref:System.Int32> i <xref:System.String>) pochodzą z biblioteki podstawowej klasy CLR. Te biblioteki nie są mapowane na typowy domyślny określonej struktury przestrzeń nazw XAML i w związku z tym muszą być mapowane prefiks dla użycie języka XAML.  
  
 Za pomocą ogranicznik przecinkami, można określić więcej niż jedną nazwę typu XAML.  
  
 Ograniczenia ogólne, same użycie typów ogólnych argumentów typu zagnieżdżonego ograniczenia mogą wchodzić w skład nawiasów ().  
  
 Należy pamiętać, że ta definicja `x:TypeArguments` jest przeznaczony dla usług .NET Framework XAML i przy użyciu zapasowy CLR. Poziom języka definicji znajduje się w [ \[MS XAML\] sekcji 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Przykłady użycia  
 Te przykłady założono, że następujące definicje przestrzeni nazw XAML są deklarowane jako:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Lista\<ciąg >  
 `<scg:List x:TypeArguments="sys:String" ...>`Tworzy nowy <xref:System.Collections.Generic.List%601> z <xref:System.String> argument typu.  
  
### <a name="dictionarystringstring"></a>Słownik\<ciąg, ciąg >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`Tworzy nowy <xref:System.Collections.Generic.Dictionary%602> z dwoma <xref:System.String> argumentów typu.  
  
### <a name="queuekeyvaluepairstringstring"></a>Kolejki < KeyValuePair\<ciąg, ciąg >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`Tworzy nowy <xref:System.Collections.Generic.Queue%601> mający ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami typu Ograniczenie wewnętrzne <xref:System.String> i <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 i WPF XAML ogólnego zastosowania  
 Dla XAML 2006 użycia i XAML, który jest używany w aplikacji WPF, istnieją następujące ograniczenia `x:TypeArguments` i użycia typu ogólnego z XAML w ogólne:  
  
-   Tylko element główny pliku XAML może obsługiwać ogólnego użycia XAML, który odwołuje się do typu ogólnego.  
  
-   Element główny musi być zamapowany przy użyciu co najmniej jeden typ argumentu typu ogólnego. Na przykład <xref:System.Windows.Navigation.PageFunction%601>. Funkcje strony są podstawowego scenariusza obsługi ogólnego użycia XAML w WPF.  
  
-   Element główny element XAML obiektu dla ogólnych musi również deklarować częściowej klasy przy użyciu `x:Class`. Dotyczy to nawet wtedy, gdy akcja kompilacji Definiowanie WPF.  
  
-   `x:TypeArguments`Nie można odwołać zagnieżdżonych ograniczenia ogólne.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 lub 2006 XAML bez WPF 3.0 lub WPF 3.5 zależności  
 .NET Framework XAML Services for XAML 2006 lub XAML 2009 rozluźnić są ograniczenia związane z WPF na ogólne użycie języka XAML. Można utworzyć wystąpienia elementu obiekt generyczny w każdej pozycji w XAML kod znaczników, który może obsługiwać zapasowy typ systemu i obiekt modelu.  
  
 Jeśli używasz XAML 2009 zamiast mapowania CLR typy uzyskać dla wspólnych elementów podstawowych języka XAML typy podstawowe, możesz użyć [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako elementów informacji w `typeString`. Na przykład można zadeklarować następujące (przestrzeń nazw XAML języka XAML dla XAML 2009 jest mapowania prefiksów, które nie są wyświetlane, ale x):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 Na platformie WPF i przeznaczonych dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć XAML 2009 — funkcje razem z `x:TypeArguments` , ale tylko w przypadku utracić XAML (XAML, który nie jest kompilowany do znaczników). Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje. Jeśli potrzebne do znaczników kompilowania pliku XAML, muszą być ustawione na ograniczenia wymienione w sekcji "XAML 2006 and WPF ogólny XAML użycia".  
  
## <a name="see-also"></a>Zobacz też  
 [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x: Type — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [Typy ogólne w XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)
