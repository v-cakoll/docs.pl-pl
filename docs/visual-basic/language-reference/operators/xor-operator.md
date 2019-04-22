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
ms.openlocfilehash: 0cba3a995fb1ab774c8a5308e58f0b6905fc23f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827071"
---
# <a name="xor-operator-visual-basic"></a>Xor — Operator (Visual Basic)
Wykonuje logiczne wykluczenie na dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` lub zmienna liczbowych. Dla porównania logiczna `result` jest wykluczenie logiczne (wyłączne rozłączenie logiczne) z dwóch `Boolean` wartości. W przypadku operacji bitowej `result` jest wartością liczbową, reprezentujący bitowe wykluczenie dwóch wzorców bitowych liczbowych (wyłączne bitowego rozłączenia).  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla porównania logiczna `result` jest `True` tylko wtedy, gdy dokładnie jeden z `expression1` i `expression2` daje w wyniku `True`. Oznacza to, że tylko wtedy, gdy `expression1` i `expression2` oceny do przeciwnego `Boolean` wartości. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Wartość logiczna porównania `Xor` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury. Nie ma odpowiednika short-circuiting do `Xor`, ponieważ wynik zależy od zawsze oba operandy. Aby uzyskać *zwarcie* operatorów logicznych, zobacz [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) i [orelse — Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 W przypadku operacji bitowej `Xor` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bitu w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
 Na przykład 5 `Xor` 3 to 6. Aby zobaczyć, dlaczego jest to tak, Konwertuj do ich reprezentacji binarnych, 101 i 011 5 i 3. Następnie użyj poprzedniej tabeli, aby określić, że 101 Xor 011 wynosi 110, czyli reprezentacja binarna liczba dziesiętna 6.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.  
  
 Aby uzyskać `Boolean` jest typ danych wyniku porównania, `Boolean`. Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Xor` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Xor` operatora wykonywanego wykluczenie logiczne (rozłączenie logiczne wyłączne) na dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy jest dokładnie jedno wyrażenie `True`.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Poprzedni przykład generuje wyniki `False`, `True`, i `False`, odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Xor` operatora wykonywanego wykluczenie logiczne (rozłączenie logiczne wyłączne) na poszczególnych bity dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli dokładnie jeden z odpowiednich bitów w operandów jest ustawiona na 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Poprzedni przykład generuje wyniki, 2, 12 i 14, odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
