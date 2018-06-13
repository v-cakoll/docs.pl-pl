---
title: Funkcje śródwierszowe (F#)
description: 'Dowiedz się, jak używać F # funkcji śródwierszowych zintegrowanych bezpośrednio z kodu wywołującego.'
ms.date: 05/16/2016
ms.openlocfilehash: d265f9b4e828946c510bd8e84b14d5236ab511fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563511"
---
# <a name="inline-functions"></a><span data-ttu-id="3af72-103">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="3af72-103">Inline Functions</span></span>

<span data-ttu-id="3af72-104">*Funkcje śródwierszowe* są funkcje, które są zintegrowane bezpośrednio do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="3af72-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="3af72-105">Przy użyciu funkcji śródwierszowych</span><span class="sxs-lookup"><span data-stu-id="3af72-105">Using Inline Functions</span></span>
<span data-ttu-id="3af72-106">Gdy używane są parametry typu na statycznych, wszystkie funkcje, które mają zdefiniowane przez parametry typu musi być wbudowany.</span><span class="sxs-lookup"><span data-stu-id="3af72-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="3af72-107">Gwarantuje to, że kompilator rozpozna tych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="3af72-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="3af72-108">Parametry typu ogólnego zwykłej nie ma żadnych tych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="3af72-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="3af72-109">Inne niż umożliwia używanie ograniczenia elementu członkowskiego, wbudowane funkcje mogą być pomocne w Optymalizacja kodu.</span><span class="sxs-lookup"><span data-stu-id="3af72-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="3af72-110">Zbyt częste używanie funkcji śródwierszowych może jednak spowodować kodu za mniej odporne na zmiany w optymalizacje kompilatora i stosowania funkcji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3af72-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="3af72-111">Z tego powodu należy unikać używania wbudowane funkcje optymalizacji, chyba że nastąpiła innych technik optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="3af72-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="3af72-112">Tworzenie wbudowanej funkcji lub metody czasami może poprawić wydajność, ale które nie zawsze jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="3af72-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="3af72-113">W związku z tym należy też używać wskaźników wydajności, aby sprawdzić, czy wprowadzania żadnych wbudowanego daną funkcję w rzeczywistości mają pozytywny wpływ.</span><span class="sxs-lookup"><span data-stu-id="3af72-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="3af72-114">`inline` Modyfikator może odnosić się do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="3af72-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="3af72-115">Poniższy przykładowy kod przedstawia wbudowanej funkcji najwyższego poziomu, metody wystąpienia wbudowanego i statyczne metodą wbudowaną.</span><span class="sxs-lookup"><span data-stu-id="3af72-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="3af72-116">Funkcje śródwierszowe a wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="3af72-116">Inline Functions and Type Inference</span></span>
<span data-ttu-id="3af72-117">Obecność `inline` wpływa na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="3af72-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="3af72-118">Jest to spowodowane wbudowane funkcje mogą mieć statycznie rozwiązywane parametry typu podczas, gdy nie można z systemem innym niż wbudowane funkcje.</span><span class="sxs-lookup"><span data-stu-id="3af72-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="3af72-119">Poniższy przykład kodu pokazuje przypadku gdzie `inline` jest przydatne, ponieważ w przypadku korzystania z funkcji, która ma parametr typu statycznie rozwiązywane `float` operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="3af72-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="3af72-120">Bez `inline` , modyfikator wnioskowanie o typie wymusza funkcja do wykonania określonego typu, w tym przypadku `int`.</span><span class="sxs-lookup"><span data-stu-id="3af72-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="3af72-121">Ale `inline` modyfikator, funkcja jest również wartością parametru typu statycznie rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="3af72-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="3af72-122">Z `inline` modyfikator, typu jest wywnioskowany być następujące:</span><span class="sxs-lookup"><span data-stu-id="3af72-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="3af72-123">Oznacza to, że funkcja akceptuje dowolnego typu, który obsługuje konwersji na **float**.</span><span class="sxs-lookup"><span data-stu-id="3af72-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="3af72-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3af72-124">See Also</span></span>
[<span data-ttu-id="3af72-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="3af72-125">Functions</span></span>](index.md)

[<span data-ttu-id="3af72-126">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="3af72-126">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="3af72-127">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="3af72-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
