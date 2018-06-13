---
title: '?: — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 68e7daac63a5f7d9bd1f48adfdee973bd695a13e
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457219"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="20a4c-102">?: — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="20a4c-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="20a4c-103">Operator warunkowy (`?:`), powszechnie znane jako trójargumentowy operator warunkowy zwraca jeden z dwóch wartości w zależności od wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="20a4c-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="20a4c-104">Poniżej przedstawiono składnię operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="20a4c-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="20a4c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20a4c-105">Remarks</span></span>  
 <span data-ttu-id="20a4c-106">`condition` Musi być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="20a4c-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="20a4c-107">Jeśli `condition` jest `true`, `first_expression` jest obliczane i staje się wynik.</span><span class="sxs-lookup"><span data-stu-id="20a4c-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="20a4c-108">Jeśli `condition` jest `false`, `second_expression` jest obliczane i staje się wynik.</span><span class="sxs-lookup"><span data-stu-id="20a4c-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="20a4c-109">Obliczane jest tylko jedno z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="20a4c-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="20a4c-110">Typ elementu `first_expression` i `second_expression` muszą być takie same lub niejawna konwersja musi istnieć z jednego typu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="20a4c-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="20a4c-111">Można wyrazić obliczeń, które w przeciwnym razie mogą wymagać `if-else` konstrukcji więcej zwięzłym, przy użyciu operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="20a4c-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="20a4c-112">Na przykład w poniższym kodzie użyto najpierw `if` instrukcji, a następnie operator warunkowy do klasyfikowania całkowitą jako dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="20a4c-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="20a4c-113">Operator warunkowy ma łączność do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="20a4c-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="20a4c-114">Wyrażenie `a ? b : c ? d : e` jest szacowana jako `a ? b : (c ? d : e)`, nie jako `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="20a4c-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="20a4c-115">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="20a4c-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20a4c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="20a4c-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="20a4c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20a4c-117">See Also</span></span>  
 [<span data-ttu-id="20a4c-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="20a4c-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="20a4c-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="20a4c-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="20a4c-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="20a4c-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="20a4c-121">if-else</span><span class="sxs-lookup"><span data-stu-id="20a4c-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 <span data-ttu-id="20a4c-122">[Operatory ?. i ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="20a4c-122">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
 [<span data-ttu-id="20a4c-123">??, operator</span><span class="sxs-lookup"><span data-stu-id="20a4c-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
