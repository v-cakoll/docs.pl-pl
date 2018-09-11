---
title: Operator % (odwołanie w C#)
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 9cd2f7ad3856feb34667686979c942ecb21887c2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266699"
---
# <a name="-operator-c-reference"></a>Operator % (odwołanie w C#)

Operator reszty `%` oblicza pozostałą po podzieleniu pierwszy argument operacji za drugim argumentem. Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `%` operatora. Gdy `%` jest przeciążona, [operator przypisania reszty](remainder-assignment-operator.md) `%=` jest również niejawnie przeciążona.

Wszystkie typy liczbowe obsługuje operator reszty.

## <a name="integer-remainder"></a>Pozostała liczba całkowita
  
Dla argumentów liczby całkowitej, wynik `a % b` wartość jest generowany przez `a - (a / b) * b`. Znak resztę różna od zera jest taka sama, jak w przypadku pierwszego operandu w poniższym przykładzie pokazano:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a>Zmiennoprzecinkową resztę

Dla [float](../keywords/float.md) i [double](../keywords/double.md) operandów, wynik `x % y` dla skończonego `x` i `y` jest wartością `z` tak, aby

- znak `z`, jeśli różna od zera, jest taka sama jak znak `x`;
- wartość bezwzględna `z` wartość jest generowany przez `|x| - n * |y|` gdzie `n` jest największa możliwa liczba całkowita, która jest mniejsza niż lub równa `|x| / |y|` i `|x|` i `|y|` są wartości bezwzględne dla `x` i `y`, odpowiednio.

Aby uzyskać informacje o zachowanie `%` operatora w przypadku argumentów operacji nieskończona, zobacz [operator reszty](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) części [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/index).

> [!NOTE]
> Ta metoda obliczeniowych reszta jest odpowiednikiem używanym dla liczby całkowitej argumentów, ale różni się od IEEE 754. Operacja Reminder, który jest zgodny z IEEE 754, należy użyć <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

W poniższym przykładzie pokazano zachowanie operator reszty dla `float` i `double` argumenty:

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

Należy pamiętać, błędy zaokrąglania, które mogą być skojarzone z typów zmiennoprzecinkowych.

Dla [dziesiętna](../keywords/decimal.md) argumentów operacji, operator reszty `%` jest odpowiednikiem [operator reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
