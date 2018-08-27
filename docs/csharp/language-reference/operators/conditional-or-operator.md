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
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925543"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="26734-102">Operator || (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="26734-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="26734-103">Operator warunkowy OR (`||`) wykonuje logiczne OR z jego `bool` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="26734-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="26734-104">Jeśli pierwszy operand ma wartość `true`, drugi argument nie jest poddawany ocenie.</span><span class="sxs-lookup"><span data-stu-id="26734-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="26734-105">Jeśli pierwszy operand ma wartość `false`, drugi operator określa, czy wyrażenie OR jako całość daje w wyniku `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="26734-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26734-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26734-106">Remarks</span></span>  
 <span data-ttu-id="26734-107">Operacja</span><span class="sxs-lookup"><span data-stu-id="26734-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="26734-108">odnosi się do operacji</span><span class="sxs-lookup"><span data-stu-id="26734-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="26734-109">z wyjątkiem, że jeśli `x` jest `true`, `y` nie jest oceniany, ponieważ jest w operacji OR `true` niezależnie od wartości `y`.</span><span class="sxs-lookup"><span data-stu-id="26734-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="26734-110">Takie podejście jest znana jako "ocena zwarcia".</span><span class="sxs-lookup"><span data-stu-id="26734-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="26734-111">Operator warunkowy OR nie mogą być przeciążone, ale przeciążenia regularne operatorów logicznych i [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) operatorów z pewnymi ograniczeniami również uważana za przeciążenia Operatory logiczne warunkowe.</span><span class="sxs-lookup"><span data-stu-id="26734-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26734-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="26734-112">Example</span></span>  
 <span data-ttu-id="26734-113">W poniższych przykładach wyrażenia, który używa `||` oblicza tylko pierwszy operand.</span><span class="sxs-lookup"><span data-stu-id="26734-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="26734-114">Wyrażenie, które używa `|` ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="26734-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="26734-115">W drugim przykładzie wyjątek czasu wykonywania występuje, gdy oba operandy są oceniane.</span><span class="sxs-lookup"><span data-stu-id="26734-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="26734-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26734-116">See Also</span></span>

- [<span data-ttu-id="26734-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="26734-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="26734-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="26734-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="26734-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="26734-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
