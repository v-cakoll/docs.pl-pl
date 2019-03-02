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
ms.openlocfilehash: 7d9b02a9c997ffcfdd61e277a6ed3779d8821831
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202460"
---
# <a name="-operator-visual-basic"></a>/ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wynik zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
 `expression2`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynikiem jest pełna iloraz `expression1` podzielona przez `expression2`, włączając wszelkie pozostałe.  
  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych, co powoduje resztę.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych wynik zależy od typów argumentów. W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.  
  
|Argumentami o typach danych|Typ danych wyniku|  
|------------------------|----------------------|  
|Oba wyrażenia są integralnymi typami danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Jedno wyrażenie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) — typ danych, a druga nie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Jedno wyrażenie jest [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — typ danych, a druga nie jest [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md) lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Albo wyrażenie jest [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — typ danych|`Double`|  
  
 Przed wykonaniem dzielenia rozszerzone do dowolnego typu całkowitego wyrażeń liczbowych `Double`. Jeśli przypiszesz wynik do typu liczby całkowitej danych, Visual Basic stara się przekonwertować wynik `Double` do tego typu. Może zgłosić wyjątek, jeśli wynik nie mieści się w tym typie. W szczególności zobacz "Próba dzielenia przez Zero" na tej stronie pomocy.  
  
 Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Jeśli `expression2` osiągnie wartość zero, `/` operator zachowuje się inaczej dla różnych argumentami o typach danych. W poniższej tabeli przedstawiono możliwe zachowania.  
  
|Argumentami o typach danych|Zachowanie Jeśli `expression2` wynosi zero|  
|------------------------|---------------------------------------|  
|Zmiennoprzecinkowe (`Single` lub `Double`)|Zwraca infinity (<xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity>), lub <xref:System.Double.NaN> (nie liczba) Jeśli `expression1` również wynosi zero|  
|`Decimal`|Zgłasza wyjątek <xref:System.DivideByZeroException>|  
|Całkowite (podpisane lub niepodpisane)|Próba konwersji do typu całkowitego zgłasza <xref:System.OverflowException> ponieważ typów całkowitych nie może akceptować <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, lub <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `/` operator przeprowadzić dzielenia liczb zmiennopozycyjnych. Wynik jest równy ilorazowi dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Wyrażenia w poprzednim przykładzie wartości zwracanych z 2.5 i 3.333333. Należy pamiętać, że wynik zawsze zmiennoprzecinkowych (`Double`), nawet jeśli oba operandy są stałe całkowite.  
  
## <a name="see-also"></a>Zobacz także
- [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Typy danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
