---
title: ++ — Operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: db716f0d8cfe252462abeee9c80baaab880e212b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235647"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="49459-102">++ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="49459-102">++ Operator (C# Reference)</span></span>

<span data-ttu-id="49459-103">Jednoargumentowy operator inkrementacji `++` zwiększa się argumentem operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="49459-103">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="49459-104">Jest obsługiwany w dwóch formach: przyrostkowego operatora inkrementacyjnego `x++`i operator inkrementacji prefiks `++x`.</span><span class="sxs-lookup"><span data-stu-id="49459-104">It's supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

## <a name="postfix-increment-operator"></a><span data-ttu-id="49459-105">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="49459-105">Postfix increment operator</span></span>

<span data-ttu-id="49459-106">Wynik `x++` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="49459-106">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a><span data-ttu-id="49459-107">Operator inkrementacji przedrostka</span><span class="sxs-lookup"><span data-stu-id="49459-107">Prefix increment operator</span></span>

<span data-ttu-id="49459-108">Wynik `++x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="49459-108">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a><span data-ttu-id="49459-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49459-109">Remarks</span></span>

<span data-ttu-id="49459-110">Operator inkrementacji jest wstępnie zdefiniowane dla wszystkich [typów całkowitych](../keywords/integral-types-table.md) (w tym [char](../keywords/char.md) typu), [typów zmiennoprzecinkowych](../keywords/floating-point-types-table.md)oraz wszelkie [wyliczenia](../keywords/enum.md) Typ.</span><span class="sxs-lookup"><span data-stu-id="49459-110">The increment operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="49459-111">Operand operatora inkrementacji musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="49459-111">An operand of the increment operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="49459-112">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="49459-112">Operator overloadability</span></span>

<span data-ttu-id="49459-113">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `++` operatora.</span><span class="sxs-lookup"><span data-stu-id="49459-113">User-defined types can [overload](../keywords/operator.md) the `++` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="49459-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="49459-114">C# language specification</span></span>

<span data-ttu-id="49459-115">Aby uzyskać więcej informacji, zobacz [przyrostka inkrementacji i dekrementacji operatory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) i [przedrostkowe i operatory dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="49459-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49459-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49459-116">See also</span></span>

- [<span data-ttu-id="49459-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="49459-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="49459-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="49459-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="49459-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="49459-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="49459-120">--, operator</span><span class="sxs-lookup"><span data-stu-id="49459-120">-- Operator</span></span>](decrement-operator.md)
- [<span data-ttu-id="49459-121">Porady: inkrementacja i dekrementacja wskaźników</span><span class="sxs-lookup"><span data-stu-id="49459-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
