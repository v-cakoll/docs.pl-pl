---
title: << operator - C# odwołania
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219440"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="01f9e-102">\<\< Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="01f9e-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="01f9e-103">Operator przesunięcia w lewo `<<` pierwszy argument operacji lewo o liczbę bitów definicją drugim argumentem operacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="01f9e-103">The left-shift operator `<<` shifts its first operand left by the number of bits defined by its second operand.</span></span> <span data-ttu-id="01f9e-104">Obsługa wszystkich typów całkowitych `<<` operatora.</span><span class="sxs-lookup"><span data-stu-id="01f9e-104">All integer types support the `<<` operator.</span></span> <span data-ttu-id="01f9e-105">Jednak typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.</span><span class="sxs-lookup"><span data-stu-id="01f9e-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="01f9e-106">Najbardziej znaczących bitów, które są poza zakresem typu wyniku są odrzucane, a następnie pozycje bitów pusty niskiego rzędu są ustawiane na zero, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="01f9e-106">The high-order bits that are outside the range of the result type are discarded, and the low-order empty bit positions are set to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a><span data-ttu-id="01f9e-107">Licznik przesunięć</span><span class="sxs-lookup"><span data-stu-id="01f9e-107">Shift count</span></span>

<span data-ttu-id="01f9e-108">Dla wyrażenia `x << count`, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="01f9e-108">For the expression `x << count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="01f9e-109">Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest nadawana przez niskiego rzędu *pięć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="01f9e-109">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="01f9e-110">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="01f9e-110">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="01f9e-111">Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest nadawana przez niskiego rzędu *sześć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="01f9e-111">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="01f9e-112">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="01f9e-112">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="01f9e-113">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="01f9e-113">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="01f9e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01f9e-114">Remarks</span></span>

<span data-ttu-id="01f9e-115">Operacje przesunięcia nigdy nie powodują przepełnienia i działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.</span><span class="sxs-lookup"><span data-stu-id="01f9e-115">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="01f9e-116">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="01f9e-116">Operator overloadability</span></span>

<span data-ttu-id="01f9e-117">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `<<` operatora.</span><span class="sxs-lookup"><span data-stu-id="01f9e-117">User-defined types can [overload](../keywords/operator.md) the `<<` operator.</span></span> <span data-ttu-id="01f9e-118">Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `<<` operatora, musi być typem pierwszego operandu `T` i typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="01f9e-118">If a user-defined type `T` overloads the `<<` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="01f9e-119">Gdy `<<` operator jest przeciążony, [operator przypisania przesunięcia w lewo](left-shift-assignment-operator.md) `<<=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="01f9e-119">When the `<<` operator is overloaded, the [left-shift assignment operator](left-shift-assignment-operator.md) `<<=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="01f9e-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="01f9e-120">C# language specification</span></span>

<span data-ttu-id="01f9e-121">Aby uzyskać więcej informacji, zobacz [operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="01f9e-121">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01f9e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01f9e-122">See also</span></span>

- [<span data-ttu-id="01f9e-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="01f9e-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="01f9e-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="01f9e-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="01f9e-125">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="01f9e-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="01f9e-126">>> — operator</span><span class="sxs-lookup"><span data-stu-id="01f9e-126">>> operator</span></span>](right-shift-operator.md)
