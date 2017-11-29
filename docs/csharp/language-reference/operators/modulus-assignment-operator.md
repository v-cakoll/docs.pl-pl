---
title: "Operator %= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="86f01-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="86f01-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="86f01-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="86f01-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f01-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86f01-104">Remarks</span></span>  
 <span data-ttu-id="86f01-105">Za pomocą wyrażenia `%=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="86f01-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="86f01-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="86f01-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="86f01-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="86f01-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="86f01-108">[% Operator](../../../csharp/language-reference/operators/modulus-operator.md) jest wstępnie zdefiniowane na typy liczbowe do obliczenia resztę po dzielenia.</span><span class="sxs-lookup"><span data-stu-id="86f01-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="86f01-109">`%=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="86f01-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86f01-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="86f01-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="86f01-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86f01-111">See Also</span></span>  
 [<span data-ttu-id="86f01-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="86f01-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="86f01-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86f01-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="86f01-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="86f01-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
