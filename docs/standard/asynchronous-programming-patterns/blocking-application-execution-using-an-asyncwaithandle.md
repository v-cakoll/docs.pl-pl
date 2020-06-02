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
ms.openlocfilehash: 6184e52c3f6e39e452331af27b83520e498062aa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289931"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="a44b4-102">Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="a44b4-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="a44b4-103">Aplikacje, które nie mogą kontynuować wykonywania innych zadań podczas oczekiwania na wyniki operacji asynchronicznej, muszą być blokowane do momentu zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="a44b4-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="a44b4-104">Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na ukończenie operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="a44b4-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="a44b4-105">Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości <xref:System.IAsyncResult> zwracanej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a44b4-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="a44b4-106">Ta metoda jest przedstawiona w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a44b4-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="a44b4-107">Wywołaj metodę **End**_OperationName_ operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a44b4-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="a44b4-108">Aby zapoznać się z przykładem, który ilustruje to podejście, zobacz [blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="a44b4-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="a44b4-109">Aplikacje używające co najmniej jednego <xref:System.Threading.WaitHandle> obiektu do zablokowania do momentu ukończenia operacji asynchronicznej zwykle wywołują metodę **BEGIN**_OperationName_ , wykonują wszelkie zadania, które można wykonać bez wyników operacji, a następnie blokują do momentu zakończenia operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="a44b4-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="a44b4-110">Aplikacja może blokować pojedyncze operacje, wywołując jedną z <xref:System.Threading.WaitHandle.WaitOne%2A> metod przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A> .</span><span class="sxs-lookup"><span data-stu-id="a44b4-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="a44b4-111">Aby zablokować podczas oczekiwania na zakończenie zestawu operacji asynchronicznych, należy przechowywać skojarzone <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołać jedną z <xref:System.Threading.WaitHandle.WaitAll%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="a44b4-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="a44b4-112">Aby zablokować podczas oczekiwania na zakończenie jednego z zestawów operacji asynchronicznych, należy przechowywać skojarzone <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywoływać jedną z <xref:System.Threading.WaitHandle.WaitAny%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="a44b4-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a44b4-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a44b4-113">Example</span></span>  
 <span data-ttu-id="a44b4-114">Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie DNS w celu pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a44b4-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="a44b4-115">W przykładzie pokazano blokowanie przy użyciu <xref:System.Threading.WaitHandle> skojarzonego z operacją asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="a44b4-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="a44b4-116">Należy pamiętać, że `null` ( `Nothing` w Visual Basic) są przesyłane do <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` parametrów i, `stateObject` ponieważ nie są one wymagane podczas korzystania z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="a44b4-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a44b4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a44b4-117">See also</span></span>

- [<span data-ttu-id="a44b4-118">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="a44b4-118">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="a44b4-119">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="a44b4-119">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
