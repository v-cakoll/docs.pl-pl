---
title: Przeciążenie operatora — odwołanie do języka C#
description: Dowiedz się, jak przeciążyć operatora języka C# i które operatory języka C# są przeciążalne.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 18da3a22d22f338d2f319d394d50d08e4d35e7eb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121430"
---
# <a name="operator-overloading-c-reference"></a>Przeciążenie operatora (odwołanie do języka C#)

Typ zdefiniowany przez użytkownika może przeciążyć wstępnie zdefiniowany operator języka C#. Oznacza to, że typ może zapewnić niestandardową implementację operacji w przypadku, gdy jeden lub oba argumenty są tego typu. [Przeciążona operatorów](#overloadable-operators) sekcja pokazuje, które operatory Języka C# mogą być przeciążone.

Użyj `operator` słowa kluczowego, aby zadeklarować operatora. Deklaracja operatora musi spełniać następujące zasady:

- Zawiera zarówno `public` `static` modyfikator, jak i modyfikator.
- Operator jednoobaryczny ma jeden parametr wejściowy. Operator binarny ma dwa parametry wejściowe. W każdym przypadku co najmniej jeden `T` `T?` parametr `T` musi mieć typ lub gdzie jest typ, który zawiera deklarację operatora.

Poniższy przykład definiuje uproszczoną strukturę reprezentującą liczbę racjonalną. Struktura przeciąża niektóre [operatory arytmetyczne:](arithmetic-operators.md)

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

Poprzedni przykład można rozszerzyć, [definiując niejawną konwersję](user-defined-conversion-operators.md) z `int` do `Fraction`. Następnie przeciążony operatorów będzie obsługiwać argumenty tych dwóch typów. Oznacza to, że stałoby się możliwe dodanie liczby całkowitej do ułamka i uzyskanie ułamka w wyniku.

Za pomocą `operator` słowa kluczowego można również zdefiniować konwersję typu niestandardowego. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Przeciążeni operatorzy

Poniższa tabela zawiera informacje o przeciążeniu operatorów języka C#:

| Operatory | Przeciążenie |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [!x](boolean-logical-operators.md#logical-negation-operator-) [--](arithmetic-operators.md#decrement-operator---), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), , [true](true-false-operators.md), [false](true-false-operators.md)|Te operatory bezemisowe mogą być przeciążone.|
|[x + y](addition-operator.md), [x - y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), x % [y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-), x = [y](equality-operators.md#equality-operator-), [x , x , x ,](equality-operators.md#inequality-operator-)x [ \< y](comparison-operators.md#less-than-operator-), [x > , x ,](comparison-operators.md#greater-than-operator-)x [>](comparison-operators.md#greater-than-or-equal-operator-) [, x \<](comparison-operators.md#less-than-or-equal-operator-)|Te operatory binarne mogą być przeciążone. Niektóre podmioty gospodarcze muszą być przeciążone parami; Aby uzyskać więcej informacji, zobacz notatkę, która znajduje się w tej tabeli.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Warunkowe operatory logiczne nie mogą być przeciążone. Jednak jeśli typ z przeciążony [ `true` `false` i operatorów](true-false-operators.md) również `&` <code>&#124;</code> przeciąża lub operatora `&&` w <code>&#124;&#124;</code> określony sposób, lub operatora, odpowiednio, mogą być oceniane dla operands tego typu. Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika warunkowe operatory logiczne](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [w specyfikacji języka C#](~/_csharplang/spec/introduction.md).|
|[&#91;i&#93;](member-access-operators.md#indexer-operator-)|Dostęp do elementów nie jest uważany za przeciążony operator, ale można zdefiniować [indeksator](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-expression)|Operator rzutowanego nie może być przeciążony, ale można zdefiniować niestandardowe konwersje typu, które mogą być wykonywane przez wyrażenie rzutowane. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment) [ \* ](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment) [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), , , [^=](boolean-logical-operators.md#compound-assignment)&#124;[ \< \< ](bitwise-and-shift-operators.md#compound-assignment) [=](boolean-logical-operators.md#compound-assignment), ,[>>=](bitwise-and-shift-operators.md#compound-assignment)|Operatory przypisania złożonego nie mogą być jawnie przeciążone. Jednak po przeciążeniu operatora binarnego, odpowiedni operator przypisania złożonego, jeśli istnieje, jest również niejawnie przeciążony. Na przykład `+=` jest `+`oceniany przy użyciu , które mogą być przeciążone.|
|[^x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x.y](member-access-operators.md#member-access-expression-), [c ? t : f](conditional-operator.md), x [?? y](null-coalescing-operator.md), [x ?? = y](null-coalescing-operator.md), [x.. y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md), [, f(x)](member-access-operators.md#invocation-expression-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [delegate](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof,](nameof.md) [new](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Operatory te nie mogą być przeciążone.|

> [!NOTE]
> Operatory porównania muszą być przeciążone parami. Oznacza to, że jeśli którykolwiek z operatorów pary jest przeciążony, drugi operator musi być przeciążony, jak również. Takie pary są następujące:
>
> - `==`i `!=` operatorów
> - `<`i `>` operatorów
> - `<=`i `>=` operatorów

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Przeładowanie operatora](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operatory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md)
- [Wskazówki dotyczące projektowania — przeciążenia operatora](../../../standard/design-guidelines/operator-overloads.md)
- [Wytyczne dotyczące projektowania — operatory równości](../../../standard/design-guidelines/equality-operators.md)
- [Dlaczego przeciążone operatory są zawsze statyczne w języku C#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
