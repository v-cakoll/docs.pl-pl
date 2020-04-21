---
title: Operatory arytmetyczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje mnożenia, dzielenia, pozostałej, dodawania i odejmowania za pomocą typów liczbowych.
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
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738735"
---
# <a name="arithmetic-operators-c-reference"></a>Operatory arytmetyczne (odwołanie do języka C#)

Następujące operatory wykonują operacje arytmetyczne z operandami typów liczbowych:

- Operatory [ `++` niepokalane (przyrost)](#increment-operator-), [ `--` (dekrementowanie)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)
- Operatory [ `*` binarne (mnożenie)](#multiplication-operator-), [ `/` (podział)](#division-operator-), [ `%` (reszta)](#remainder-operator-), [ `+` (dodawanie)](#addition-operator-)i [ `-` (odejmowanie)](#subtraction-operator--)

Operatory te są obsługiwane przez wszystkie typy liczbowe [całkowane](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)

## <a name="increment-operator-"></a>Operator przyrostu ++

Operator `++` przyrostu bezemisowego zwiększa swój operand o 1. Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)

Operator przyrostu jest obsługiwany w dwóch formach: operator `x++`przyrostu po poprawce i operator `++x`przyrostu prefiksu, .

### <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartość `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operator przyrostu prefiksu

Wynik `++x` jest wartość `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operator dekrementacji --

Operator `--` dekrementacji nieobsadzowej zmniejsza swoją operand o 1. Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)

Operator dekrementacji jest obsługiwany w dwóch formach: operator `x--`usuwania poprawek i operator `--x`dekrementacji prefiksu, .

### <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartość `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operator dekrementacji prefiksu

Wynik `--x` jest wartość `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Operatory Unary plus i minus

Operator unary `+` zwraca wartość jego operand. Operator unary `-` oblicza numeryczne negację jego operandu.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Typ [ulong](../builtin-types/integral-numeric-types.md) nie obsługuje operatora `-` bezparowi.

## <a name="multiplication-operator-"></a>Operator mnożenia *

Operator `*` mnożenia oblicza produkt swoich operandów:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Operator unary `*` jest [operatorem pośrednim wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operator działu /

Operator `/` dywizji dzieli swój lewoskręt przez jego prawicowy operand.

### <a name="integer-division"></a>Podział liczby całkowitej

W przypadku argumentów typów całkowitych wynik `/` operatora jest typu całkowitej i jest równy ilorazowi dwóch argumentów zaokrąglonych do zera:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Aby uzyskać iloraz dwóch argumentów jako liczbę zmiennoprzecinkową, należy użyć `float`, `double`lub `decimal` typu:

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Podział zmiennoprzecinowy

Dla `float`, `double`i `decimal` typów, wynikiem `/` operatora jest iloraz dwóch operandów:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

Jeśli jeden z `decimal`operandów jest , inny `float` operand nie może być ani, `double`ponieważ ani `float` nie `double` jest w sposób dorozumiany zamienny na `decimal`. Należy jawnie przekonwertować `float` lub `decimal` `double` operand do typu. Aby uzyskać więcej informacji o konwersjach między typami liczbowymi, zobacz [Wbudowane konwersje liczbowe](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Pozostały operator %

Pozostała część `%` operatora oblicza pozostałą część po podzieleniu jego lewej opery przez jego prawej operyndu.

### <a name="integer-remainder"></a>Pozostała część całkowita

Dla argumentów typów całkowitych wynikiem `a % b` jest wartość wyprodukowana `a - (a / b) * b`przez . Znak pozostałej niezerowej jest taki sam jak w leworęcznym operand, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<xref:System.Math.DivRem%2A?displayProperty=nameWithType> Metoda służy do obliczania zarówno wyników podziału liczby całkowitej, jak i pozostałej.

### <a name="floating-point-remainder"></a>Pozostała część zmiennoprzecinowa

Dla `float` i `double` operands, wynik `x % y` dla skończonego `x` i `z` `y` jest wartość taka, że

- Znak `z`, jeśli nie zero, jest taki sam `x`jak znak .
- Wartość bezwzględna `z` jest wartością `|x| - n * |y|` `n` wytwarzaną przez miejsce, w którym jest `|x| / |y|` największą możliwą liczą całkowitą, która jest mniejsza lub równa `|x|` i i `|y|` jest wartością bezwzględną `x` i `y`, odpowiednio.

> [!NOTE]
> Ta metoda obliczania pozostałej części jest analogiczna do tej używanej dla argumentów całkowitych, ale różni się od specyfikacji IEEE 754. Jeśli potrzebujesz pozostałej operacji zgodnej ze specyfikacją IEEE 754, użyj tej <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

Aby uzyskać informacje na `%` temat zachowania operatora z nieo skończonymi operandami, zobacz sekcję [Operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

W `decimal` przypadku argumentów operator `%` pozostałej części jest odpowiednikiem [pozostałego operatora](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.

Poniższy przykład pokazuje zachowanie pozostałego operatora z argumentami zmiennoprzecinkowymi:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operator dodawania +

Operator `+` dodawania oblicza sumę swoich operandów:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Operator można również `+` użyć do łączenia ciągów i delegować kombinację. Aby uzyskać więcej informacji, zobacz artykuł [ `+` i `+=` operatorów.](addition-operator.md)

## <a name="subtraction-operator--"></a>Operator odejmowania -

Operator odejmowania `-` odejmuje jego prawej opery od jego lewej operndu:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

Można również użyć `-` operatora do usuwania delegatów. Aby uzyskać więcej informacji, zobacz artykuł [ `-` i `-=` operatorów.](subtraction-operator.md)

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

z `x` tą różnicą, że jest oceniana tylko raz.

Poniższy przykład pokazuje użycie przypisania złożonego z operatorami arytmetycznymi:

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

Ze względu na [promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` niejawnie wymienialny na typ `x`. W takim przypadku, `op` jeśli jest wstępnie zdefiniowanym operatorem, a wynik operacji jest `T` `x`jawnie wymienialny na `x op= y` typ , `x = (T)(x op y)`wyrażenie `x` przypisania złożonego formularza jest równoważne , z tą różnicą, że jest oceniane tylko raz. Poniższy przykład pokazuje, że zachowanie:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Operatory `+=` i `-=` operatorzy również subskrybują i wypisują się z [wydarzenia,](../keywords/event.md)odpowiednio. Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i anulować subskrypcję .](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo i zespolenie operatora

Następująca lista porządkuuje operatorów arytmetycznych, począwszy od najwyższego pierwszeństwa do najniższego:

- Operatory przyrostu `x++` i zmniejszania `x--` poprawek
- `++x` Przyrost prefiksu i `--x` dekrementacji i unary `+` i `-` operatorów
- `*`Mnożenie `/`i `%` operatory
- Dodatki `+` `-` i podmioty gospodarcze

Operatory arytmetyczne binarne są lewozespole. Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.

Użyj nawiasów, `()`aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora i zespolenie.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu [pierwszeństwa, zobacz sekcję pierwszeństwo operatora](index.md#operator-precedence) w artykule [Operatory języka C#.](index.md)

## <a name="arithmetic-overflow-and-division-by-zero"></a>Przepełnienie i podział arytmetyczny przez zero

Gdy wynik operacji arytmetycznej znajduje się poza zakresem możliwych wartości skończonych danego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego argumentów.

### <a name="integer-arithmetic-overflow"></a>Przepełnienie arytmetyczne liczby całkowitej

Podział liczby całkowitej przez zero <xref:System.DivideByZeroException>zawsze rzuca .

W przypadku przepełnienia arytmetycznego liczby całkowitej kontekst sprawdzania przepełnienia, który można [sprawdzić lub odeszło od zaznaczenia,](../keywords/checked-and-unchecked.md)kontroluje wynikowe zachowanie:

- W sprawdzonym kontekście, jeśli przepełnienie odbywa się w wyrażeniu stałym, występuje błąd w czasie kompilacji. W przeciwnym razie, gdy operacja jest <xref:System.OverflowException> wykonywana w czasie wykonywania, jest generowany.
- W kontekście niezaznaczone wynik jest obcinana przez odrzucenie bitów wysokiego rzędu, które nie mieszczą się w typie docelowym.

Wraz z [zaznaczonych i niesprawdzonych](../keywords/checked-and-unchecked.md) instrukcji, można użyć `checked` i `unchecked` operatorów do kontrolowania kontekstu sprawdzania przepełnienia, w którym wyrażenie jest oceniane:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Domyślnie operacje arytmetyczne występują w *niezaznaczone kontekście.*

### <a name="floating-point-arithmetic-overflow"></a>Przepełnienie arytmetyczne zmiennoprzecinające

Operacje arytmetyczne `float` z `double` i typów nigdy nie zgłaszać wyjątek. Wynik operacji arytmetycznych z tymi typami może być jedną ze specjalnych wartości, które reprezentują nieskończoność i nie-liczbę:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

Dla operandów `decimal` typu przepełnienie arytmetyczne zawsze <xref:System.OverflowException> rzuca i dzielenie przez <xref:System.DivideByZeroException>zero zawsze rzuca .

## <a name="round-off-errors"></a>Błędy zaokrąglania

Ze względu na ogólne ograniczenia zmiennoprzecinkową reprezentacji liczb rzeczywistych i arytmetyki zmiennoprzecinkowej błędy zaokrąglania mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi. Oznacza to, że wynik wytworzyny wyrażenia może różnić się od oczekiwanego wyniku matematycznego. Poniższy przykład pokazuje kilka takich przypadków:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Aby uzyskać więcej informacji, zobacz uwagi na [stronach System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)lub [System.Decimal.](/dotnet/api/system.decimal#remarks)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory arytmetyczne dwuarchikę (`++`, `--` `+` `-`, , i ) i binarne (`*` `/`, `%`, `+`, i `-`) . Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Operatory przyrostu i zmniejszania poprawek](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operatory przyrostu i zmniejszania prefiksów](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Operator Unary plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Operator unary minus](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operator działu](~/_csharplang/spec/expressions.md#division-operator)
- [Operator pozostałej części](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operator dodawania](~/_csharplang/spec/expressions.md#addition-operator)
- [Operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sprawdzone i niesprawdzone operatory](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
