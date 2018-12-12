---
title: / — Operator - C# odwołania
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286536"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8d07b-102">/ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8d07b-102">/ Operator (C# Reference)</span></span>

<span data-ttu-id="8d07b-103">Operator dzielenia `/` dzieli pierwszy argument operacji za drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="8d07b-103">The division operator `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="8d07b-104">Wszystkie typy liczbowe obsługuje operator dzielenia.</span><span class="sxs-lookup"><span data-stu-id="8d07b-104">All numeric types support the division operator.</span></span>

## <a name="integer-division"></a><span data-ttu-id="8d07b-105">Dzielenie liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="8d07b-105">Integer division</span></span>

<span data-ttu-id="8d07b-106">Dla argumentów typu Liczba całkowita, wynikiem `/` operator jest typu Liczba całkowita i równości iloraz dwóch argumentów operacji, zaokrąglana w kierunku zera:</span><span class="sxs-lookup"><span data-stu-id="8d07b-106">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

<span data-ttu-id="8d07b-107">Aby uzyskać iloraz dwóch argumentów operacji jako liczba zmiennoprzecinkowa, należy użyć `float`, `double`, lub `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="8d07b-107">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a><span data-ttu-id="8d07b-108">Dzielenie zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="8d07b-108">Floating-point division</span></span>

<span data-ttu-id="8d07b-109">Aby uzyskać `float`, `double`, i `decimal` typów, wynikiem `/` operatora jest równy ilorazowi dwóch argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="8d07b-109">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

<span data-ttu-id="8d07b-110">Jeśli jeden z operandów jest `decimal`, inny argument może być żadnego `float` ani `double`, ponieważ ani `float` ani `double` jest niejawnie konwertowany na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8d07b-110">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="8d07b-111">Należy jawnie przekonwertować `float` lub `double` operand `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="8d07b-111">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="8d07b-112">Aby uzyskać więcej informacji na temat niejawne konwersje między typów liczbowych, zobacz [Tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="8d07b-112">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8d07b-113">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="8d07b-113">Operator overloadability</span></span>

<span data-ttu-id="8d07b-114">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `/` operatora.</span><span class="sxs-lookup"><span data-stu-id="8d07b-114">User-defined types can [overload](../keywords/operator.md) the `/` operator.</span></span> <span data-ttu-id="8d07b-115">Gdy `/` operator jest przeciążony, [operator przypisania dzielenia](division-assignment-operator.md) `/=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="8d07b-115">When the `/` operator is overloaded, the [division assignment operator](division-assignment-operator.md) `/=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d07b-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8d07b-116">C# language specification</span></span>

<span data-ttu-id="8d07b-117">Aby uzyskać więcej informacji, zobacz [operator dzielenia](~/_csharplang/spec/expressions.md#division-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d07b-117">For more information, see the [Division operator](~/_csharplang/spec/expressions.md#division-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d07b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d07b-118">See also</span></span>

- [<span data-ttu-id="8d07b-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8d07b-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d07b-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8d07b-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d07b-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8d07b-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8d07b-122">%, operator</span><span class="sxs-lookup"><span data-stu-id="8d07b-122">% Operator</span></span>](remainder-operator.md)
