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
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401514"
---
# <a name="mod-operator-visual-basic"></a>Mod — operator (Visual Basic)

Dzieli dwie liczby i zwraca tylko resztę.

## <a name="syntax"></a>Składnia

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Części

`result` \
Wymagany. Dowolna zmienna lub właściwość numeryczna.

`number1` \
Wymagany. Dowolne wyrażenie liczbowe.

`number2` \
Wymagany. Dowolne wyrażenie liczbowe.

## <a name="supported-types"></a>Obsługiwane typy

Wszystkie typy liczbowe. Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .

## <a name="result"></a>Wynik

Wynik jest resztą po `number1` poddzieleniu przez `number2` . Na przykład wyrażenie `14 Mod 4` ma wartość 2.

> [!NOTE]
> Istnieje różnica między *resztą* i *modulo* w postaci matematyki z różnymi wynikami dla liczb ujemnych. `Mod`Operator w Visual Basic, `op_Modulus` operator .NET Framework i źródłowa instrukcja [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il All wykonują resztę operacji.

Wynik `Mod` operacji zachowuje znak dywidendy, `number1` a więc może być dodatnia lub ujemna. Wynik jest zawsze z zakresu (- `number2` , `number2` ), z wyłączeniem. Przykład:

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

Jeśli `number1` lub `number2` jest wartością zmiennoprzecinkową, zwracana jest pozostała część podziału zmiennoprzecinkowego. Typ danych wyniku to najmniejszy typ danych, który może zawierać wszystkie możliwe wartości wynikające z dzielenia z typami danych `number1` i `number2` .

Jeśli `number1` lub `number2` zwróci wartość [Nothing](../nothing.md), jest traktowany jako zero.

Operatory pokrewne obejmują następujące elementy:

- [Operator \ (Visual Basic)](integer-division-operator.md) zwraca iloraz całkowity dzielenia. Na przykład wyrażenie `14 \ 4` ma wartość 3.

- [Operator/(Visual Basic)](floating-point-division-operator.md) zwraca pełny iloraz, łącznie z resztą, jako liczbę zmiennoprzecinkową. Na przykład wyrażenie `14 / 4` ma wartość 3,5.

## <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero

Jeśli `number2` wartość jest równa zero, zachowanie `Mod` operatora zależy od typu danych operandów:

- <xref:System.DivideByZeroException>W przypadku, gdy `number2` nie można określić w czasie kompilacji i generuje błąd czasu kompilacji, jeśli wartość `BC30542 Division by zero occurred while evaluating this expression` `number2` jest szacowana na zero w czasie kompilacji.
- Podział liczby zmiennoprzecinkowej zwraca <xref:System.Double.NaN?displayProperty=nameWithType> .

## <a name="equivalent-formula"></a>Odpowiednik formuły

Wyrażenie `a Mod b` jest równoważne jednej z następujących formuł:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Niedokładność zmiennoprzecinkowa

Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają precyzyjną reprezentację dziesiętną w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównywanie wartości i `Mod` operator. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Przeciążenie

`Mod`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura mogą definiować jego zachowanie. Jeśli Twój kod odnosi się `Mod` do wystąpienia klasy lub struktury, która zawiera takie Przeciążenie, należy poznać jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Przykład

Poniższy przykład używa operatora, `Mod` Aby podzielić dwie liczby i zwrócić tylko resztę. Jeśli liczba jest liczbą zmiennoprzecinkową, wynik jest liczbą zmiennoprzecinkową, która reprezentuje resztę.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje potencjalną niedokładność argumentów operacji zmiennoprzecinkowych. W pierwszej instrukcji operandy są `Double` i 0,2 to nieskończonie powtarzające się ułamek binarny z przechowywaną wartością 0.20000000000000001. W drugiej instrukcji znak typu literału `D` wymusza oba operandy do `Decimal` , i 0,2 ma dokładną reprezentację.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Rozwiązywanie problemów związanych z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ — Operator (Visual Basic)](integer-division-operator.md)
