---
title: Operatory arytmetyczne - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują operacje mnożenie, dzielenie, pozostałą, dodawania i odejmowania za pomocą typów liczbowych.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: aaa6af8067707162a440ab69b46f08b612eae9b3
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545510"
---
# <a name="arithmetic-operators-c-reference"></a>Operatory arytmetyczne (C# odwołania)

Następujące operatory wykonywać operacji arytmetycznych na wartościach typy liczbowe:

- Jednoargumentowy [ `++` (inkrementacja)](#increment-operator-), [ `--` (dekrementacja)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators), i [ `-` (minus)](#unary-plus-and-minus-operators) operatorów.
- Binarny [ `*` (mnożenie)](#multiplication-operator-), [ `/` (dział)](#division-operator-), [ `%` (resztę)](#remainder-operator-), [ `+` () Dodawanie)](#addition-operator-), i [ `-` (odejmowanie)](#subtraction-operator-) operatorów.

Te operatory obsługują wszystkie [całkowitego](../keywords/integral-types-table.md) i [zmiennoprzecinkowych](../keywords/floating-point-types-table.md) typów liczbowych.

## <a name="increment-operator-"></a>Operator inkrementacji ++

Jednoargumentowy operator inkrementacji `++` zwiększa się argumentem operacji o 1. Argument musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.

Operator inkrementacji jest obsługiwana w dwóch formach: przyrostkowego operatora inkrementacyjnego `x++`i operator inkrementacji prefiks `++x`.

### <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operator inkrementacji przedrostka

Wynik `++x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operator dekrementacji--

Jednoargumentowy operator dekrementacji `--` zmniejsza argumentem operacji o 1. Argument musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.

Operator dekrementacji jest obsługiwany w dwóch formach: przyrostkowego operatora dekrementacyjnego `x--`i operator dekrementacji prefiksu, `--x`.

### <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operator dekrementacji przedrostka

Wynik `--x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Jednoargumentowe plus lub minus operatorów

Jednoargumentowy `+` operator zwraca wartość swojego operandu. Jednoargumentowy `-` operator oblicza liczbowych negacji swojego operandu.

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Jednoargumentowy `-` nie obsługuje operatora [ulong](../keywords/ulong.md) typu.

## <a name="multiplication-operator-"></a>Operator mnożenia *

Operator mnożenia `*` Oblicza iloczyn argumentów:

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Jednoargumentowy `*` operator jest [operatora pośredniego wskaźnika](multiplication-operator.md#pointer-indirection-operator).

## <a name="division-operator-"></a>Operator dzielenia /

Operator dzielenia `/` dzieli pierwszy argument operacji za drugim argumentem.

### <a name="integer-division"></a>Dzielenie liczby całkowitej

Dla argumentów typu Liczba całkowita, wynikiem `/` operator jest typu Liczba całkowita i równości iloraz dwóch argumentów operacji, zaokrąglana w kierunku zera:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Aby uzyskać iloraz dwóch argumentów operacji jako liczba zmiennoprzecinkowa, należy użyć `float`, `double`, lub `decimal` typu:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Dzielenie zmiennoprzecinkowe

Aby uzyskać `float`, `double`, i `decimal` typów, wynikiem `/` operatora jest równy ilorazowi dwóch argumentów operacji:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Jeśli jeden z operandów jest `decimal`, inny argument może być żadnego `float` ani `double`, ponieważ ani `float` ani `double` jest niejawnie konwertowany na `decimal`. Należy jawnie przekonwertować `float` lub `double` operand `decimal` typu. Aby uzyskać więcej informacji na temat niejawne konwersje między typów liczbowych, zobacz [Tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).

## <a name="remainder-operator-"></a>Resztę operator %

Operator reszty `%` oblicza pozostałą po podzieleniu pierwszy argument operacji za drugim argumentem.

### <a name="integer-remainder"></a>Pozostała liczba całkowita
  
Dla argumentów typu Liczba całkowita, wynikiem `a % b` wartość jest generowany przez `a - (a / b) * b`. Znak resztę różna od zera jest taka sama, jak w przypadku pierwszego operandu w poniższym przykładzie pokazano:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Użyj <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metodę w celu obliczenia zarówno dzielenie liczby całkowitej, jak i resztę wyników.

### <a name="floating-point-remainder"></a>Zmiennoprzecinkową resztę

Aby uzyskać `float` i `double` operandów, wynik `x % y` dla skończonego `x` i `y` jest wartością `z` tak, aby

- Znak `z`, jeśli różna od zera, jest taka sama jak znak `x`.
- wartość bezwzględna `z` wartość jest generowany przez `|x| - n * |y|` gdzie `n` jest największa możliwa liczba całkowita, która jest mniejsza niż lub równa `|x| / |y|` i `|x|` i `|y|` są wartości bezwzględne dla `x` i `y`, odpowiednio.

> [!NOTE]
> Ta metoda obliczeniowych reszta jest odpowiednikiem używanym dla liczby całkowitej argumentów, ale różni się od IEEE 754. Operacja Reminder, który jest zgodny z IEEE 754, należy użyć <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

Aby uzyskać informacje o zachowanie `%` operator nieskończona argumentów, zobacz [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać `decimal` argumentów operacji, operator reszty `%` jest odpowiednikiem [operator reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.

Poniższy przykład pokazuje zachowanie operator reszty z argumentów operacji zmiennoprzecinkowej:

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operator dodawania +

Operator dodawania `+` oblicza sumę argumentów:

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Możesz również użyć `+` operator dla kombinacji parametrów łączenia i delegata. Aby uzyskać więcej informacji, zobacz [ `+` operator](addition-operator.md) artykułu.

## <a name="subtraction-operator--"></a>Operator odejmowania-

Operator odejmowania `-` odejmuje jej drugiego operandu od jego pierwszego operandu:

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Możesz również użyć `-` operator usuwanie delegata. Aby uzyskać więcej informacji, zobacz [ `-` operator](subtraction-operator.md) artykułu.

## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo i kojarzenie operatorów

Poniższa lista zamówień operatorów arytmetycznych, zaczynając od najwyższy priorytet do najniższego:

- Inkrementacja przyrostkowa `x++` i dekrementacyjne `x--` operatorów.
- Inkrementacja przedrostkowa `++x` i dekrementacyjne `--x` i jednoargumentowe `+` i `-` operatorów.
- Mnożenia `*`, `/`, i `%` operatorów.
- Dodatek `+` i `-` operatorów.

Operatory arytmetyczne binarne są lewostronne. Oznacza to operatory o tym samym poziomie priorytetu są obliczane od lewej do prawej.

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo i kojarzenie operatorów.

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).

## <a name="compound-assignment"></a>Przydział złożony

Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczany tylko raz.

W poniższym przykładzie pokazano użycie przydział złożony z operatorów arytmetycznych:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Możesz także użyć `+=` i `-=` operatory subskrybowanie i anulowanie subskrypcji [zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="arithmetic-overflow-and-division-by-zero"></a>Przepełnienie arytmetyczne i dzielenie przez zero

Gdy wynik operacji arytmetycznej jest spoza zakresu możliwych wartości skończoną zaangażowane typu liczbowego, zachowanie jest operator arytmetyczny zależy od typu argumentów.

### <a name="integer-arithmetic-overflow"></a>Liczba całkowita przepełnienie arytmetyczne

Dzielenie liczby całkowitej przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.

W przypadku przepełnienia arytmetycznego liczby całkowitej, przepełnienie sprawdzanie kontekstu, który może być [zaznaczony lub niezaznaczony](../keywords/checked-and-unchecked.md), kontroluje zachowanie wynikową:

- W kontekście sprawdzanym przepełnienie odbywa się w wyrażeniu stałym kompilacji błędu. W przeciwnym razie, gdy operacja jest wykonywana w czasie wykonywania, <xref:System.OverflowException> zgłaszany.
- W kontekście niesprawdzanym wynik jest obcinana odrzucając wszystkie bity wyższego rzędu, które nie mieszczą się w typie docelowym.

Wraz z [checked i unchecked](../keywords/checked-and-unchecked.md) instrukcji, można użyć `checked` i `unchecked` operatory, aby kontrolować przepełnienia, sprawdzając kontekst, w którym wyrażenie jest obliczane:

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Domyślnie operacje arytmetyczne występują w *unchecked* kontekstu.

### <a name="floating-point-arithmetic-overflow"></a>Zmiennoprzecinkowe przepełnienie arytmetyczne

Operacji arytmetycznych na wartościach `float` i `double` typy nigdy nie zgłasza wyjątku. Wynik operacji arytmetycznych na wartościach tych typów może być jedną z wartości specjalne, które reprezentują nieskończoność i nie nieliczbowych:

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

Dla argumentów operacji `decimal` typu arytmetycznego przepełnienia zawsze zgłasza <xref:System.OverflowException> i dzielenie przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Błędy zaokrąglania

Ze względu na ograniczenia ogólne zmiennoprzecinkowych reprezentacji w postaci liczby rzeczywiste i arytmetyki zmiennoprzecinkowej mogą wystąpić błędy zaokrąglania, w obliczeniach z typów zmiennoprzecinkowych. Oznacza to, że utworzone wynik wyrażenia różnić się od oczekiwanego wyniku matematyczne. W poniższym przykładzie pokazano kilka takich przypadkach:

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowe (`++`, `--`, `+`, i `-`) i binarny (`*`, `/`, `%`, `+`i `-`) operatory arytmetyczne. Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Inkrementacja przyrostkowa i operatory dekrementacji](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Przedrostkowe i operatory dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Jednoargumentowy operator plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Jednoargumentowy operator minus](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operator dzielenia](~/_csharplang/spec/expressions.md#division-operator)
- [Operator reszty](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operator dodawania](~/_csharplang/spec/expressions.md#addition-operator)
- [Operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment)
- [Operatory checked i unchecked](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)