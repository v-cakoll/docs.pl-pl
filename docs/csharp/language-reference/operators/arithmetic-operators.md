---
title: Operatory arytmetyczne — odwołanie w C#
description: Dowiedz się więcej na temat operatorów języka C#, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania z typami liczbowymi.
ms.date: 05/11/2020
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
ms.openlocfilehash: d004ab466bc053ed286d85bcbee2766d8a087286
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207239"
---
# <a name="arithmetic-operators-c-reference"></a>Operatory arytmetyczne (odwołanie w C#)

Następujące operatory wykonują operacje arytmetyczne z argumentami typu liczbowego:

- Operatory jednoargumentowe [ `++` (przyrostowe)](#increment-operator-), ( [ `--` zmniejszanie](#decrement-operator---)), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)
- Operatory binarne [ `*` (mnożenie)](#multiplication-operator-), [ `/` (dzielenie)](#division-operator-), [ `%` (reszta)](#remainder-operator-), [ `+` (Dodawanie)](#addition-operator-)i [ `-` (Odejmowanie)](#subtraction-operator--)

Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .

W przypadku typów całkowitych operatory te (poza `++` `--` operatorami i) są zdefiniowane dla `int` `uint` typów,, `long` i `ulong` . Gdy operandy są innymi typami całkowitymi ( `sbyte` , `byte` , `short` , `ushort` lub `char` ), ich wartości są konwertowane na `int` Typ, który jest również typem wyniku operacji. Gdy operandy są różnych typów całkowitych lub zmiennoprzecinkowych, ich wartości są konwertowane na najbliższy typ zawierający, jeśli taki typ istnieje. Aby uzyskać więcej informacji, zobacz sekcję [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md). `++`Operatory i `--` są zdefiniowane dla wszystkich typów liczb całkowitych i zmiennoprzecinkowych oraz typu [char](../builtin-types/char.md) .

## <a name="increment-operator-"></a>Increment — operator + +

Jednoargumentowy operator przyrostu `++` zwiększa jego operand o 1. Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .

Operator przyrostu jest obsługiwany w dwóch formach: Przyrostkowy operator przyrostu, `x++` i operator przyrostu wartości prefiksu `++x` .

### <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operator przyrostu prefiksu

Wynik `++x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Zmniejsz operator--

Operator zmniejszania jednoargumentowego `--` zmniejsza jego operand o 1. Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .

Operator zmniejszania jest obsługiwany w dwóch formach: operator zmniejszania przyrostu, `x--` i operator zmniejszania prefiksu `--x` .

### <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operator zmniejszania prefiksu

Wynik `--x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Operatory jednoargumentowe Plus i minus

Operator jednoargumentowy `+` zwraca wartość jego operandu. Operator jednoargumentowy `-` oblicza liczbę negacji operandu.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Typ [ULONG](../builtin-types/integral-numeric-types.md) nie obsługuje operatora jednoargumentowego `-` .

## <a name="multiplication-operator-"></a>Operator mnożenia *

Operator mnożenia `*` Oblicza iloczyn argumentów operacji:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Operator jednoargumentowy `*` jest [operatorem pośredni wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operator dzielenia/

Operator dzielenia `/` dzieli swój operand z lewej strony przez jego operand po prawej stronie.

### <a name="integer-division"></a>Dzielenie liczb całkowitych

Dla argumentów operacji typu Integer wynik `/` operatora jest typu integer i jest równy ilorazowi dwóch operandów zaokrąglonych na zero:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Aby uzyskać iloraz dwóch operandów jako liczby zmiennoprzecinkowej, użyj `float` `double` typu,, lub `decimal` :

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Dzielenie zmiennoprzecinkowe

W przypadku `float` `double` typów, i `decimal` , wynik `/` operatora jest ilorazem dwóch operandów:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

Jeśli jeden z operandów to `decimal` , inny operand nie może być ani `float` `double` , ponieważ ani nie `float` `double` jest niejawnie konwertowany na `decimal` . Należy jawnie skonwertować `float` `double` operand or na `decimal` Typ. Aby uzyskać więcej informacji na temat konwersji typów liczbowych, zobacz [wbudowane konwersje numeryczne](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Procent pozostałej części

Operator reszty `%` oblicza resztę po podzieleniu operandu po lewej stronie przez jego operand po prawej stronie.

### <a name="integer-remainder"></a>Reszta całkowita

W przypadku operandów typu Integer wynik `a % b` jest wartością wygenerowaną przez `a - (a / b) * b` . Znak niezerowej reszty jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

Użyj <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metody, aby obliczyć podział liczby całkowitej i reszty.

### <a name="floating-point-remainder"></a>Pozostała część zmiennoprzecinkowa

Dla `float` argumentów i `double` , wynik `x % y` dla `x` wartości skończone i `y` jest wartością `z` taką jak

- Znak `z` , jeśli wartość niezerowa, jest taki sam jak znak `x` .
- Wartość bezwzględna `z` jest wartością wygenerowaną przez, `|x| - n * |y|` gdzie `n` jest największą możliwą liczbą całkowitą, która jest mniejsza lub równa `|x| / |y|` i jest `|x|` `|y|` odpowiednio wartością bezwzględną `x` i `y` .

> [!NOTE]
> Ta metoda przetwarzania reszty jest analogiczna do tego, który jest używany dla argumentów wartości całkowitych, ale różni się od specyfikacji IEEE 754. Jeśli potrzebujesz pozostałej operacji, która jest zgodna ze specyfikacją IEEE 754, użyj <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

Aby uzyskać informacje o zachowaniu `%` operatora z nieskończone operandami, zobacz sekcję [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

Dla `decimal` operandów operator reszty `%` jest równoważny [operatorowi reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.

Poniższy przykład demonstruje zachowanie operatora reszty z argumentami operacji zmiennoprzecinkowych:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operator dodawania +

Operator dodawania `+` oblicza sumę argumentów operacji:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Operatora można także użyć `+` do łączenia ciągów i delegatów. Aby uzyskać więcej informacji, zobacz artykuł [ `+` `+=` Operatory i](addition-operator.md) .

## <a name="subtraction-operator--"></a>Operator odejmowania —

Operator odejmowania `-` odejmuje swój prawy operand od jego operandu po lewej stronie:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

Można również użyć `-` operatora do usuwania delegatów. Aby uzyskać więcej informacji, zobacz artykuł [ `-` `-=` Operatory i](subtraction-operator.md) .

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

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być niejawnie konwertowany na typ `T` `x` . W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x` , wyrażenie przypisania złożonego formularza `x op= y` jest równoważne z `x = (T)(x op y)` , z tą różnicą, że `x` jest tylko raz oceniane. Poniższy przykład ilustruje takie zachowanie:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Należy również użyć `+=` operatorów i `-=` , aby subskrybować lub anulować subskrypcję [zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo operatorów i łączność

Na poniższej liście przedstawiono operatory arytmetyczne zaczynające się od najwyższego priorytetu do najniższego:

- Operatory przyrostka `x++` i zmniejszenie `x--`
- Przyrost i `++x` zmniejszenie prefiksu `--x` oraz jednoargumentowe `+` i `-` Operatory
- Mnożenia `*` , `/` , i `%` Operatory
- Dodatek `+` i `-` Operatory

Binarne operatory arytmetyczne są z lewej strony skojarzenia. Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.

Użyj nawiasów, `()` , aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów i łączność.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [operatory języka c#](index.md) .

## <a name="arithmetic-overflow-and-division-by-zero"></a>Przepełnienie arytmetyczne i dzielenie przez zero

Gdy wynik operacji arytmetycznej jest poza zakresem możliwych wartości skończonego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.

### <a name="integer-arithmetic-overflow"></a>Przepełnienie arytmetyczne liczb całkowitych

Dzielenie liczby całkowitej przez zero zawsze zgłasza <xref:System.DivideByZeroException> .

W przypadku przepełnienia arytmetycznego wartości całkowitych, kontekst sprawdzania przepełnienia, który można [sprawdzić lub nie zaznaczyć](../keywords/checked-and-unchecked.md), kontroluje zachowanie wyników:

- Jeśli przepełnienie ma miejsce w wyrażeniu stałym, wystąpi błąd w czasie kompilacji. W przeciwnym razie, gdy operacja zostanie wykonana w czasie wykonywania, <xref:System.OverflowException> zostanie zgłoszony.
- W kontekście niesprawdzonym wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.

Wraz z [sprawdzonymi i niesprawdzonymi](../keywords/checked-and-unchecked.md) instrukcjami można użyć `checked` operatorów i, `unchecked` Aby kontrolować kontekst sprawdzania przepełnienia, w którym jest oceniane wyrażenie:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Domyślnie operacje arytmetyczne odbywają się w *niesprawdzonym* kontekście.

### <a name="floating-point-arithmetic-overflow"></a>Przepełnienie arytmetyczne zmiennoprzecinkowe

Operacje arytmetyczne z `float` `double` typami i nigdy nie generują wyjątku. Wynik operacji arytmetycznych z tymi typami może być jedną z wartości specjalnych, które reprezentują nieskończoność i nie liczbę:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

W przypadku operandów `decimal` typu, przepełnienie arytmetyczne zawsze zgłasza, <xref:System.OverflowException> a dzielenie przez zero zawsze zgłasza <xref:System.DivideByZeroException> .

## <a name="round-off-errors"></a>Błędy zaokrągleń

Ze względu na ogólne ograniczenia reprezentacji liczb zmiennoprzecinkowych i arytmetycznych zmiennoprzecinkowych błędy zaokrągleń mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi. Oznacza to, że wygenerowany wynik wyrażenia może być inny niż oczekiwany wynik matematyczny. Poniższy przykład ilustruje kilka takich przypadków:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Aby uzyskać więcej informacji, zobacz uwagi na stronach referencyjnych [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)lub [System. Decimal](/dotnet/api/system.decimal#remarks) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory jednoargumentowe ( `++` , `--` , `+` i `-` ) oraz binarnych ( `*` , `/` ,, `%` `+` i `-` ) arytmetycznych. Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):

- [Operatory przyrostka i zmniejszenie](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operatory prefiksów inkrementacji i dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
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

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
