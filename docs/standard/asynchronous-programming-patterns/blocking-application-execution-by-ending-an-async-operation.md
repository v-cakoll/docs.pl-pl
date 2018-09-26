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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: db8255e28818cc4def69e6dcd9da06eb7f9251a0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216763"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="66203-102">Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="66203-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="66203-103">Aplikacje, które nie mogą w dalszym ciągu wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej należy zablokować, aż do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="66203-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="66203-104">Blokowanie wątku głównego aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="66203-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="66203-105">Wywoływanie operacji asynchronicznych \**zakończenia \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="66203-105">Call the asynchronous operations \**End\*\*\*OperationName* method.</span></span> <span data-ttu-id="66203-106">To podejście jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="66203-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="66203-107">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną \**rozpocząć \*\*\* OperationName* metody.</span><span class="sxs-lookup"><span data-stu-id="66203-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method.</span></span> <span data-ttu-id="66203-108">Aby uzyskać przykład demonstrujący takie podejście, zobacz [blokowania aplikacji wykonywania za pomocą właściwości AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="66203-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="66203-109">Aplikacje, które używają \**zakończenia \*\*\* OperationName* zazwyczaj wywoła metodę, aby zablokować do czasu ukończenia operacji asynchronicznej \**rozpocząć \*\*\* OperationName* metody, wykonać wszelkie prace, które można zrobić bez wyniki operacji, a następnie wywołania \**zakończenia \*\*\* OperationName*.</span><span class="sxs-lookup"><span data-stu-id="66203-109">Applications that use the \**End\*\*\*OperationName* method to block until an asynchronous operation is complete will typically call the \**Begin\*\*\*OperationName* method, perform any work that can be done without the results of the operation, and then call \**End\*\*\*OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66203-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="66203-110">Example</span></span>  
 <span data-ttu-id="66203-111">Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji System nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="66203-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="66203-112">Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.</span><span class="sxs-lookup"><span data-stu-id="66203-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="66203-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66203-113">See also</span></span>

- [<span data-ttu-id="66203-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="66203-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="66203-115">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="66203-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
