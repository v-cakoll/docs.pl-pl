---
title: "Funkcje śródwierszowe (F#)"
description: "Dowiedz się, jak używać F # funkcji śródwierszowych zintegrowanych bezpośrednio z kodu wywołującego."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a><span data-ttu-id="aa753-104">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="aa753-104">Inline Functions</span></span>

<span data-ttu-id="aa753-105">*Funkcje śródwierszowe* są funkcje, które są zintegrowane bezpośrednio do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="aa753-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="aa753-106">Przy użyciu funkcji śródwierszowych</span><span class="sxs-lookup"><span data-stu-id="aa753-106">Using Inline Functions</span></span>
<span data-ttu-id="aa753-107">Gdy używane są parametry typu na statycznych, wszystkie funkcje, które mają zdefiniowane przez parametry typu musi być wbudowany.</span><span class="sxs-lookup"><span data-stu-id="aa753-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="aa753-108">Gwarantuje to, że kompilator rozpozna tych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="aa753-108">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="aa753-109">Parametry typu ogólnego zwykłej nie ma żadnych tych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="aa753-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="aa753-110">Inne niż umożliwia używanie ograniczenia elementu członkowskiego, wbudowane funkcje mogą być pomocne w Optymalizacja kodu.</span><span class="sxs-lookup"><span data-stu-id="aa753-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="aa753-111">Zbyt częste używanie funkcji śródwierszowych może jednak spowodować kodu za mniej odporne na zmiany w optymalizacje kompilatora i stosowania funkcji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="aa753-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="aa753-112">Z tego powodu należy unikać używania wbudowane funkcje optymalizacji, chyba że nastąpiła innych technik optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="aa753-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="aa753-113">Tworzenie wbudowanej funkcji lub metody czasami może poprawić wydajność, ale które nie zawsze jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="aa753-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="aa753-114">W związku z tym należy też używać wskaźników wydajności, aby sprawdzić, czy wprowadzania żadnych wbudowanego daną funkcję w rzeczywistości mają pozytywny wpływ.</span><span class="sxs-lookup"><span data-stu-id="aa753-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="aa753-115">`inline` Modyfikator może odnosić się do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="aa753-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="aa753-116">Poniższy przykładowy kod przedstawia wbudowanej funkcji najwyższego poziomu, metody wystąpienia wbudowanego i statyczne metodą wbudowaną.</span><span class="sxs-lookup"><span data-stu-id="aa753-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="aa753-117">Funkcje śródwierszowe a wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="aa753-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="aa753-118">Obecność `inline` wpływa na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="aa753-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="aa753-119">Jest to spowodowane wbudowane funkcje mogą mieć statycznie rozwiązywane parametry typu podczas, gdy nie można z systemem innym niż wbudowane funkcje.</span><span class="sxs-lookup"><span data-stu-id="aa753-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="aa753-120">Poniższy przykład kodu pokazuje przypadku gdzie `inline` jest przydatne, ponieważ w przypadku korzystania z funkcji, która ma parametr typu statycznie rozwiązywane `float` operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="aa753-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="aa753-121">Bez `inline` , modyfikator wnioskowanie o typie wymusza funkcja do wykonania określonego typu, w tym przypadku `int`.</span><span class="sxs-lookup"><span data-stu-id="aa753-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="aa753-122">Ale `inline` modyfikator, funkcja jest również wartością parametru typu statycznie rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="aa753-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="aa753-123">Z `inline` modyfikator, typu jest wywnioskowany być następujące:</span><span class="sxs-lookup"><span data-stu-id="aa753-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="aa753-124">Oznacza to, że funkcja akceptuje dowolnego typu, który obsługuje konwersji na **float**.</span><span class="sxs-lookup"><span data-stu-id="aa753-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="aa753-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa753-125">See Also</span></span>
[<span data-ttu-id="aa753-126">Funkcje</span><span class="sxs-lookup"><span data-stu-id="aa753-126">Functions</span></span>](index.md)

[<span data-ttu-id="aa753-127">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="aa753-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="aa753-128">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="aa753-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
