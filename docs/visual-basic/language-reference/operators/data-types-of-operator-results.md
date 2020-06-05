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
ms.openlocfilehash: b80508c5619770da0c7dc78003ff9d4847dd94d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371430"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Typy danych wyników operatora (Visual Basic)
Visual Basic określa typ danych wyniku operacji na podstawie typów danych argumentów operacji. W niektórych przypadkach może to być typ danych z większym zakresem niż każdy operand.  
  
## <a name="data-type-ranges"></a>Zakresy typu danych  
 Zakresy odpowiednich typów danych, w kolejności od najmniejszej do największej, są następujące:  
  
- [Wartość logiczna](../data-types/boolean-data-type.md) — dwie możliwe wartości  
  
- [SByte](../data-types/sbyte-data-type.md) [Nieparzystość, bajt](../data-types/byte-data-type.md) 256 — możliwe wartości całkowite  
  
- [Krótkie](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md) — 65 536 (6.5... E + 4) możliwe wartości całkowite  
  
- [Liczba całkowita](../data-types/integer-data-type.md), [UInteger —](../data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) możliwe wartości całkowite  
  
- [Long](../data-types/long-data-type.md), [ULONG](../data-types/ulong-data-type.md) — 18446744073709551615 są (1.8... E + 19) możliwe wartości całkowite  
  
- [Liczba dziesiętna](../data-types/decimal-data-type.md) — 1,5... e + 29 możliwych wartości całkowitych, maksymalny zakres 7,9... e + 28 (wartość bezwzględna)  
  
- [Single](../data-types/single-data-type.md) — maksymalny zakres 3.4... E + 38 (wartość bezwzględna)  
  
- [Double](../data-types/double-data-type.md) — maksymalny zakres 1.7... E + 308 (wartość bezwzględna)  
  
 Aby uzyskać więcej informacji na temat Visual Basic typów danych, zobacz [typy danych](../data-types/index.md).  
  
 Jeśli operand zwróci wartość [Nothing](../nothing.md), Visual Basic operatory arytmetyczne traktują je jako zero.  
  
## <a name="decimal-arithmetic"></a>Arytmetyka dziesiętna  
 Należy zauważyć, że typ danych [dziesiętnych](../data-types/decimal-data-type.md) nie jest ani zmiennoprzecinkowy, ani liczbą całkowitą.  
  
 Jeśli jeden z operandów `+` , `–` , `*` ,, `/` lub `Mod` operacji jest, `Decimal` a drugi nie jest `Single` lub `Double` , Visual Basic poszerza drugi operand do `Decimal` . Wykonuje operację w `Decimal` , a typ danych wynik jest `Decimal` .  
  
## <a name="floating-point-arithmetic"></a>Arytmetyka zmiennoprzecinkowa  
 Visual Basic wykonuje większość operacji arytmetycznych zmiennoprzecinkowych w postaci [podwójnej](../data-types/double-data-type.md), która jest najbardziej wydajnym typem danych dla tego typu. Jeśli jednak jeden operand jest [pojedynczy](../data-types/single-data-type.md) , a drugi nie `Double` , Visual Basic wykonuje operację w `Single` . Każdy operand jest rozszerzany do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
### <a name="-and--operators"></a>Operatory/i ^  
 `/`Operator jest zdefiniowany tylko dla typów danych [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)i [Double](../data-types/double-data-type.md) . Visual Basic rozszerza każdy operand jako niezbędny do odpowiedniego typu danych przed operacją, a wynik ma ten typ danych.  
  
 W poniższej tabeli przedstawiono typy danych wynikowych dla `/` operatora. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Dowolny typ liczby całkowitej|  
|`Decimal`|Wartość dziesiętna|Single|Double|Wartość dziesiętna|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Dowolny typ liczby całkowitej|Wartość dziesiętna|Single|Double|Double|  
  
 `^`Operator jest zdefiniowany tylko dla `Double` typu danych. Visual Basic rozszerza każdy operand w miarę potrzeb `Double` przed operacją, a typ danych wynik jest zawsze `Double` .  
  
