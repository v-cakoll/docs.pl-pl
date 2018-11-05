---
title: Wnioskowanie o typie (F#)
description: Dowiedz się, jak kompilator F# wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.
ms.date: 05/16/2016
ms.openlocfilehash: fd826ac48fb9a70aa6f4ff746599c11b7e21a02e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865699"
---
# <a name="type-inference"></a><span data-ttu-id="b918d-103">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="b918d-103">Type Inference</span></span>

<span data-ttu-id="b918d-104">W tym temacie opisano, jak kompilator F# wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="b918d-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="b918d-105">Wnioskowanie o typie ogólnie rzecz biorąc</span><span class="sxs-lookup"><span data-stu-id="b918d-105">Type Inference in General</span></span>

<span data-ttu-id="b918d-106">Koncepcja wnioskowanie o typie jest, czy jest konieczne określanie typów konstrukcje F#, z wyjątkiem sytuacji, gdy kompilator ostatecznie nie można wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="b918d-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="b918d-107">Pomijanie informacji o typie jawne nie oznacza, że F# to język o typach określanych dynamicznie lub że wartości w F# jest słabo z kontrolą typów.</span><span class="sxs-lookup"><span data-stu-id="b918d-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="b918d-108">Język F# jest statycznie typizowanym językiem, co oznacza, że kompilator wywnioskowuje, że typem dokładne dla każdego konstrukcji podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b918d-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="b918d-109">Jeśli nie jest wystarczająco dużo informacji dla kompilatora wywnioskowanie typów każdego konstrukcji, dodatkowy typ informacji, musisz podać zwykle przez dodawanie adnotacji typu jawnego gdzieś w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b918d-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="b918d-110">Wnioskowanie parametrów i zwracanych typów</span><span class="sxs-lookup"><span data-stu-id="b918d-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="b918d-111">Na liście parametrów nie należy określić typ każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="b918d-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="b918d-112">I jeszcze, F# to język statycznie wpisane, a w związku z tym każdy wartość i wyrażenie ma określony typ w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b918d-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="b918d-113">Dla tych typów, które nie są jawnie określone kompilator wnioskuje typ na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b918d-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="b918d-114">Jeśli typ nie jest w przeciwnym razie określone, wynika to ogólny.</span><span class="sxs-lookup"><span data-stu-id="b918d-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="b918d-115">Jeśli kod używa wartości niespójnie, w taki sposób, to nie pojedynczy wywnioskować typ, który spełnia wszystkie przypadki użycia wartości, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="b918d-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="b918d-116">Zwracany typ funkcji jest określana przez typ ostatniego wyrażenia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b918d-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="b918d-117">Na przykład w poniższym kodzie, typy parametrów `a` i `b` i zwracany typ jest wnioskowany jako `int` ponieważ literału `100` typu `int`.</span><span class="sxs-lookup"><span data-stu-id="b918d-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="b918d-118">Może mieć wpływ na wnioskowanie o typie, zmieniając literały.</span><span class="sxs-lookup"><span data-stu-id="b918d-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="b918d-119">Jeśli wprowadzisz `100` `uint32` , dodając sufiks `u`, typy `a`, `b`, i wartość zwracana jest wywnioskowana `uint32`.</span><span class="sxs-lookup"><span data-stu-id="b918d-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="b918d-120">Możesz również zmieniać wnioskowanie o typie przy użyciu innych konstrukcji, sugerujących ograniczenia dotyczące typu, na przykład funkcji i metod, które działają z określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b918d-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="b918d-121">Ponadto można zastosować jawnego typu adnotacji do parametrów funkcji lub metody lub zmiennych w wyrażeniach, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="b918d-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="b918d-122">Błędy wyniku, jeśli występują konflikty między różnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="b918d-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="b918d-123">Można również jawnie określić wartość zwracaną przez funkcję, udostępniając adnotacji typu po wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="b918d-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="b918d-124">Często zdarza, gdzie adnotacji typu przydaje się w parametrze jest, gdy parametr jest typu obiektu, a użytkownik chce, należy użyć członka.</span><span class="sxs-lookup"><span data-stu-id="b918d-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="b918d-125">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="b918d-125">Automatic Generalization</span></span>

<span data-ttu-id="b918d-126">Jeśli kod funkcji nie jest zależny od typu parametru, kompilator traktuje parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="b918d-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="b918d-127">Jest to nazywane *automatyczna Generalizacja*, i może być zaawansowanym pomocy do pisania kodu ogólny bez zwiększania stopnia złożoności.</span><span class="sxs-lookup"><span data-stu-id="b918d-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="b918d-128">Na przykład następująca funkcja łączy dwa parametry dowolnego typu w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b918d-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="b918d-129">Typ jest wnioskowany jako</span><span class="sxs-lookup"><span data-stu-id="b918d-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="b918d-130">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="b918d-130">Additional Information</span></span>

<span data-ttu-id="b918d-131">Wnioskowanie o typie jest opisany bardziej szczegółowo w specyfikacji języka F#.</span><span class="sxs-lookup"><span data-stu-id="b918d-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="b918d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b918d-132">See also</span></span>

- [<span data-ttu-id="b918d-133">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="b918d-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
