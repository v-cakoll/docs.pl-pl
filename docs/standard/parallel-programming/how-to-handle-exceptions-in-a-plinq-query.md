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
ms.openlocfilehash: ef107ae0dceb7ee937b21d65cba92cbcf6a9a96c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628999"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="93f9b-102">Instrukcje: Obsługa wyjątków w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="93f9b-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="93f9b-103">Pierwszy przykład w tym temacie przedstawiono sposób obsługi <xref:System.AggregateException?displayProperty=nameWithType> , mogą być generowane w wyniku zapytania PLINQ, podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="93f9b-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="93f9b-104">Drugi przykład pokazuje, jak umieścić bloków try-catch w obrębie delegatów, w jak najbardziej zbliżony do której zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="93f9b-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="93f9b-105">W ten sposób możesz przechwytywać je jak najszybciej występują i ewentualnie kontynuować wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="93f9b-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="93f9b-106">Kiedy wyjątki mogą się pojawiać z powrotem w sąsiednim wątku, jest możliwe, że zapytanie może w dalszym ciągu przetwarzać niektóre elementy po wyjątku jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="93f9b-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="93f9b-107">W niektórych przypadkach PLINQ powraca do wykonywania sekwencyjnego, gdy wystąpi wyjątek, wyjątek może być propagowane bezpośrednio i nie zostały opakowane w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="93f9b-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="93f9b-108">Ponadto <xref:System.Threading.ThreadAbortException>s zawsze są propagowane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="93f9b-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93f9b-109">Po włączeniu "Tylko mój kod" Visual Studio będzie przerwania w wierszu, który zgłasza wyjątek i wyświetlać komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="93f9b-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="93f9b-110">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="93f9b-110">This error is benign.</span></span> <span data-ttu-id="93f9b-111">Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="93f9b-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="93f9b-112">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="93f9b-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="93f9b-113">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="93f9b-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="93f9b-114">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="93f9b-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f9b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="93f9b-115">Example</span></span>  
 <span data-ttu-id="93f9b-116">W tym przykładzie pokazano, jak umieścić bloków try-catch wokół kodu, który wykonuje zapytanie, aby przechwytywać wszystkie <xref:System.AggregateException?displayProperty=nameWithType>s, które są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="93f9b-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="93f9b-117">W tym przykładzie zapytanie nie może kontynuować po wyrzuceniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="93f9b-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="93f9b-118">Według czasu, w kodzie aplikacji przechwytuje wyjątek PLINQ została już zatrzymana zapytanie we wszystkich wątkach.</span><span class="sxs-lookup"><span data-stu-id="93f9b-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f9b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="93f9b-119">Example</span></span>  
 <span data-ttu-id="93f9b-120">Poniższy przykład pokazuje, jak umieścić bloku try / catch w delegacie, aby umożliwić przechwytywać wyjątek, a następnie kontynuuj wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="93f9b-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93f9b-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="93f9b-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="93f9b-122">Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu próbka danych PLINQ i wywołać metodę z Main.</span><span class="sxs-lookup"><span data-stu-id="93f9b-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="93f9b-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="93f9b-123">Robust Programming</span></span>  
 <span data-ttu-id="93f9b-124">Nie przechwytuj wyjątek, chyba że wiesz, jak je obsłużyć, dzięki czemu nie spowodują uszkodzenia stanu programu.</span><span class="sxs-lookup"><span data-stu-id="93f9b-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f9b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93f9b-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="93f9b-126">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="93f9b-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
