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
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817126"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso — Operator (Visual Basic)
Wykonuje zwarcie logicznego połączenia dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`result`|Wymagana. Wszelkie `Boolean` wyrażenia. Wynik jest `Boolean` wynik porównania dwóch wyrażeń.|  
|`expression1`|Wymagana. Wszelkie `Boolean` wyrażenia.|  
|`expression2`|Wymagana. Wszelkie `Boolean` wyrażenia.|  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest nazywany *zwarcie* Jeśli skompilowany kod może obejść przedziały oceny jedno wyrażenie w zależności od wyniku innego wyrażenia. Jeśli wynik pierwsze wyrażenie obliczane określi ostateczny wynik operacji, nie ma potrzeby do oceny, drugie wyrażenie, ponieważ nie można zmienić, wynik końcowy. Zwarcie może poprawić wydajność, jeśli pominięto wyrażenie jest złożone, czy obejmuje wywołania procedur.  
  
 Jeśli oba wyrażenia mają `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nie oceniono)|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `AndAlso` Operator jest zdefiniowany tylko w przypadku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy argument konieczny do `Boolean` i wykonuje operację całkowicie w `Boolean`. Jeśli wynik jest przypisany do typu numerycznego, Visual Basic konwertuje go z `Boolean` do tego typu. Może to powodować nieoczekiwane zachowanie. Na przykład `5 AndAlso 12` skutkuje `–1` podczas konwersji na `Integer`.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operatora](../../../visual-basic/language-reference/operators/and-operator.md) i [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ, który klasy lub struktury. Przeciążanie `And` i `IsFalse` operatory wpływa na zachowanie `AndAlso` operatora. Jeśli kod używa `AndAlso` dla klasy lub struktury, która przeciążenia `And` i `IsFalse`, należy zrozumieć ich zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AndAlso` operator przeprowadzić logicznego połączenia dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy cały conjoined wyrażenie ma wartość true. Jeśli pierwsze wyrażenie jest `False`, drugi nie jest oceniany.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Poprzedni przykład generuje wyniki `True`, `False`, i `False`, odpowiednio. Podczas obliczania `secondCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `False`. Jednak drugie wyrażenie jest obliczane w obliczeniach kluczowych `thirdCheck`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Function` procedury, która wyszukuje danej wartości wśród elementów tablicy. Jeśli tablica jest pusta lub przekroczeniu długość tablicy `While` instrukcji Testuj elementu tablicy względem wartości wyszukiwania.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And, operator](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
