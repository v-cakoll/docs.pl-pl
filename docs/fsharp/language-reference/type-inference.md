---
title: Wnioskowanie o typie (F#)
description: 'Dowiedz się, jak kompilator języka F # wnioskuje typy wartości, zmienne, parametrów i zwracanych wartości.'
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-inference"></a><span data-ttu-id="41b23-103">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="41b23-103">Type Inference</span></span>

<span data-ttu-id="41b23-104">W tym temacie opisano, jak kompilator języka F # wnioskuje typy wartości, zmienne, parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="41b23-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="41b23-105">Wnioskowanie o typie ogólnie</span><span class="sxs-lookup"><span data-stu-id="41b23-105">Type Inference in General</span></span>
<span data-ttu-id="41b23-106">Pomysł wnioskowanie o typie jest, że nie trzeba określić typy F # konstrukcje, z wyjątkiem przypadków, gdy kompilator ostatecznie nie można wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="41b23-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="41b23-107">Pominięcie jawnego typu informacji nie oznacza, że F # jest typach określanych dynamicznie języka lub czy wartości w języku F # słabo wpisywania.</span><span class="sxs-lookup"><span data-stu-id="41b23-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="41b23-108">F # to język typami statycznymi, co oznacza, że kompilator deduces dokładnego typu dla każdego konstrukcji podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41b23-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="41b23-109">Jeśli nie ma wystarczającej ilości informacji dla kompilatora, aby ustalić typy każdego konstrukcji, musisz podać dodatkowe informacje, zazwyczaj przez dodanie adnotacji typu jawnego gdzieś w kodzie.</span><span class="sxs-lookup"><span data-stu-id="41b23-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="41b23-110">Wnioskowanie parametrów i zwracanych typów</span><span class="sxs-lookup"><span data-stu-id="41b23-110">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="41b23-111">Na liście parametrów nie trzeba określić typ każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="41b23-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="41b23-112">Jeszcze, F # jest językiem typami statycznymi i w związku z tym każda wartość i wyrażenie ma typ określoną w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41b23-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="41b23-113">Dla typów, które nie określają jawnie kompilator wnioskuje typ na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="41b23-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="41b23-114">Jeśli typ nie jest w inny sposób określona, jest wywnioskowany aby wartość była ogólna.</span><span class="sxs-lookup"><span data-stu-id="41b23-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="41b23-115">Jeśli kod używa wartości niespójnie, w taki sposób, że istnieje jeden nie wywnioskować typu, który spełnia wszystkie używa wartości, kompilator zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="41b23-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="41b23-116">Zwracany typ funkcji jest określana przez typ ostatniego wyrażenia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="41b23-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="41b23-117">Na przykład w poniższym kodzie, typy parametrów `a` i `b` i typ zwracany są wywnioskować jako `int` ponieważ literał `100` jest typu `int`.</span><span class="sxs-lookup"><span data-stu-id="41b23-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="41b23-118">Wnioskowanie o typie może mieć wpływ, zmieniając literały.</span><span class="sxs-lookup"><span data-stu-id="41b23-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="41b23-119">Jeśli wprowadzisz `100` `uint32` przez dodanie sufiksu `u`, typy `a`, `b`, i wartości zwracanej są wywnioskować jako `uint32`.</span><span class="sxs-lookup"><span data-stu-id="41b23-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="41b23-120">Można również określić wnioskowanie typu przy użyciu innych konstrukcji sugerujących ograniczenia dotyczące typu, na przykład funkcje i metody, które współpracują z określonego typu.</span><span class="sxs-lookup"><span data-stu-id="41b23-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="41b23-121">Ponadto można zastosować jawnego typu adnotacji do parametrów funkcji lub metody lub do zmiennych w wyrażeniach, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="41b23-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="41b23-122">Powoduje błędy, jeśli występują konflikty między różne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="41b23-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="41b23-123">Można również jawnie określić wartość zwracaną przez funkcję, zapewniając adnotację typu, po wszystkich parametrach.</span><span class="sxs-lookup"><span data-stu-id="41b23-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="41b23-124">Typowych przypadkach, gdy adnotację typu jest przydatne w parametrze jest, gdy parametr jest typu obiektu i chcesz użyć członka.</span><span class="sxs-lookup"><span data-stu-id="41b23-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="41b23-125">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="41b23-125">Automatic Generalization</span></span>
<span data-ttu-id="41b23-126">Jeśli kod funkcji nie jest zależny od typu parametru, kompilator uwzględnia parametr, aby wartość była ogólna.</span><span class="sxs-lookup"><span data-stu-id="41b23-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="41b23-127">Ta metoda jest wywoływana *automatyczna Generalizacja*, i może być zaawansowaną pomoc do pisania kodu ogólnego bez zwiększania złożoności.</span><span class="sxs-lookup"><span data-stu-id="41b23-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="41b23-128">Na przykład następująca funkcja łączy dwa parametry dowolnego typu w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="41b23-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="41b23-129">Typ jest wywnioskowany się</span><span class="sxs-lookup"><span data-stu-id="41b23-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="41b23-130">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="41b23-130">Additional Information</span></span>
<span data-ttu-id="41b23-131">Wnioskowanie o typie jest opisany bardziej szczegółowo w specyfikacji języka F #.</span><span class="sxs-lookup"><span data-stu-id="41b23-131">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="41b23-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41b23-132">See Also</span></span>
[<span data-ttu-id="41b23-133">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="41b23-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
