---
title: "Operator % (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d4294-102">Operator % (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d4294-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="d4294-103">`%` Operator oblicza resztę po podzieleniu jego pierwszym argumentem przez jego sekundy.</span><span class="sxs-lookup"><span data-stu-id="d4294-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="d4294-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory resztę.</span><span class="sxs-lookup"><span data-stu-id="d4294-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4294-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4294-105">Remarks</span></span>  
 <span data-ttu-id="d4294-106">Typy definiowane przez użytkownika można przeciążać `%` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d4294-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d4294-107">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="d4294-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4294-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4294-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="d4294-109">Komentarze</span><span class="sxs-lookup"><span data-stu-id="d4294-109">Comments</span></span>  
 <span data-ttu-id="d4294-110">Należy pamiętać, błędów zaokrąglania skojarzonych z typu double.</span><span class="sxs-lookup"><span data-stu-id="d4294-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4294-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4294-111">See Also</span></span>  
 [<span data-ttu-id="d4294-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d4294-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d4294-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d4294-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d4294-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="d4294-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
