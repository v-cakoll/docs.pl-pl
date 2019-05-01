---
title: '\ — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 1753199e2ecf3f156b90d8c0a5cacd672397260d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013559"
---
# <a name="-operator-visual-basic"></a>\ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wyniku liczby całkowitej.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
 `expression2`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynik jest równy ilorazowi całkowitą `expression1` podzielona przez `expression2`, która odrzuca wszystkie pozostałe i zachowuje tylko część całkowitą. Jest to nazywane *obcięcie*.  
  
 Typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) zwraca pełny iloraz, która zachowuje reszta w ułamkową część.  
  
## <a name="remarks"></a>Uwagi  
 Przed wykonaniem instrukcji podziału, Visual Basic stara się przekonwertować dowolne wyrażenie numeryczne zmiennoprzecinkowych aby `Long`. Jeśli `Option Strict` jest `On`, występuje błąd kompilatora. Jeśli `Option Strict` jest `Off`, <xref:System.OverflowException> jest możliwe, jeśli wartość jest poza zakresem [Long — typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md). Konwersja na `Long` jest również podlegają *banker przez zaokrąglenie*. Aby uzyskać więcej informacji, zobacz "Części ułamkowych" w [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Jeśli `expression2` osiągnie wartość zero, `\` zgłasza operator <xref:System.DivideByZeroException> wyjątku. Ta zasada obowiązuje dla wszystkich typów liczbowych operandu.  
  
> [!NOTE]
>  `\` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `\` operatora, aby wykonać dzielenie liczby całkowitej. Wynik jest liczbą całkowitą reprezentującą iloraz liczb całkowitych o dwa operandy z pozostałą odrzucone.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Wyrażenia w poprzednim przykładzie zwracają wartości 2, 3, 33 i -22, odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
