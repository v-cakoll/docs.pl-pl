---
title: Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121327"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="5c8c1-102">Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c8c1-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="5c8c1-103">Aplikacje, które nie mogą kontynuować wykonywania innych prac podczas oczekiwania na wyniki operacji asynchronicznej, muszą blokować, dopóki operacja nie zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="5c8c1-104">Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="5c8c1-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="5c8c1-105">Wywołaj operacje asynchroniczne **End**_OperationName_ metody.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="5c8c1-106">Takie podejście przedstawiono w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="5c8c1-107">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="5c8c1-108">Na przykład, który demonstruje to podejście, zobacz [Blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="5c8c1-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="5c8c1-109">Aplikacje, które używają **End**_OperationName_ metody do blokowania aż do zakończenia operacji asynchronicznej zazwyczaj wywoła **Begin**_OperationName_ metody, wykonać dowolną pracę, która może być wykonana bez wyników operacji, a następnie **wywołać End**_OperationName_.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c8c1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c8c1-110">Example</span></span>  
 <span data-ttu-id="5c8c1-111">Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="5c8c1-112">Należy `null` zauważyć,`Nothing` że ( w <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` języku Visual Basic) jest przekazywana dla parametrów i `stateObject` ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="5c8c1-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5c8c1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c8c1-113">See also</span></span>

- [<span data-ttu-id="5c8c1-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="5c8c1-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="5c8c1-115">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="5c8c1-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
