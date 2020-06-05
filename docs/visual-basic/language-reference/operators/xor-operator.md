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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406343"
---
# <a name="xor-operator-visual-basic"></a>Xor — Operator (Visual Basic)
Wykonuje logiczne wykluczenie dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolna `Boolean` lub zmienna numeryczna. W przypadku porównania logicznego `result` jest to logiczne wykluczenie (wyłączne odłączenie logiczne) dwóch `Boolean` wartości. W przypadku operacji bitowych `result` jest wartością liczbową, która reprezentuje wykluczenie bitowe (wyłączne rozłączenie bitowe) dwóch liczbowych wzorców bitowych.  
  
 `expression1`  
 Wymagany. `Boolean`Wyrażenie dowolne lub liczbowe.  
  
 `expression2`  
 Wymagany. `Boolean`Wyrażenie dowolne lub liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku porównania logicznego, `result` jest `True` if i tylko wtedy, gdy dokładnie jeden z `expression1` i jest `expression2` obliczany do `True` . To znaczy, jeśli i tylko wtedy, gdy `expression1` i `expression2` szacują wartości przeciwne `Boolean` . W poniższej tabeli przedstawiono sposób `result` określania.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> W porównaniu wartości logicznej `Xor` operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. Nie ma żadnych krótkich obwodów `Xor` , ponieważ wynik zawsze zależy od obu operandów. Aby uzyskać *krótkie* operatory logiczne, zobacz [operator AndAlso](andalso-operator.md) i [operator OrElse](orelse-operator.md).  
  
 W przypadku operacji bitowych `Xor` operator wykonuje bitowe porównanie identycznie ustawionych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w zależności od `result` poniższej tabeli.  
  
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
 Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False` ) i wykonuje operację bitową.  
  
 Dla `Boolean` porównania, typ danych wyniku `Boolean` . W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2` . Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Xor`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Xor` operatora do przeprowadzenia logicznego wykluczenia (wyłączne logiczne rozłączenie) w dwóch wyrażeniach. Wynik jest `Boolean` wartością, która reprezentuje, czy dokładnie jedno wyrażenie jest `True` .  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Poprzedni przykład daje wyniki `False` , `True` i `False` , odpowiednio.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Xor` operatora do wykonywania logicznego wykluczenia (wyłączne logiczne rozłączenie) w poszczególnych bitach dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiony, jeśli dokładnie jeden z odpowiednich bitów w operandach jest ustawiony na 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 W poprzednim przykładzie wyniki są odpowiednio 2, 12 i 14.  
  
## <a name="see-also"></a>Zobacz też

- [Operatory logiczne/bitowe (Visual Basic)](logical-bitwise-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
