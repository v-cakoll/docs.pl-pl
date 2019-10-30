---
title: Operatory arytmetyczne C# — odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania z typami liczbowymi.
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
ms.openlocfilehash: ca2513a0f865fd7da728f7d3247bdb7b50a2f48a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036427"
---
# <a name="arithmetic-operators-c-reference"></a>Operatory arytmetyczneC# (odwołanie)

Następujące operatory wykonują operacje arytmetyczne z argumentami typu liczbowego:

- Operatory jednoargumentowe [`++` (Increment)](#increment-operator-), [`--` (zmniejszania)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators)i [`-` (minus)](#unary-plus-and-minus-operators)
- `*` binarny [(mnożenie)](#multiplication-operator-), [`/` (dzielenie)](#division-operator-), [`%` (reszta)](#remainder-operator-), [`+` (Dodawanie)](#addition-operator-)i [`-` (Odejmowanie)](#subtraction-operator--) operatorów

Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .

## <a name="increment-operator-"></a>Increment — operator + +

Jednoargumentowy operator przyrostu `++` zwiększa jego operand o 1. Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .

Operator przyrostu jest obsługiwany w dwóch formach: Przyrostkowy operator przyrostu, `x++` i operator przyrostu prefiksu, `++x`.

### <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operator przyrostu prefiksu

Wynik `++x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Zmniejsz operator--

Operator zmniejszania jednoargumentowego `--` zmniejsza jego operand o 1. Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .

Operator zmniejszania jest obsługiwany w dwóch formach: operator zmniejszania przyrostkowego, `x--` i operator zmniejszania prefiksu, `--x`.

### <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operator zmniejszania prefiksu

Wynik `--x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Operatory jednoargumentowe Plus i minus

Jednoargumentowy operator `+` zwraca wartość operandu. Jednoargumentowy operator `-` oblicza liczbową negację operandu.

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Typ [ULONG](../builtin-types/integral-numeric-types.md) nie obsługuje operatora jednoargumentowego `-`.

## <a name="multiplication-operator-"></a>Operator mnożenia *

Operator mnożenia `*` oblicza iloczynu jego operandów:

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Jednoargumentowy operator `*` jest [operatorem pośredni wskaźnik](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operator dzielenia/

Operator dzielenia `/` dzieli jego operand po lewej stronie przez jego operand po prawej stronie.

### <a name="integer-division"></a>Dzielenie liczb całkowitych

W przypadku operandów typu Integer wynik operatora `/` jest typu integer i jest równy ilorazowi dwóch operandów zaokrąglonych na zero:

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Aby uzyskać iloraz dwóch operandów jako liczby zmiennoprzecinkowej, użyj typu `float`, `double` lub `decimal`:

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Dzielenie zmiennoprzecinkowe

Dla typów `float`, `double` i `decimal`, wynik operatora `/` jest ilorazem dwóch operandów:

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Jeśli jeden z operandów jest `decimal`, inny operand nie może być ani `float` ani `double`, ponieważ żadne `float` ani `double` nie są niejawnie konwertowane na `decimal`. Należy jawnie skonwertować operand `float` lub `double` na typ `decimal`. Aby uzyskać więcej informacji na temat konwersji typów liczbowych, zobacz [wbudowane konwersje numeryczne](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Procent pozostałej części

Operator reszty `%` oblicza resztę po podzieleniu operandu po lewej stronie przez jego operand po prawej stronie.

### <a name="integer-remainder"></a>Reszta całkowita

W przypadku operandów typu Integer wynik `a % b` jest wartością wygenerowaną przez `a - (a / b) * b`. Znak niezerowej reszty jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Użyj metody <xref:System.Math.DivRem%2A?displayProperty=nameWithType>, aby obliczyć podział liczby całkowitej i reszty.

### <a name="floating-point-remainder"></a>Pozostała część zmiennoprzecinkowa

W przypadku operandów `float` i `double` wynik `x % y` dla skończonego `x` i `y` jest wartością `z` taką, która

- Znak `z`, jeśli wartość jest różna od zera, jest taka sama jak znak `x`.
- Wartość bezwzględna `z` jest wartością wygenerowaną przez `|x| - n * |y|`, gdzie `n` jest największą możliwą liczbą całkowitą, która jest mniejsza lub równa `|x| / |y|` i `|x|` i `|y|` są wartościami bezwzględnymi `x` i `y` piwo.

> [!NOTE]
> Ta metoda przetwarzania reszty jest analogiczna do tego, który jest używany dla argumentów wartości całkowitych, ale różni się od specyfikacji IEEE 754. Jeśli potrzebujesz pozostałej operacji, która jest zgodna ze specyfikacją IEEE 754, użyj metody <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.

Aby uzyskać informacje o zachowaniu operatora `%` z nieskończone operandy, zobacz sekcję [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Dla operandów `decimal` operator reszty `%` jest równoważny [operatorowi reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) typu <xref:System.Decimal?displayProperty=nameWithType>.

Poniższy przykład demonstruje zachowanie operatora reszty z argumentami operacji zmiennoprzecinkowych:

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operator dodawania +

Operator dodawania `+` oblicza sumę argumentów operacji:

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Można też użyć operatora `+`, aby łączyć ciągów i delegatów. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [operatorów `+` i `+=`](addition-operator.md) .

## <a name="subtraction-operator--"></a>Operator odejmowania —

Operator odejmowania `-` odejmuje swój prawy operand od jego operandu po lewej stronie:

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Można też użyć operatora `-` do usuwania delegatów. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [operatorów`-` i `-=`](subtraction-operator.md) .

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczana tylko raz.

Poniższy przykład ilustruje użycie przypisania złożonego z operatorami arytmetycznymi:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik operacji `op` może nie być niejawnie konwertowany na typ `T` `x`. W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x`, wyrażenie złożonego przypisania formularza `x op= y` jest równoważne `x = (T)(x op y)` , z tą różnicą, że `x` jest oceniane tylko raz. Poniższy przykład ilustruje takie zachowanie:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Możesz również użyć operatorów `+=` i `-=`, aby subskrybować lub anulować subskrypcję [zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [How to: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo operatorów i łączność

Na poniższej liście przedstawiono operatory arytmetyczne zaczynające się od najwyższego priorytetu do najniższego:

- Przyrosty przyrostkowe `x++` i zmniejszania `x--` operatory
- `++x` przyrostu prefiksu i zmniejszaj `--x` i `+` operatory jednoargumentowe i `-`
- Mnożenia `*`, `/`i operatory `%`
- Addytywne `+` i operatory `-`

Binarne operatory arytmetyczne są z lewej strony skojarzenia. Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.

Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów i łączność.

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .

## <a name="arithmetic-overflow-and-division-by-zero"></a>Przepełnienie arytmetyczne i dzielenie przez zero

Gdy wynik operacji arytmetycznej jest poza zakresem możliwych wartości skończonego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.

### <a name="integer-arithmetic-overflow"></a>Przepełnienie arytmetyczne liczb całkowitych

Dzielenie liczby całkowitej przez zero zawsze zgłasza <xref:System.DivideByZeroException>.

W przypadku przepełnienia arytmetycznego wartości całkowitych, kontekst sprawdzania przepełnienia, który można [sprawdzić lub nie zaznaczyć](../keywords/checked-and-unchecked.md), kontroluje zachowanie wyników:

- Jeśli przepełnienie ma miejsce w wyrażeniu stałym, wystąpi błąd w czasie kompilacji. W przeciwnym razie, gdy operacja zostanie wykonana w czasie wykonywania, zostanie zgłoszony <xref:System.OverflowException>.
- W kontekście niesprawdzonym wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.

Oprócz instrukcji [sprawdzonych i niesprawdzonych](../keywords/checked-and-unchecked.md) można użyć operatorów `checked` i `unchecked` do kontrolowania kontekstu sprawdzania przepełnienia, w którym jest oceniane wyrażenie:

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Domyślnie operacje arytmetyczne odbywają się w *niesprawdzonym* kontekście.

### <a name="floating-point-arithmetic-overflow"></a>Przepełnienie arytmetyczne zmiennoprzecinkowe

Operacje arytmetyczne o typach `float` i `double` nigdy nie generują wyjątku. Wynik operacji arytmetycznych z tymi typami może być jedną z wartości specjalnych, które reprezentują nieskończoność i nie liczbę:

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

W przypadku operandów typu `decimal` przepełnienie arytmetyczne zawsze zgłasza <xref:System.OverflowException> i dzielenie przez zero zawsze zgłasza <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Błędy zaokrągleń

Ze względu na ogólne ograniczenia reprezentacji liczb zmiennoprzecinkowych i arytmetycznych zmiennoprzecinkowych błędy zaokrągleń mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi. Oznacza to, że wygenerowany wynik wyrażenia może być inny niż oczekiwany wynik matematyczny. Poniższy przykład ilustruje kilka takich przypadków:

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Aby uzyskać więcej informacji, zobacz uwagi na stronach referencyjnych [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)lub [System. Decimal](/dotnet/api/system.decimal#remarks) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) jednoargumentowy (`++`, `--`, `+`i `-`) oraz binarny operator arytmetyczny (`*`, `/`, `%`, `+`i `-`). Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operatory przyrostka i zmniejszenie](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operatory przyrostu i zmniejszania prefiksu](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Jednoargumentowy operator plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Jednoargumentowy operator minus](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operator dzielenia](~/_csharplang/spec/expressions.md#division-operator)
- [Operator reszty](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operator dodawania](~/_csharplang/spec/expressions.md#addition-operator)
- [Operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sprawdzone i niesprawdzone operatory](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
