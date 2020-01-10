---
title: Przeciążenia operatorów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 4cea3c17de40a873d977223f36b6dcef4f2c2d78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709143"
---
# <a name="operator-overloads"></a>Przeciążenia operatorów
Przeciążenia operatorów pozwalają na wyświetlanie typów struktur, tak jakby były wbudowane jako elementy pierwotne języka.  
  
 Chociaż dozwolone i przydatne w niektórych sytuacjach, przeciążenia operatorów powinny być stosowane ostrożnie. Istnieje wiele przypadków, w których przeciążanie operatora zostało nadmiarowe, na przykład gdy projektanci struktury zaczynali używać operatorów dla operacji, które powinny być prostymi metodami. Poniższe wskazówki powinny pomóc określić, kiedy i jak należy używać przeciążania operatora.  
  
 **X AVOID** Definiowanie przeciążenia operatora w typów, które powinny uznać, takich jak typy pierwotne (wbudowane).  
  
 **✓ CONSIDER** Definiowanie przeciążenia operatora w typie, który powinien uznać, takie jak typ pierwotny.  
  
 Na przykład <xref:System.String?displayProperty=nameWithType> ma zdefiniowane `operator==` i `operator!=`.  
  
 **✓ DO** definiować przeciążeń operatora w strukturach, które reprezentują numery (takie jak <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** można cute podczas definiowania przeciążenia operatora.  
  
 Przeciążanie operatora jest przydatne w przypadkach, w których jest od razu oczywisty, co jest wynikiem operacji. Na przykład warto mieć możliwość odejmowania jednego <xref:System.DateTime> od innego `DateTime` i uzyskania <xref:System.TimeSpan>. Nie jest jednak konieczne użycie operatora Union Logical do złożenia dwóch zapytań bazy danych lub użycie operatora przesunięcia do zapisu w strumieniu.  
  
 **X DO NOT** Podaj operator overloads, chyba że jest co najmniej jeden z argumentów typu Definiowanie przeciążenia.  
  
 **✓ DO** przeciążać operatory w sposób symetrycznego.  
  
 Na przykład w przypadku przeciążenia `operator==`należy również przeciążyć `operator!=`. Podobnie w przypadku przeciążenia `operator<`należy również przeciążać `operator>`i tak dalej.  
  
 **✓ CONSIDER** zapewniając metod przyjaznych nazw, które odpowiadają do każdego przeciążonego operatora.  
  
 Wiele języków nie obsługuje przeciążania operatora. Z tego powodu zaleca się, aby typy, które zawierają operatory przeciążeń, uwzględniają dodatkową metodę z odpowiednią nazwą domeny, która zapewnia równorzędną funkcjonalność.  
  
 Poniższa tabela zawiera listę operatorów i odpowiednich przyjaznych nazw metod.  
  
|C#Symbol operatora|Nazwa metadanych|Przyjazna nazwa|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a>Przeciążanie operatora = =  
 Przeciążenie `operator ==` jest dość skomplikowane. Semantyka operatora musi być zgodna z kilkoma innymi elementami członkowskimi, takimi jak <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operatory konwersji  
 Operatory konwersji to operatory jednoargumentowe, które umożliwiają konwersję z jednego typu na drugi. Operatory muszą być zdefiniowane jako statyczne elementy członkowskie dla operandu lub typu zwracanego. Istnieją dwa typy operatorów konwersji: niejawne i jawne.  
  
 **X DO NOT** Podaj operatora konwersji, jeśli takie konwersja nie jest wyraźnie oczekiwany przez użytkowników końcowych.  
  
 **X DO NOT** definiować operatory konwersji poza domeny typu.  
  
 Na przykład <xref:System.Int32>, <xref:System.Double>i <xref:System.Decimal> to wszystkie typy liczbowe, natomiast <xref:System.DateTime> nie jest. W związku z tym nie powinien istnieć operator konwersji do konwersji `Double(long)` na `DateTime`. Konstruktor jest preferowany w takich przypadkach.  
  
 **X DO NOT** Podaj operator niejawnej konwersji, jeśli konwersja jest potencjalnie stratnej.  
  
 Na przykład nie powinna być niejawna konwersja z `Double` na `Int32`, ponieważ `Double` ma szerszy zakres niż `Int32`. Jawny Operator konwersji można podać, nawet jeśli konwersja jest potencjalnie stratna.  
  
 **X DO NOT** zgłaszanie wyjątków z niejawnego rzutowania.  
  
 Bardzo trudne jest, aby użytkownicy końcowi wiedzieli, co się dzieje, ponieważ mogą nie wiedzieć, że odbywa się konwersja.  
  
 **✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> jeśli powoduje wywołanie operatora rzutowania stratnej konwersji i kontrakt operator nie zezwala stratnej konwersji.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
