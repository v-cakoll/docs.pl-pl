---
title: "Typy danych wyników operatora (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61e8fb785830152acfd7e8e2e1784294053ac66e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-of-operator-results-visual-basic"></a>Typy danych wyników operatora (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Określa typ danych wyniku na podstawie typów danych z argumentów operacji. W niektórych przypadkach może to być typ dane z większego zakresu niż którykolwiek argument operacji.  
  
## <a name="data-type-ranges"></a>Zakresy typu danych  
 Zakresy typów danych w kolejności od wartości najmniejszej do największej, są następujące:  
  
-   [Wartość logiczna](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dwa możliwe wartości  
  
-   [SByte —](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 wartości całkowitych  
  
-   [Krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65 536 (6.5... E + 4) możliwe wartości całkowitych  
  
-   [Liczba całkowita](../../../visual-basic/language-reference/data-types/integer-data-type.md), [uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) możliwe wartości całkowitych  
  
-   [Długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) możliwe wartości całkowitych  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1.5... E + 29 możliwych wartości całkowitych na wartości, maksymalny zakres 7,9... E + 28 (wartość bezwzględna)  
  
-   [Pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) — maksymalny zakres 3.4 w... E + 38 (wartość bezwzględna)  
  
-   [Podwójna](../../../visual-basic/language-reference/data-types/double-data-type.md) — maksymalny zakres 1.7 w... E + 308 (wartość bezwzględna)  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , zobacz [typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Jeśli argument operacji daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] operatorów arytmetycznych traktować go jako zero.  
  
## <a name="decimal-arithmetic"></a>Decimal arytmetyczne  
 Należy pamiętać, że [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — typ danych nie jest zmiennoprzecinkowe ani liczby całkowitej.  
  
 Jeśli którykolwiek argument operacji z `+`, `–`, `*`, `/`, lub `Mod` operacji `Decimal` , a drugi nie `Single` lub `Double`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rozszerzenie argument operacji do `Decimal`. Wykonuje operację w `Decimal`, i jest typu danych `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Zmiennoprzecinkowe operacje arytmetyczne  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wykonuje większość zmiennoprzecinkowe operacje arytmetyczne w [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md), który jest najbardziej wydajnym danych typu dla takich operacji. Jednak jeśli jest jeden operand [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) , a drugi nie `Double`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wykonuje operację w `Single`. Rozszerzenie go każdy argument odpowiednio do typu odpowiednie dane przed operacją, a wynik zawiera tego typu danych.  
  
### <a name="-and--operators"></a>/ i ^ operatory  
 `/` Operator jest zdefiniowana tylko dla [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md), i [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md) typów danych. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]rozszerzenie każdy argument odpowiednio do typu odpowiednie dane przed operacji, a wynik jest tego typu danych.  
  
 W poniższej tabeli przedstawiono wyniki typów danych `/` operatora. Należy pamiętać, że ta tabela symetrycznego; dla danego kombinację typów danych argumentu operacji typu danych jest taka sama niezależnie od Kolejność argumentów operacji.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Dowolnego typu Liczba całkowita|  
|`Decimal`|Wartość dziesiętna|Single|Double|Wartość dziesiętna|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Dowolnego typu Liczba całkowita|Wartość dziesiętna|Single|Double|Double|  
  
 `^` Operator jest zdefiniowana tylko dla `Double` — typ danych. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]rozszerzenie każdy argument operacji niezbędny do `Double` przed operacji, a wynik jest zawsze typu danych `Double`.  
  
## <a name="integer-arithmetic"></a>Operacja arytmetyczna liczba całkowita  
 Typ danych wyniku operacji na wartościach całkowitych zależy od argumenty typów danych. Ogólnie rzecz biorąc [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] korzysta z następujących zasad określania typu danych:  
  
-   Jeśli obydwa argumenty operacji operatora binarnego mają taki sam typ danych, wynik zawiera tego typu danych. Wyjątkiem jest `Boolean`, która wymusza na `Short`.  
  
-   Jeśli należy operand bez znaku z argumentem podpisem, wynik zawiera poziomu typu ze znakiem z co najmniej duży zakres jako którykolwiek argument operacji.  
  
-   W przeciwnym razie wynik ma zazwyczaj większy z dwóch typów danych argumentu operacji.  
  
 Należy pamiętać, że typu danych nie może być taka sama jak albo typem danych argumentu operacji.  
  
> [!NOTE]
>  Typ danych wyników nie zawsze jest wystarczająco duży do przechowywania wszystkich możliwych wartości wynikające z operacji. <xref:System.OverflowException> Wyjątek może wystąpić, jeśli wartość jest za duża dla typu danych.  
  
### <a name="unary--and--operators"></a>Jednoargumentowy + i — operatory  
 W poniższej tabeli przedstawiono wyniki typy danych dla dwóch operatory jednoargumentowe, `+` i `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Jednoargumentowe`+`|krótki|SByte|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|Jednoargumentowe`–`|krótki|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|Wartość dziesiętna|  
  
### <a name="-and--operators"></a><\<i >> operatorów  
 W poniższej tabeli przedstawiono wyniki typy danych dla dwóch operatory przesunięcia bitowego, `<<` i `>>`. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]traktuje każdy bit-shift operatora jako operatora jednoargumentowego na jego lewy operand (wzorca bitowego lekkie).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|krótki|SByte|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
  
 Jeśli lewy operand jest `Decimal`, `Single`, `Double`, lub `String`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] próbuje przekonwertować go na `Long` przed operacji i wynikiem jest typ danych `Long`. Prawy argument operacji (liczba pozycji bitowe przesunięcie) musi być `Integer` lub typ rozszerzająca do `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binarny +, -, * i operatory Mod  
 W poniższej tabeli przedstawiono wyniki typów dla pliku binarnego `+` i `–` operatory i `*` i `Mod` operatorów. Należy pamiętać, że ta tabela symetrycznego; dla danego kombinację typów danych argumentu operacji typu danych jest taka sama niezależnie od Kolejność argumentów operacji.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|krótki|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|Wartość dziesiętna|  
|`SByte`|SByte|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|Wartość dziesiętna|  
|`Byte`|krótki|krótki|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Short`|krótki|krótki|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|Wartość dziesiętna|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długa|długa|Wartość dziesiętna|  
|`UInteger`|długa|długa|Uinteger —|długa|Uinteger —|długa|Uinteger —|długa|ULong|  
|`Long`|długa|długa|długa|długa|długa|długa|długa|długa|Wartość dziesiętna|  
|`ULong`|Wartość dziesiętna|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|Wartość dziesiętna|ULong|  
  
### <a name="-operator"></a>\ — Operator  
 W poniższej tabeli przedstawiono wyniki typów danych `\` operatora. Należy pamiętać, że ta tabela symetrycznego; dla danego kombinację typów danych argumentu operacji typu danych jest taka sama niezależnie od Kolejność argumentów operacji.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|krótki|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`SByte`|SByte|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`Byte`|krótki|krótki|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Short`|krótki|krótki|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`UInteger`|długa|długa|Uinteger —|długa|Uinteger —|długa|Uinteger —|długa|ULong|  
|`Long`|długa|długa|długa|długa|długa|długa|długa|długa|długa|  
|`ULong`|długa|długa|ULong|długa|ULong|długa|ULong|długa|ULong|  
  
 Jeśli którykolwiek argument operacji z `\` operator jest [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md), lub [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] próbuje przekonwertować go na [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) przed operacji i wynikiem jest typ danych `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relacyjnych i operatory porównania  
 Typ wyniku danych relacyjnych operacji (`=`, `<>`, `<`, `>`, `<=`, `>=`) jest zawsze `Boolean` [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md). To samo dotyczy operacji logicznych (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` argumentów operacji.  
  
 Typ danych wynik operacji logicznych zależy od argumenty typów danych. Należy pamiętać, że `AndAlso` i `OrElse` są definiowane tylko w przypadku `Boolean`, i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] konwertuje każdy argument operacji niezbędny do `Boolean` przed wykonaniem tej operacji.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<=, a > = operatory  
 Jeśli oba argumenty operacji są `Boolean`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uwzględnia `True` za mniej niż `False`. Jeśli typ liczbowy jest porównywana z `String`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] próbuje przekonwertować `String` do `Double` przed operacją. A `Char` lub `Date` argument można porównać tylko z innego operand typu danych. Typ danych wyniku jest zawsze `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Operator Not — Operator  
 W poniższej tabeli przedstawiono wyniki typów danych dla operatora testu koniunkcji `Not` operatora.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
  
 Jeśli argument jest `Decimal`, `Single`, `Double`, lub `String`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] próbuje przekonwertować go na `Long` przed operacji i wynikiem jest typ danych `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operator i, lub i operatory Xor  
 W poniższej tabeli przedstawiono wyniki typów danych dla operatora testu koniunkcji `And`, `Or`, i `Xor` operatorów. Należy pamiętać, że ta tabela symetrycznego; dla danego kombinację typów danych argumentu operacji typu danych jest taka sama niezależnie od Kolejność argumentów operacji.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`SByte`|SByte|SByte|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`Byte`|krótki|krótki|Byte|krótki|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Short`|krótki|krótki|krótki|krótki|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`UShort`|Liczba całkowita|Liczba całkowita|UShort|Liczba całkowita|UShort|Liczba całkowita|Uinteger —|długa|ULong|  
|`Integer`|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|Liczba całkowita|długa|długa|długa|  
|`UInteger`|długa|długa|Uinteger —|długa|Uinteger —|długa|Uinteger —|długa|ULong|  
|`Long`|długa|długa|długa|długa|długa|długa|długa|długa|długa|  
|`ULong`|długa|długa|ULong|długa|ULong|długa|ULong|długa|ULong|  
  
 Jeśli argument operacji jest `Decimal`, `Single`, `Double`, lub `String`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] próbuje przekonwertować go na `Long` przed operacji, a dane wynikowe typ jest taki sam tak, jakby już tym argumentem `Long`.  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
 `&` Operator jest zdefiniowana tylko dla łączenia z `String` argumentów operacji. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Konwertuje każdy argument operacji niezbędny do `String` przed operacji, a wynik jest zawsze typu danych `String`. Na potrzeby `&` operator, wszystkie konwersje do `String` są uważane za rozszerzenia, nawet jeśli `Option Strict` jest `On`.  
  
 `Is` i `IsNot` operatory wymagają oba argumenty typu odwołania. `TypeOf`... `Is` wyrażenie wymaga pierwszy argument typu odwołania, a drugi operand Nazwa typu danych. We wszystkich tych przypadkach dane wynikowe jest typu `Boolean`.  
  
 `Like` Zdefiniowano operator tylko do dopasowywania do wzorca z `String` argumentów operacji. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]próbuje przekonwertować każdy argument operacji niezbędny do `String` przed operacją. Typ danych wyniku jest zawsze `Boolean`.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory](../../../visual-basic/language-reference/operators/index.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
