---
title: Przeciążanie operatora — C# odwołanie
description: Dowiedz się, jak C# przeciążać C# operatora i które operatory są przeciążone.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 5fcf9c774592c0fbcdcca951ef99c1a2efa6f05e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922294"
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
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Te operatory jednoargumentowe mogą być przeciążone.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x > > y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Te operatory binarne mogą być przeciążone. Niektóre operatory muszą być przeciążone w parach; Więcej informacji można znaleźć w poniższej tabeli.|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Warunkowe operatory logiczne nie mogą być przeciążone. Jednakże, jeśli typ ze przeciążonym [ `true` operatorem `false` i operatory](true-false-operators.md) przeciążą <code>&#124;</code> `&` operator OR w określony sposób, `&&` lub, <code>&#124;&#124;</code> odpowiednio, można ocenić operator or. operandy tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).|
|[a&#91;i&#93;](member-access-operators.md#indexer-operator-)|Dostęp do elementu nie jest traktowany jako operator z możliwością przeciążenia, ale można zdefiniować [indeksator](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-operator-)|Operator rzutowania nie może być przeciążony, ale można zdefiniować nowe operatory konwersji. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operatory przypisania złożonego nie mogą być jawnie przeciążone. Jednak w przypadku przeciążenia operatora binarnego odpowiedni operator przypisania złożonego, jeśli istnieje, również jest niejawnie przeciążony. Na przykład, `+=` jest oceniane przy `+`użyciu, który może być przeciążony.|
|[x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c? t: f](conditional-operator.md), [x?, y](null-coalescing-operator.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-cast.md#as-operator), [Checked](../keywords/checked.md), [](../keywords/unchecked.md)unchecked, [default](default.md), [Delegat](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Te operatory nie mogą być przeciążone.|

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
