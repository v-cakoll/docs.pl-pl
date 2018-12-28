---
title: 'Wyjątki: Try... finally — wyrażenie'
description: Dowiedz się, jak F# "try... finally" wyrażenie umożliwia wykonanie kodu oczyszczania, nawet wtedy, gdy blok kodu zgłasza wyjątek.
ms.date: 05/16/2016
ms.openlocfilehash: 24613185818c8ea30b27dcf639b22af320c4b401
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611623"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="02f4d-103">Wyjątki: Try... finally — wyrażenie</span><span class="sxs-lookup"><span data-stu-id="02f4d-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="02f4d-104">`try...finally` Wyrażenie umożliwia wykonanie kodu oczyszczania, nawet wtedy, gdy blok kodu zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="02f4d-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="02f4d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="02f4d-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="02f4d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02f4d-106">Remarks</span></span>

<span data-ttu-id="02f4d-107">`try...finally` Wyrażenie może służyć do wykonywania kodu w *wyrażenie2* w poprzedniej składni, niezależnie od tego, czy wyjątek jest generowany podczas wykonywania *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="02f4d-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="02f4d-108">Typ *wyrażenie2* nie wpływa wartość całego wyrażenia; typ zwracany, gdy nie występuje wyjątek jest ostatnią wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="02f4d-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="02f4d-109">Gdy wystąpi wyjątek, jest zwracana żadna wartość, a przepływ sterowania przesyła do następnego dopasowania obsługi wyjątków w górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="02f4d-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="02f4d-110">Jeśli żadna procedura obsługi wyjątku zostanie znaleziony, program zakończy działanie.</span><span class="sxs-lookup"><span data-stu-id="02f4d-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="02f4d-111">Zanim wykonywany jest kod w pasującej klauzuli obsługi lub program kończy działanie, kod w `finally` gałęzi jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="02f4d-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="02f4d-112">Poniższy przykład demonstruje użycie `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="02f4d-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="02f4d-113">Dostępne są następujące dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="02f4d-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="02f4d-114">Jak widać z danych wyjściowych, strumień został zamknięty, zanim zewnętrzne wyjątek został obsłużony, a plik `test.txt` zawiera tekst `test1`, co oznacza, że bufory opróżnionych i zapisywane na dysku, nawet jeśli wyjątek przesyłane do obsługi wyjątku zewnętrznym kontrolować.</span><span class="sxs-lookup"><span data-stu-id="02f4d-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="02f4d-115">Należy pamiętać, że `try...with` konstrukcja jest oddzielnym konstrukcji z `try...finally` konstruowania.</span><span class="sxs-lookup"><span data-stu-id="02f4d-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="02f4d-116">W związku z tym jeśli kod wymaga zarówno `with` bloku i `finally` bloku, należy zagnieździć dwóch konstrukcji, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="02f4d-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="02f4d-117">W kontekście wyrażenia obliczeń, w tym wyrażenia sekwencji i asynchroniczne przepływy pracy, **try... finally** wyrażeń może mieć implementację niestandardową.</span><span class="sxs-lookup"><span data-stu-id="02f4d-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="02f4d-118">Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="02f4d-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02f4d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02f4d-119">See also</span></span>

- [<span data-ttu-id="02f4d-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="02f4d-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="02f4d-121">Wyjątki: `try...with` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="02f4d-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)