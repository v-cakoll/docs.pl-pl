---
title: '- Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633006"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="e6491-102">-— operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="e6491-102">- operator (C# Reference)</span></span>

<span data-ttu-id="e6491-103">`-` Operator może działać jako jednoargumentowy lub binarny.</span><span class="sxs-lookup"><span data-stu-id="e6491-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6491-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6491-104">Remarks</span></span>

<span data-ttu-id="e6491-105">Jednoargumentowy `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="e6491-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="e6491-106">Wynik jednoargumentowy `-` operacja na typ liczbowy jest liczbowe negacji operandu.</span><span class="sxs-lookup"><span data-stu-id="e6491-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="e6491-107">Binarny `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych i wyliczenia na potrzeby odejmowania drugiego operandu od pierwszego.</span><span class="sxs-lookup"><span data-stu-id="e6491-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="e6491-108">Typy delegatów udostępniają dane binarne `-` operatora, który wykonuje usuwanie delegata.</span><span class="sxs-lookup"><span data-stu-id="e6491-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="e6491-109">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `-` binarnej i `-` operatorów.</span><span class="sxs-lookup"><span data-stu-id="e6491-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="e6491-110">Aby uzyskać więcej informacji, zobacz [operator — słowo kluczowe](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="e6491-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6491-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6491-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="e6491-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6491-112">See also</span></span>

- [<span data-ttu-id="e6491-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e6491-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e6491-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e6491-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e6491-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="e6491-115">C# operators</span></span>](index.md)
