---
title: Niszczenie wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: 1852135e9b7f48d6556e27f16819ddd48805af21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138093"
---
# <a name="destroying-threads"></a><span data-ttu-id="e8bdd-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="e8bdd-102">Destroying threads</span></span>
<span data-ttu-id="e8bdd-103">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> służy do trwałego zatrzymania wątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="e8bdd-104">Gdy wywołasz <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątku docelowym, który może zostać przechwycony przez wątek docelowy.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="e8bdd-105">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8bdd-106">Jeśli wątek wykonuje kod niezarządzany, gdy jego Metoda <xref:System.Threading.Thread.Abort%2A> jest wywoływana, środowisko uruchomieniowe go oznaczy <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e8bdd-107">Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="e8bdd-108">Po przerwaniu wątku nie można go ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="e8bdd-109">Metoda <xref:System.Threading.Thread.Abort%2A> nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonać dowolne ilości kodu w bloku `finally`.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="e8bdd-110">Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, jeśli chcesz poczekać na zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="e8bdd-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="e8bdd-112">Przerwany wątek może wywołać metodę <xref:System.Threading.Thread.ResetAbort%2A> lub wykonać nieograniczone przetwarzanie w bloku `finally`, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="e8bdd-113">Wątki, które oczekują na wywołanie metody <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> mogą zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="e8bdd-114">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="e8bdd-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="e8bdd-115">Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której jest uruchomiony wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia wątków) , wątek musi obsłużyć <xref:System.Threading.ThreadAbortException> i wykonać wszelkie końcowe przetwarzanie w klauzuli `finally`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="e8bdd-116">Kod czyszczący musi znajdować się w klauzuli `catch` lub klauzuli `finally`, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany przez system na końcu klauzuli `finally` lub na końcu klauzuli `catch`, jeśli nie ma klauzuli `finally`.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="e8bdd-117">Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując metodę <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e8bdd-118">Jednak należy to zrobić tylko wtedy, gdy własny kod spowodował <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="e8bdd-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8bdd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8bdd-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="e8bdd-120">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="e8bdd-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
