---
title: Przeciążenie operatora — odwołanie do języka C#
description: Dowiedz się, jak przeciążać operatora C# i które operatory Języka C# są przeładowywalne.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: cdb35b212d5bfc4cc685fbfd6c294066983709df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847303"
---
# <a name="operator-overloading-c-reference"></a>Przeciążenie operatora (odwołanie do Języka C#)

Typ zdefiniowany przez użytkownika może przeciążać wstępnie zdefiniowany operator Języka C#. Oznacza to, że typ może zapewnić implementację niestandardową operacji w przypadku jednego lub obu operands są tego typu. Sekcja [Operatory przeciążenia](#overloadable-operators) pokazuje, które operatory Języka C# mogą być przeciążone.

Użyj `operator` słowa kluczowego, aby zadeklarować operatora. Deklaracja podmiotu gospodarczego musi spełniać następujące zasady:

- Zawiera zarówno `public` modyfikator, jak `static` i modyfikator.
- Operator jednoargumentowy ma jeden parametr wejściowy. Operator binarny ma dwa parametry wejściowe. W każdym przypadku co najmniej jeden `T` `T?` parametr `T` musi mieć typ lub gdzie jest typem, który zawiera deklarację operatora.

Poniższy przykład definiuje uproszczoną strukturę reprezentującą liczbę racjonalną. Struktura przeciąża niektóre [operatory arytmetyczne:](arithmetic-operators.md)

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

Poprzedni przykład można rozszerzyć, [definiując konwersję niejawną](user-defined-conversion-operators.md) z `int` do `Fraction`. Następnie przeciążone operatory będą obsługiwać argumenty tych dwóch typów. Oznacza to, że stałoby się możliwe dodanie liczby całkowitej do ułamka i uzyskanie ułamka w wyniku.

`operator` Słowo kluczowe służy również do definiowania konwersji typu niestandardowego. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Operatorzy z możliwością przeciążenia

Poniższa tabela zawiera informacje na temat przeciążenia operatorów Języka C#:

| Operatory | Przeciążenie |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [!x](boolean-logical-operators.md#logical-negation-operator-) [--](arithmetic-operators.md#decrement-operator---), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [true](true-false-operators.md), [false](true-false-operators.md)|Te operatory niedziałające mogą być przeciążone.|
|[x + y](addition-operator.md), [x - y](subtraction-operator.md), x [ \* y](arithmetic-operators.md#multiplication-operator-), x / [y](arithmetic-operators.md#division-operator-), x [% y](arithmetic-operators.md#remainder-operator-), x & [y](boolean-logical-operators.md#logical-and-operator-), x [&#124; y](boolean-logical-operators.md#logical-or-operator-), x , [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), x >> [y](bitwise-and-shift-operators.md#right-shift-operator-), [x == y](equality-operators.md#equality-operator-), x [!= y](equality-operators.md#inequality-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-)x [ \< y](comparison-operators.md#less-than-operator-), x > [y](comparison-operators.md#greater-than-operator-), [ \<x = y](comparison-operators.md#less-than-or-equal-operator-), x >= [y](comparison-operators.md#greater-than-or-equal-operator-)|Te operatory binarne mogą być przeciążone. Niektóre operatory muszą być przeciążone w parach; Aby uzyskać więcej informacji, zobacz notatkę, która jest zgodna z poniższą tabelą.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Warunkowe operatory logiczne nie mogą być przeciążone. Jednakże jeśli typ z [ `true` przeciążonych `false` i operatorów](true-false-operators.md) również przeciążenia `&&` <code>&#124;&#124;</code> `&` lub <code>&#124;</code> operatora w określony sposób, lub operator, odpowiednio, mogą być oceniane dla operandów tego typu. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne warunkowe zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)|
|[&#91;i&#93;](member-access-operators.md#indexer-operator-)|Dostęp do elementu nie jest uważany za operator przeciążenia, ale można zdefiniować [indeksator](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-operator-)|Operator rzutowania nie może być przeciążony, ale można zdefiniować nowe operatory konwersji. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment)[-=](arithmetic-operators.md#compound-assignment), [ \* ](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment) [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment),&#124;[^=](boolean-logical-operators.md#compound-assignment) [ \< \< ](bitwise-and-shift-operators.md#compound-assignment) [=](boolean-logical-operators.md#compound-assignment), ,[>>=](bitwise-and-shift-operators.md#compound-assignment)|Operatory przypisania złożonego nie mogą być jawnie przeciążone. Jednak podczas przeciążenia operatora binarnego, odpowiedni operator przypisania złożonego, jeśli istnieje, jest również niejawnie przeciążony. Na przykład `+=` jest oceniana przy użyciu `+`, które mogą być przeciążone.|
|[^x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x.y](member-access-operators.md#member-access-operator-), [c ? t : f](conditional-operator.md), x [?? y](null-coalescing-operator.md), x [?? = y](null-coalescing-operator.md), [x.. y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md), , [f(x)](member-access-operators.md#invocation-operator-), [jak](type-testing-and-cast.md#as-operator), [await](await.md), [sprawdzone](../keywords/checked.md), [niezaznaczone](../keywords/unchecked.md), [domyślnie](default.md), [delegat](delegate-operator.md), [jest](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [nowy](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Operatory te nie mogą być przeciążone.|

> [!NOTE]
> Operatory porównania muszą być przeciążone w parach. Oznacza to, że jeśli którykolwiek z operatorów pary jest przeciążony, inny operator musi być przeciążony, jak również. Takie pary są następujące:
>
> - `==`i `!=` operatorów
> - `<`i `>` operatorów
> - `<=`i `>=` operatorów

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Przeciążenie operatora](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operatory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md)
- [Wytyczne projektowe - Przeciążenia operatora](../../../standard/design-guidelines/operator-overloads.md)
- [Wytyczne projektowe - Operatorzy równości](../../../standard/design-guidelines/equality-operators.md)
- [Dlaczego przeciążone operatory są zawsze statyczne w języku C#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
