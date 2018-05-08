---
title: '- — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="--operator-visual-basic"></a>- — Operator (Visual Basic)
Zwraca różnicę dwóch wyrażeń liczbowych lub wartość ujemną wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagany, chyba że `–` operator jest obliczenie wartości ujemnej. Dowolne wyrażenie liczbowe.  
  
## <a name="result"></a>Wynik  
 Wynik jest różnica między `expression1` i `expression2`, lub o zanegowaną wartość `expression1`.  
  
 Typ danych wyniku jest odpowiednie dla typów dane typu liczbowego `expression1` i `expression2`. Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe. Obejmuje to typy bez znaku i zmiennoprzecinkowych i `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 W pierwsze użycie składnią pokazana wcześniej `–` operator jest *binarne* operator arytmetyczny odejmowania różnicę między dwóch wyrażeń liczbowych.  
  
 W drugim użycia składnią pokazana wcześniej `–` operator jest *jednoargumentowy* operator negacji ujemną wartość wyrażenia. W tym sensie negacji składa się z cofania znak `expression1` tak, że wynik jest dodatnią Jeśli `expression1` jest ujemna.  
  
 Jeśli wyrażenie zwraca [nic](../../../visual-basic/language-reference/nothing.md), `–` operator traktuje ją jako zero.  
  
> [!NOTE]
>  `–` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz, jego zachowanie ponownie zdefiniowany. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `–` operatora, aby obliczyć i zwraca różnicę dwóch liczb, a następnie, aby odwrócić liczbą.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Po wykonaniu tych instrukcji `binaryResult` zawiera 124.45 i `unaryResult` zawiera –334.90.  
  
## <a name="see-also"></a>Zobacz też  
 [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
