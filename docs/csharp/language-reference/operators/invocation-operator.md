---
title: () — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 29097dc4aa0bf712b9b2beda4450820a66472ba7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891522"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d70bb-102">() — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d70bb-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="d70bb-103">Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="d70bb-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="d70bb-104">Określanie rzutowania lub konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="d70bb-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="d70bb-105">Wywoływanie metody lub delegatów.</span><span class="sxs-lookup"><span data-stu-id="d70bb-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="d70bb-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d70bb-106">Remarks</span></span>  
 <span data-ttu-id="d70bb-107">Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d70bb-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="d70bb-108">Aby zdefiniować operatora konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md) definiowanie operatorów konwersji.</span><span class="sxs-lookup"><span data-stu-id="d70bb-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="d70bb-109">Operator `()` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="d70bb-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="d70bb-110">Aby uzyskać więcej informacji, zobacz [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md). </span><span class="sxs-lookup"><span data-stu-id="d70bb-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="d70bb-111">Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="d70bb-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d70bb-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d70bb-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d70bb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d70bb-113">See Also</span></span>

- [<span data-ttu-id="d70bb-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d70bb-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d70bb-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d70bb-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d70bb-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d70bb-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