## <a name="integer-arithmetic"></a>Arytmetyka liczb całkowitych  
 Typ danych wynikowych operacji całkowitej zależy od typów danych operandów. Ogólnie rzecz biorąc, Visual Basic używa następujących zasad do określania typu danych wynik:  
  
- Jeśli oba operandy operatora binarnego mają ten sam typ danych, wynik ma ten typ danych. Wyjątek `Boolean` , który jest wymuszany do `Short` .  
  
- Jeśli argument operacji bez znaku jest częścią podpisanego operandu, wynik ma typ podpisany z co najmniej tak dużym zakresem, jak każdy operand.  
  
- W przeciwnym razie wynik zwykle jest większy spośród dwóch typów danych operandu.  
  
 Należy zauważyć, że typ danych wynik może nie być taki sam jak typ danych operandu.  
  
> [!NOTE]
> Typ danych wynikowych nie zawsze jest wystarczająco duży, aby pomieścić wszystkie możliwe wartości wynikające z operacji. <xref:System.OverflowException>Wyjątek może wystąpić, jeśli wartość jest zbyt duża dla typu danych wynik.  
  
### <a name="unary--and--operators"></a>Operatory jednoargumentowe + i –  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch jednoargumentowych operatorów `+` i `–` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Jednostk`+`|Wybierak|SByte|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|Jednostk`–`|Wybierak|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Wartość dziesiętna|  
  
### <a name="-and--operators"></a><\< and >Operatory>  
 W poniższej tabeli przedstawiono typy danych wynikowych dla dwóch operatorów transmisji bitów `<<` i `>>` . Visual Basic traktuje każdy operator przesunięcia bitowego jako operator jednoargumentowy na lewym operandzie (wzorzec bitowy, który ma zostać przesunięty).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Wybierak|SByte|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
  
 Jeśli argument operacji po lewej stronie to `Decimal` , `Single` , `Double` , lub `String` , Visual Basic próbuje wykonać konwersję do `Long` przed operacją, a typ danych wynik to `Long` . Prawy operand (liczba pozycji bitowych do przesunięcia) musi być `Integer` lub typem, który jest poszerzany do `Integer` .  
  
### <a name="binary----and-mod-operators"></a>Operatory Binary +, –, \* i mod  
 W poniższej tabeli przedstawiono typy danych wynikowych dla elementów binarnych i operatorów oraz `+` `–` `*` `Mod` Operatory i. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Wybierak|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Wartość dziesiętna|  
|`SByte`|SByte|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Wartość dziesiętna|  
|`Byte`|Wybierak|Wybierak|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Short`|Wybierak|Wybierak|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Wartość dziesiętna|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długo|Długo|Wartość dziesiętna|  
|`UInteger`|Długo|Długo|UInteger —|Długo|UInteger —|Długo|UInteger —|Długo|ULong|  
|`Long`|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Wartość dziesiętna|  
|`ULong`|Wartość dziesiętna|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|  
  
### <a name="-operator"></a>\\, operator  
 W poniższej tabeli przedstawiono typy danych wynikowych dla `\` operatora. Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Wybierak|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`SByte`|SByte|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`Byte`|Wybierak|Wybierak|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Short`|Wybierak|Wybierak|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`UInteger`|Długo|Długo|UInteger —|Długo|UInteger —|Długo|UInteger —|Długo|ULong|  
