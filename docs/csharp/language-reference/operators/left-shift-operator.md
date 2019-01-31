---
title: << operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 0271c97bc624a8946b90508e9ce39d217a128c05
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261753"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ce17b-102">\<\< Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ce17b-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="ce17b-103">Operator przesunięcia w lewo (`<<`) pierwszy argument operacji lewo o liczbę bitów określoną przez drugim argumentem operacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="ce17b-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="ce17b-104">Typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma wstępnie zdefiniowanych niejawnej konwersji liczbowych do `int`.</span><span class="sxs-lookup"><span data-stu-id="ce17b-104">The type of the second operand must be an [int](../keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce17b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce17b-105">Remarks</span></span>

<span data-ttu-id="ce17b-106">Jeśli pierwszy argument jest [int](../keywords/int.md) lub [uint](../keywords/uint.md) (32-bitowy), licznik przesunięć oblicza niskiego rzędu pięć bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="ce17b-106">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="ce17b-107">Licznik przesunięć rzeczywistego jest bitów 0 do 31.</span><span class="sxs-lookup"><span data-stu-id="ce17b-107">That is, the actual shift count is 0 to 31 bits.</span></span>

<span data-ttu-id="ce17b-108">Jeśli pierwszy argument jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand.</span><span class="sxs-lookup"><span data-stu-id="ce17b-108">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="ce17b-109">Licznik przesunięć rzeczywistego jest 0, 63 bity.</span><span class="sxs-lookup"><span data-stu-id="ce17b-109">That is, the actual shift count is 0 to 63 bits.</span></span>

<span data-ttu-id="ce17b-110">Wszystkie bity wyższego rzędu, które są nie w zakresie typem pierwszego operandu po zmiany zostaną odrzucone i mniej znaczące bity puste są wypełnione przez zera.</span><span class="sxs-lookup"><span data-stu-id="ce17b-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="ce17b-111">Operacje przesunięcia nigdy nie powodują przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="ce17b-111">Shift operations never cause overflows.</span></span>

<span data-ttu-id="ce17b-112">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `<<` — operator (zobacz [operator](../keywords/operator.md)); typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="ce17b-112">User-defined types can overload the `<<` operator (see [operator](../keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="ce17b-113">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="ce17b-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="ce17b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce17b-114">Example</span></span>

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a><span data-ttu-id="ce17b-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="ce17b-115">Comments</span></span>

<span data-ttu-id="ce17b-116">Należy pamiętać, że `i<<1` i `i<<33` dają taki sam efekt, ponieważ 1 i 33 mają ten sam mniej znaczące bity pięć.</span><span class="sxs-lookup"><span data-stu-id="ce17b-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce17b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce17b-117">See also</span></span>

- [<span data-ttu-id="ce17b-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce17b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce17b-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ce17b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce17b-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ce17b-120">C# Operators</span></span>](index.md)
