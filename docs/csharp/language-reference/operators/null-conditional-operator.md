---
title: "?? Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="41486-103">??</span><span class="sxs-lookup"><span data-stu-id="41486-103">??</span></span> <span data-ttu-id="41486-104">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="41486-104">Operator (C# Reference)</span></span>
<span data-ttu-id="41486-105">`??` Operator jest nazywany operatora łączenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="41486-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="41486-106">Zwraca argument operacji z lewej strony, jeśli ma on wartość inną niż null; w przeciwnym razie zwraca argument operacji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="41486-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41486-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41486-107">Remarks</span></span>  
 <span data-ttu-id="41486-108">Typ dopuszczający wartość null może reprezentować wartość z domeny typu albo wartość może być niezdefiniowana (w tym przypadku wartość jest równa null).</span><span class="sxs-lookup"><span data-stu-id="41486-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="41486-109">Można użyć `??` wyrazistość składni operatora do zwrócenia ją odpowiednią wartością (argument prawej) kiedy Lewy argument operacji ma typ dopuszczający wartość null, którego wartość jest równa null.</span><span class="sxs-lookup"><span data-stu-id="41486-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="41486-110">Jeśli spróbujesz przypisać typu wartości null na typ wartości niedopuszczający wartości null bez użycia `??` operatora, zostanie wygenerowany błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41486-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="41486-111">Jeśli używasz rzutowanie i typ wartości null jest obecnie Niezdefiniowany `InvalidOperationException` zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="41486-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="41486-112">Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="41486-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="41486-113">Wynik?</span><span class="sxs-lookup"><span data-stu-id="41486-113">The result of a ??</span></span> <span data-ttu-id="41486-114">operator nie jest uważany za stałą, nawet, jeśli oba argumenty są stałe.</span><span class="sxs-lookup"><span data-stu-id="41486-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41486-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="41486-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="41486-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41486-116">See Also</span></span>  
 [<span data-ttu-id="41486-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="41486-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="41486-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="41486-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="41486-119">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="41486-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="41486-120">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="41486-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="41486-121">Jakie dokładnie jest "Unosiło" oznacza?</span><span class="sxs-lookup"><span data-stu-id="41486-121">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)
