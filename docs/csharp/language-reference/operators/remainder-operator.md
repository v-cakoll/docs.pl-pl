---
title: Operator % — C# odwołania
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: a5c12b6683e35cc1ec2d40446dd0ed068c3d2552
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236482"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="396e8-102">Operator % (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="396e8-102">% Operator (C# Reference)</span></span>

<span data-ttu-id="396e8-103">Operator reszty `%` oblicza pozostałą po podzieleniu pierwszy argument operacji za drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="396e8-103">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

<span data-ttu-id="396e8-104">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `%` operatora.</span><span class="sxs-lookup"><span data-stu-id="396e8-104">User-defined types can [overload](../keywords/operator.md) the `%` operator.</span></span> <span data-ttu-id="396e8-105">Gdy `%` jest przeciążona, [operator przypisania reszty](remainder-assignment-operator.md) `%=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="396e8-105">When the `%` is overloaded, the [remainder assignment operator](remainder-assignment-operator.md) `%=` is also implicitly overloaded.</span></span>

<span data-ttu-id="396e8-106">Wszystkie typy liczbowe obsługuje operator reszty.</span><span class="sxs-lookup"><span data-stu-id="396e8-106">All numeric types support the remainder operator.</span></span>

## <a name="integer-remainder"></a><span data-ttu-id="396e8-107">Pozostała liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="396e8-107">Integer remainder</span></span>
  
<span data-ttu-id="396e8-108">Dla argumentów liczby całkowitej, wynik `a % b` wartość jest generowany przez `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="396e8-108">For the integer operands, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="396e8-109">Znak resztę różna od zera jest taka sama, jak w przypadku pierwszego operandu w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="396e8-109">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a><span data-ttu-id="396e8-110">Zmiennoprzecinkową resztę</span><span class="sxs-lookup"><span data-stu-id="396e8-110">Floating-point remainder</span></span>

<span data-ttu-id="396e8-111">Dla [float](../keywords/float.md) i [double](../keywords/double.md) operandów, wynik `x % y` dla skończonego `x` i `y` jest wartością `z` tak, aby</span><span class="sxs-lookup"><span data-stu-id="396e8-111">For the [float](../keywords/float.md) and [double](../keywords/double.md) operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="396e8-112">znak `z`, jeśli różna od zera, jest taka sama jak znak `x`;</span><span class="sxs-lookup"><span data-stu-id="396e8-112">the sign of `z`, if non-zero, is the same as the sign of `x`;</span></span>
- <span data-ttu-id="396e8-113">wartość bezwzględna `z` wartość jest generowany przez `|x| - n * |y|` gdzie `n` jest największa możliwa liczba całkowita, która jest mniejsza niż lub równa `|x| / |y|` i `|x|` i `|y|` są wartości bezwzględne dla `x` i `y`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="396e8-113">the absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

<span data-ttu-id="396e8-114">Aby uzyskać informacje o zachowanie `%` operator nieskończona argumentów, zobacz [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="396e8-114">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="396e8-115">Ta metoda obliczeniowych reszta jest odpowiednikiem używanym dla liczby całkowitej argumentów, ale różni się od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="396e8-115">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="396e8-116">Operacja Reminder, który jest zgodny z IEEE 754, należy użyć <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="396e8-116">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="396e8-117">W poniższym przykładzie pokazano zachowanie operator reszty dla `float` i `double` argumenty:</span><span class="sxs-lookup"><span data-stu-id="396e8-117">The following example demonstrates the behavior of the remainder operator for `float` and `double` operands:</span></span>

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

<span data-ttu-id="396e8-118">Należy pamiętać, błędy zaokrąglania, które mogą być skojarzone z typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="396e8-118">Note the round-off errors that can be associated with the floating-point types.</span></span>

<span data-ttu-id="396e8-119">Dla [dziesiętna](../keywords/decimal.md) argumentów operacji, operator reszty `%` jest odpowiednikiem [operator reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="396e8-119">For the [decimal](../keywords/decimal.md) operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

## <a name="see-also"></a><span data-ttu-id="396e8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="396e8-120">See also</span></span>

- [<span data-ttu-id="396e8-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="396e8-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="396e8-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="396e8-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="396e8-123">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="396e8-123">C# Operators</span></span>](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
