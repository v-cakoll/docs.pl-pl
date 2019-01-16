---
title: '! Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 6b6d1796032f536aac0be49d4f101c1380b4e98f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333229"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6d2cb-103">!</span><span class="sxs-lookup"><span data-stu-id="6d2cb-103">!</span></span> <span data-ttu-id="6d2cb-104">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6d2cb-104">operator (C# Reference)</span></span>

<span data-ttu-id="6d2cb-105">Operator logiczny negacji (`!`) jest operatorem jednoargumentowym, który neguje swój argument operacji.</span><span class="sxs-lookup"><span data-stu-id="6d2cb-105">The logical negation operator (`!`) is a unary operator that negates its operand.</span></span> <span data-ttu-id="6d2cb-106">Jest zdefiniowany dla typu `bool` i zwraca wartość `true` tylko wtedy, gdy argument operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6d2cb-106">It is defined for `bool` and returns `true` if and only if its operand is `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d2cb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d2cb-107">Remarks</span></span>

<span data-ttu-id="6d2cb-108">Typy definiowane przez użytkownika mogą przeciążać operator `!` (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6d2cb-108">User-defined types can overload the `!` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="6d2cb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d2cb-109">Example</span></span>

[!code-csharp[csRefOperators#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#7)]

## <a name="see-also"></a><span data-ttu-id="6d2cb-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d2cb-110">See also</span></span>

- [<span data-ttu-id="6d2cb-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6d2cb-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d2cb-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6d2cb-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d2cb-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6d2cb-113">C# Operators</span></span>](index.md)