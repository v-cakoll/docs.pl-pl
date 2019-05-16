---
title: Wnioskowanie o typie
description: Dowiedz się, jak F# kompilator wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.
ms.date: 05/16/2016
ms.openlocfilehash: ab1a4aa8df4312287df749d5d6d0ea2858091152
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641677"
---
# <a name="type-inference"></a><span data-ttu-id="20764-103">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="20764-103">Type Inference</span></span>

<span data-ttu-id="20764-104">W tym temacie opisano sposób, w jaki F# kompilator wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="20764-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="20764-105">Wnioskowanie o typie ogólnie rzecz biorąc</span><span class="sxs-lookup"><span data-stu-id="20764-105">Type Inference in General</span></span>

<span data-ttu-id="20764-106">Koncepcja wnioskowanie o typie jest, że trzeba określić typy F# konstrukcji, z wyjątkiem sytuacji, gdy kompilator ostatecznie nie można wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="20764-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="20764-107">Pomijanie informacji o typie jawne nie oznacza to, że F# jest dynamicznie typizowanym językiem, lub że wartości w F# czy ze słabą kontrolą typów.</span><span class="sxs-lookup"><span data-stu-id="20764-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="20764-108">F#jest statycznie typizowanym językiem, co oznacza, że kompilator wywnioskowuje, że typem dokładne dla każdego konstrukcji podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="20764-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="20764-109">Jeśli nie jest wystarczająco dużo informacji dla kompilatora wywnioskowanie typów każdego konstrukcji, dodatkowy typ informacji, musisz podać zwykle przez dodawanie adnotacji typu jawnego gdzieś w kodzie.</span><span class="sxs-lookup"><span data-stu-id="20764-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="20764-110">Wnioskowanie parametrów i zwracanych typów</span><span class="sxs-lookup"><span data-stu-id="20764-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="20764-111">Na liście parametrów nie należy określić typ każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="20764-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="20764-112">I jeszcze F# jest statycznie typizowanym językiem, a w związku z tym każdy wartość i wyrażenie ma określony typ w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="20764-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="20764-113">Dla tych typów, które nie są jawnie określone kompilator wnioskuje typ na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="20764-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="20764-114">Jeśli typ nie jest w przeciwnym razie określone, wynika to ogólny.</span><span class="sxs-lookup"><span data-stu-id="20764-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="20764-115">Jeśli kod używa wartości niespójnie, w taki sposób, to nie pojedynczy wywnioskować typ, który spełnia wszystkie przypadki użycia wartości, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="20764-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="20764-116">Zwracany typ funkcji jest określana przez typ ostatniego wyrażenia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="20764-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="20764-117">Na przykład w poniższym kodzie, typy parametrów `a` i `b` i zwracany typ jest wnioskowany jako `int` ponieważ literału `100` typu `int`.</span><span class="sxs-lookup"><span data-stu-id="20764-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="20764-118">Może mieć wpływ na wnioskowanie o typie, zmieniając literały.</span><span class="sxs-lookup"><span data-stu-id="20764-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="20764-119">Jeśli wprowadzisz `100` `uint32` , dodając sufiks `u`, typy `a`, `b`, i wartość zwracana jest wywnioskowana `uint32`.</span><span class="sxs-lookup"><span data-stu-id="20764-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="20764-120">Możesz również zmieniać wnioskowanie o typie przy użyciu innych konstrukcji, sugerujących ograniczenia dotyczące typu, na przykład funkcji i metod, które działają z określonego typu.</span><span class="sxs-lookup"><span data-stu-id="20764-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="20764-121">Ponadto można zastosować jawnego typu adnotacji do parametrów funkcji lub metody lub zmiennych w wyrażeniach, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="20764-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="20764-122">Błędy wyniku, jeśli występują konflikty między różnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="20764-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="20764-123">Można również jawnie określić wartość zwracaną przez funkcję, udostępniając adnotacji typu po wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="20764-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="20764-124">Często zdarza, gdzie adnotacji typu przydaje się w parametrze jest, gdy parametr jest typu obiektu, a użytkownik chce, należy użyć członka.</span><span class="sxs-lookup"><span data-stu-id="20764-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="20764-125">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="20764-125">Automatic Generalization</span></span>

<span data-ttu-id="20764-126">Jeśli kod funkcji nie jest zależny od typu parametru, kompilator traktuje parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="20764-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="20764-127">Jest to nazywane *automatyczna Generalizacja*, i może być zaawansowanym pomocy do pisania kodu ogólny bez zwiększania stopnia złożoności.</span><span class="sxs-lookup"><span data-stu-id="20764-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="20764-128">Na przykład następująca funkcja łączy dwa parametry dowolnego typu w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20764-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="20764-129">Typ jest wnioskowany jako</span><span class="sxs-lookup"><span data-stu-id="20764-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="20764-130">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="20764-130">Additional Information</span></span>

<span data-ttu-id="20764-131">Wnioskowanie o typie jest opisany bardziej szczegółowo w F# specyfikacji języka.</span><span class="sxs-lookup"><span data-stu-id="20764-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="20764-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20764-132">See also</span></span>

- [<span data-ttu-id="20764-133">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="20764-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
