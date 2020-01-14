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
ms.openlocfilehash: efd4c596f67d5eabace8ecafb48f2d350df6a18e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938048"
---
# <a name="destroying-threads"></a><span data-ttu-id="54fa2-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="54fa2-102">Destroying threads</span></span>

<span data-ttu-id="54fa2-103">Aby zakończyć wykonywanie wątku, zazwyczaj używany jest [wspólny model anulowania](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="54fa2-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="54fa2-104">Czasami nie jest możliwe zatrzymywanie wątku wspólnie, ponieważ uruchamia kod innej firmy, który nie został zaprojektowany w celu uzyskania spółdzielni.</span><span class="sxs-lookup"><span data-stu-id="54fa2-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="54fa2-105">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> w .NET Framework może służyć do kończenia wymuszania wątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="54fa2-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="54fa2-106">Gdy wywołasz <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątku docelowym, który może zostać przechwycony przez wątek docelowy.</span><span class="sxs-lookup"><span data-stu-id="54fa2-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="54fa2-107">Aby uzyskać więcej informacji, zobacz temat <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="54fa2-108">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fa2-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="54fa2-109">Jeśli konieczne jest zakończenie wykonywania kodu innej firmy w programie .NET Core, należy uruchomić go w osobnym procesie i użyć <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="54fa2-110">Jeśli wątek wykonuje kod niezarządzany, gdy jego Metoda <xref:System.Threading.Thread.Abort%2A> jest wywoływana, środowisko uruchomieniowe go oznaczy <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="54fa2-111">Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="54fa2-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="54fa2-112">Po przerwaniu wątku nie można go ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="54fa2-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="54fa2-113">Metoda <xref:System.Threading.Thread.Abort%2A> nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonać dowolne ilości kodu w bloku `finally`.</span><span class="sxs-lookup"><span data-stu-id="54fa2-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="54fa2-114">Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, jeśli chcesz poczekać na zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="54fa2-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="54fa2-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="54fa2-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="54fa2-116">Przerwany wątek może wywołać metodę <xref:System.Threading.Thread.ResetAbort%2A> lub wykonać nieograniczone przetwarzanie w bloku `finally`, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="54fa2-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="54fa2-117">Wątki, które oczekują na wywołanie metody <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> mogą zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="54fa2-118">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="54fa2-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="54fa2-119">Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do zakończenia wątków), wątek musi obsłużyć <xref:System.Threading.ThreadAbortException> i wykonać wszelkie końcowe przetwarzanie w klauzuli `finally`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="54fa2-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="54fa2-120">Kod czyszczący musi znajdować się w klauzuli `catch` lub klauzuli `finally`, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany przez system na końcu klauzuli `finally` lub na końcu klauzuli `catch`, jeśli nie ma klauzuli `finally`.</span><span class="sxs-lookup"><span data-stu-id="54fa2-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="54fa2-121">Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując metodę <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="54fa2-122">Jednak należy to zrobić tylko wtedy, gdy własny kod spowodował <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="54fa2-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fa2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54fa2-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="54fa2-124">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="54fa2-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
