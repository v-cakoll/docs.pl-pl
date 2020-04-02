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
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587984"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="e9b92-102">Porady: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="e9b92-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="e9b92-103">Pierwszy przykład w tym temacie pokazuje, jak <xref:System.AggregateException?displayProperty=nameWithType> obsługiwać, które mogą być generowane z kwerendy PLINQ podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e9b92-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="e9b92-104">W drugim przykładzie pokazano, jak umieścić try-catch bloków w delegatów, jak najbliżej, gdzie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e9b92-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="e9b92-105">W ten sposób można je złapać, jak tylko wystąpią i ewentualnie kontynuować wykonywanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="e9b92-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="e9b92-106">Gdy wyjątki są dozwolone do bańki z powrotem do wątku łączącego, a następnie jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyjątek jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="e9b92-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="e9b92-107">W niektórych przypadkach, gdy PLINQ powraca do wykonywania sekwencyjnego i występuje wyjątek, wyjątek <xref:System.AggregateException>może być propagowany bezpośrednio, a nie zawinięty w .</span><span class="sxs-lookup"><span data-stu-id="e9b92-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="e9b92-108">Ponadto <xref:System.Threading.ThreadAbortException>s są zawsze propagowane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e9b92-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="e9b92-109">Gdy "Tylko mój kod" jest włączona, Visual Studio zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z napisem "wyjątek nie obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="e9b92-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e9b92-110">Ten błąd jest łagodny.</span><span class="sxs-lookup"><span data-stu-id="e9b92-110">This error is benign.</span></span> <span data-ttu-id="e9b92-111">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, które jest pokazane w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="e9b92-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="e9b92-112">Aby zapobiec przerywaniu pierwszego błędu w programie Visual Studio, po prostu wyczyść pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="e9b92-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="e9b92-113">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9b92-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e9b92-114">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e9b92-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="e9b92-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9b92-115">Example</span></span>

<span data-ttu-id="e9b92-116">W tym przykładzie pokazano, jak umieścić try-catch bloków wokół <xref:System.AggregateException?displayProperty=nameWithType>kodu, który wykonuje kwerendę, aby złapać wszelkie s, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="e9b92-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="e9b92-117">W tym przykładzie kwerenda nie może kontynuować po zarzuceniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="e9b92-118">Do czasu, gdy kod aplikacji łapie wyjątek, PLINQ już zatrzymał kwerendę na wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="e9b92-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="e9b92-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9b92-119">Example</span></span>

<span data-ttu-id="e9b92-120">W poniższym przykładzie pokazano, jak umieścić blok try-catch w delegata, aby umożliwić przechwyt wyjątek i kontynuować wykonywanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="e9b92-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="e9b92-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e9b92-121">Compiling the Code</span></span>

- <span data-ttu-id="e9b92-122">Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu przykładu danych PLINQ i wywołaj metodę z main.</span><span class="sxs-lookup"><span data-stu-id="e9b92-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="e9b92-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e9b92-123">Robust Programming</span></span>

<span data-ttu-id="e9b92-124">Nie należy przechwytywać wyjątek, chyba że wiesz, jak go obsłużyć, tak aby nie uszkodzić stan programu.</span><span class="sxs-lookup"><span data-stu-id="e9b92-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9b92-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9b92-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="e9b92-126">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e9b92-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
