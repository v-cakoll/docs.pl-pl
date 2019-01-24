---
title: Operatory z możliwością przeciążenia - C# Programming Guide
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: ce346920c301aabf652ea0e141d4a2f66a3e8b2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616254"
---
# <a name="overloadable-operators-c-programming-guide"></a>Operatory z możliwością przeciążenia (C# Programming Guide)

C# umożliwia typy zdefiniowane przez użytkownika próby przeciążania operatorów, definiując statyczne funkcje Członkowskie przy użyciu [operator](../../language-reference/keywords/operator.md) — słowo kluczowe. Nie wszystkie operatory mogą być przeciążone, i inne ograniczenia, mają zgodnie z opisem w poniższej tabeli:

| Operatory | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/logical-negation-operator.md), [~](../../language-reference/operators/bitwise-complement-operator.md), [++](../../language-reference/operators/increment-operator.md), [--](../../language-reference/operators/decrement-operator.md) , [true](../../language-reference/keywords/true.md), [false](../../language-reference/keywords/false.md)|Te operatory jednoargumentowe, mogą być przeciążone.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/multiplication-operator.md), [/](../../language-reference/operators/division-operator.md), [%](../../language-reference/operators/modulus-operator.md), [&](../../language-reference/operators/and-operator.md), [&#124;](../../language-reference/operators/or-operator.md), [^](../../language-reference/operators/xor-operator.md), [\<\<](../../language-reference/operators/left-shift-operator.md), [>>](../../language-reference/operators/right-shift-operator.md)|Te operatory dwuargumentowe mogą być przeciążone.|
|[==](../../language-reference/operators/equality-comparison-operator.md), [!=](../../language-reference/operators/not-equal-operator.md), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|Operatory porównania mogą być przeciążone (ale patrz Notatka poniżej tej tabeli).|
|[&&](../../language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../language-reference/operators/conditional-or-operator.md)|Nie mogą być przeciążone operatory logiczne warunkowe, ale są obliczane przy użyciu `&` i <code>&#124;</code>, które mogą być przeciążone.|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|Operatora indeksowania tablicy nie mogą być przeciążone, ale można zdefiniować [indeksatory](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Nie może zostać Przeciążony operator rzutowania, ale można definiować nowych operatorów konwersji (zobacz [jawne](../../language-reference/keywords/explicit.md) i [niejawne](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/multiplication-assignment-operator.md), [/=](../../language-reference/operators/division-assignment-operator.md), [%=](../../language-reference/operators/modulus-assignment-operator.md), [&=](../../language-reference/operators/and-assignment-operator.md), [&#124;=](../../language-reference/operators/or-assignment-operator.md), [^=](../../language-reference/operators/xor-assignment-operator.md), [\<\<=](../../language-reference/operators/left-shift-assignment-operator.md), [>>=](../../language-reference/operators/right-shift-assignment-operator.md)|Operatory przypisania nie może być jawnie przeciążona. Jednak jeśli można przeciążać operatora binarnego, odpowiedniego operatora przypisania, jest również niejawnie przeciążona. Na przykład `+=` jest obliczane przy użyciu `+`, które mogą być przeciążone.|
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
