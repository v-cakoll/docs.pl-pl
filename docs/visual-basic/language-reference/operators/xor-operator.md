---
title: Xor — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 34d317da5d85127e371c2df7229e0f0873972f50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xor-operator-visual-basic"></a>Xor — Operator (Visual Basic)
Wykonuje logiczne wykluczenie na dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` lub zmienna numeryczna. Dla porównania Boolean `result` jest wykluczenie logiczne (wyłączne rozłączenie logiczne) z dwóch `Boolean` wartości. Dla Operacje bitowe `result` wartość liczbową reprezentujący z bitowego wykluczenia dwa wzorce bit liczbowych (wyłączne z bitowego rozłączenia).  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla porównania Boolean `result` jest `True` tylko wtedy, gdy dokładnie jeden z `expression1` i `expression2` daje w wyniku `True`. Oznacza to, że tylko wtedy, gdy `expression1` i `expression2` oceny do przeciwnego `Boolean` wartości. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logiczna porównania `Xor` operator zawsze ocenia oba wyrażenia, które mogą obejmować tworzenie wywołań procedur. Nie ma odpowiednika short-circuiting do `Xor`, ponieważ wynik zależy od zawsze oba argumenty. Dla *zwarcie* operatorów logicznych, zobacz [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) i [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Dla Operacje bitowe `Xor` operator przeprowadza porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wykonywania.  
  
 Na przykład 5 `Xor` 3 to 6. Aby sprawdzić, dlaczego jest tak, Konwertuj na ich binarne oświadczenia 101 i 011 5 i 3. Następnie użyj poprzedniej tabeli, aby określić, że 101 Xor 011 jest 110, która jest binarna reprezentacja liczbę dziesiętną 6.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego `Boolean` wyrażenie i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje operacji.  
  
 Aby uzyskać `Boolean` jest typ danych w wyniku porównania, `Boolean`. Porównanie bitowe, typu danych jest typ liczbowy odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i operator porównania" [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Xor` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Xor` operatora, aby wykonać wykluczenie logiczne (rozłączenie logiczne wyłączne) na dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy jest dokładnie jedno z wyrażeń `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 Poprzedni przykład tworzy wyniki `False`, `True`, i `False`odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Xor` operatora, aby wykonać wykluczenie logiczne (rozłączenie logiczne wyłączne) na poszczególnych bitów dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli dokładnie jeden z odpowiednich bitów w operandy jest ustawiona na 1.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 Poprzedni przykład tworzy odpowiednio wyniki z 2, 12 i 14.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
