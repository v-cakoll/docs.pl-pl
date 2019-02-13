---
title: '>> Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219727"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="59d31-102">>> — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="59d31-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="59d31-103">Operator przesunięcia w prawo `>>` bezpośrednio przenosi swojego pierwszego operandu przez liczbę bitów definicją drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="59d31-103">The right-shift operator `>>` shifts its first operand right by the number of bits defined by its second operand.</span></span> <span data-ttu-id="59d31-104">Obsługa wszystkich typów całkowitych `>>` operatora.</span><span class="sxs-lookup"><span data-stu-id="59d31-104">All integer types support the `>>` operator.</span></span> <span data-ttu-id="59d31-105">Jednak typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.</span><span class="sxs-lookup"><span data-stu-id="59d31-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="59d31-106">Operacja przesunięcia w prawo powoduje odrzucenie mniej znaczące bity.</span><span class="sxs-lookup"><span data-stu-id="59d31-106">The right-shift operation discards the low-order bits.</span></span> <span data-ttu-id="59d31-107">Pozycje bitów pusty wyższego rzędu jest ustawiona na podstawie typu pierwszego operandu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="59d31-107">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="59d31-108">Jeśli pierwszy operand jest typu [int](../keywords/int.md) lub [długie](../keywords/long.md), operator przesunięcia w prawo wykonuje **arytmetyczne** shift: wartość najbardziej znaczący bit (bit znaku) pierwszego argument operacji jest propagowana do pozycji bitów pusty wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="59d31-108">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an **arithmetic** shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="59d31-109">Oznacza to, pozycje bitów pusty wyższego rzędu są ustawiane na zero, jeśli pierwszy argument jest ujemna i ustawiony na wartość 1, jeśli jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="59d31-109">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

- <span data-ttu-id="59d31-110">Jeśli pierwszy operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), operator przesunięcia w prawo wykonuje **logiczne** shift: pozycje bitów pusty wyższego rzędu są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="59d31-110">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a **logical** shift: the high-order empty bit positions are always set to zero.</span></span>

<span data-ttu-id="59d31-111">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="59d31-111">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a><span data-ttu-id="59d31-112">Licznik przesunięć</span><span class="sxs-lookup"><span data-stu-id="59d31-112">Shift count</span></span>

<span data-ttu-id="59d31-113">Dla wyrażenia `x >> count`, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="59d31-113">For the expression `x >> count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="59d31-114">Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest nadawana przez niskiego rzędu *pięć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="59d31-114">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="59d31-115">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="59d31-115">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="59d31-116">Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest nadawana przez niskiego rzędu *sześć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="59d31-116">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="59d31-117">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="59d31-117">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="59d31-118">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="59d31-118">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="59d31-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59d31-119">Remarks</span></span>

<span data-ttu-id="59d31-120">Operacje przesunięcia nigdy nie powodują przepełnienia i działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.</span><span class="sxs-lookup"><span data-stu-id="59d31-120">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="59d31-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="59d31-121">Operator overloadability</span></span>

<span data-ttu-id="59d31-122">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `>>` operatora.</span><span class="sxs-lookup"><span data-stu-id="59d31-122">User-defined types can [overload](../keywords/operator.md) the `>>` operator.</span></span> <span data-ttu-id="59d31-123">Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `>>` operatora, musi być typem pierwszego operandu `T` i typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="59d31-123">If a user-defined type `T` overloads the `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="59d31-124">Gdy `>>` operator jest przeciążony, [operator przypisania przesunięcia w prawo](right-shift-assignment-operator.md) `>>=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="59d31-124">When the `>>` operator is overloaded, the [right-shift assignment operator](right-shift-assignment-operator.md) `>>=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59d31-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="59d31-125">C# language specification</span></span>

<span data-ttu-id="59d31-126">Aby uzyskać więcej informacji, zobacz [operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="59d31-126">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59d31-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59d31-127">See also</span></span>

- [<span data-ttu-id="59d31-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="59d31-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59d31-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="59d31-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59d31-130">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="59d31-130">C# operators</span></span>](index.md)
- [<span data-ttu-id="59d31-131"><< — operator</span><span class="sxs-lookup"><span data-stu-id="59d31-131"><< operator</span></span>](left-shift-operator.md)