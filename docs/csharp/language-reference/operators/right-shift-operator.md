---
title: '>> Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 703d4ee50bb9f49c66df029de9c5a280449d11fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255318"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c3ca7-102">>> — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="c3ca7-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="c3ca7-103">Operator przesunięcia w prawo (`>>`) przenosi pierwszy argument operacji w prawo o liczbę bitów określoną przez drugim argumentem operacji.</span><span class="sxs-lookup"><span data-stu-id="c3ca7-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3ca7-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3ca7-104">Remarks</span></span>

<span data-ttu-id="c3ca7-105">Jeśli pierwszy argument jest [int](../keywords/int.md) lub [uint](../keywords/uint.md) (32-bitowy), licznik przesunięć oblicza mniej znaczące bity pięć, drugi operand (drugi operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="c3ca7-105">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>

<span data-ttu-id="c3ca7-106">Jeśli pierwszy argument jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand (drugi operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="c3ca7-106">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>

<span data-ttu-id="c3ca7-107">Jeśli pierwszy argument jest [int](../keywords/int.md) lub [długie](../keywords/long.md), prawy shift jest arytmetycznego przesunięcia (wyższego rzędu pusty bity są ustawione na bit znaku).</span><span class="sxs-lookup"><span data-stu-id="c3ca7-107">If the first operand is an [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="c3ca7-108">Jeśli pierwszy operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), prawy shift to Przesunięcie logiczne (bity wyższego rzędu są wypełnione przez zera).</span><span class="sxs-lookup"><span data-stu-id="c3ca7-108">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>

<span data-ttu-id="c3ca7-109">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `>>` operator; typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="c3ca7-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../keywords/int.md). For more information, see [operator](../keywords/operator.md).</span></span> <span data-ttu-id="c3ca7-110">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="c3ca7-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="c3ca7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3ca7-111">Example</span></span>

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a><span data-ttu-id="c3ca7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3ca7-112">See also</span></span>

- [<span data-ttu-id="c3ca7-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c3ca7-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c3ca7-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c3ca7-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c3ca7-115">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="c3ca7-115">C# operators</span></span>](index.md)