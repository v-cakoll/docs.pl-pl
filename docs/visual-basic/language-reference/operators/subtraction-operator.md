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
ms.openlocfilehash: 1a5c47a2f1bc8a8b9e1b0263b90006a0e58e17bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830672"
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
 Wymagana. Dowolne wyrażenie numeryczne.  
  
 `expression2`  
 Wymagane, chyba że `–` operator obliczania wartości ujemnej. Dowolne wyrażenie numeryczne.  
  
## <a name="result"></a>Wynik  
 Wynik jest różnica między `expression1` i `expression2`, lub zanegowaną wartość `expression1`.  
  
 Typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkich typów liczbowych. Obejmuje to typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 W pierwsze użycie, które są wyświetlane w składni przedstawionej wcześniej `–` operator jest *binarne* operator odejmowania arytmetycznych, różnicy między dwóch wyrażeń liczbowych.  
  
 Użycie drugiej, wyświetlana w składni przedstawionej wcześniej `–` operator jest *jednoargumentowe* operator negacji ujemną wartość wyrażenia. W tym sensie negację składa się z cofania znak `expression1` tak, aby wynik jest dodatni Jeśli `expression1` jest ujemna.  
  
 Jeśli wyrażenie zwraca [nic](../../../visual-basic/language-reference/nothing.md), `–` operator traktuje ją jako zero.  
  
> [!NOTE]
>  `–` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `–` operator, aby obliczyć i zwracać różnicę między dwoma liczbami, a następnie do zanegowania liczbą.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Po wykonaniu tych instrukcji `binaryResult` zawiera 124.45 i `unaryResult` zawiera –334.90.  
  
## <a name="see-also"></a>Zobacz także

- [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
