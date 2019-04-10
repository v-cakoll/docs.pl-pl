---
title: '| operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312881"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d03ba-102">| Operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="d03ba-102">| operator (C# Reference)</span></span>

<span data-ttu-id="d03ba-103">Operatory binarne `|` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="d03ba-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="d03ba-104">W przypadku typów całkowitych `|` oblicza logiczną lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="d03ba-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="d03ba-105">Dla `bool` operandów, `|` oblicza logiczne OR operandów; oznacza to wynik jest `false` tylko wtedy, gdy oba jego operandy są `false`.</span><span class="sxs-lookup"><span data-stu-id="d03ba-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d03ba-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d03ba-106">Remarks</span></span>

<span data-ttu-id="d03ba-107">Plik binarny `|` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operator warunkowy OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span><span class="sxs-lookup"><span data-stu-id="d03ba-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span></span>

<span data-ttu-id="d03ba-108">W typach definiowanych przez użytkownika można przeciążać operator `|` (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d03ba-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="d03ba-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d03ba-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="d03ba-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d03ba-110">See also</span></span>

- [<span data-ttu-id="d03ba-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d03ba-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d03ba-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d03ba-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d03ba-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d03ba-113">C# operators</span></span>](index.md)