---
title: --Operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 4fba014e8dabc13cd874e17f23515dc29d93f24b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236931"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="89aff-102">Operator -- (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="89aff-102">-- Operator (C# Reference)</span></span>

<span data-ttu-id="89aff-103">Jednoargumentowy operator dekrementacji `--` zmniejsza argumentem operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="89aff-103">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="89aff-104">Jest obsługiwany w dwóch formach: przyrostkowego operatora dekrementacyjnego `x--`i operator dekrementacji prefiksu, `--x`.</span><span class="sxs-lookup"><span data-stu-id="89aff-104">It's supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

## <a name="postfix-decrement-operator"></a><span data-ttu-id="89aff-105">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="89aff-105">Postfix decrement operator</span></span>

<span data-ttu-id="89aff-106">Wynik `x--` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="89aff-106">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a><span data-ttu-id="89aff-107">Operator dekrementacji przedrostka</span><span class="sxs-lookup"><span data-stu-id="89aff-107">Prefix decrement operator</span></span>

<span data-ttu-id="89aff-108">Wynik `--x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="89aff-108">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a><span data-ttu-id="89aff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89aff-109">Remarks</span></span>

<span data-ttu-id="89aff-110">Operator dekrementacji jest wstępnie zdefiniowane dla wszystkich [typów całkowitych](../keywords/integral-types-table.md) (w tym [char](../keywords/char.md) typu), [typów zmiennoprzecinkowych](../keywords/floating-point-types-table.md)oraz wszelkie [wyliczenia](../keywords/enum.md) Typ.</span><span class="sxs-lookup"><span data-stu-id="89aff-110">The decrement operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="89aff-111">Argument operacji operatora dekrementacyjnego musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="89aff-111">An operand of the decrement operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="89aff-112">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="89aff-112">Operator overloadability</span></span>

<span data-ttu-id="89aff-113">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `--` operatora.</span><span class="sxs-lookup"><span data-stu-id="89aff-113">User-defined types can [overload](../keywords/operator.md) the `--` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89aff-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="89aff-114">C# language specification</span></span>

<span data-ttu-id="89aff-115">Aby uzyskać więcej informacji, zobacz [przyrostka inkrementacji i dekrementacji operatory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) i [przedrostkowe i operatory dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="89aff-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89aff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89aff-116">See also</span></span>

- [<span data-ttu-id="89aff-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="89aff-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89aff-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="89aff-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="89aff-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="89aff-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="89aff-120">++, operator</span><span class="sxs-lookup"><span data-stu-id="89aff-120">++ Operator</span></span>](increment-operator.md)
- [<span data-ttu-id="89aff-121">Porady: inkrementacja i dekrementacja wskaźników</span><span class="sxs-lookup"><span data-stu-id="89aff-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
