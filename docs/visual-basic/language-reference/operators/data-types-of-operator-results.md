---
title: Typy danych wyników operatora
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331468"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Typy danych wyników operatora (Visual Basic)
Visual Basic określa typ danych wyniku operacji na podstawie typów danych argumentów operacji. W niektórych przypadkach może to być typ danych z większym zakresem niż każdy operand.  
  
## <a name="data-type-ranges"></a>Zakresy typu danych  
 Zakresy odpowiednich typów danych, w kolejności od najmniejszej do największej, są następujące:  
  
- [Wartość logiczna](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dwie możliwe wartości  
  
- [](../../../visual-basic/language-reference/data-types/sbyte-data-type.md) [Nieparzystość, bajt](../../../visual-basic/language-reference/data-types/byte-data-type.md) 256 — możliwe wartości całkowite  
  
- [Krótkie](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65 536 (6.5... E + 4) możliwe wartości całkowite  
  
- [Liczba całkowita](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) możliwe wartości całkowite  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18446744073709551615 są (1.8... E + 19) możliwe wartości całkowite  
  
- [Liczba dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1,5... e + 29 możliwych wartości całkowitych, maksymalny zakres 7,9... e + 28 (wartość bezwzględna)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) — maksymalny zakres 3.4... E + 38 (wartość bezwzględna)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — maksymalny zakres 1.7... E + 308 (wartość bezwzględna)  
  
 Aby uzyskać więcej informacji na temat Visual Basic typów danych, zobacz [typy danych](../../../visual-basic/language-reference/data-types/index.md).  
  
 Jeśli operand zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), Visual Basic operatory arytmetyczne traktują je jako zero.  
  
## <a name="decimal-arithmetic"></a>Arytmetyka dziesiętna  
 Należy zauważyć, że typ danych [dziesiętnych](../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie jest ani zmiennoprzecinkowy, ani liczbą całkowitą.  
  
 Jeśli jeden z argumentów operacji `+`, `–`, `*`, `/`lub `Mod` jest `Decimal`, a drugi nie `Single` lub `Double`, Visual Basic poszerzyć inny operand do `Decimal`. Wykonuje operację w `Decimal`, a typ danych wynik jest `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Arytmetyka zmiennoprzecinkowa  
 Visual Basic wykonuje większość operacji arytmetycznych zmiennoprzecinkowych w postaci [podwójnej](../../../visual-basic/language-reference/data-types/double-data-type.md), która jest najbardziej wydajnym typem danych dla tego typu. Jeśli jednak jeden operand jest [pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) , a drugi nie `Double`, Visual Basic wykonuje operację w `Single`. Każdy operand jest rozszerzany do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
### <a name="-and--operators"></a>Operatory/i ^  
 Operator `/` jest zdefiniowany tylko dla typów danych [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)i [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) . Visual Basic rozszerza każdy operand jako niezbędny do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatora `/`. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Dowolny typ liczby całkowitej|  
|`Decimal`|Dziesiętna|Pojedyncze|Podwójne|Dziesiętna|  
|`Single`|Pojedyncze|Pojedyncze|Podwójne|Pojedyncze|  
|`Double`|Podwójne|Podwójne|Podwójne|Podwójne|  
|Dowolny typ liczby całkowitej|Dziesiętna|Pojedyncze|Podwójne|Podwójne|  
  
 Operator `^` jest zdefiniowany tylko dla typu danych `Double`. Visual Basic rozszerza każdy operand jako niezbędny do `Double` przed operacją, a typ danych wynik jest zawsze `Double`.  
  
## <a name="integer-arithmetic"></a>Arytmetyka liczb całkowitych  
 Typ danych wynikowych operacji całkowitej zależy od typów danych operandów. Ogólnie rzecz biorąc, Visual Basic używa następujących zasad do określania typu danych wynik:  
  
- Jeśli oba operandy operatora binarnego mają ten sam typ danych, wynik ma ten typ danych. Wyjątek jest `Boolean`, który jest wymuszany `Short`.  
  
- Jeśli argument operacji bez znaku jest częścią podpisanego operandu, wynik ma typ podpisany z co najmniej tak dużym zakresem, jak każdy operand.  
  
- W przeciwnym razie wynik zwykle jest większy spośród dwóch typów danych operandu.  
  
 Należy zauważyć, że typ danych wynik może nie być taki sam jak typ danych operandu.  
  
> [!NOTE]
> Typ danych wynikowych nie zawsze jest wystarczająco duży, aby pomieścić wszystkie możliwe wartości wynikające z operacji. Wyjątek <xref:System.OverflowException> może wystąpić, jeśli wartość jest zbyt duża dla typu danych wynik.  
  
### <a name="unary--and--operators"></a>Operatory jednoargumentowe + i –  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch jednoargumentowych operatorów, `+` i `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`+` jednoargumentowe|Krótkie|Sbyte —|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`–` jednoargumentowe|Krótkie|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Dziesiętna|  
  
### <a name="-and--operators"></a><operatory \< i > >  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch operatorów przesunięcia bitowego, `<<` i `>>`. Visual Basic traktuje każdy operator przesunięcia bitowego jako operator jednoargumentowy na lewym operandzie (wzorzec bitowy, który ma zostać przesunięty).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Krótkie|Sbyte —|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
  
 Jeśli lewy operand to `Decimal`, `Single`, `Double`lub `String`, Visual Basic próbuje przekonwertować go na `Long` przed operacją, a typ danych wynik jest `Long`. Prawy operand (liczba pozycji bitowych do przesunięcia) musi być `Integer` lub typem rozszerzającym `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Operatory binarne +, –, \*i mod  
 W poniższej tabeli przedstawiono typy danych wyników dla `+` binarnych i operatory `–` oraz operatory `*` i `Mod`. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótkie|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Dziesiętna|  
|`SByte`|Sbyte —|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Dziesiętna|  
|`Byte`|Krótkie|Krótkie|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Dziesiętna|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Dziesiętna|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Dziesiętna|  
|`ULong`|Dziesiętna|Dziesiętna|ULong|Dziesiętna|ULong|Dziesiętna|ULong|Dziesiętna|ULong|  
  
### <a name="-operator"></a>\\, operator  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatora `\`. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krótkie|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`SByte`|Sbyte —|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`Byte`|Krótkie|Krótkie|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|  
|`ULong`|Długie|Długie|ULong|Długie|ULong|Długie|ULong|Długie|ULong|  
  
 Jeśli każdy operand operatora `\` ma wartość [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic próbuje skonwertować ją na wartość [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) przed operacją, a typ danych wynikowych jest `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Porównania relacyjne i bitowe  
 Typ danych wyniku operacji relacyjnej (`=`, `<>`, `<`, `>`, `<=`, `>=`) jest zawsze `Boolean`[typem danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Ta sama wartość dotyczy operacji logicznych (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) dla argumentów operacji `Boolean`.  
  
 Typ danych wynikowych bitowej operacji logicznej zależy od typów danych operandów. Należy zauważyć, że `AndAlso` i `OrElse` są zdefiniowane tylko dla `Boolean`i Visual Basic konwertuje każdy operand jako niezbędny do `Boolean` przed wykonaniem operacji.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= i > = operatory  
 Jeśli oba operandy są `Boolean`, Visual Basic uznaje, że `True` być mniejsze niż `False`. Jeśli typ liczbowy jest porównywany z `String`, Visual Basic próbuje skonwertować `String` na `Double` przed operacją. Operand `Char` lub `Date` można porównać tylko z innym operandem tego samego typu danych. Typ danych wynikowych jest zawsze `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Operator not bitowego  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatora `Not` bitowego.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|Sbyte —|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
  
 Jeśli operand jest `Decimal`, `Single`, `Double`lub `String`, Visual Basic próbuje przekonwertować go na `Long` przed operacją, a typ danych wynik jest `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operatory bitowe and, or i XOR  
 W poniższej tabeli przedstawiono typy danych wyników dla operatorów `And`, `Or`i `Xor`. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`SByte`|Sbyte —|Sbyte —|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`Byte`|Krótkie|Krótkie|Bajtów|Krótkie|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Short`|Krótkie|Krótkie|Krótkie|Krótkie|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długie|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długie|Długie|Długie|  
|`UInteger`|Długie|Długie|UInteger —|Długie|UInteger —|Długie|UInteger —|Długie|ULong|  
|`Long`|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|Długie|  
|`ULong`|Długie|Długie|ULong|Długie|ULong|Długie|ULong|Długie|ULong|  
  
 Jeśli operand jest `Decimal`, `Single`, `Double`lub `String`, Visual Basic próbuje przekonwertować go do `Long` przed operacją, a typ danych wynik będzie taki sam jak wtedy, gdy ten operand został już `Long`.  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
 Operator `&` jest zdefiniowany tylko w celu łączenia argumentów operacji `String`. Visual Basic konwertuje każdy operand jako niezbędny do `String` przed operacją, a typ danych wynik jest zawsze `String`. Na potrzeby operatora `&` wszystkie konwersje do `String` są uważane za rozszerzane, nawet jeśli `Option Strict` `On`.  
  
 Operatory `Is` i `IsNot` wymagają, aby oba operandy były typu referencyjnego. Wyrażenie `TypeOf`...`Is` wymaga, aby pierwszy operand był typu referencyjnego, a drugi operand jest nazwą typu danych. We wszystkich przypadkach typem danych wynik jest `Boolean`.  
  
 Operator `Like` jest zdefiniowany tylko dla dopasowania wzorca `String` operandów. Visual Basic próbuje skonwertować każdego operandu, aby `String` przed operacją. Typ danych wynikowych jest zawsze `Boolean`.  
  
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
