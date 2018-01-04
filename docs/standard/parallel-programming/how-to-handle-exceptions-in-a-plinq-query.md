---
title: "Porady: obsługa wyjątków w zapytaniu PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3e09bc2b285d014a7d3a6ed6fc4e50f85b537d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="aa808-102">Porady: obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="aa808-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="aa808-103">Pierwszym przykładzie w tym temacie przedstawiono sposób obsługi <xref:System.AggregateException?displayProperty=nameWithType> który mógł zostać zgłoszony w zapytaniu PLINQ podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aa808-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="aa808-104">Drugi przykład przedstawia sposób możliwie, do której zostanie wyjątek put bloków try-catch w obrębie obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="aa808-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="aa808-105">W ten sposób można je catch natychmiast wystąpić i być może kontynuować wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="aa808-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="aa808-106">Jest wywoływane, gdy wyjątki mogą bąbelkowy się wstecz do łącząca wątku, możliwe zapytania mogą nadal przetwarzania niektórych elementów po wyjątku jest.</span><span class="sxs-lookup"><span data-stu-id="aa808-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="aa808-107">W niektórych przypadkach po PLINQ powraca do wykonywania sekwencyjnego, i wystąpi wyjątek, wyjątek może być propagowane bezpośrednio i nie są ujęte w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="aa808-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="aa808-108">Ponadto <xref:System.Threading.ThreadAbortException>s zawsze są propagowane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="aa808-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa808-109">Po włączeniu "Tylko mój kod" programu Visual Studio będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="aa808-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="aa808-110">Ten błąd jest niegroźne.</span><span class="sxs-lookup"><span data-stu-id="aa808-110">This error is benign.</span></span> <span data-ttu-id="aa808-111">Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="aa808-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="aa808-112">Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="aa808-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="aa808-113">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="aa808-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="aa808-114">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="aa808-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa808-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa808-115">Example</span></span>  
 <span data-ttu-id="aa808-116">W tym przykładzie pokazano, jak put bloków try-catch wokół kod, który wykonuje zapytanie, aby wykryć wszelkie <xref:System.AggregateException?displayProperty=nameWithType>, które są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="aa808-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="aa808-117">W tym przykładzie zapytanie nie może kontynuować po wyjątku.</span><span class="sxs-lookup"><span data-stu-id="aa808-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="aa808-118">W czasie przechwycony wyjątek w kodzie aplikacji PLINQ ma już przestał wykonywać zapytanie na wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="aa808-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa808-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa808-119">Example</span></span>  
 <span data-ttu-id="aa808-120">Poniższy przykład pokazuje, jak wprowadzić bloku try-catch w pełnomocnika, aby umożliwić catch wyjątku i kontynuować wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="aa808-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa808-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aa808-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="aa808-122">Aby skompilować i uruchomić te przykłady, skopiuj je do przykład próbka danych PLINQ i wywołać metodę z głównym.</span><span class="sxs-lookup"><span data-stu-id="aa808-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="aa808-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="aa808-123">Robust Programming</span></span>  
 <span data-ttu-id="aa808-124">Nie przechwytuj wyjątków, jeśli nie wiadomo, jak obsługiwać go tak, aby nie spowodować uszkodzenie stanu programu.</span><span class="sxs-lookup"><span data-stu-id="aa808-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa808-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa808-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="aa808-126">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="aa808-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
