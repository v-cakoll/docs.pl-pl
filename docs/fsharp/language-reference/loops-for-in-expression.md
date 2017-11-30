---
title: "Pętle: for...in — Wyrażenie (F#)"
description: "Zobacz temat jak for. F #.. w wyrażeniu konstrukcji pętli jest używanej do wykonywania iteracji dopasowania wzorca w kolekcji wyliczalny."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a><span data-ttu-id="0cc4b-104">Pętle: for...in — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0cc4b-104">Loops: for...in Expression</span></span>

<span data-ttu-id="0cc4b-105">Ta konstrukcja pętli jest używanej do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak wyrażenia zakres, sekwencji, listy, tablicy lub innych konstrukcji obsługującego wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-105">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="0cc4b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cc4b-106">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="0cc4b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cc4b-107">Remarks</span></span>
<span data-ttu-id="0cc4b-108">`for...in` Wyrażenie, które można porównać do `for each` instrukcji w innych językach .NET, ponieważ jest używany do pętli wartości wyliczenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-108">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="0cc4b-109">Jednak `for...in` obsługuje również wzorzec dopasowany w kolekcji, a nie tylko iteracji w całej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-109">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="0cc4b-110">Wyliczalny wyrażenie, które można określić jako wyliczalny kolekcji lub, za pomocą `..` operatora jako zakres na typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-110">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="0cc4b-111">Wyliczalny kolekcje zawierają list, sekwencji, tablic, zestawy, map i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-111">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="0cc4b-112">Dowolnego typu, który implementuje `System.Collections.IEnumerable` mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-112">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="0cc4b-113">Gdy express zakresu przy użyciu `..` operatora, należy użyć następującej składni.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-113">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="0cc4b-114">*Uruchom* ...</span><span class="sxs-lookup"><span data-stu-id="0cc4b-114">*start* ..</span></span> <span data-ttu-id="0cc4b-115">*Zakończ*</span><span class="sxs-lookup"><span data-stu-id="0cc4b-115">*finish*</span></span>

<span data-ttu-id="0cc4b-116">Można również użyć wersji, która obejmuje przyrostu o nazwie *pominąć*, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-116">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="0cc4b-117">*Uruchom* ...</span><span class="sxs-lookup"><span data-stu-id="0cc4b-117">*start* ..</span></span> <span data-ttu-id="0cc4b-118">*Pomiń* ...</span><span class="sxs-lookup"><span data-stu-id="0cc4b-118">*skip* ..</span></span> <span data-ttu-id="0cc4b-119">*Zakończ*</span><span class="sxs-lookup"><span data-stu-id="0cc4b-119">*finish*</span></span>

<span data-ttu-id="0cc4b-120">Gdy używasz integralną zakresy i zmienną prostego licznika jako wzorzec typowe zachowanie jest aby zwiększyć wartości zmiennej licznika przez 1 w każdej iteracji, ale jeśli zakres zawiera wartość pomijania, licznik jest zwiększany o wartość Pomiń zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-120">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="0cc4b-121">Można także dopasować we wzorcu wartości w wyrażeniu treści.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-121">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="0cc4b-122">Następujący przykładowy kod, przedstawiający zastosowanie `for...in` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-122">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="0cc4b-123">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0cc4b-123">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="0cc4b-124">Poniższy przykład przedstawia sposób pętli sekwencji i sposobu użycia wzorca krotki zamiast prostej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-124">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="0cc4b-125">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0cc4b-125">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="0cc4b-126">Poniższy przykład pokazuje, jak pętli w zakresie proste liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-126">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="0cc4b-127">Dane wyjściowe function1 ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-127">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="0cc4b-128">Poniższy przykład pokazuje, jak pętli w zakresie z pominięciem 2, w tym każdy element zakresu.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-128">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="0cc4b-129">Dane wyjściowe `function2` ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-129">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="0cc4b-130">Poniższy przykład przedstawia użycie zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-130">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="0cc4b-131">Dane wyjściowe `function3` ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-131">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="0cc4b-132">Poniższy przykład przedstawia użycie wartości ujemnej Pomiń dla odwrotnej iteracji.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-132">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="0cc4b-133">Dane wyjściowe `function4` ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-133">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="0cc4b-134">Początek i koniec zakresu można także wyrażeń, takich jak funkcje, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-134">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="0cc4b-135">Dane wyjściowe `function5` z tych danych wejściowych jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-135">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="0cc4b-136">W kolejnym przykładzie pokazano użycie symbolu wieloznacznego (_), jeśli element nie jest konieczne w pętli.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-136">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="0cc4b-137">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0cc4b-137">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="0cc4b-138">`Note`Można użyć `for...in` w wyrażeniach sekwencji i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `for...in` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-138">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="0cc4b-139">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0cc4b-139">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="0cc4b-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cc4b-140">See Also</span></span>
[<span data-ttu-id="0cc4b-141">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="0cc4b-141">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="0cc4b-142">Pętle: `for...to` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="0cc4b-142">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="0cc4b-143">Pętle: `while...do` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="0cc4b-143">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
