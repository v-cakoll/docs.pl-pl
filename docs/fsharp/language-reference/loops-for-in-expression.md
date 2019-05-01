---
title: 'Pętle: for...in — Wyrażenie'
description: Zobacz jak F# for... w wyrażeniu konstrukcji pętli jest używany do wykonywania iteracji dopasowania wzorca w kolekcji wyliczenia.
ms.date: 05/16/2016
ms.openlocfilehash: adaf448a49cf53c63c41f9156d40ee5d1ad3caeb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024446"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="5a9e2-103">Pętle: for...in — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="5a9e2-103">Loops: for...in Expression</span></span>

<span data-ttu-id="5a9e2-104">Tej konstrukcji pętli jest używany do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak wyrażenie zakresu, sekwencji, listy, tablicy lub innej konstrukcji, który obsługuje wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a9e2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a9e2-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="5a9e2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a9e2-106">Remarks</span></span>

<span data-ttu-id="5a9e2-107">`for...in` Wyrażenia można porównać do wyrażenia `for each` instrukcji w innych językach .NET, ponieważ służy on do pętli wartości w kolekcji wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="5a9e2-108">Jednak `for...in` obsługuje również dopasowywanie wzorców względem kolekcji, a nie po prostu iteracji przez całą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="5a9e2-109">Wyliczalne wyrażenia można określić jako wyliczalny kolekcji, lub za pomocą `..` operatora, jako zakres na typ całkowitoliczbowy.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="5a9e2-110">Przeliczalne kolekcje zawierają listy, sekwencji, tablice, zestawy, mapy i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="5a9e2-111">Dowolny typ, który implementuje `System.Collections.IEnumerable` mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="5a9e2-112">Gdy zakres jest wyrazić za pomocą `..` operatora, należy użyć następującej składni.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="5a9e2-113">*Rozpocznij* ...</span><span class="sxs-lookup"><span data-stu-id="5a9e2-113">*start* ..</span></span> <span data-ttu-id="5a9e2-114">*Zakończ*</span><span class="sxs-lookup"><span data-stu-id="5a9e2-114">*finish*</span></span>

<span data-ttu-id="5a9e2-115">Można również użyć wersji, który zawiera przyrostu o nazwie *pominąć*, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="5a9e2-116">*Rozpocznij* ...</span><span class="sxs-lookup"><span data-stu-id="5a9e2-116">*start* ..</span></span> <span data-ttu-id="5a9e2-117">*Pomiń* ...</span><span class="sxs-lookup"><span data-stu-id="5a9e2-117">*skip* ..</span></span> <span data-ttu-id="5a9e2-118">*Zakończ*</span><span class="sxs-lookup"><span data-stu-id="5a9e2-118">*finish*</span></span>

<span data-ttu-id="5a9e2-119">Korzystając z typu całkowitego zakresów i zmienną licznika prostego jako wzorzec, typowe zachowanie to zwiększyć wartości zmiennej licznika o 1 w każdej iteracji, ale jeśli ten zakres obejmuje wartości skip, licznik jest zwiększany przez wartość Pomiń zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="5a9e2-120">Można także dopasować we wzorcu wartości w wyrażeniu treści.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="5a9e2-121">Poniższe przykłady kodu ilustrują używanie `for...in` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="5a9e2-122">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="5a9e2-123">Poniższy przykład pokazuje sposób pętli sekwencji oraz korzystania z wzorca krotki zamiast prostej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="5a9e2-124">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-124">The output is as follows.</span></span>

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

<span data-ttu-id="5a9e2-125">Poniższy przykład pokazuje, jak w pętli za pośrednictwem prostego liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="5a9e2-126">Dane wyjściowe function1 wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="5a9e2-127">Poniższy przykład pokazuje, jak w pętli w zakresie z pominięciem 2, która zawiera każdy inny element zakresu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="5a9e2-128">Dane wyjściowe `function2` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="5a9e2-129">Poniższy przykład pokazuje, jak używać zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="5a9e2-130">Dane wyjściowe `function3` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="5a9e2-131">Poniższy przykład pokazuje, jak używać wartości ujemne Pomiń dla iteracji odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="5a9e2-132">Dane wyjściowe `function4` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="5a9e2-133">Początek i koniec zakresu, może być również wyrażeń, takie jak functions, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="5a9e2-134">Dane wyjściowe `function5` z tych danych wejściowych jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="5a9e2-135">W kolejnym przykładzie pokazano użycie symbolu wieloznacznego (\_) Jeśli element nie jest potrzebna w pętli.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="5a9e2-136">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="5a9e2-137">`Note` Możesz użyć `for...in` w sekwencji, wyrażenia i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `for...in` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="5a9e2-138">Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a9e2-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a9e2-139">See also</span></span>

- [<span data-ttu-id="5a9e2-140">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="5a9e2-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5a9e2-141">Pętle: `for...to` Expression</span><span class="sxs-lookup"><span data-stu-id="5a9e2-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="5a9e2-142">Pętle: `while...do` Expression</span><span class="sxs-lookup"><span data-stu-id="5a9e2-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)