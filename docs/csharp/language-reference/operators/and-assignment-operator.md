---
title: "&amp;= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="b0518-102">&amp;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b0518-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="b0518-103">Operator przypisania AND.</span><span class="sxs-lookup"><span data-stu-id="b0518-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0518-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0518-104">Remarks</span></span>  
 <span data-ttu-id="b0518-105">Za pomocą wyrażenia `&=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="b0518-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="b0518-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="b0518-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="b0518-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="b0518-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b0518-108">[& — Operator](../../../csharp/language-reference/operators/and-operator.md) dokonuje logicznego operacji i na całkowite argumenty i logiczny AND `bool` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="b0518-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="b0518-109">`&=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać plik binarny [& — operator](../../../csharp/language-reference/operators/and-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b0518-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0518-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0518-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b0518-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0518-111">See Also</span></span>  
 [<span data-ttu-id="b0518-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b0518-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b0518-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b0518-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b0518-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="b0518-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
