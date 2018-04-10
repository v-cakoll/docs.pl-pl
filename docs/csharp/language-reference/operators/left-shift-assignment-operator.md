---
title: '&lt;&lt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5c2a177182561075442afc3f1b76603c6646bd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="bc6f4-102">&lt;&lt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bc6f4-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="bc6f4-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="bc6f4-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc6f4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc6f4-104">Remarks</span></span>  
 <span data-ttu-id="bc6f4-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="bc6f4-105">An expression of the form</span></span>  
  
```  
x <<= y  
```  
  
 <span data-ttu-id="bc6f4-106">jest szacowana jako</span><span class="sxs-lookup"><span data-stu-id="bc6f4-106">is evaluated as</span></span>  
  
```  
x = x << y  
```  
  
 <span data-ttu-id="bc6f4-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="bc6f4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bc6f4-108">[<< Operator](../../../csharp/language-reference/operators/left-shift-operator.md) przewiduje `x` pozostawionego przez liczbę bitów określony przez `y`.</span><span class="sxs-lookup"><span data-stu-id="bc6f4-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="bc6f4-109">`<<=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bc6f4-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6f4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc6f4-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bc6f4-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc6f4-111">See Also</span></span>  
 [<span data-ttu-id="bc6f4-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="bc6f4-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bc6f4-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bc6f4-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bc6f4-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="bc6f4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
