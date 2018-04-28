---
title: 'Wyjątki: try...finally — Wyrażenie (F#)'
description: 'Dowiedz się, jak F # "try... finally" wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 588e4edb4d25c6d25ef103ba724613db997f68d7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="de7b8-103">Wyjątki: try...finally — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="de7b8-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="de7b8-104">`try...finally` Wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="de7b8-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="de7b8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="de7b8-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="de7b8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de7b8-106">Remarks</span></span>
<span data-ttu-id="de7b8-107">`try...finally` Wyrażenie może służyć do wykonywania kodu w *wyrażenie2* w powyższej składni niezależnie od tego, czy wyjątek jest generowany podczas wykonywania *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="de7b8-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="de7b8-108">Typ *wyrażenie2* nie wpływa na wartość całego wyrażenia; typ zwracany, gdy występuje wyjątek jest ostatnią wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="de7b8-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="de7b8-109">Po wystąpieniu wyjątku, jest zwracana wartość nie i przesyła przepływu sterowania do następnego dopasowania obsługi wyjątków górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="de7b8-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="de7b8-110">Jeśli zostanie znaleziony żaden moduł obsługi wyjątku, program zakończy się.</span><span class="sxs-lookup"><span data-stu-id="de7b8-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="de7b8-111">Przed wykonywany jest kod obsługi zgodnych lub program zakończy kod w `finally` gałęzi jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="de7b8-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="de7b8-112">Poniższy kod przedstawia użycie `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="de7b8-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="de7b8-113">Poniżej przedstawiono dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="de7b8-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="de7b8-114">Jak widać z danych wyjściowych, strumień został zamknięty przed zewnętrzne wyjątek został obsłużony, a plik `test.txt` zawiera tekst `test1`, co oznacza, że bufory zostały opróżnione i zapisywane na dysku, nawet jeśli wyjątek transferu kontrolowanie do obsługi Wyjątek zewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="de7b8-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="de7b8-115">Należy pamiętać, że `try...with` konstrukcja jest osobnym konstrukcja z `try...finally` utworzenia.</span><span class="sxs-lookup"><span data-stu-id="de7b8-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="de7b8-116">W związku z tym jeśli kod wymaga obu `with` bloku i `finally` bloku, trzeba zagnieździć dwóch konstrukcje, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="de7b8-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="de7b8-117">W kontekście wyrażenia obliczeń, w tym wyrażeniach sekwencji i asynchroniczne przepływy pracy, **try... finally** wyrażenia może mieć niestandardowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="de7b8-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="de7b8-118">Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="de7b8-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="de7b8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de7b8-119">See Also</span></span>
[<span data-ttu-id="de7b8-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="de7b8-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="de7b8-121">Wyjątki: `try...with` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="de7b8-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
