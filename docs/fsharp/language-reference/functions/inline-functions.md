---
title: Funkcje śródwierszowe (F#)
description: 'Dowiedz się, jak używać języka F # funkcji śródwierszowych wbudowane bezpośrednio w kodzie.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264561"
---
# <a name="inline-functions"></a><span data-ttu-id="bc449-103">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="bc449-103">Inline Functions</span></span>

<span data-ttu-id="bc449-104">*Funkcje śródwierszowe* funkcji, które są zintegrowane bezpośrednio w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="bc449-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="bc449-105">Za pomocą funkcji śródwierszowych</span><span class="sxs-lookup"><span data-stu-id="bc449-105">Using Inline Functions</span></span>

<span data-ttu-id="bc449-106">Gdy używasz statycznych parametrów typu, wszystkie funkcje, które są parametryzowane przez parametry typu musi być wbudowany.</span><span class="sxs-lookup"><span data-stu-id="bc449-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="bc449-107">Gwarantuje to, że kompilator może rozpoznać te parametry typu.</span><span class="sxs-lookup"><span data-stu-id="bc449-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="bc449-108">Korzystając z parametrami typu generycznego zwykłych istnieje nie tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bc449-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="bc449-109">Inne niż umożliwiające korzystanie z ograniczeniami elementu członkowskiego, wbudowane funkcje może być pomocne w optymalizacji kodu.</span><span class="sxs-lookup"><span data-stu-id="bc449-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="bc449-110">Jednak nadużyciami wbudowanych funkcji może spowodować kodu jako mniej odporne na zmiany w optymalizacji kompilatora i stosowania funkcji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bc449-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="bc449-111">Z tego powodu należy unikać używania wbudowane funkcje optymalizacji, chyba że Wypróbowano innych technik optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="bc449-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="bc449-112">Co wbudowanej funkcji lub metody czasami może poprawić wydajność, ale nie zawsze jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="bc449-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="bc449-113">W związku z tym aby sprawdzić, dzięki czemu wszystkie wbudowane daną funkcję w rzeczywistości ma pozytywny wpływ należy również użyć pomiarów wydajności.</span><span class="sxs-lookup"><span data-stu-id="bc449-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="bc449-114">`inline` Modyfikator może odnosić się do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="bc449-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="bc449-115">Poniższy przykład kodu ilustruje funkcja śródwierszowa najwyższego poziomu, metoda wystąpienia wbudowane i wbudowane metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="bc449-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="bc449-116">Funkcje śródwierszowe i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="bc449-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="bc449-117">Obecność `inline` wpływa na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="bc449-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="bc449-118">Jest to spowodowane wbudowane funkcje mogą mieć parametry typu statycznie rozpoznanych, natomiast nie funkcji innych niż inline.</span><span class="sxs-lookup"><span data-stu-id="bc449-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="bc449-119">Poniższy przykład kodu pokazuje przypadek gdzie `inline` jest przydatne, ponieważ korzysta z funkcji, która ma parametr typu statycznie rozpoznanych `float` operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="bc449-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="bc449-120">Bez `inline` modyfikator, wnioskowanie o typie wymusza funkcji w celu określonego typu, w tym przypadku `int`.</span><span class="sxs-lookup"><span data-stu-id="bc449-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="bc449-121">Ale `inline` modyfikator, funkcja również wywnioskowana ma parametr typu statycznie rozpoznanych.</span><span class="sxs-lookup"><span data-stu-id="bc449-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="bc449-122">Za pomocą `inline` modyfikator, typ jest wnioskowany być następujące:</span><span class="sxs-lookup"><span data-stu-id="bc449-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="bc449-123">Oznacza to, że funkcja ta akceptuje dowolny typ, który obsługuje konwersję **float**.</span><span class="sxs-lookup"><span data-stu-id="bc449-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc449-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc449-124">See also</span></span>

- [<span data-ttu-id="bc449-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="bc449-125">Functions</span></span>](index.md)
- [<span data-ttu-id="bc449-126">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="bc449-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="bc449-127">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="bc449-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
