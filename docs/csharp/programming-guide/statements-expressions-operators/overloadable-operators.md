---
title: Operatory z możliwością przeciążenia - C# Programming Guide
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: d474f5663448af39333b41c76d3fc93b2a7a187d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678642"
---
# <a name="overloadable-operators-c-programming-guide"></a>Operatory z możliwością przeciążenia (C# Programming Guide)

C# umożliwia typy zdefiniowane przez użytkownika próby przeciążania operatorów, definiując statyczne funkcje Członkowskie przy użyciu [operator](../../language-reference/keywords/operator.md) — słowo kluczowe. Nie wszystkie operatory mogą być przeciążone, i inne ograniczenia, mają zgodnie z opisem w poniższej tabeli:

| Operatory | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---) , [true](../../language-reference/keywords/true-false-operators.md), [false](../../language-reference/keywords/true-false-operators.md)|Te operatory jednoargumentowe, mogą być przeciążone.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|Te operatory dwuargumentowe mogą być przeciążone.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|Operatory porównania mogą być przeciążone (ale patrz Notatka poniżej tej tabeli).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Nie mogą być przeciążone operatory logiczne warunkowe, ale są obliczane przy użyciu `&` i <code>&#124;</code>, które mogą być przeciążone.|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|Operatora indeksowania tablicy nie mogą być przeciążone, ale można zdefiniować [indeksatory](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Nie może zostać Przeciążony operator rzutowania, ale można definiować nowych operatorów konwersji (zobacz [jawne](../../language-reference/keywords/explicit.md) i [niejawne](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|Operatory przypisania nie może być jawnie przeciążona. Jednak jeśli można przeciążać operatora binarnego, odpowiedniego operatora przypisania, jest również niejawnie przeciążona. Na przykład `+=` jest obliczane przy użyciu `+`, które mogą być przeciążone.|
|[=](../../language-reference/operators/assignment-operator.md), [. ](../../language-reference/operators/member-access-operator.md), [?:](../../language-reference/operators/conditional-operator.md), [?? ](../../language-reference/operators/null-coalescing-operator.md), [ -> ](../../language-reference/operators/dereference-operator.md), [ => ](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/invocation-operator.md), [jako](../../language-reference/keywords/as.md), [zaznaczone ](../../language-reference/keywords/checked.md), [unchecked](../../language-reference/keywords/unchecked.md), [domyślne](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegować](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [jest](../../language-reference/keywords/is.md), [nowe](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/keywords/typeof.md)|Te operatory nie mogą być przeciążone.|

> [!NOTE]
> Operatory porównania, jeżeli przeciążona, musi być przeciążane parami; oznacza to jeśli `==` jest przeciążona, `!=` musi również być przeciążony. Występuje również sytuacja odwrotna ma wartość true, jeżeli przeciążenie `!=` wymaga przeciążenie dla elementu `==`. To samo dotyczy operatory porównania `<` i `>` i `<=` i `>=`.

Aby uzyskać informacje o tym, jak próby przeciążania operatora, zobacz [operator](../../language-reference/keywords/operator.md) artykułu — słowo kluczowe.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Instrukcje, wyrażenia i operatory](index.md)
- [Operatory](operators.md)
- [Operatory języka C#](../../language-reference/operators/index.md)
- [Dlaczego są przeciążone operatory zawsze statycznych w języku C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
