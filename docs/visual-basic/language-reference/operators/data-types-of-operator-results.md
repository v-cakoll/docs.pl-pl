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
ms.openlocfilehash: b0ebdb723df6bdb4f74e1558537c307ddb917f64
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2019
ms.locfileid: "69923273"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Typy danych wyników operatora (Visual Basic)
Visual Basic określa typ danych wyniku operacji na podstawie typów danych argumentów operacji. W niektórych przypadkach może to być typ danych z większym zakresem niż każdy operand.  
  
## <a name="data-type-ranges"></a>Zakresy typu danych  
 Zakresy odpowiednich typów danych, w kolejności od najmniejszej do największej, są następujące:  
  
- [Wartość logiczna](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dwie możliwe wartości  
  
- [](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)Nieparzystość, [bajt](../../../visual-basic/language-reference/data-types/byte-data-type.md) 256 — możliwe wartości całkowite  
  
- [Krótkie](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65 536 (6.5... E + 4) możliwe wartości całkowite  
  
- [Liczba całkowita](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) możliwe wartości całkowite  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18446744073709551615 są (1.8... E + 19) możliwe wartości całkowite  
  
- [Liczba dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1,5... e + 29 możliwych wartości całkowitych, maksymalny zakres 7,9... e + 28 (wartość bezwzględna)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) — maksymalny zakres 3.4... E + 38 (wartość bezwzględna)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — maksymalny zakres 1.7... E + 308 (wartość bezwzględna)  
  
 Aby uzyskać więcej informacji na temat Visual Basic typów danych, zobacz [typy danych](../../../visual-basic/language-reference/data-types/index.md).  
  
 Jeśli operand zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), Visual Basic operatory arytmetyczne traktują je jako zero.  
  
## <a name="decimal-arithmetic"></a>Arytmetyka dziesiętna  
 Należy zauważyć, [](../../../visual-basic/language-reference/data-types/decimal-data-type.md) że typ danych dziesiętnych nie jest ani zmiennoprzecinkowy, ani liczbą całkowitą.  
  
 Jeśli `+`jeden z operandów `*`, `–`,, `/`, lub `Mod` operacji jest `Decimal` , a drugi nie `Single` jest lub `Double`, Visual Basic poszerza drugi operand do `Decimal`. Wykonuje operację w `Decimal`, a typ danych wynik jest `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Arytmetyka zmiennoprzecinkowa  
 Visual Basic wykonuje większość operacji arytmetycznych zmiennoprzecinkowych [](../../../visual-basic/language-reference/data-types/double-data-type.md)w postaci podwójnej, która jest najbardziej wydajnym typem danych dla tego typu. Jeśli jednak jeden operand jest [pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) , a drugi nie `Double`, Visual Basic wykonuje operację w. `Single` Każdy operand jest rozszerzany do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
### <a name="-and--operators"></a>Operatory/i ^  
 Operator jest zdefiniowany tylko dla typów danych [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)i [Double.](../../../visual-basic/language-reference/data-types/double-data-type.md) `/` Visual Basic rozszerza każdy operand jako niezbędny do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
 W poniższej tabeli przedstawiono typy danych wynikowych dla `/` operatora. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Dowolny typ liczby całkowitej|  
|`Decimal`|Wartość dziesiętna|Single|Double|Wartość dziesiętna|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Podwójne|Podwójne|Double|  
|Dowolny typ liczby całkowitej|Wartość dziesiętna|Single|Double|Double|  
  
 Operator jest zdefiniowany tylko `Double` dla typu danych. `^` Visual Basic rozszerza każdy operand w miarę potrzeb `Double` przed operacją, a typ danych wynik jest zawsze. `Double`  
  
## <a name="integer-arithmetic"></a>Arytmetyka liczb całkowitych  
 Typ danych wynikowych operacji całkowitej zależy od typów danych operandów. Ogólnie rzecz biorąc, Visual Basic używa następujących zasad do określania typu danych wynik:  
  
- Jeśli oba operandy operatora binarnego mają ten sam typ danych, wynik ma ten typ danych. Wyjątek `Boolean`, który jest wymuszany do `Short`.  
  
- Jeśli argument operacji bez znaku jest częścią podpisanego operandu, wynik ma typ podpisany z co najmniej tak dużym zakresem, jak każdy operand.  
  
- W przeciwnym razie wynik zwykle jest większy spośród dwóch typów danych operandu.  
  
 Należy zauważyć, że typ danych wynik może nie być taki sam jak typ danych operandu.  
  
> [!NOTE]
> Typ danych wynikowych nie zawsze jest wystarczająco duży, aby pomieścić wszystkie możliwe wartości wynikające z operacji. <xref:System.OverflowException> Wyjątek może wystąpić, jeśli wartość jest zbyt duża dla typu danych wynik.  
  
### <a name="unary--and--operators"></a>Operatory jednoargumentowe + i –  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch jednoargumentowych operatorów `+` i `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Jednostk`+`|Krótkie|SByte|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|Jednostk`–`|Krótkie|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Wartość dziesiętna|  
  
### <a name="-and--operators"></a><\<Operatory > >  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch operatorów `<<` transmisji bitów i. `>>` Visual Basic traktuje każdy operator przesunięcia bitowego jako operator jednoargumentowy na lewym operandzie (wzorzec bitowy, który ma zostać przesunięty).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Krótkie|SByte|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
  
 Jeśli argument operacji po lewej `Decimal`stronie `Single`to `Double`,, `String`, lub, Visual Basic próbuje wykonać `Long` konwersję do przed operacją, a typ danych `Long`wynik to. Prawy operand (liczba pozycji bitowych do przesunięcia) musi być `Integer` lub typem, który jest poszerzany do. `Integer`  
  
### <a name="binary----and-mod-operators"></a>Operatory Binary +, –, * i mod  
 W poniższej tabeli przedstawiono typy danych wynikowych dla elementów `+` binarnych `–` i `*` operatorów oraz operatory `Mod` i. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótkie|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Wartość dziesiętna|  
|`SByte`|SByte|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Wartość dziesiętna|  
|`Byte`|Krótkie|Krótkie|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Wartość dziesiętna|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Wartość dziesiętna|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Wartość dziesiętna|  
|`ULong`|Wartość dziesiętna|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|  
  
### <a name="-operator"></a>\ — Operator  
 W poniższej tabeli przedstawiono typy danych wynikowych dla `\` operatora. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótkie|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`SByte`|SByte|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`Byte`|Krótkie|Krótkie|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|  
|`ULong`|Długie|Długie|ULong|Długie|ULong|Długie|ULong|Długie|ULong|  
  
 Jeśli każdy operand `\` operatora ma wartość [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [pojedynczą](../../../visual-basic/language-reference/data-types/single-data-type.md)lub [podwójną](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic próbuje skonwertować ją na wartość [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) przed operacją, a typ danych wynik `Long`to.  
  
## <a name="relational-and-bitwise-comparisons"></a>Porównania relacyjne i bitowe  
 Typ`=`danych wyniku operacji relacyjnej (, `<>`, `<`, `>` `<=`,, `>=`) jest zawsze `Boolean` [typem danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Ta sama wartość dotyczy`And`operacji logicznych (, `AndAlso`, `Not` `OrElse` `Or`,,, `Xor`) `Boolean` dla operandów.  
  
 Typ danych wynikowych bitowej operacji logicznej zależy od typów danych operandów. Należy pamiętać `AndAlso` , `OrElse` że i są zdefiniowane `Boolean`tylko dla, `Boolean` i Visual Basic konwertuje każdy operand w razie potrzeby przed wykonaniem operacji.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= i > = operatory  
 Jeśli oba operandy są `Boolean`, Visual Basic uznaje `True` za mniejsze niż `False`. Jeśli typ liczbowy jest porównywany z `String`, Visual Basic próbuje `String` skonwertować do `Double` przed operacją. Operand `Char` lub`Date` można porównać tylko z innym operandem tego samego typu danych. Typ danych wynikowych jest zawsze `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Operator not bitowego  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatora bitowego `Not` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|Sbyte —|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
  
 Jeśli argumentem jest `Decimal`, `Single`, `Double`, lub `String`, Visual Basic próbuje przekonwertować go do `Long` przed operacją, a typ danych wynik jest `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operatory bitowe and, or i XOR  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatorów bitowe `And`, `Or`i `Xor` . Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`SByte`|SByte|SByte|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`Byte`|Krótkie|Krótkie|Byte|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|  
|`ULong`|Długie|Długie|ULong|Długie|ULong|Długie|ULong|Długie|ULong|  
  
 Jeśli argumentem jest `Decimal`, `Single`, `Double`, lub `String`, Visual Basic próbuje przekonwertować go do `Long` przed operacją, a typ danych wynik będzie taki sam, jak gdyby ten operand już `Long`należał.  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
 Operator jest zdefiniowany tylko w celu łączenia `String` argumentów operacji. `&` Visual Basic konwertuje każdy operand w razie potrzeby `String` przed operacją, a typ danych wynik jest zawsze. `String` Na potrzeby `&` operatora wszystkie konwersje na `String` są uznawane za rozszerzające, nawet jeśli `Option Strict` są `On`.  
  
 Operatory `Is` i`IsNot` wymagają, aby oba operandy były typu referencyjnego. `TypeOf`... `Is` wyrażenie wymaga, aby pierwszy operand był typu referencyjnego, a drugi operand jest nazwą typu danych. We wszystkich przypadkach typem danych wynik jest `Boolean`.  
  
 Operator jest zdefiniowany tylko dla `String` dopasowania wzorca argumentów operacji. `Like` Visual Basic próbuje przekonwertować każdy operand w razie potrzeby `String` przed operacją. Typ danych wynikowych jest zawsze `Boolean`.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory](../../../visual-basic/language-reference/operators/index.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
