---
title: Funkcje śródwierszowe
description: Dowiedz się, F# jak używać funkcji wbudowanych, które są zintegrowane bezpośrednio z wywoływanym kodem.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630680"
---
# <a name="inline-functions"></a><span data-ttu-id="56fe1-103">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="56fe1-103">Inline Functions</span></span>

<span data-ttu-id="56fe1-104">*Funkcje wbudowane* to funkcje, które są zintegrowane bezpośrednio z wywoływanym kodem.</span><span class="sxs-lookup"><span data-stu-id="56fe1-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="56fe1-105">Korzystanie z funkcji wbudowanych</span><span class="sxs-lookup"><span data-stu-id="56fe1-105">Using Inline Functions</span></span>

<span data-ttu-id="56fe1-106">W przypadku używania parametrów typu statycznego wszystkie funkcje, które są sparametryzowane przez parametry typu, muszą być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="56fe1-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="56fe1-107">Gwarantuje to, że kompilator może rozpoznać te parametry typu.</span><span class="sxs-lookup"><span data-stu-id="56fe1-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="56fe1-108">W przypadku używania zwykłych parametrów typu ogólnego nie ma takich ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="56fe1-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="56fe1-109">Oprócz włączania ograniczeń elementu członkowskiego funkcje wbudowane mogą być pomocne podczas optymalizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="56fe1-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="56fe1-110">Jednak użycie funkcji wbudowanych może spowodować, że kod będzie mniej odporny na zmiany optymalizacji kompilatora i implementację funkcji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="56fe1-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="56fe1-111">Z tego powodu należy unikać używania funkcji wbudowanych do optymalizacji, chyba że ponowią wszystkie inne techniki optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="56fe1-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="56fe1-112">Wprowadzenie funkcji lub metody w tekście może czasami zwiększyć wydajność, ale nie zawsze jest to przypadek.</span><span class="sxs-lookup"><span data-stu-id="56fe1-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="56fe1-113">W związku z tym należy również użyć pomiarów wydajności, aby upewnić się, że udostępnianie każdej funkcji wbudowanej w rzeczywistości ma pozytywny wpływ.</span><span class="sxs-lookup"><span data-stu-id="56fe1-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="56fe1-114">`inline` Modyfikator można zastosować do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody klasy.</span><span class="sxs-lookup"><span data-stu-id="56fe1-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="56fe1-115">Poniższy przykład kodu ilustruje funkcję wbudowaną na najwyższym poziomie, wbudowaną metodę wystąpienia i wbudowaną metodę statyczną.</span><span class="sxs-lookup"><span data-stu-id="56fe1-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="56fe1-116">Funkcje śródwierszowe i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="56fe1-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="56fe1-117">Obecność `inline` ma wpływ na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="56fe1-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="56fe1-118">Wynika to z faktu, że funkcje wbudowane mogą mieć statycznie rozpoznane parametry typu, podczas gdy nie można korzystać z funkcji wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="56fe1-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="56fe1-119">Poniższy przykład kodu pokazuje przypadek, gdzie `inline` jest przydatne, ponieważ używana jest funkcja, która ma parametr typu statycznie rozpoznany `float` , Operator konwersji.</span><span class="sxs-lookup"><span data-stu-id="56fe1-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="56fe1-120">Bez modyfikatora, wnioskowanie typu wymusza, aby funkcja przejęcia określonego typu w tym przypadku `int`. `inline`</span><span class="sxs-lookup"><span data-stu-id="56fe1-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="56fe1-121">Ale z `inline` modyfikatorem, funkcja jest również wnioskowana, aby miał statycznie rozpoznany parametr typu.</span><span class="sxs-lookup"><span data-stu-id="56fe1-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="56fe1-122">`inline` Z modyfikatorem, typ jest wywnioskowany jako następujący:</span><span class="sxs-lookup"><span data-stu-id="56fe1-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="56fe1-123">Oznacza to, że funkcja akceptuje dowolny typ, który obsługuje konwersjęna wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="56fe1-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="56fe1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56fe1-124">See also</span></span>

- [<span data-ttu-id="56fe1-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="56fe1-125">Functions</span></span>](index.md)
- [<span data-ttu-id="56fe1-126">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="56fe1-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="56fe1-127">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="56fe1-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
