---
title: / — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 238c062b2dd0744ba96cf9ba8591c0ef39f81bb3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592194"
---
# <a name="-operator-visual-basic"></a>/ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynikiem jest pełny iloraz `expression1` podzielona przez `expression2`, w tym wszystkie pozostałe.  
  
 [Operator \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) zwraca iloraz całkowity, który porzuca resztę.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych wyniku zależy od typów operandów. W poniższej tabeli przedstawiono sposób określania typu danych wyniku.  
  
|Typy danych operandu|Typ danych wynikowych|  
|------------------------|----------------------|  
|Oba wyrażenia są typami danych całkowitych[(](../../../visual-basic/language-reference/data-types/sbyte-data-type.md) [bajty, Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótkie](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Jedno wyrażenie jest [pojedynczym](../../../visual-basic/language-reference/data-types/single-data-type.md) typem danych, a drugi nie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Jedno wyrażenie jest typu danych [dziesiętnych](../../../visual-basic/language-reference/data-types/decimal-data-type.md) , a drugi nie jest [pojedynczym](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [podwójnym](../../../visual-basic/language-reference/data-types/double-data-type.md) .|`Decimal`|  
|Jedno wyrażenie jest [podwójnym](../../../visual-basic/language-reference/data-types/double-data-type.md) typem danych|`Double`|  
  
 Przed wykonaniem dzielenia wszystkie całkowite wyrażenia liczbowe są rozszerzane do `Double`. Jeśli zostanie przypisany wynik do typu danych całkowitych, Visual Basic próbuje skonwertować wynik z `Double` do tego typu. Może zgłosić wyjątek, jeśli wynik nie mieści się w danym typie. W szczególności Zobacz "Próba dzielenia przez zero" na tej stronie pomocy.  
  
 Jeśli `expression1` lub`expression2` zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero  
 Jeśli wartość `expression2` jest równa zero, operator `/` zachowuje się inaczej dla różnych typów danych operandu. W poniższej tabeli przedstawiono możliwe zachowania.  
  
|Typy danych operandu|Zachowanie, jeśli `expression2` wynosi zero|  
|------------------------|---------------------------------------|  
|Zmiennoprzecinkowe (`Single` lub `Double`)|Zwraca nieskończoność (<xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>) lub <xref:System.Double.NaN> (nie liczbę), jeśli `expression1` jest również równa zero|  
|`Decimal`|Zgłasza <xref:System.DivideByZeroException>|  
|Całka (ze znakiem lub bez znaku)|Próba konwersji z powrotem na typ całkowity zgłasza <xref:System.OverflowException>, ponieważ typy całkowite nie mogą akceptować <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity> lub <xref:System.Double.NaN>|  
  
> [!NOTE]
> Operator `/` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład używa operatora `/` do wykonywania dzielenia zmiennoprzecinkowego. Wynik jest ilorazem dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Wyrażenia w poprzednim przykładzie zwracają wartości 2,5 i 3,333333. Należy zauważyć, że wynik jest zawsze zmiennoprzecinkowy (`Double`), mimo że oba operandy są stałymi całkowitymi.  
  
## <a name="see-also"></a>Zobacz także

- [Operator/= (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Typy danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
