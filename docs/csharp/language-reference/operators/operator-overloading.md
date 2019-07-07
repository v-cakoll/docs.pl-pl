---
title: Operator przeciążenia - C# odwołania
description: Dowiedz się, jak przeciążenia C# operator, który C# są operatory z możliwością przeciążenia.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: f9085f2a550dfacc670857a70f5b22de9e028107
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610610"
---
# <a name="operator-overloading-c-reference"></a>Przeładowanie operatora (C# odwołania)

Typ zdefiniowany przez użytkownika może doprowadzić do przeciążenia wstępnie zdefiniowanej C# operatora. Oznacza to typem może zapewnić niestandardową implementację operacją, gdy jeden lub oba operandy są typu. [Operatory z możliwością przeciążenia](#overloadable-operators) sekcji pokazano, które C# operatory mogą być przeciążone.

Użyj `operator` — słowo kluczowe do deklarowania operatora. Deklaracja operatora musi spełniać następujące reguły:

- Obejmuje zarówno `public` i `static` modyfikator.
- Operator jednoargumentowy przyjmuje jeden parametr. Operator binarny przyjmuje dwa parametry. W każdym przypadku co najmniej jeden parametr musi mieć typ `T` lub `T?` gdzie `T` to typ, który zawiera deklarację operatora.

W poniższym przykładzie zdefiniowano uproszczoną strukturę do reprezentowania Liczba wymierna. Struktury przeciążenia część [operatorów arytmetycznych](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

## <a name="overloadable-operators"></a>Operatory z możliwością przeciążenia

Poniższa tabela zawiera informacje o overloadability z C# operatory:

| Operatory | Overloadability |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---) , [true](true-false-operators.md), [false](true-false-operators.md)|Te operatory jednoargumentowe, mogą być przeciążone.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|Te operatory dwuargumentowe mogą być przeciążone. Niektórych operatorów muszą być przeciążone w parach; Aby uzyskać więcej informacji zobacz uwagi poniżej tej tabeli.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Nie mogą być przeciążone operatory logiczne warunkowe. Jednak jeśli typ za pomocą przeciążonych [ `true` i `false` operatory](true-false-operators.md) także przeciążenia `&` lub <code>&#124;</code> operatora w określony sposób, `&&` lub <code>&#124;&#124;</code> operatora odpowiednio może zostać obliczone dla argumentów typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Dostęp do elementu nie jest uważany za Oczekiwano operatora, ale można zdefiniować [indeksatora](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Nie może zostać Przeciążony operator rzutowania, ale można definiować nowych operatorów konwersji (zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md)).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Złożone operatory nie mogą być przeciążone jawnie do przypisania. Jednak po użytkownik przeciążenia operatora binarnego, odpowiedniego operatora przypisania złożonego, jeśli jest również niejawnie przeciążona. Na przykład `+=` jest obliczane przy użyciu `+`, które mogą być przeciążone.|
|[=](assignment-operator.md), [. ](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [?? ](null-coalescing-operator.md), [ -> ](pointer-related-operators.md#pointer-member-access-operator--), [ => ](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [jako](type-testing-and-conversion-operators.md#as-operator), [zaznaczone ](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [domyślne](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegować](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [jest](type-testing-and-conversion-operators.md#is-operator), [nameof](../keywords/nameof.md), [nowe](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Te operatory nie mogą być przeciążone.|

> [!NOTE]
> Musi być przeciążone operatory porównania w parach. Oznacza to jeśli albo operator pary jest przeciążona, innych operatora musi być przeciążane także. Takie pary są następujące:
>
> - `==` i `!=` operatorów
> - `<` i `>` operatorów
> - `<=` i `>=` operatorów

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Przeładowanie operatora](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operatory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Dlaczego są przeciążone operatory zawsze statycznych w języku C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
