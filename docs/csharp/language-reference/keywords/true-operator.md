---
title: TRUE — operator (C# odwołania)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130679"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="34f73-102">TRUE — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="34f73-102">true operator (C# Reference)</span></span>

<span data-ttu-id="34f73-103">Zwraca [bool](bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true.</span><span class="sxs-lookup"><span data-stu-id="34f73-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="34f73-104">Jeśli typ definiuje `true` operatora on również muszą definiować [false — operator](false-operator.md).</span><span class="sxs-lookup"><span data-stu-id="34f73-104">If a type defines the `true` operator, it must also define the [false operator](false-operator.md).</span></span> <span data-ttu-id="34f73-105">`true` i `false` operatorów nie ma gwarancji uzupełniają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="34f73-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

<span data-ttu-id="34f73-106">Na przykład, który definiuje zarówno `true` i `false` operatorów, zobacz [false — operator](false-operator.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="34f73-106">For the example that defines both `true` and `false` operators, see the [false operator](false-operator.md) article.</span></span>

> [!TIP]
> <span data-ttu-id="34f73-107">Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu logicznego.</span><span class="sxs-lookup"><span data-stu-id="34f73-107">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="34f73-108">Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="34f73-108">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="34f73-109">Jeśli typ za pomocą zdefiniowanego `true` operator [przeciążenia](operator.md) [operator logiczny OR](../operators/or-operator.md) `|` w określony sposób, [warunkowego logicznego operatora OR](../operators/conditional-or-operator.md) `||`, czyli short-circuiting, mogą być obliczane w przypadku argumentów operacji tego typu.</span><span class="sxs-lookup"><span data-stu-id="34f73-109">If a type with the defined `true` operator [overloads](operator.md) the [logical OR operator](../operators/or-operator.md) `|` in a certain way, the [conditional logical OR operator](../operators/conditional-or-operator.md) `||`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="34f73-110">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="34f73-110">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="34f73-111">Typ za pomocą zdefiniowanego `true` operator może być typ wyniku wyrażenia warunkowego kontroli w [Jeśli](if-else.md), [czy](do.md), [podczas](while.md), i [ Aby uzyskać](for.md) instrukcji i [operator warunkowy `?:` ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="34f73-111">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span> <span data-ttu-id="34f73-112">Aby uzyskać więcej informacji, zobacz [wyrażeń logicznych](~/_csharplang/spec/expressions.md#boolean-expressions) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="34f73-112">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34f73-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34f73-113">See also</span></span>

- [<span data-ttu-id="34f73-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="34f73-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="34f73-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="34f73-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="34f73-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="34f73-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="34f73-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="34f73-117">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="34f73-118">`true` literał</span><span class="sxs-lookup"><span data-stu-id="34f73-118">`true` literal</span></span>](true-literal.md)