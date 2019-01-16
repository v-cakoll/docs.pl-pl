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
ms.openlocfilehash: 8cf6e8871a88e2b37b9531ecbd616289523473c7
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333762"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="0652e-102">-— operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="0652e-102">- operator (C# Reference)</span></span>

<span data-ttu-id="0652e-103">`-` Operator może działać jako jednoargumentowy lub binarny.</span><span class="sxs-lookup"><span data-stu-id="0652e-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="0652e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0652e-104">Remarks</span></span>

<span data-ttu-id="0652e-105">Jednoargumentowy `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="0652e-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="0652e-106">Wynik jednoargumentowy `-` operacja na typ liczbowy jest liczbowe negacji operandu.</span><span class="sxs-lookup"><span data-stu-id="0652e-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="0652e-107">Binarny `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych i wyliczenia na potrzeby odejmowania drugiego operandu od pierwszego.</span><span class="sxs-lookup"><span data-stu-id="0652e-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="0652e-108">Typy delegatów udostępniają dane binarne `-` operatora, który wykonuje usuwanie delegata.</span><span class="sxs-lookup"><span data-stu-id="0652e-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="0652e-109">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `-` binarnej i `-` operatorów.</span><span class="sxs-lookup"><span data-stu-id="0652e-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="0652e-110">Aby uzyskać więcej informacji, zobacz [operator — słowo kluczowe](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="0652e-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="0652e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0652e-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="0652e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0652e-112">See also</span></span>

- [<span data-ttu-id="0652e-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0652e-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0652e-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0652e-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0652e-115">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="0652e-115">C# operators</span></span>](index.md)