---
title: '| Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 19a37bbb54d2ef3e15e4465df05c9b6df705206c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240362"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="67fe4-102">| — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="67fe4-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="67fe4-103">Operatory binarne `|` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="67fe4-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="67fe4-104">W przypadku typów całkowitych `|` oblicza logiczną lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="67fe4-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="67fe4-105">Dla `bool` operandów, `|` oblicza logiczne OR operandów; oznacza to wynik jest `false` tylko wtedy, gdy oba jego operandy są `false`.</span><span class="sxs-lookup"><span data-stu-id="67fe4-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67fe4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67fe4-106">Remarks</span></span>  
 <span data-ttu-id="67fe4-107">Plik binarny `|` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operator warunkowy OR](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="67fe4-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="67fe4-108">W typach definiowanych przez użytkownika można przeciążać operator `|` (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="67fe4-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67fe4-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="67fe4-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="67fe4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67fe4-110">See Also</span></span>

- [<span data-ttu-id="67fe4-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="67fe4-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67fe4-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
