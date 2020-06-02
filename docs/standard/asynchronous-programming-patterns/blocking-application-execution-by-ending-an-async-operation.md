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
ms.openlocfilehash: 74976176acc0fbb948c514358b7bd323cc20c134
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289957"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="4294d-102">Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="4294d-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="4294d-103">Aplikacje, które nie mogą kontynuować wykonywania innych zadań podczas oczekiwania na wyniki operacji asynchronicznej, muszą być blokowane do momentu zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="4294d-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="4294d-104">Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na ukończenie operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="4294d-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="4294d-105">Wywołaj metodę **kończenia**_operacji operacji_ asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="4294d-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="4294d-106">Ta metoda jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="4294d-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="4294d-107">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości <xref:System.IAsyncResult> zwracanej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="4294d-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="4294d-108">Przykład demonstrujący tę metodę można znaleźć w temacie [blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="4294d-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="4294d-109">Aplikacje korzystające z **metody End**_OperationName_ do blokowania do momentu ukończenia operacji asynchronicznej zwykle wywołują **metodę Begin**_OperationName_ , wykonują wszelkie zadania, które można wykonać bez wyników operacji, a następnie Wywołaj **zakończenie**_operacji_.</span><span class="sxs-lookup"><span data-stu-id="4294d-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4294d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4294d-110">Example</span></span>  
 <span data-ttu-id="4294d-111">Poniższy przykład kodu demonstruje użycie metod asynchronicznych w <xref:System.Net.Dns> klasie w celu pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4294d-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="4294d-112">Należy zauważyć, że `null` ( `Nothing` w Visual Basic) jest przekazane do <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` parametrów i, `stateObject` ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="4294d-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4294d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4294d-113">See also</span></span>

- [<span data-ttu-id="4294d-114">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="4294d-114">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="4294d-115">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="4294d-115">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
