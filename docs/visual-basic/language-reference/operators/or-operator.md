---
title: "Or — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c9429eb2bdeb86bfa73786433231fdc22a230d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="or-operator-visual-basic"></a>Or — Operator (Visual Basic)
Dokonuje logicznego rozłączenia dwóch `Boolean` wyrażeń lub bitowego rozłączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego. Aby uzyskać `Boolean` porównania, `result` jest łączną sumę logiczną na dwóch `Boolean` wartości. Dla Operacje bitowe `result` włącznie bitowego rozłączenia dwóch wzorców liczbowych bit reprezentujący wartość liczbową.  
  
 `expression1`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla `Boolean` porównania, `result` jest `False` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` obliczać `False`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  W `Boolean` porównania, `Or` operator zawsze ocenia oba wyrażenia, które mogą obejmować tworzenie wywołań procedur. [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `True`, następnie `expression2` nie jest obliczane.  
  
 Dla Operacje bitowe `Or` operator przeprowadza porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wykonywania.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego `Boolean` wyrażenie i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje operacji.  
  
 Aby uzyskać `Boolean` jest typ danych w wyniku porównania, `Boolean`. Porównanie bitowe, typu danych jest typ liczbowy odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i operator porównania" [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Or` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na dwóch wyrażeniach. Wynik jest `Boolean` wartość wskazującą, czy jest jeden z dwóch wyrażeń `True`.  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 Powyższy przykład produkuje wyniki `True`, `True`, i `False`odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na poszczególnych bitów dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli albo odpowiednich bitów w operandy jest ustawiona na 1.  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 Powyższy przykład produkuje wyników 10, 14 i 14, odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [OrElse — Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
