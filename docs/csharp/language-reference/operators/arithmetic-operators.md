---
title: Operatory arytmetyczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania za pomocą typów liczbowych.
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
ms.openlocfilehash: f03084fa611c35c5504190b28fab79563d560d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399260"
---
# <a name="arithmetic-operators-c-reference"></a>Operatory arytmetyczne (odwołanie do języka C#)

Następujące operatory wykonują operacje arytmetyczne z operandami typów numerycznych:

- Operatory [ `++` nieulatyczni (przyrostowe),](#increment-operator-) [ `--` (decrement)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)
- Operatory [ `*` binarne (mnożenie),](#multiplication-operator-) [ `/` (podział),](#division-operator-) [ `%` (reszta)](#remainder-operator-) [ `+` , (dodawanie)](#addition-operator-)i [ `-` (odejmowanie)](#subtraction-operator--)

Te operatory są obsługiwane przez wszystkie [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)

## <a name="increment-operator-"></a>Operator przyrostu ++

Operator `++` przyrostu unary zwiększa swój operand o 1. Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)

Operator przyrostu jest obsługiwany w dwóch formach: operator przyrostu przyrostu przyrostu, `x++`i `++x`operator przyrostu prefiksu, .

### <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operator przyrostu prefiksu

Wynik `++x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operator decrement --

Operator `--` unary decrementzmniejsza swój operand o 1. Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)

Operator decrement jest obsługiwany w dwóch formach: operator `x--`decrement przyrostka, i `--x`operator decrement prefiksu, .

### <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operator zmniejszania prefiksów

Wynik `--x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Operatorzy bezsilnikowy plus i minus

Operator unary `+` zwraca wartość swojego operandu. Operator unary `-` oblicza numeryczną negacja jego operandu.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

[Ulong](../builtin-types/integral-numeric-types.md) type nie obsługuje operatora `-` unary.

## <a name="multiplication-operator-"></a>Operator mnożenia *

Operator `*` mnożenia oblicza iloczyn swoich operandów:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Operator jednoargumentowy `*` jest [operatorem pośredniowym wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operator działu /

Operator `/` podziału dzieli swój lewy operand przez jego prawy operand.

### <a name="integer-division"></a>Podział liczby całkowitej

W przypadku argumentów typów całkowitych wynik `/` operatora jest typu całkowitego i jest równy ilorazowi dwóch argumentów zaokrąglonych w kierunku zera:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Aby uzyskać iloraz dwóch argumentów jako liczby zmiennoprzecinkowej, należy użyć `float`, `double`lub `decimal` typu:

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Podział zmiennoprzecinkowych

Dla `float`, `double`i `decimal` typy, wynik `/` operatora jest iloraz emancypów dwóch argumentów:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

Jeśli jednym z argumentów `decimal`jest , inny operand nie może `float` `double` być ani, `float` ani `double`, ponieważ ani nie jest niejawnie cabrio do `decimal`. Należy jawnie przekonwertować `float` lub `double` `decimal` operand do typu. Aby uzyskać więcej informacji o konwersjach między typami liczbowymi, zobacz [Wbudowane konwersje liczbowe](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Reszta operatora %

Pozostały operator `%` oblicza pozostałą część po podzieleniu jego polewej operand przez jego prawostronny operand.

### <a name="integer-remainder"></a>Pozostała liczba całkowita

Dla operandów typów całkowitych `a % b` wynikiem jest wartość produkowana przez `a - (a / b) * b`. Znak pozostałej reszty niezerowej jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

Metoda <xref:System.Math.DivRem%2A?displayProperty=nameWithType> służy do obliczania zarówno podziału liczby całkowitej, jak i pozostałych wyników.

### <a name="floating-point-remainder"></a>Pozostała część zmiennoprzecinkową

W `float` przypadku `double` argumentów, wynikiem `x % y` dla `x` skończonego `y` i `z` jest wartość taka, że

- Znak `z`, jeśli nie zero, jest taki sam `x`jak znak .
- Wartość bezwzględna `z` jest wartością `|x| - n * |y|` `n` wytwarzaną przez to, gdzie jest to `|x| / |y|` największa `|x|` `|y|` możliwa liczba `x` całkowita, która jest mniejsza lub równa i są wartościami bezwzględnymi i `y`, odpowiednio.

> [!NOTE]
> Ta metoda obliczania pozostałej kwoty jest analogiczna do metody stosowanej w przypadku operacji całkowitych, ale różni się od specyfikacji IEEE 754. Jeśli potrzebujesz pozostałej operacji zgodnej ze specyfikacją IEEE <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 754, użyj tej metody.

Aby uzyskać informacje na `%` temat zachowania operatora z nieskończonych operandów, zobacz [reszta operator](~/_csharplang/spec/expressions.md#remainder-operator) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

W `decimal` przypadku operandów pozostały `%` operator jest odpowiednikiem <xref:System.Decimal?displayProperty=nameWithType> [pozostałego operatora](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) typu.

W poniższym przykładzie przedstawiono zachowanie pozostałego operatora z argumentami zmiennoprzecinkowych:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operator dodawania +

Operator `+` dodawania oblicza sumę swoich argumentów:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Można również użyć `+` operatora dla kombinacji ciągów i delegować kombinacji. Aby uzyskać więcej informacji, zobacz [ `+` artykuł `+=` i operatorów.](addition-operator.md)

## <a name="subtraction-operator--"></a>Operator odejmowania -

Operator `-` odejmowania odejmuje swój prawy operand od lewego operandu:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

Można również użyć `-` operatora do usuwania delegata. Aby uzyskać więcej informacji, zobacz [ `-` artykuł `-=` i operatorów.](subtraction-operator.md)

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

chyba `x` że jest oceniana tylko raz.

W poniższym przykładzie przedstawiono użycie przypisania złożonego z operatorami arytmetycznymi:

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` `x`niejawnie konwertowalny na typ . W takim przypadku, `op` jeśli jest wstępnie zdefiniowanyoperator i wynik operacji jest `T` jawnie konwertowalne na typ `x`, wyrażenie przypisania złożonego formularza `x op= y` jest równoważne `x = (T)(x op y)`, z wyjątkiem, że `x` jest oceniane tylko raz. W poniższym przykładzie przedstawiono to zachowanie:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Użytkownik korzysta `+=` również `-=` z operatorów i do subskrybowania i rezygnacji z [subskrypcji wydarzenia,](../keywords/event.md)odpowiednio. Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo operatora i zespolenie

Następująca lista nakazuje operatorom arytmetycznym począwszy od najwyższego pierwszeństwa do najniższego:

- Operatory przyrostkowe `x++` i `x--` zmniejszania
- `++x` Przyrost prefiksu i `--x` dekrementacji i unary `+` i `-` operatorów
- `*`Mnożenie `/`i `%` operatory
- `+` Dodatki `-` i podmioty gospodarcze

Operatory arytmetyczne binarne są lewoskojarzone. Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.

Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora i kojarzenie.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)

## <a name="arithmetic-overflow-and-division-by-zero"></a>Przepełnienie arytmetyczne i dzielenie przez zero

Gdy wynik operacji arytmetycznej wykracza poza zakres możliwych skończonych wartości typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.

### <a name="integer-arithmetic-overflow"></a>Całkowite przepełnienie arytmetyczne

Podział całkowity przez zero zawsze <xref:System.DivideByZeroException>rzuca .

W przypadku przepełnienia arytmetycznego liczby całkowitej kontekst sprawdzania przepełnienia, który można [sprawdzić lub odznaczyć,](../keywords/checked-and-unchecked.md)kontroluje wynikowe zachowanie:

- W kontekście sprawdzonym jeśli przepełnienie dzieje się w wyrażeniu stałym, występuje błąd w czasie kompilacji. W przeciwnym razie, gdy operacja jest <xref:System.OverflowException> wykonywana w czasie wykonywania, jest generowany.
- W kontekście niezaznaczone wynik jest obcinane przez odrzucenie wszelkie bity wysokiego rzędu, które nie mieszczą się w typie docelowym.

Wraz z [instrukcjami zaznaczone i niezaznaczone,](../keywords/checked-and-unchecked.md) można użyć `checked` i `unchecked` operatorów do kontrolowania kontekstu sprawdzania przepełnienia, w którym wyrażenie jest oceniane:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Domyślnie operacje arytmetyczne występują w *niezaznaczonej* kontekście.

### <a name="floating-point-arithmetic-overflow"></a>Przepełnienie arytmetyczne zmiennoprzecinkowe

Operacje arytmetyczne `float` z `double` i typów nigdy nie zgłaszać wyjątek. Wynik operacji arytmetycznych z tymi typami może być jedną ze specjalnych wartości, które reprezentują nieskończoność, a nie liczbę:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

Dla operandów `decimal` typu, przepełnienie arytmetyczne zawsze <xref:System.OverflowException> rzuca i podział przez <xref:System.DivideByZeroException>zero zawsze rzuca .

## <a name="round-off-errors"></a>Błędy zaokrąglania

Ze względu na ogólne ograniczenia przestawnej reprezentacji liczb rzeczywistych i arytmetyki zmiennoprzecinkowej, błędy zaokrąglania mogą występować w obliczeniach z typami zmiennoprzecinkowymi. Oznacza to, że wynik wyrażenia może różnić się od oczekiwanego wyniku matematycznego. Poniższy przykład pokazuje kilka takich przypadków:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Aby uzyskać więcej informacji, zobacz uwagi na stronach odniesienia [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)lub [System.Decimal.](/dotnet/api/system.decimal#remarks)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory arytmetyczne `%` `+`bezzasadne (`++` `--`, `+`, i ) i `-`binarne (`*`, `/`, , i ) operatory `-`arytmetyczne. Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Operatory przyrostkowe i zmniejszania](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operatory przyrostu prefiksu i zmniejszania](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Operator Unary plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Operator minus nieary](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operator oddziału](~/_csharplang/spec/expressions.md#division-operator)
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
