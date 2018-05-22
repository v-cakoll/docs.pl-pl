---
title: Operator || (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: d22e57d097edb0fe52b604e9c6431e167c410f0b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c255b-102">Operator || (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c255b-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="c255b-103">Operator warunkowy OR (`||`) wykonuje logiczne lub z jego `bool` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="c255b-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="c255b-104">Jeśli pierwszy argument operacji daje w wyniku `true`, drugi argument nie jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="c255b-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="c255b-105">Jeśli pierwszy argument operacji daje w wyniku `false`, drugi — operator określa, czy wyrażenie OR jako całość daje w wyniku `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="c255b-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c255b-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c255b-106">Remarks</span></span>  
 <span data-ttu-id="c255b-107">Operacja</span><span class="sxs-lookup"><span data-stu-id="c255b-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="c255b-108">odnosi się do operacji</span><span class="sxs-lookup"><span data-stu-id="c255b-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="c255b-109">z wyjątkiem, że jeśli `x` jest `true`, `y` nie jest oceniany, ponieważ operacja OR `true` niezależnie od wartości `y`.</span><span class="sxs-lookup"><span data-stu-id="c255b-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="c255b-110">To pojęcie jest ogólnie znana jako "zwarcia" oceny.</span><span class="sxs-lookup"><span data-stu-id="c255b-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="c255b-111">Operator warunkowy OR nie może zostać przeciążony, ale overloads regularnych operatorów logicznych i [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) operatorów z pewnymi ograniczeniami również uważa się za przeciążenia Operatory logiczne warunkowe.</span><span class="sxs-lookup"><span data-stu-id="c255b-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c255b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c255b-112">Example</span></span>  
 <span data-ttu-id="c255b-113">W poniższych przykładach wyrażenia, który używa `||` ocenia tylko pierwszy argument operacji.</span><span class="sxs-lookup"><span data-stu-id="c255b-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="c255b-114">Wyrażenie, które używa `|` ocenia oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="c255b-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="c255b-115">W drugim przykładzie wyjątek czasu wykonywania występuje, jeśli obydwa argumenty operacji są oceniane.</span><span class="sxs-lookup"><span data-stu-id="c255b-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c255b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c255b-116">See Also</span></span>  
 [<span data-ttu-id="c255b-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c255b-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c255b-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c255b-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c255b-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c255b-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
