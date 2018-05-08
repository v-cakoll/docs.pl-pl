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
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>\ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wynik liczby całkowitej.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynik jest iloraz liczb całkowitych z `expression1` rozdzielonych `expression2`, które odrzuca wszystkie pozostałe i zachowuje całkowitą część. Jest to nazywane *obcięcie*.  
  
 Typ danych wyniku jest odpowiednie dla typów dane typu liczbowego `expression1` i `expression2`. Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Zwraca iloraz pełnego, który zachowuje reszta w część ułamkowa.  
  
## <a name="remarks"></a>Uwagi  
 Przed wykonaniem podziału, Visual Basic próbuje przekonwertować zmiennoprzecinkowe wyrażenie liczbowe, aby `Long`. Jeśli `Option Strict` jest `On`, wystąpi błąd kompilatora. Jeśli `Option Strict` jest `Off`, <xref:System.OverflowException> jest możliwe, jeśli wartość jest poza zakresem [typu danych Long](../../../visual-basic/language-reference/data-types/long-data-type.md). Konwersja do `Long` jest również podlegają *zaokrąglenie do zaokrąglania*. Aby uzyskać więcej informacji, zobacz "Ułamkowych części" w [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Jeśli `expression2` daje w wyniku wartość 0, `\` zgłasza operator <xref:System.DivideByZeroException> wyjątku. Dotyczy to wszystkich typów danych numerycznych argumenty operacji.  
  
> [!NOTE]
>  `\` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `\` operatora, aby wykonać dzielenie liczby całkowitej. Wynik jest liczba całkowita, która reprezentuje iloraz liczb całkowitych z dwóch argumentów operacji pozostałych odrzucone.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 Wyrażenia w poprzednim przykładzie zwracają wartości 2, 3, 33 i -22, odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
