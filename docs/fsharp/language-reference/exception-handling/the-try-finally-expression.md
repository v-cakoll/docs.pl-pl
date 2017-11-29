---
title: "Wyjątki: try...finally — Wyrażenie (F#)"
description: "Dowiedz się, jak F # \"try... finally\" wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="7e8cf-104">Wyjątki: try...finally — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7e8cf-104">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="7e8cf-105">`try...finally` Wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-105">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="7e8cf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e8cf-106">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="7e8cf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e8cf-107">Remarks</span></span>
<span data-ttu-id="7e8cf-108">`try...finally` Wyrażenie może służyć do wykonywania kodu w *wyrażenie2* w powyższej składni niezależnie od tego, czy wyjątek jest generowany podczas wykonywania *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-108">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="7e8cf-109">Typ *wyrażenie2* nie wpływa na wartość całego wyrażenia; typ zwracany, gdy występuje wyjątek jest ostatnią wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-109">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="7e8cf-110">Po wystąpieniu wyjątku, jest zwracana wartość nie i przesyła przepływu sterowania do następnego dopasowania obsługi wyjątków górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-110">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="7e8cf-111">Jeśli zostanie znaleziony żaden moduł obsługi wyjątku, program zakończy się.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-111">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="7e8cf-112">Przed wykonywany jest kod obsługi zgodnych lub program zakończy kod w `finally` gałęzi jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-112">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="7e8cf-113">Poniższy kod przedstawia użycie `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-113">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="7e8cf-114">Poniżej przedstawiono dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-114">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="7e8cf-115">Jak widać z danych wyjściowych, strumień został zamknięty przed zewnętrzne wyjątek został obsłużony, a plik `test.txt` zawiera tekst `test1`, co oznacza, że bufory zostały opróżnione i zapisywane na dysku, nawet jeśli wyjątek transferu kontrolowanie do obsługi Wyjątek zewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-115">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="7e8cf-116">Należy pamiętać, że `try...with` konstrukcja jest osobnym konstrukcja z `try...finally` utworzenia.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-116">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="7e8cf-117">W związku z tym jeśli kod wymaga obu `with` bloku i `finally` bloku, trzeba zagnieździć dwóch konstrukcje, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-117">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="7e8cf-118">W kontekście wyrażenia obliczeń, w tym wyrażeniach sekwencji i asynchroniczne przepływy pracy, **try... finally** wyrażenia może mieć niestandardowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="7e8cf-118">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="7e8cf-119">Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7e8cf-119">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="7e8cf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e8cf-120">See Also</span></span>
[<span data-ttu-id="7e8cf-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="7e8cf-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="7e8cf-122">Wyjątki: `try...with` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7e8cf-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
