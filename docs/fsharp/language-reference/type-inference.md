---
title: Wnioskowanie o typie
description: Dowiedz się F# , w jaki sposób kompilator wnioskuje typy wartości, zmienne, parametry i wartości zwracane.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630184"
---
# <a name="type-inference"></a><span data-ttu-id="98380-103">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="98380-103">Type Inference</span></span>

<span data-ttu-id="98380-104">W tym temacie opisano sposób F# , w jaki kompilator wnioskuje typy wartości, zmiennych, parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="98380-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="98380-105">Ogólne wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="98380-105">Type Inference in General</span></span>

<span data-ttu-id="98380-106">Pomysłem na wnioskowanie o typie jest to, że nie trzeba określać typów F# konstrukcji, z wyjątkiem sytuacji, w których kompilator nie może jednoznacznie wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="98380-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="98380-107">Pomijanie jawnych informacji o typie nie oznacza F# , że jest to język wpisany dynamicznie lub że F# wartości w są słabo wpisane.</span><span class="sxs-lookup"><span data-stu-id="98380-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="98380-108">F#jest statycznie wpisanym językiem, co oznacza, że kompilator określa dokładny typ dla każdej konstrukcji podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="98380-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="98380-109">Jeśli nie ma wystarczającej ilości informacji dla kompilatora do ustalenia typów każdej konstrukcji, należy podać dodatkowe informacje o typie, zazwyczaj poprzez dodanie jawnych adnotacji typu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="98380-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="98380-110">Wnioskowanie dotyczące parametrów i zwracanych typów</span><span class="sxs-lookup"><span data-stu-id="98380-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="98380-111">Na liście parametrów nie trzeba określać typu każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="98380-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="98380-112">A jeszcze, F# to statycznie wpisany język, w związku z czym każda wartość i wyrażenie ma określony typ w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="98380-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="98380-113">Dla tych typów, które nie są jawnie określone, kompilator wnioskuje typ na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="98380-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="98380-114">Jeśli typ nie jest określony w inny sposób, jest wywnioskowany jako ogólny.</span><span class="sxs-lookup"><span data-stu-id="98380-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="98380-115">Jeśli kod używa wartości niespójnie, w taki sposób, że nie istnieje pojedynczy typ, który spełnia wszystkie zastosowania wartości, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="98380-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="98380-116">Zwracany typ funkcji jest określany na podstawie typu ostatniego wyrażenia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="98380-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="98380-117">Na przykład, w `a` poniższym kodzie, typy parametrów i `b` i typ zwracany są wywnioskowane jako `int` , ponieważ literał `100` jest typu `int`.</span><span class="sxs-lookup"><span data-stu-id="98380-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="98380-118">Można mieć wpływ na wnioskowanie o typie, zmieniając literały.</span><span class="sxs-lookup"><span data-stu-id="98380-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="98380-119">W przypadku wybrania `100` a `uint32` przez dołączenie `a`sufiksu `u`, typy, `b`i wartość zwracana są wywnioskowane `uint32`.</span><span class="sxs-lookup"><span data-stu-id="98380-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="98380-120">Można również wpływać na wnioskowanie o typie przy użyciu innych konstrukcji, które oznaczają ograniczenia dotyczące typu, takie jak funkcje i metody, które współpracują z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="98380-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="98380-121">Ponadto można zastosować jawne adnotacje typu do parametrów funkcji lub metod lub do zmiennych w wyrażeniach, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="98380-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="98380-122">Wynik błędów w przypadku konfliktów między różnymi ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="98380-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="98380-123">Można również jawnie określić wartość zwracaną funkcji, dostarczając adnotację typu po wszystkich parametrach.</span><span class="sxs-lookup"><span data-stu-id="98380-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="98380-124">Typowy przypadek, w którym adnotacja typu jest przydatna na parametrze, gdy parametr jest typem obiektu i chcesz użyć elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="98380-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="98380-125">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="98380-125">Automatic Generalization</span></span>

<span data-ttu-id="98380-126">Jeśli kod funkcji nie zależy od typu parametru, kompilator traktuje parametr jako generyczny.</span><span class="sxs-lookup"><span data-stu-id="98380-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="98380-127">Jest to nazywane *automatycznym uogólnieniem*i może być zaawansowaną pomocą do pisania kodu generycznego bez zwiększania złożoności.</span><span class="sxs-lookup"><span data-stu-id="98380-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="98380-128">Na przykład następująca funkcja łączy dwa parametry dowolnego typu do krotki.</span><span class="sxs-lookup"><span data-stu-id="98380-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="98380-129">Typ jest wywnioskowany jako</span><span class="sxs-lookup"><span data-stu-id="98380-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="98380-130">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="98380-130">Additional Information</span></span>

<span data-ttu-id="98380-131">Wnioskowanie o typie zostało opisane bardziej szczegółowo w F# specyfikacji języka.</span><span class="sxs-lookup"><span data-stu-id="98380-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="98380-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98380-132">See also</span></span>

- [<span data-ttu-id="98380-133">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="98380-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)
