---
title: 'Wyjątki: Wyrażenie try...finally'
description: Dowiedz się F# , jak "try... Finally "wyrażenie umożliwia wykonywanie kodu czyszczącego, nawet jeśli blok kodu zgłasza wyjątek.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083007"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="fceaf-103">Wyjątki: Wyrażenie try...finally</span><span class="sxs-lookup"><span data-stu-id="fceaf-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="fceaf-104">`try...finally` Wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fceaf-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="fceaf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fceaf-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="fceaf-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fceaf-106">Remarks</span></span>

<span data-ttu-id="fceaf-107">Wyrażenie może służyć do wykonywania kodu w wyrażenie2 w powyższej składni, bez względu na to, czy wyjątek jest generowany podczas wykonywania elementu *wyrażenie1*. `try...finally`</span><span class="sxs-lookup"><span data-stu-id="fceaf-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="fceaf-108">Typ *wyrażenie2* nie przyczynia się do wartości całego wyrażenia; Typ zwracany, gdy wyjątek nie występuje, jest ostatnią wartością elementu *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="fceaf-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="fceaf-109">W przypadku wystąpienia wyjątku nie jest zwracana żadna wartość i przepływ sterowania jest przesyłany do następnego dopasowania do stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="fceaf-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="fceaf-110">Jeśli nie zostanie znaleziona procedura obsługi wyjątków, program zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="fceaf-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="fceaf-111">Przed wykonaniem kodu w zgodnej procedurze obsługi lub przerwaniem działania programu kod w `finally` gałęzi jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="fceaf-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="fceaf-112">Poniższy kod ilustruje użycie `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fceaf-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="fceaf-113">Dane wyjściowe konsoli programu są następujące.</span><span class="sxs-lookup"><span data-stu-id="fceaf-113">The output to the console is as follows.</span></span>

```console
Closing stream
Exception handled.
```

<span data-ttu-id="fceaf-114">Jak widać na podstawie danych wyjściowych, strumień został zamknięty przed przeprowadzeniem zewnętrznego wyjątku, a plik `test.txt` zawiera tekst `test1`, który wskazuje, że bufory zostały opróżnione i zapisywana na dysku, nawet jeśli wyjątek został przesłany kontrolka na zewnętrzny program obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fceaf-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="fceaf-115">Należy zauważyć, `try...with` że konstrukcja jest oddzielna konstrukcja `try...finally` od konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="fceaf-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="fceaf-116">W związku z tym, jeśli kod wymaga `with` zarówno bloku, `finally` jak i bloku, należy zagnieździć dwa konstrukcje, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="fceaf-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="fceaf-117">W kontekście wyrażeń obliczeń, w tym wyrażeń sekwencji i asynchronicznych przepływów pracy, **spróbuj... wyrażenia finally** mogą mieć implementację niestandardową.</span><span class="sxs-lookup"><span data-stu-id="fceaf-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="fceaf-118">Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fceaf-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fceaf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fceaf-119">See also</span></span>

- [<span data-ttu-id="fceaf-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="fceaf-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="fceaf-121">Wyjątki: `try...with` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="fceaf-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
