---
title: '| — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: d95fe29aa7ffab9938e8edc57999445268fe41a8
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001233"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79a23-102">| — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="79a23-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="79a23-103">Operatory binarne `|` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="79a23-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="79a23-104">W przypadku typów całkowitych `|` oblicza logiczną lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="79a23-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="79a23-105">Dla `bool` operandów, `|` oblicza logiczne OR operandów; oznacza to wynik jest `false` tylko wtedy, gdy oba jego operandy są `false`.</span><span class="sxs-lookup"><span data-stu-id="79a23-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79a23-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79a23-106">Remarks</span></span>  
 <span data-ttu-id="79a23-107">Plik binarny `|` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operator warunkowy OR] (warunkowych lub operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="79a23-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator]     (conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="79a23-108">Typy definiowane przez użytkownika mogą przeciążać operator `|` — (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="79a23-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79a23-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="79a23-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79a23-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79a23-110">See Also</span></span>

- [<span data-ttu-id="79a23-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="79a23-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="79a23-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79a23-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="79a23-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="79a23-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
