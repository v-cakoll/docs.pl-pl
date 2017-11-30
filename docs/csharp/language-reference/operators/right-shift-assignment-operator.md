---
title: "&gt;&gt;= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="666e8-102">&gt;&gt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="666e8-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="666e8-103">Operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="666e8-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="666e8-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="666e8-104">Remarks</span></span>  
 <span data-ttu-id="666e8-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="666e8-105">An expression of the form</span></span>  
  
```  
x >>= y  
```  
  
 <span data-ttu-id="666e8-106">jest szacowana jako</span><span class="sxs-lookup"><span data-stu-id="666e8-106">is evaluated as</span></span>  
  
```  
x = x >> y  
```  
  
 <span data-ttu-id="666e8-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="666e8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="666e8-108">[>> Operator](../../../csharp/language-reference/operators/right-shift-operator.md) przewiduje `x` prawej przez wartość określoną w `y`.</span><span class="sxs-lookup"><span data-stu-id="666e8-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="666e8-109">>> = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="666e8-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="666e8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="666e8-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="666e8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="666e8-111">See Also</span></span>  
 [<span data-ttu-id="666e8-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="666e8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="666e8-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="666e8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="666e8-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="666e8-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
