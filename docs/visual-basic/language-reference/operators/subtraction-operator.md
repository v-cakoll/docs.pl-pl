---
title: '- Operator'
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
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348225"
---
# <a name="--operator-visual-basic"></a>- — Operator (Visual Basic)
Zwraca różnicę między dwoma wyrażeniami liczbowymi lub wartością ujemną wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
expression1 – expression2
```
  
lub

```vb  
–expression1  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagany, chyba że operator `–` oblicza wartość ujemną. Dowolne wyrażenie liczbowe.  
  
## <a name="result"></a>Wynik  
 Wynikiem jest różnica między `expression1` i `expression2`lub Negacja wartości `expression1`.  
  
 Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2`. Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe. Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 W pierwszym użyciu pokazanym w pokazanej wcześniej składni operator `–` to *binarny* operator odejmowania arytmetycznego dla różnicy między dwoma wyrażeniami liczbowymi.  
  
 W drugim wykorzystaniu pokazanym wcześniej składni operator `–` jest operatorem *jednoargumentowym* operatora negacji dla wartości ujemnej wyrażenia. W tym sensie Negacja składa się z odwrócenia znaku `expression1`, aby wynik był dodatni, jeśli `expression1` jest ujemna.  
  
 Jeśli wyrażenie zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), operator `–` traktuje ją jako zero.  
  
> [!NOTE]
> Operator `–` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `–`, aby obliczyć i zwrócić różnicę między dwiema liczbami, a następnie Negate liczbę.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Po wykonaniu tych instrukcji `binaryResult` zawiera 124,45 i `unaryResult` Contains – 334,90.  
  
## <a name="see-also"></a>Zobacz także

- [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
