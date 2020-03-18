---
title: 'Porady: obsługa wyjątków w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 3645f5dc470ef53710aa7f4c78c60431fb27ecfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123090"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="917d0-102">Porady: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="917d0-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="917d0-103">Pierwszy przykład w tym temacie pokazuje, jak <xref:System.AggregateException?displayProperty=nameWithType> obsługiwać, które mogą być generowane z kwerendy PLINQ podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="917d0-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="917d0-104">Drugi przykład pokazuje, jak umieścić try-catch bloki w delegatów, jak najbliżej, gdzie wyjątek zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="917d0-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="917d0-105">W ten sposób można je złapać, gdy tylko wystąpią i ewentualnie kontynuować wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="917d0-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="917d0-106">Gdy wyjątki mogą bąbelkować z powrotem do wątku łączącego, jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyłączeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="917d0-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="917d0-107">W niektórych przypadkach, gdy PLINQ wraca do wykonania sekwencyjnego i występuje wyjątek, wyjątek może <xref:System.AggregateException>być propagowane bezpośrednio i nie zawinięte w .</span><span class="sxs-lookup"><span data-stu-id="917d0-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="917d0-108">Ponadto <xref:System.Threading.ThreadAbortException>s są zawsze propagowane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="917d0-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="917d0-109">Gdy opcja "Tylko mój kod" jest włączona, program Visual Studio zostanie przerwany w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="917d0-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="917d0-110">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="917d0-110">This error is benign.</span></span> <span data-ttu-id="917d0-111">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="917d0-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="917d0-112">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="917d0-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="917d0-113">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="917d0-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="917d0-114">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="917d0-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="917d0-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="917d0-115">Example</span></span>

<span data-ttu-id="917d0-116">W tym przykładzie pokazano, jak umieścić try-catch bloki wokół <xref:System.AggregateException?displayProperty=nameWithType>kodu, który wykonuje kwerendę do połowu wszystkich s, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="917d0-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="917d0-117">W tym przykładzie kwerenda nie może kontynuować po wyjątek wyjątek.</span><span class="sxs-lookup"><span data-stu-id="917d0-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="917d0-118">Do czasu kodu aplikacji przechwytuje wyjątek, PLINQ już zatrzymał kwerendę we wszystkich wątkach.</span><span class="sxs-lookup"><span data-stu-id="917d0-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="917d0-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="917d0-119">Example</span></span>

<span data-ttu-id="917d0-120">W poniższym przykładzie pokazano, jak umieścić blok try-catch w pełnomocnika, aby umożliwić przechwycać wyjątek i kontynuować wykonywanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="917d0-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="917d0-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="917d0-121">Compiling the Code</span></span>

- <span data-ttu-id="917d0-122">Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu próbki danych PLINQ i wywołaj metodę z Main.</span><span class="sxs-lookup"><span data-stu-id="917d0-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="917d0-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="917d0-123">Robust Programming</span></span>

<span data-ttu-id="917d0-124">Nie łapiesz wyjątku, chyba że wiesz, jak go obsługiwać, aby nie uszkodzić stanu programu.</span><span class="sxs-lookup"><span data-stu-id="917d0-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="917d0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="917d0-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="917d0-126">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="917d0-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
