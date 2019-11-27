---
title: Xor, operator
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
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335406"
---
# <a name="xor-operator-visual-basic"></a>Xor — Operator (Visual Basic)
Wykonuje logiczne wykluczenie dwóch wyrażeń `Boolean` lub bitowego wykluczenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Dowolna `Boolean` lub zmienna numeryczna. W przypadku porównania logicznego `result` jest wykluczeniem logicznym (wyłączne odłączenie logiczne) dwóch `Boolean` wartości. W przypadku operacji bitowych `result` jest wartością liczbową reprezentującą wykluczenie bitowe (wyłączne rozłączenie bitowe) dwóch liczbowych wzorców bitowych.  
  
 `expression1`  
 Wymagana. Dowolne `Boolean` lub wyrażenie liczbowe.  
  
 `expression2`  
 Wymagana. Dowolne `Boolean` lub wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku porównania logicznego `result` jest `True`, jeśli dokładnie jeden z `expression1` i `expression2` jest obliczany jako `True`. To znaczy, jeśli i tylko wtedy, gdy `expression1` i `expression2` są oceniane jako przeciwległe wartości `Boolean`. W poniższej tabeli przedstawiono sposób określania `result`.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> W porównaniu wartości logicznej operator `Xor` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. Nie ma żadnych krótkich obwodów do `Xor`, ponieważ wynik zawsze zależy od obu operandów. Aby uzyskać *krótkie* operatory logiczne, zobacz [operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) i [operator OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 W przypadku operacji bitowych operator `Xor` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
 Na przykład 5 `Xor` 3 to 6. Aby sprawdzić, dlaczego jest to zrobione, przekonwertuj 5 i 3 na ich reprezentacje binarne, 101 i 011. Następnie użyj poprzedniej tabeli, aby określić, że 101 XOR 011 wynosi 110, czyli reprezentację binarną liczby dziesiętnej 6.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.  
  
 W przypadku porównania `Boolean` typ danych wyniku jest `Boolean`. W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`. Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `Xor` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `Xor` do wykonywania logicznego wykluczenia (wyłączne logiczne rozłączenie) w dwóch wyrażeniach. Wynikiem jest wartość `Boolean`, która reprezentuje, czy dokładnie jedno z wyrażeń jest `True`.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Poprzedni przykład generuje odpowiednio wyniki `False`, `True`i `False`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `Xor`, aby przeprowadzić wykluczenie logiczne (wyłączne odłączenie logiczne) na poszczególnych bitach dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiony, jeśli dokładnie jeden z odpowiednich bitów w operandach jest ustawiony na 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 W poprzednim przykładzie wyniki są odpowiednio 2, 12 i 14.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
