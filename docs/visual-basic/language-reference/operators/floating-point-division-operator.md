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
ms.openlocfilehash: 17eb3eddfae3cf7c818514a2fee20f646876a6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>/ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynik jest pełna iloraz `expression1` podzielona przez `expression2`, w tym wszelkie pozostałe.  
  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych, co powoduje resztę.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych w wyniku zależy od typów argumenty operacji. W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.  
  
|Argument operacji typy danych|Typ danych wyników|  
|------------------------|----------------------|  
|Oba wyrażenia są typy całkowite danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długi](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Jedno wyrażenie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) — typ danych, a druga nie jest [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Jedno wyrażenie jest [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — typ danych, a druga nie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Jedno z wyrażeń ma [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md) — typ danych|`Double`|  
  
 Przed wykonaniem dzielenia rozszerzone są wszystkie wartości całkowitych wyrażenia liczbowego, tak aby `Double`. Jeśli Przypisz wynik do typu całkowitego danych, Visual Basic próbuje przekonwertować wynik `Double` dla tego typu. To Zgłoś wyjątek, jeśli wynik nie mieści się w danym typie. Na tej stronie pomocy, w szczególności, zobacz "Próba dzielenia przez Zero".  
  
 Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Jeśli `expression2` daje w wyniku wartość 0, `/` operator zależy od operand różne typy danych. W poniższej tabeli przedstawiono możliwe zachowania.  
  
|Argument operacji typy danych|Zachowanie Jeśli `expression2` wynosi zero|  
|------------------------|---------------------------------------|  
|Zmiennoprzecinkowe (`Single` lub `Double`)|Zwraca infinity (<xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>), lub <xref:System.Double.NaN> (nie liczba) Jeśli `expression1` również wynosi zero|  
|`Decimal`|Zgłasza wyjątek <xref:System.DivideByZeroException>|  
|Typy całkowite (podpisane lub bez znaku)|Próba konwersji do typu całkowitego zgłasza <xref:System.OverflowException> ponieważ typy całkowite nie akceptuje <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, lub <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `/` operatora, aby wykonać dzielenia liczb zmiennoprzecinkowych. Wynik jest równy ilorazowi dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Wyrażenia w poprzednim przykładzie zwracać wartości 2.5 i 3.333333. Należy pamiętać, że wynik zawsze liczb zmiennoprzecinkowych (`Double`), nawet jeśli obydwa argumenty operacji są stałe całkowite.  
  
## <a name="see-also"></a>Zobacz też  
 [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [Typy danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
