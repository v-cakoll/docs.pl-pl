---
title: operator () - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333281"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="56b4a-102">() — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="56b4a-102">() operator (C# Reference)</span></span>

<span data-ttu-id="56b4a-103">Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="56b4a-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>

1. <span data-ttu-id="56b4a-104">Określanie rzutowania lub konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="56b4a-104">Specify casts, or type conversions.</span></span>

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. <span data-ttu-id="56b4a-105">Wywoływanie metody lub delegatów.</span><span class="sxs-lookup"><span data-stu-id="56b4a-105">Invoke methods or delegates.</span></span>

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a><span data-ttu-id="56b4a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56b4a-106">Remarks</span></span>

<span data-ttu-id="56b4a-107">Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="56b4a-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="56b4a-108">Aby zdefiniować operatora konwersji, zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md) definiowanie operatorów konwersji.</span><span class="sxs-lookup"><span data-stu-id="56b4a-108">To define a conversion operator, see [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md).</span></span>

 <span data-ttu-id="56b4a-109">Operator `()` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="56b4a-109">The `()` operator cannot be overloaded.</span></span>

 <span data-ttu-id="56b4a-110">Aby uzyskać więcej informacji, zobacz [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md). </span><span class="sxs-lookup"><span data-stu-id="56b4a-110">For more information, see [Casting and Type Conversions](../../programming-guide/types/casting-and-type-conversions.md).</span></span>

 <span data-ttu-id="56b4a-111">Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="56b4a-111">For more information about method invocation, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="56b4a-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="56b4a-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="56b4a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56b4a-113">See also</span></span>

- [<span data-ttu-id="56b4a-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="56b4a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="56b4a-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="56b4a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="56b4a-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="56b4a-116">C# Operators</span></span>](index.md)