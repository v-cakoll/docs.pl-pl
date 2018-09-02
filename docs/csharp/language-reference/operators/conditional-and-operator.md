---
title: '&amp;&amp; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388296"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="52664-102">&amp;&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="52664-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="52664-103">Operator warunkowy i - AND, (`&&`) wykonuje koniunkcję jego argumentów typu `bool`. W razie potrzeby ocenia wartośc tylko drugiego z argumentów.</span><span class="sxs-lookup"><span data-stu-id="52664-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52664-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52664-104">Remarks</span></span>  
 <span data-ttu-id="52664-105">Operacja</span><span class="sxs-lookup"><span data-stu-id="52664-105">The operation</span></span>  
  
```csharp  
x && y  
```  
  
 <span data-ttu-id="52664-106">odnosi się do operacji</span><span class="sxs-lookup"><span data-stu-id="52664-106">corresponds to the operation</span></span>  
  
```csharp  
x & y  
```  
  
 <span data-ttu-id="52664-107">Z wyjątkiem tego, że jeśli `x` jest `false`, to `y` nie zostanie ocenione, ponieważ wynikiem operacji będzie `false` niezależnie od tego, jaką wartość ma `y`.</span><span class="sxs-lookup"><span data-stu-id="52664-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="52664-108">Taki zabieg nazywamy oceną typu „short-circuit”.</span><span class="sxs-lookup"><span data-stu-id="52664-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="52664-109">Operator warunkowy 'AND' nie może być przeciążony, ale przeciążenia zwykłych operatorów logicznych oraz [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) są dopuszczalne z odpowiednimi ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="52664-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52664-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="52664-110">Example</span></span>  
 <span data-ttu-id="52664-111">W poniższym przykładzie drugi blok warunkowy `if` ocenia tylko pierwszy argumentów operacji AND, ponieważ ten zwraca wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="52664-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="52664-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="52664-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="52664-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52664-113">See Also</span></span>

- [<span data-ttu-id="52664-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="52664-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="52664-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52664-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="52664-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="52664-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
