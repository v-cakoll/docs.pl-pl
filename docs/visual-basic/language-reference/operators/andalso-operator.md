---
title: AndAlso — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 549d14cc35d285ac2e4a02a37dd201cc669c5627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="andalso-operator-visual-basic"></a>AndAlso — Operator (Visual Basic)
Wykonuje skrótowe połączenie logiczne dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`result`|Wymagana. Wszelkie `Boolean` wyrażenia. W rezultacie `Boolean` wynik porównania dwóch wyrażeń.|  
|`expression1`|Wymagana. Wszelkie `Boolean` wyrażenia.|  
|`expression2`|Wymagana. Wszelkie `Boolean` wyrażenia.|  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest określany jako *zwarcie* Jeśli skompilowanego kodu można pominąć obliczania jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynik pierwsze wyrażenie obliczane określa końcowego wyniku operacji, jest niepotrzebna można oszacować wyrażenia drugiego, ponieważ nie można zmienić wynik końcowy. Zwarcie może zwiększyć wydajność, jeśli pominięto wyrażenie jest złożony, czy obejmuje on wywołań procedur.  
  
 Jeśli oba wyrażenia mają `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nie jest oceniany)|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `AndAlso` Operator jest zdefiniowana tylko dla [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy argument operacji niezbędny do `Boolean` i wykonuje operację wyłącznie w `Boolean`. Przypisz wynik do typu liczbowego, Visual Basic przekonwertuje go z `Boolean` dla tego typu. Można to osiągnąć nieoczekiwane zachowanie. Na przykład `5 AndAlso 12` powoduje `–1` po konwersji na `Integer`.  
  
## <a name="overloading"></a>Przeciążenie  
 [i operatora](../../../visual-basic/language-reference/operators/and-operator.md) i [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury można zmienić ich zachowania, gdy argument operacji ma typ, który klasy lub struktury. Przeciążanie `And` i `IsFalse` operatory wpływa na działanie `AndAlso` operatora. Jeśli używa Twój kod `AndAlso` na klasę lub strukturę, która overloads `And` i `IsFalse`, trzeba koniecznie zapoznać się ich zachowanie ponownie zdefiniowany. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AndAlso` operatora, aby wykonać koniunkcję logiczną na dwóch wyrażeniach. Wynik jest `Boolean` wartość wskazującą, czy cały conjoined wyrażenie ma wartość true. Jeśli pierwsze wyrażenie jest `False`, drugie nie jest obliczane.  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 Powyższy przykład produkuje wyniki `True`, `False`, i `False`odpowiednio. Podczas obliczania `secondCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `False`. Jednak drugie wyrażenie jest obliczane w obliczeniach `thirdCheck`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Function` procedury, która przeszukuje dla danej wartości między elementami tablicy. Jeśli tablica jest pusta lub przekroczeniu długości tablicy `While` instrukcji nie sprawdza elementu tablicy względem wartości wyszukiwania.  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [And, operator](../../../visual-basic/language-reference/operators/and-operator.md)  
 [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
