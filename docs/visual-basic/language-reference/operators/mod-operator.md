---
title: Mod — Operator (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: f1334ff7aa07f49139bfe684746ae9cc3cf8087c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663169"
---
# <a name="mod-operator-visual-basic"></a>Mod — operator (Visual Basic)
Dzieli dwie liczby i zwraca tylko resztę z dzielenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Części  
 `number1`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
 `number2`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkich typów liczbowych. Obejmuje to typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.  
  
## <a name="result"></a>Wynik

Wynik jest resztę po `number1` jest dzielona przez `number2`. Na przykład, wyrażenie `14 Mod 4` daje w wyniku 2.  

> [!NOTE]
> Istnieje różnica pomiędzy *resztę* i *modulo* w matematyce, przy użyciu różne wyniki dla liczb ujemnych. `Mod` Operatora w języku Visual Basic .NET Framework `op_Modulus` operatora i podstawowych [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) instrukcja IL wykonywać wszystkie operacje resztę.

Wynik `Mod` operacja zachowuje znak dzielna `number1`, a więc może być dodatnia lub ujemna. Wynik jest zawsze w zakresie (-`number2`, `number2`), wyłączności. Na przykład:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Uwagi  
 Jeśli `number1` lub `number2` jest wartość zmiennoprzecinkowa jest zwracana zmiennoprzecinkową resztę z dzielenia. Typ danych wyniku jest najmniejszego typu danych, który może pomieścić wszystkich możliwych wartości, które wynikają z dzielenia z typami danych `number1` i `number2`.  
  
 Jeśli `number1` lub `number2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.  
  
 Operatory powiązane są następujące:  
  
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych z dzielenia. Na przykład, wyrażenie `14 \ 4` daje w wyniku 3.  
  
- [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) zwraca pełny iloraz, w tym resztę, jako liczba zmiennoprzecinkowa. Na przykład, wyrażenie `14 / 4` daje w wyniku 3.5.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero  
 Jeśli `number2` daje w wyniku wartość zero, zachowanie `Mod` operator zależy od typu danych operandu. Zgłasza dzielenia liczby całkowitej <xref:System.DivideByZeroException> wyjątku. Zwraca dzielenia liczb zmiennopozycyjnych <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Równoważne formuły  
 Wyrażenie `a Mod b` odpowiada jednej z następujących formuł:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Zmiennoprzecinkowe niedokładności  
 Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają precyzyjną formie dziesiętnej w pamięci. Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Mod` Operator może być *przeciążone*, co oznacza, że klasy lub struktury zdefiniować ponownie jego zachowanie. Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która obejmuje takie przeciążenia, upewnij się, zrozumieć zachowania zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Mod` operator dzielenia dwóch liczb i zwraca tylko resztę. Jeśli albo liczba jest liczba zmiennoprzecinkowa, wynik jest liczba zmiennoprzecinkowa, który reprezentuje resztę.  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano potencjał niedokładności argumentów operacji zmiennoprzecinkowej. W pierwszej instrukcji argumenty operacji są `Double`, a 0.2 jest nieskończenie powtarzające się ułamek binarne, przy użyciu przechowywaną wartość 0.20000000000000001. W drugiej instrukcji literału wpisz znak `D` wymusza oba operandy `Decimal`, i 0.2 jej reprezentacji dokładne.  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
