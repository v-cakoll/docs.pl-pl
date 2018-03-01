---
title: "&amp;&amp;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="ddee5-102">&amp;&amp;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ddee5-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="ddee5-103">Warunkowe — i — operator (`&&`) wykonuje logiczną — i jego `bool` argumentów operacji, ale tylko ocenia jego drugiego operandu w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ddee5-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddee5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddee5-104">Remarks</span></span>  
 <span data-ttu-id="ddee5-105">Operacja</span><span class="sxs-lookup"><span data-stu-id="ddee5-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="ddee5-106">odnosi się do operacji</span><span class="sxs-lookup"><span data-stu-id="ddee5-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="ddee5-107">z wyjątkiem, że jeśli `x` jest `false`, `y` nie jest oceniany, ponieważ wynik operacji i `false` niezależnie od tego, jakie wartości `y` jest.</span><span class="sxs-lookup"><span data-stu-id="ddee5-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="ddee5-108">Jest to określane jako "zwarcia" oceny.</span><span class="sxs-lookup"><span data-stu-id="ddee5-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="ddee5-109">Warunkowe- i operator nie może być przeciążona, overloads regularnych operatorów logicznych, ale i operatory [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) z pewnymi ograniczeniami również pełnią funkcję przeciążenia Operatory logiczne warunkowego.</span><span class="sxs-lookup"><span data-stu-id="ddee5-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddee5-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddee5-110">Example</span></span>  
 <span data-ttu-id="ddee5-111">W poniższym przykładzie wyrażenia warunkowego, w ciągu sekundy `if` instrukcji ocenia tylko pierwszy argument operacji, ponieważ argument zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="ddee5-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ddee5-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ddee5-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ddee5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddee5-113">See Also</span></span>  
 [<span data-ttu-id="ddee5-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ddee5-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ddee5-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ddee5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddee5-116">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="ddee5-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
