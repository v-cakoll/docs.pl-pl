---
title: 'Pętle: for...in — Wyrażenie'
description: Zobacz, F# jak... w konstrukcji zapętlania wyrażeń jest używany do iteracji na dopasowaniach wzorca w wyliczalnej kolekcji.
ms.date: 05/16/2016
ms.openlocfilehash: 640b0f91f6c641f3b49a99dc67abe7e4c31911ea
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630715"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="19ae2-103">Pętle: for...in — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="19ae2-103">Loops: for...in Expression</span></span>

<span data-ttu-id="19ae2-104">Ta konstrukcja zapętlenia służy do iteracji na dopasowaniach wzorca w wyliczalnej kolekcji, takiej jak wyrażenie zakresu, sekwencja, lista, tablica lub inna konstrukcja, która obsługuje Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="19ae2-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="19ae2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="19ae2-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="19ae2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19ae2-106">Remarks</span></span>

<span data-ttu-id="19ae2-107">Wyrażenie można porównać `for each` z instrukcją w innych językach .NET, ponieważ jest używana do pętli w przypadku wartości w wyliczalnej kolekcji. `for...in`</span><span class="sxs-lookup"><span data-stu-id="19ae2-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="19ae2-108">Program `for...in` obsługuje jednak również dopasowanie wzorców do kolekcji, a nie tylko iteracji w całej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="19ae2-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="19ae2-109">Wyliczalne wyrażenie może być określone jako wyliczalna kolekcja lub, za `..` pomocą operatora, jako zakresu w typie całkowitym.</span><span class="sxs-lookup"><span data-stu-id="19ae2-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="19ae2-110">Wyliczalne kolekcje obejmują listy, sekwencje, tablice, zestawy, mapy itd.</span><span class="sxs-lookup"><span data-stu-id="19ae2-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="19ae2-111">Można użyć dowolnego typu `System.Collections.IEnumerable` , który implementuje.</span><span class="sxs-lookup"><span data-stu-id="19ae2-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="19ae2-112">Gdy wyrażasz zakres przy użyciu `..` operatora, możesz użyć następującej składni.</span><span class="sxs-lookup"><span data-stu-id="19ae2-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="19ae2-113">*Rozpocznij* ..</span><span class="sxs-lookup"><span data-stu-id="19ae2-113">*start* ..</span></span> <span data-ttu-id="19ae2-114">*ukończyć*</span><span class="sxs-lookup"><span data-stu-id="19ae2-114">*finish*</span></span>

<span data-ttu-id="19ae2-115">Możesz również użyć wersji, która zawiera przyrost o nazwie *Skip*, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="19ae2-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="19ae2-116">*Rozpocznij* ..</span><span class="sxs-lookup"><span data-stu-id="19ae2-116">*start* ..</span></span> <span data-ttu-id="19ae2-117">*Pomiń* ..</span><span class="sxs-lookup"><span data-stu-id="19ae2-117">*skip* ..</span></span> <span data-ttu-id="19ae2-118">*ukończyć*</span><span class="sxs-lookup"><span data-stu-id="19ae2-118">*finish*</span></span>

<span data-ttu-id="19ae2-119">W przypadku korzystania z zakresów całkowitych i prostej zmiennej licznika jako wzorca typowym zachowaniem jest zwiększenie zmiennej licznika o 1 dla każdej iteracji, ale jeśli zakres zawiera wartość pomijania, licznik zostanie zwiększony przez wartość pomijania.</span><span class="sxs-lookup"><span data-stu-id="19ae2-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="19ae2-120">W wyrażeniu treści można także użyć wartości pasujących do wzorca.</span><span class="sxs-lookup"><span data-stu-id="19ae2-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="19ae2-121">Poniższe przykłady kodu ilustrują użycie `for...in` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="19ae2-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="19ae2-122">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="19ae2-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="19ae2-123">Poniższy przykład pokazuje, jak wykonać pętlę w sekwencji i jak używać wzorca krotek zamiast prostej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="19ae2-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="19ae2-124">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="19ae2-124">The output is as follows.</span></span>

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

<span data-ttu-id="19ae2-125">Poniższy przykład pokazuje, jak wykonać pętlę dla prostego zakresu liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="19ae2-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="19ae2-126">Dane wyjściowe function1 są następujące.</span><span class="sxs-lookup"><span data-stu-id="19ae2-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="19ae2-127">Poniższy przykład pokazuje, jak pętla w zakresie z pominięciem 2, które obejmuje każdy inny element zakresu.</span><span class="sxs-lookup"><span data-stu-id="19ae2-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="19ae2-128">Dane wyjściowe `function2` są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="19ae2-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="19ae2-129">Poniższy przykład pokazuje, jak używać zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="19ae2-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="19ae2-130">Dane wyjściowe `function3` są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="19ae2-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="19ae2-131">Poniższy przykład pokazuje, jak używać ujemnej wartości pomijania dla iteracji odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="19ae2-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="19ae2-132">Dane wyjściowe `function4` są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="19ae2-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="19ae2-133">Początek i koniec zakresu mogą również być wyrażeniami, takimi jak funkcje, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="19ae2-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="19ae2-134">Dane wyjściowe `function5` z tymi danymi wejściowymi są następujące.</span><span class="sxs-lookup"><span data-stu-id="19ae2-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="19ae2-135">W następnym przykładzie pokazano użycie symbolu wieloznacznego (\_), gdy element nie jest wymagany w pętli.</span><span class="sxs-lookup"><span data-stu-id="19ae2-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="19ae2-136">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="19ae2-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="19ae2-137">`Note`Można używać `for...in` w wyrażeniach sekwencji i innych wyrażeniach obliczeniowych, w tym przypadku używana jest dostosowana wersja `for...in` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="19ae2-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="19ae2-138">Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje, [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="19ae2-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19ae2-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19ae2-139">See also</span></span>

- [<span data-ttu-id="19ae2-140">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="19ae2-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="19ae2-141">Pętli `for...to`Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="19ae2-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="19ae2-142">Pętli `while...do`Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="19ae2-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
