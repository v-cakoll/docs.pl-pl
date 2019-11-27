---
title: Mod — Operator
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
ms.openlocfilehash: b7552550d4b0496d6ad7ee76a7327054d544b874
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350920"
---
# <a name="mod-operator-visual-basic"></a>Mod — operator (Visual Basic)

Dzieli dwie liczby i zwraca tylko resztę.

## <a name="syntax"></a>Składnia

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Części

`result` \
Wymagana. Dowolna zmienna lub właściwość numeryczna.

`number1` \
Wymagana. Dowolne wyrażenie liczbowe.

`number2` \
Wymagana. Dowolne wyrażenie liczbowe.

## <a name="supported-types"></a>Obsługiwane typy

Wszystkie typy liczbowe. Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.

## <a name="result"></a>Wynik

Wynik jest resztą po poddzieleniu `number1` przez `number2`. Na przykład wyrażenie `14 Mod 4` ma wartość 2.

> [!NOTE]
> Istnieje różnica między *resztą* i *modulo* w postaci matematyki z różnymi wynikami dla liczb ujemnych. Operator `Mod` w Visual Basic, operator `op_Modulus` .NET Framework i źródłowa instrukcja [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il All wykonuje operację reszty.

Wynikiem operacji `Mod` jest zachowanie znaku dywidendy, `number1`, a więc może być dodatnia lub ujemna. Wynik jest zawsze z zakresu (-`number2`, `number2`), na wyłączność. Na przykład:

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

Jeśli `number1` lub `number2` jest wartością zmiennoprzecinkową, zwracana jest pozostała część podziału zmiennoprzecinkowego. Typ danych wyniku to najmniejszy typ danych, który może zawierać wszystkie możliwe wartości, wynikające z dzielenia z typami danych `number1` i `number2`.

Jeśli `number1` lub `number2` zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.

Operatory pokrewne obejmują następujące elementy:

- [Operator \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) zwraca iloraz całkowity dzielenia. Na przykład wyrażenie `14 \ 4` ma wartość 3.

- [Operator/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) zwraca pełny iloraz, łącznie z resztą, jako liczbę zmiennoprzecinkową. Na przykład wyrażenie `14 / 4` oblicza do 3,5.

## <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero

Jeśli `number2` ma wartość zero, zachowanie operatora `Mod` zależy od typu danych operandów:

- W przypadku gdy nie można ustalić `number2` w czasie kompilacji, w przypadku gdy w czasie kompilowania `number2` zostanie obliczony `BC30542 Division by zero occurred while evaluating this expression` błąd czasu kompilacji, w przypadku nieznanego podziału zostanie wygenerowany wyjątek <xref:System.DivideByZeroException>.
- Dzielenie zmiennoprzecinkowe zwraca <xref:System.Double.NaN?displayProperty=nameWithType>.

## <a name="equivalent-formula"></a>Odpowiednik formuły

Wyrażenie `a Mod b` jest równoważne z jedną z następujących formuł:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Niedokładność zmiennoprzecinkowa

Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają precyzyjną reprezentację dziesiętną w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i operator `Mod`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Przeciążenie

Operator `Mod` może być *przeciążony*, co oznacza, że Klasa lub struktura mogą definiować jego zachowanie. Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która zawiera takie Przeciążenie, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Przykład

Poniższy przykład używa operatora `Mod`, aby podzielić dwie liczby i zwrócić tylko resztę. Jeśli liczba jest liczbą zmiennoprzecinkową, wynik jest liczbą zmiennoprzecinkową, która reprezentuje resztę.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje potencjalną niedokładność argumentów operacji zmiennoprzecinkowych. W pierwszej instrukcji operandy są `Double`, a 0,2 to nieskończonie powtarzające się ułamek binarny z przechowywaną wartością 0.20000000000000001. W drugiej instrukcji znak typu literału `D` wymusza oba operandy do `Decimal`, a 0,2 ma dokładną reprezentację.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
