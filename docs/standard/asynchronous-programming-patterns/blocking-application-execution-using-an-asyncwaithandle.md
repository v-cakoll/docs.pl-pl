---
title: Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 380080c0aa05bc5b94c9ec5fe471f2f255562cd2
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="51be5-102">Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="51be5-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="51be5-103">Aplikacje, których nie można nadal wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej zablokować przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="51be5-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="51be5-104">Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych wątku głównego aplikacji, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="51be5-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="51be5-105">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć *** OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="51be5-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method.</span></span> <span data-ttu-id="51be5-106">Takie podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="51be5-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="51be5-107">Wywołaj operację asynchroniczną **zakończenia *** OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="51be5-107">Call the asynchronous operation's **End***OperationName* method.</span></span> <span data-ttu-id="51be5-108">Na przykład, który pokazuje tej metody, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="51be5-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="51be5-109">Aplikacje korzystające z co najmniej jeden <xref:System.Threading.WaitHandle> zwykle wywoła obiekty mają być blokowane, aż do zakończenia operacji asynchronicznej **rozpocząć *** OperationName* metody, wykonać pracę, które mogą być przeprowadzane bez wyników Operacja, a następnie bloku dopiero po zakończeniu operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="51be5-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin***OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="51be5-110">Aplikacja może zablokować w ramach jednej operacji, wywołując jedną z <xref:System.Threading.WaitHandle.WaitOne%2A> przy użyciu metody <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="51be5-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="51be5-111">Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych zbiór, przechowywania skojarzonych <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołanie jedną <xref:System.Threading.WaitHandle.WaitAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51be5-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="51be5-112">Mają być blokowane podczas oczekiwania na dowolny zbiór na zakończenie operacji asynchronicznych, przechowywania skojarzonych <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołanie jedną <xref:System.Threading.WaitHandle.WaitAny%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51be5-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51be5-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="51be5-113">Example</span></span>  
 <span data-ttu-id="51be5-114">Poniższy przykład kodu pokazuje używanie metod asynchronicznych klasy DNS można pobrać informacji o systemie nazw domen dla komputera określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51be5-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="51be5-115">W przykładzie pokazano, blokowanie, przy użyciu <xref:System.Threading.WaitHandle> skojarzone z operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="51be5-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="51be5-116">Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametrów, ponieważ nie są one wymagane przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="51be5-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="51be5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51be5-117">See Also</span></span>  
 [<span data-ttu-id="51be5-118">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="51be5-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="51be5-119">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="51be5-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
