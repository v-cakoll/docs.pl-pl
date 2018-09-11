---
title: Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 054af36987d60c8aeb752c9c711f1cce19733efc
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339581"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="feb1e-102">Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="feb1e-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="feb1e-103">Aplikacje, które nie mogą w dalszym ciągu wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej należy zablokować, aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="feb1e-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="feb1e-104">Blokowanie wątku głównego aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="feb1e-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="feb1e-105">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną \**rozpocząć \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="feb1e-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method.</span></span> <span data-ttu-id="feb1e-106">To podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="feb1e-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="feb1e-107">Wywołaj operację asynchroniczną \**zakończenia \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="feb1e-107">Call the asynchronous operation's \**End\*\*\*OperationName* method.</span></span> <span data-ttu-id="feb1e-108">Aby uzyskać przykład demonstrujący takie podejście, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="feb1e-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="feb1e-109">Aplikacje używające co najmniej jeden <xref:System.Threading.WaitHandle> obiektów, aby zablokować do czasu ukończenia operacji asynchronicznej zazwyczaj będzie wywoływać \**rozpocząć \*\*\* OperationName* metody, wykonać wszelkie prace, które może odbywać się bez wyników Operacja, a następnie blok do momentu ukończenia operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="feb1e-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the \**Begin\*\*\*OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="feb1e-110">Aplikacja może zablokować w ramach jednej operacji, wywołując jedną z <xref:System.Threading.WaitHandle.WaitOne%2A> metod za pomocą <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="feb1e-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="feb1e-111">Aby zablokować podczas oczekiwania na zbiór na zakończenie operacji asynchronicznej, przechowywania skojarzonego <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiektów w tablicy i wywołanie jednej <xref:System.Threading.WaitHandle.WaitAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="feb1e-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="feb1e-112">Aby zablokować podczas oczekiwania na dowolny zbiór na zakończenie operacji asynchronicznej, przechowywania skojarzonego <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiektów w tablicy i wywołanie jednej <xref:System.Threading.WaitHandle.WaitAny%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="feb1e-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb1e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="feb1e-113">Example</span></span>  
 <span data-ttu-id="feb1e-114">Poniższy przykład kodu demonstruje używanie metod asynchronicznych w klasie DNS, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="feb1e-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="feb1e-115">W przykładzie pokazano, blokowanie, za pomocą <xref:System.Threading.WaitHandle> skojarzony z operacją asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="feb1e-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="feb1e-116">Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametrów, ponieważ nie są wymagane podczas używania tej metody.</span><span class="sxs-lookup"><span data-stu-id="feb1e-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="feb1e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feb1e-117">See also</span></span>

- [<span data-ttu-id="feb1e-118">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="feb1e-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="feb1e-119">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="feb1e-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
