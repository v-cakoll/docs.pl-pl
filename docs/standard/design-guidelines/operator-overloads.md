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
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400569"
---
# <a name="operator-overloads"></a>Przeciążenia operatorów
Przeciążenia operatorów umożliwiają typy struktury, które mają być wyświetlane tak, jakby były wbudowane prymitywy języka.

 Mimo że dozwolone i przydatne w niektórych sytuacjach, przeciążenia operatora powinny być używane ostrożnie. Istnieje wiele przypadków, w których przeciążenie operatora zostało nadużywane, na przykład gdy projektanci struktury zaczęli używać operatorów do operacji, które powinny być prostymi metodami. Poniższe wskazówki powinny pomóc w podjęciu decyzji, kiedy i jak używać przeciążenia operatora.

 ❌UNIKAJ definiowania przeciążeń operatora, z wyjątkiem typów, które powinny czuć się jak typy pierwotne (wbudowane).

 ✔️ ROZWAŻ definiowanie przeciążeń operatora w typie, który powinien czuć się jak typ pierwotny.

 Na przykład <xref:System.String?displayProperty=nameWithType> `operator==` ma `operator!=` i zdefiniowane.

 ✔️ Zdefiniuj przeciążenia operatora w <xref:System.Decimal?displayProperty=nameWithType>strukturach reprezentujących liczby (takie jak ).

 ❌NIE bądź uroczy podczas definiowania przeciążeń operatora.

 Przeciążenie operatora jest przydatne w przypadkach, w których od razu jest oczywiste, jaki będzie wynik operacji. Na przykład, to ma sens, aby <xref:System.DateTime> móc `DateTime` odjąć <xref:System.TimeSpan>jeden od drugiego i uzyskać . Jednak nie jest właściwe użycie operatora unii logicznej do unii dwóch kwerend bazy danych lub użyć operatora shift do zapisu do strumienia.

 ❌NIE należy podawać przeciążenia operatora, chyba że co najmniej jeden z operandów jest typu definiującego przeciążenie.

 ✔️ DO operatorów przeciążenia w sposób symetryczny.

 Na przykład, jeśli przeciążenie `operator==`, należy `operator!=`również przeciążyć . Podobnie, jeśli przeciążysz `operator<`, należy również `operator>`przeciążyć , i tak dalej.

 ✔️ ROZWAŻ dostarczenie metod o przyjaznych nazwach, które odpowiadają każdemu przeciążonemu operatorowi.

 Wiele języków nie obsługuje przeciążenia operatora. Z tego powodu zaleca się, że typy, które przeciążenia operatory zawierają metodę pomocniczą o odpowiedniej nazwie specyficznej dla domeny, która zapewnia równoważne funkcje.

 Poniższa tabela zawiera listę operatorów i odpowiadające im nazwy metod przyjaznych.

|Symbol operatora Języka C#|Nazwa metadanych|Przyjazna nazwa|
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

### <a name="overloading-operator-"></a>Operator przeciążenia ==
 Przeciążenie `operator ==` jest dość skomplikowane. Semantyka operatora musi być zgodna z kilkoma innymi <xref:System.Object.Equals%2A?displayProperty=nameWithType>członkami, takimi jak .

### <a name="conversion-operators"></a>Operatory konwersji
 Operatory konwersji są operatorami jednoargumentowymi, które umożliwiają konwersję z jednego typu na inny. Operatory muszą być zdefiniowane jako statyczne elementy członkowskie na operand lub typu zwracane. Istnieją dwa typy operatorów konwersji: niejawne i jawne.

 ❌NIE udostępniaj operatora konwersji, jeśli taka konwersja nie jest wyraźnie oczekiwana przez użytkowników końcowych.

 ❌NIE definiuj operatorów konwersji poza domeną typu.

 Na przykład <xref:System.Int32> <xref:System.Double>, <xref:System.Decimal> , i są wszystkie <xref:System.DateTime> typy liczbowe, podczas gdy nie jest. W związku z tym nie powinno `Double(long)` być `DateTime`operator konwersji do konwersji na . Konstruktor jest preferowany w takim przypadku.

 ❌NIE udostępniaj niejawnego operatora konwersji, jeśli konwersja jest potencjalnie stratna.

 Na przykład nie powinno być niejawna `Double` konwersja z `Int32` `Double` powodu `Int32` ma szerszy zakres niż . Operator konwersji jawnej można podać, nawet jeśli konwersja jest potencjalnie stratna.

 ❌NIE zgłaszaj wyjątków od rzutów niejawnych.

 Jest to bardzo trudne dla użytkowników końcowych, aby zrozumieć, co się dzieje, ponieważ mogą nie być świadomi, że konwersja ma miejsce.

 ✔️ czy <xref:System.InvalidCastException?displayProperty=nameWithType> rzucać, jeśli wywołanie odlewanego operatora powoduje stratną konwersję, a umowa operatora nie zezwala na straty konwersji.

 *Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*

## <a name="see-also"></a>Zobacz też

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
