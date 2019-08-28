---
title: 'Instrukcje: Obsługa wyjątków w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b5dce796e546bf041c28864c8bf66b5f51965e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046626"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="4b7a5-102">Instrukcje: Obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="4b7a5-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="4b7a5-103">W pierwszym przykładzie w tym temacie pokazano <xref:System.AggregateException?displayProperty=nameWithType> , jak obsłużyć, które mogą być zgłaszane z zapytania PLINQ, gdy jest ono wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="4b7a5-104">Drugi przykład pokazuje, jak umieścić bloki try-catch w delegatach, jak najbliżej miejsca, w którym zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="4b7a5-105">W ten sposób można je przechwycić zaraz po ich wystąpieniu i prawdopodobnie kontynuować wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="4b7a5-106">Gdy wyjątki mogą być rzutowane z powrotem do wątku sprzęgania, istnieje możliwość, że zapytanie może nadal przetwarzać niektóre elementy po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="4b7a5-107">W niektórych przypadkach, gdy PLINQ przechodzi do wykonywania sekwencyjnego i wystąpi wyjątek, wyjątek może być propagowany bezpośrednio i nieopakowany w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="4b7a5-108"><xref:System.Threading.ThreadAbortException>Ponadto s są zawsze propagowane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="4b7a5-109">Po włączeniu "Tylko mój kod" program Visual Studio przerwie w wierszu, który zgłasza wyjątek, i wyświetla komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="4b7a5-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="4b7a5-110">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-110">This error is benign.</span></span> <span data-ttu-id="4b7a5-111">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="4b7a5-112">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="4b7a5-113">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="4b7a5-114">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="4b7a5-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b7a5-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b7a5-115">Example</span></span>

<span data-ttu-id="4b7a5-116">W tym przykładzie pokazano, jak umieścić bloki try-catch wokół kodu, który wykonuje zapytanie, aby przechwytywać <xref:System.AggregateException?displayProperty=nameWithType>wszystkie zgłoszone elementy.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="4b7a5-117">W tym przykładzie zapytanie nie może być kontynuowane po zgłoszeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="4b7a5-118">Przez czas, gdy kod aplikacji przechwytuje wyjątek, PLINQ już zatrzymał zapytanie we wszystkich wątkach.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="4b7a5-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b7a5-119">Example</span></span>

<span data-ttu-id="4b7a5-120">Poniższy przykład pokazuje, jak umieścić blok try-catch w delegatze, aby umożliwić przechwytywanie wyjątku i kontynuować wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="4b7a5-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b7a5-121">Compiling the Code</span></span>

- <span data-ttu-id="4b7a5-122">Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu danych PLINQ i Wywołaj metodę z głównego.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="4b7a5-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="4b7a5-123">Robust Programming</span></span>

<span data-ttu-id="4b7a5-124">Nie Przechwytuj wyjątku, chyba że wiesz, jak go obsłużyć, aby nie uszkodzić stanu programu.</span><span class="sxs-lookup"><span data-stu-id="4b7a5-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b7a5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b7a5-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="4b7a5-126">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4b7a5-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
