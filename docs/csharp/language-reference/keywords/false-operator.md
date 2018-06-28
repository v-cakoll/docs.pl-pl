---
title: FALSE — operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027840"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="e0b77-102">FALSE — operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e0b77-102">false operator (C# Reference)</span></span>

<span data-ttu-id="e0b77-103">Zwraca [bool](bool.md) wartość `true` do wskazywania operand `false` i zwraca `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="e0b77-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="e0b77-104">Przed C# 2.0 `true` i `false` operatory były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="e0b77-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="e0b77-105">Jednak język teraz udostępnia wbudowaną obsługę dla typów wartości null, a w miarę możliwości należy używać tych zamiast przeładowanie `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="e0b77-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="e0b77-106">Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b77-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="e0b77-107">O wartości null wartości logiczne, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` ponieważ jedną lub obie wartości może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e0b77-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="e0b77-108">Masz przeciążenia obu `true` i `false` operatorom oddzielnie poprawnie Obsługa wartości zerowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="e0b77-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="e0b77-109">Poniższy przykład przedstawia sposób przeciążenia i użyj `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="e0b77-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="e0b77-110">Typ, który overloads `true` i `false` operatorów można używać do kontrolowania wyrażenie w [Jeśli](if-else.md), [czy](do.md), [podczas](while.md), i [ Aby uzyskać](for.md) instrukcje i [wyrażenia warunkowe](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e0b77-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="e0b77-111">Jeśli typ definiuje operator `false`, również muszą definiować operator [true](true.md).</span><span class="sxs-lookup"><span data-stu-id="e0b77-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="e0b77-112">Typem bezpośrednio nie mogą przeciążać operatory logiczne warunkowe [ && ](../operators/conditional-and-operator.md) i [ &#124; &#124; ](../operators/conditional-or-operator.md), ale sam efekt można osiągnąć przez przeładowanie operatorów logicznych regularne operatory i `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="e0b77-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0b77-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0b77-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e0b77-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0b77-114">See also</span></span>

[<span data-ttu-id="e0b77-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0b77-115">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="e0b77-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e0b77-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="e0b77-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e0b77-117">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="e0b77-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="e0b77-118">C# Operators</span></span>](../operators/index.md)  
[<span data-ttu-id="e0b77-119">true</span><span class="sxs-lookup"><span data-stu-id="e0b77-119">true</span></span>](true.md)  