|`Long`|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Długo|  
|`ULong`|Długo|Długo|ULong|Długo|ULong|Długo|ULong|Długo|ULong|  
  
 Jeśli każdy operand `\` operatora ma wartość [dziesiętną](../data-types/decimal-data-type.md), [pojedynczą](../data-types/single-data-type.md)lub [podwójną](../data-types/double-data-type.md), Visual Basic próbuje skonwertować ją na wartość [Long](../data-types/long-data-type.md) przed operacją, a typ danych wynik to `Long` .  
  
## <a name="relational-and-bitwise-comparisons"></a>Porównania relacyjne i bitowe  
 Typ danych wyniku operacji relacyjnej ( `=` , `<>` ,,, `<` `>` `<=` , `>=` ) jest zawsze `Boolean` [typem danych Boolean](../data-types/boolean-data-type.md). Ta sama wartość dotyczy operacji logicznych ( `And` ,,,, `AndAlso` `Not` `Or` `OrElse` ,) dla `Xor` `Boolean` operandów.  
  
 Typ danych wynikowych bitowej operacji logicznej zależy od typów danych operandów. Należy pamiętać, że `AndAlso` i `OrElse` są zdefiniowane tylko dla `Boolean` , i Visual Basic konwertuje każdy operand w razie potrzeby `Boolean` przed wykonaniem operacji.  
  
### <a name="-----and--operators"></a>=,  <>, \<, > , \<=, and > = Operatory  
 Jeśli oba operandy są `Boolean` , Visual Basic uznaje za `True` mniejsze niż `False` . Jeśli typ liczbowy jest porównywany z `String` , Visual Basic próbuje skonwertować `String` do `Double` przed operacją. `Char`Operand lub `Date` można porównać tylko z innym operandem tego samego typu danych. Typ danych wynikowych jest zawsze `Boolean` .  
  
### <a name="bitwise-not-operator"></a>Operator not bitowego  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatora bitowego `Not` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Wartość logiczna|SByte|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
  
 Jeśli argumentem jest `Decimal` , `Single` ,, `Double` lub `String` , Visual Basic próbuje przekonwertować go do `Long` przed operacją, a typ danych wynik jest `Long` .  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operatory bitowe and, or i XOR  
 W poniższej tabeli przedstawiono typy danych wynikowych dla operatorów bitowe `And` , `Or` i `Xor` . Należy zauważyć, że ta tabela jest symetryczna; dla danej kombinacji typów danych operandu typ danych wynik jest taki sam, niezależnie od kolejności operandów.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Wartość logiczna|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`SByte`|SByte|SByte|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`Byte`|Wybierak|Wybierak|Byte|Wybierak|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Short`|Wybierak|Wybierak|Wybierak|Wybierak|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|UInteger —|Długo|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Długo|Długo|Długo|  
|`UInteger`|Długo|Długo|UInteger —|Długo|UInteger —|Długo|UInteger —|Długo|ULong|  
|`Long`|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Długo|Długo|  
|`ULong`|Długo|Długo|ULong|Długo|ULong|Długo|ULong|Długo|ULong|  
  
 Jeśli argumentem jest `Decimal` , `Single` ,, `Double` lub `String` , Visual Basic próbuje przekonwertować go do `Long` przed operacją, a typ danych wynik będzie taki sam, jak gdyby ten operand już należał `Long` .  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
 `&`Operator jest zdefiniowany tylko w celu łączenia `String` argumentów operacji. Visual Basic konwertuje każdy operand w razie potrzeby `String` przed operacją, a typ danych wynik jest zawsze `String` . Na potrzeby `&` operatora wszystkie konwersje na `String` są uznawane za rozszerzające, nawet jeśli `Option Strict` są `On` .  
  
 `Is`Operatory i `IsNot` wymagają, aby oba operandy były typu referencyjnego. `TypeOf`Wyrażenie... `Is` wymaga, aby pierwszy operand znajdował się w typie referencyjnym, a drugi operand jest nazwą typu danych. We wszystkich przypadkach typem danych wynik jest `Boolean` .  
  
 `Like`Operator jest zdefiniowany tylko dla dopasowania wzorca `String` argumentów operacji. Visual Basic próbuje przekonwertować każdy operand w razie potrzeby `String` przed operacją. Typ danych wynikowych jest zawsze `Boolean` .  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](../data-types/index.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory](index.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Operatory porównania](comparison-operators.md)
- [Option Strict — Instrukcja](../statements/option-strict-statement.md)
