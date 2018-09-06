---
title: Typy danych wyników operatora (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 135c44217debcddb15fd4cef7e73ca2f98903c43
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872585"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Typy danych wyników operatora (Visual Basic)
Visual Basic Określa typ danych wyniku operacji na podstawie typów danych operandu. W niektórych przypadkach może to być typ danych z większego zakresu niż jeden z operandów.  
  
## <a name="data-type-ranges"></a>Zakresy typu danych  
 Zakresy typów odpowiednie dane w kolejności od najmniejszej do największej, są następujące:  
  
-   [Wartość logiczna](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dwa możliwe wartości  
  
-   [SByte —](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 wartości całkowitych  
  
-   [Krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65 536 (6.5... E + 4) możliwych wartości całkowitych  
  
-   [Liczba całkowita](../../../visual-basic/language-reference/data-types/integer-data-type.md), [uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) możliwych wartości całkowitych  
  
-   [Długi](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) możliwych wartości całkowitych  
  
-   [Dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1,5... E + 29 możliwych wartości całkowitych, maksymalny zakres 7,9... E + 28 (wartość bezwzględna)  
  
-   [Pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) — zakresu maksymalnego 3.4... E + 38 (wartość bezwzględna)  
  
-   [Podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md) — zakresu maksymalnego 1.7... E + 308 (wartość bezwzględna)  
  
 Aby uzyskać więcej informacji na temat typów danych języka Visual Basic, zobacz [typy danych](../../../visual-basic/language-reference/data-types/index.md).  
  
 Jeśli argument daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), operatory arytmetyczne w Visual Basic należy jej traktowała jako zero.  
  
## <a name="decimal-arithmetic"></a>Operacje arytmetyczne dziesiętna  
 Należy pamiętać, że [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) typ danych jest inny niż zmiennoprzecinkowych ani liczby całkowitej.  
  
 Jeśli oba operandy z `+`, `–`, `*`, `/`, lub `Mod` operacji `Decimal` , a druga nie `Single` lub `Double`, Visual Basic rozszerza się to drugi operand do `Decimal`. Wykonuje operację w `Decimal`, a typem danych wyniku `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Zmiennoprzecinkowe operacje arytmetyczne  
 Visual Basic wykonuje większość arytmetyki zmiennoprzecinkowej w [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), który jest najbardziej efektywny sposób dane w polu takich operacji. Jednak jeśli jeden z operandów jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) , a druga nie `Double`, Visual Basic wykonuje operację w `Single`. Rozszerza on się każdy argument, zgodnie z potrzebami na odpowiedni typ danych przed wykonaniem operacji, a wynik ma ten typ danych.  
  
### <a name="-and--operators"></a>/ a ^ operatorów  
 `/` Operator jest zdefiniowany tylko w przypadku [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md), i [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) typów danych. Visual Basic rozszerza się każdy argument, zgodnie z potrzebami na odpowiedni typ danych przed wykonaniem operacji, a wynik jest tego typu danych.  
  
 W poniższej tabeli przedstawiono wyniki typy danych dla `/` operatora. Należy pamiętać, że ta tabela jest symetryczne; dla podanej kombinacji argumentami o typach danych typ danych wynik jest taki sam, niezależnie od kolejności argumentów.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Dowolnego typu liczby całkowitej|  
|`Decimal`|Wartość dziesiętna|Single|Double|Wartość dziesiętna|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Dowolnego typu liczby całkowitej|Wartość dziesiętna|Single|Double|Double|  
  
 `^` Operator jest zdefiniowany tylko w przypadku `Double` typu danych. Visual Basic rozszerza się każdy argument konieczny do `Double` przed operacji, a wynik jest zawsze typu danych `Double`.  
  
## <a name="integer-arithmetic"></a>Operacje arytmetyczne liczba całkowita  
 Typ danych wyniku operacji liczby całkowitej, zależy od typy danych argumentów. Ogólnie rzecz biorąc Visual Basic używa następujących zasad do określania typu danych:  
  
-   Jeśli oba operandy operatora binarnego mają taki sam typ danych, wynik ma ten typ danych. Wyjątek stanowi `Boolean`, który jest zmuszony do `Short`.  
  
-   Jeśli operand bez znaku, należy za pomocą podpisanego operand, wynik ma typ ze znakiem z co najmniej tak dużej zakresu jako jeden z operandów.  
  
-   W przeciwnym razie wynik zazwyczaj ma większe z dwóch typów danych argumentu operacji.  
  
 Należy pamiętać, że typ danych wyniku nie może być taka sama jak albo typ danych argumentu operacji.  
  
> [!NOTE]
>  Typ danych wyniku nie zawsze jest wystarczająco duży, aby pomieścić wszystkie możliwe wartości wynikające z operacji. <xref:System.OverflowException> Wyjątek może wystąpić, jeśli wartość jest zbyt duża dla typu danych.  
  
### <a name="unary--and--operators"></a>Jednoargumentowy + i — operatory  
 W poniższej tabeli przedstawiono wyniki typów danych w dwóch operatorów jednoargumentowych `+` i `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Jednoargumentowy `+`|Krótka|SByte|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|Jednoargumentowy `–`|Krótka|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|Wartość dziesiętna|  
  
### <a name="-and--operators"></a><\< i >> operatorów  
 W poniższej tabeli przedstawiono wyniki typów danych na dwa operatory przesunięcia bitowego `<<` i `>>`. Visual Basic traktuje każdy operator przesunięcia bitowego jako operator jednoargumentowy na jego lewy operand (wzorca bitowego lekkie).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Krótka|SByte|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
  
 Jeśli Lewy argument operacji jest `Decimal`, `Single`, `Double`, lub `String`, Visual Basic próbuje przekonwertować go pod kątem `Long` przed operacji, a wynik jest typu danych `Long`. Prawy operand (liczba pozycji bitów, aby przenieść) musi być `Integer` lub typ, który rozszerza się na `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binarny +, -, * i operatorów Mod  
 W poniższej tabeli przedstawiono wyniki typy danych dla pliku binarnego `+` i `–` operatorów i `*` i `Mod` operatorów. Należy pamiętać, że ta tabela jest symetryczne; dla podanej kombinacji argumentami o typach danych typ danych wynik jest taki sam, niezależnie od kolejności argumentów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótka|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|Wartość dziesiętna|  
|`SByte`|SByte|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|Wartość dziesiętna|  
|`Byte`|Krótka|Krótka|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Short`|Krótka|Krótka|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|Wartość dziesiętna|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długi|długi|Wartość dziesiętna|  
|`UInteger`|długi|długi|Uinteger —|długi|Uinteger —|długi|Uinteger —|długi|ULong|  
|`Long`|długi|długi|długi|długi|długi|długi|długi|długi|Wartość dziesiętna|  
|`ULong`|Wartość dziesiętna|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|  
  
### <a name="-operator"></a>\ — Operator  
 W poniższej tabeli przedstawiono wyniki typy danych dla `\` operatora. Należy pamiętać, że ta tabela jest symetryczne; dla podanej kombinacji argumentami o typach danych typ danych wynik jest taki sam, niezależnie od kolejności argumentów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótka|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`SByte`|SByte|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`Byte`|Krótka|Krótka|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Short`|Krótka|Krótka|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`UInteger`|długi|długi|Uinteger —|długi|Uinteger —|długi|Uinteger —|długi|ULong|  
|`Long`|długi|długi|długi|długi|długi|długi|długi|długi|długi|  
|`ULong`|długi|długi|ULong|długi|ULong|długi|ULong|długi|ULong|  
  
 Jeśli oba operandy z `\` operator jest [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md), lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic próbuje przekonwertować go pod kątem [długich](../../../visual-basic/language-reference/data-types/long-data-type.md)przed operacji, a wynik jest typu danych `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relacyjne i bitowe porównania  
 Typ danych wyniku operacji relacyjnych (`=`, `<>`, `<`, `>`, `<=`, `>=`) jest zawsze `Boolean` [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). To samo dotyczy operacji logicznych (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` argumentów operacji.  
  
 Typ danych wyniku bitowe operacji logicznej zależy od typy danych argumentów. Należy pamiętać, że `AndAlso` i `OrElse` są zdefiniowane tylko w przypadku `Boolean`, i Visual Basic konwertuje każdy argument konieczny do `Boolean` przed wykonaniem tej operacji.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<= i > = operatory  
 Jeśli oba operandy są `Boolean`, Visual Basic traktuje `True` za mniej niż `False`. Jeśli typ liczbowy jest porównywana z `String`, Visual Basic stara się przekonwertować `String` do `Double` przed wykonaniem operacji. A `Char` lub `Date` operand można porównać tylko z innego operandu tego samego typu danych. Typ danych wyniku jest zawsze `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitowy Not Operator  
 W poniższej tabeli przedstawiono wyniki typy danych dla operatora testu koniunkcji `Not` operatora.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
  
 Jeśli argument jest `Decimal`, `Single`, `Double`, lub `String`, Visual Basic próbuje przekonwertować go pod kątem `Long` przed operacji, a wynik jest typu danych `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitowe or a, lub i operatorów Xor  
 W poniższej tabeli przedstawiono wyniki typy danych dla operatora testu koniunkcji `And`, `Or`, i `Xor` operatorów. Należy pamiętać, że ta tabela jest symetryczne; dla podanej kombinacji argumentami o typach danych typ danych wynik jest taki sam, niezależnie od kolejności argumentów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`SByte`|SByte|SByte|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`Byte`|Krótka|Krótka|Byte|Krótka|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Short`|Krótka|Krótka|Krótka|Krótka|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długi|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długi|długi|długi|  
|`UInteger`|długi|długi|Uinteger —|długi|Uinteger —|długi|Uinteger —|długi|ULong|  
|`Long`|długi|długi|długi|długi|długi|długi|długi|długi|długi|  
|`ULong`|długi|długi|ULong|długi|ULong|długi|ULong|długi|ULong|  
  
 Jeśli argument jest `Decimal`, `Single`, `Double`, lub `String`, Visual Basic próbuje przekonwertować go pod kątem `Long` przed operacji, a dane wynikowe typ jest taki sam, jakby miało operandu `Long`.  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
 `&` Operator jest zdefiniowany tylko w przypadku łączenia z `String` argumentów operacji. Visual Basic konwertuje każdy argument konieczny do `String` przed operacji, a wynik jest zawsze typu danych `String`. Na potrzeby `&` operator, wszystkie konwersje do `String` są traktowane jako rozszerzenia, nawet jeśli `Option Strict` jest `On`.  
  
 `Is` i `IsNot` operatorzy muszą mieć oba operandy typu odwołania. `TypeOf`... `Is` wyrażenie wymaga pierwszy argument operacji typu odwołania i drugiego operandu, nazwa typu danych. We wszystkich tych przypadkach dane wynikowe typ jest `Boolean`.  
  
 `Like` Operator jest zdefiniowany tylko w przypadku dopasowanie do wzorca `String` argumentów operacji. Visual Basic stara się przekonwertować każdy argument konieczny do `String` przed wykonaniem operacji. Typ danych wyniku jest zawsze `Boolean`.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory porównania w języku Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory](../../../visual-basic/language-reference/operators/index.md)  
 [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
