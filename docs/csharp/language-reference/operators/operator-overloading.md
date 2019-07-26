---
title: Przeciążanie operatora — C# odwołanie
description: Dowiedz się, jak C# przeciążać C# operatora i które operatory są przeciążone.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 2a4e6129c39c624429ecbc45de5cf9b644b28572
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363051"
---
# <a name="operator-overloading-c-reference"></a>Przeciążanie operatora (C# odwołanie)

Typ zdefiniowany przez użytkownika może przeciążać wstępnie C# zdefiniowany operator. Oznacza to, że typ może zapewnić niestandardową implementację operacji, gdy jeden lub oba operandy są tego typu. Sekcja [Operatory](#overloadable-operators) z możliwością przeciążenia pokazuje, C# które operatory mogą być przeciążone.

Użyj słowa `operator` kluczowego, aby zadeklarować operator. Deklaracja operatora musi spełniać następujące zasady:

- Zawiera `public` `static` modyfikator a i.
- Operator jednoargumentowy przyjmuje jeden parametr. Operator binarny przyjmuje dwa parametry. W każdym przypadku co najmniej jeden parametr musi mieć typ `T` lub `T?` gdzie `T` jest typem, który zawiera deklarację operatora.

Poniższy przykład definiuje uproszczoną strukturę do reprezentowania liczby wymiernej. Struktura przeciąża niektóre [Operatory arytmetyczne](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

Możesz poszerzyć poprzedni przykład, definiując niejawną konwersję `int` z `Fraction`na. Następnie przeciążone operatory obsługują argumenty tych dwóch typów. Oznacza to, że można dodać liczbę całkowitą do ułamka i uzyskać ułamek jako wynik.

Możesz również użyć słowa `operator` kluczowego, aby zdefiniować niestandardową konwersję typu. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Operatory z możliwością przeciążenia

Poniższa tabela zawiera informacje dotyczące przeciążania C# operatorów:

| Operatory | Przeciążenie |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [](true-false-operators.md) [](true-false-operators.md) , [--](arithmetic-operators.md#decrement-operator---)true, false|Te operatory jednoargumentowe mogą być przeciążone.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-) , [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-),[>=](comparison-operators.md#greater-than-or-equal-operator-)|Te operatory binarne mogą być przeciążone. Niektóre operatory muszą być przeciążone w parach; Więcej informacji można znaleźć w poniższej tabeli.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Warunkowe operatory logiczne nie mogą być przeciążone. Jednakże, jeśli typ ze przeciążonym [ `true` operatorem `false` i operatory](true-false-operators.md) przeciążą <code>&#124;</code> `&` operator OR w określony sposób, `&&` lub, <code>&#124;&#124;</code> odpowiednio, można ocenić operator or. operandy tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Dostęp do elementu nie jest traktowany jako operator z możliwością przeciążenia, ale można zdefiniować [indeksator](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Operator rzutowania nie może być przeciążony, ale można zdefiniować nowe operatory konwersji. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operatory przypisania złożonego nie mogą być jawnie przeciążone. Jednak w przypadku przeciążenia operatora binarnego odpowiedni operator przypisania złożonego, jeśli istnieje, również jest niejawnie przeciążony. Na przykład, `+=` jest oceniane przy `+`użyciu, który może być przeciążony.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [?](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md),, [f (x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-conversion-operators.md#as-operator), [Checked](../keywords/checked.md), unchecked, [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [Delegate](delegate-operator.md), [is](type-testing-and-conversion-operators.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [](../keywords/unchecked.md) [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Te operatory nie mogą być przeciążone.|

> [!NOTE]
> Operatory porównania muszą być przeciążone w parach. Oznacza to, że jeśli oba operatory pary są przeciążone, drugi operator musi być przeciążony. Takie pary są następujące:
>
> - `==`Operatory `!=` i
> - `<`Operatory `>` i
> - `<=`Operatory `>=` i

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Przeciążanie operatora](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operatory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Zdefiniowane przez użytkownika operatory konwersji](user-defined-conversion-operators.md)
- [Dlaczego przeciążone operatory zawsze są statyczne C#w?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
