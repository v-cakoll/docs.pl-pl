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
ms.openlocfilehash: 9f69773ec19008ebafd28a68e4e2007b6f9bb979
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279818"
---
# <a name="destroying-threads"></a><span data-ttu-id="2bb22-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="2bb22-102">Destroying threads</span></span>

<span data-ttu-id="2bb22-103">Aby zakończyć wykonywanie wątku, zazwyczaj używany jest [wspólny model anulowania](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2bb22-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="2bb22-104">Czasami nie jest możliwe zatrzymywanie wątku wspólnie, ponieważ uruchamia kod innej firmy, który nie został zaprojektowany w celu uzyskania spółdzielni.</span><span class="sxs-lookup"><span data-stu-id="2bb22-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="2bb22-105"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda w .NET Framework może służyć do kończenia wymuszonego wymuszenia wątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2bb22-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="2bb22-106">Podczas wywoływania <xref:System.Threading.Thread.Abort%2A> , środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątku docelowym, który wątek docelowy może przechwycić.</span><span class="sxs-lookup"><span data-stu-id="2bb22-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="2bb22-107">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bb22-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2bb22-108"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda nie jest obsługiwana w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bb22-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="2bb22-109">Jeśli konieczne jest zakończenie wykonywania kodu innej firmy w programie .NET Core, należy uruchomić go w osobnym procesie i użyć <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2bb22-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="2bb22-110">Jeśli wątek wykonuje kod niezarządzany, gdy <xref:System.Threading.Thread.Abort%2A> Metoda jest wywoływana, środowisko uruchomieniowe go oznaczy <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2bb22-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2bb22-111">Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="2bb22-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="2bb22-112">Po przerwaniu wątku nie można go ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="2bb22-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="2bb22-113"><xref:System.Threading.Thread.Abort%2A>Metoda nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonać dowolne ilości kodu w `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="2bb22-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="2bb22-114">Możesz wywołać, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli musisz poczekać na zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="2bb22-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="2bb22-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="2bb22-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="2bb22-116">Przerwany wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać nieograniczone przetwarzanie w `finally` bloku, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="2bb22-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="2bb22-117">Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody mogą zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2bb22-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="2bb22-118">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="2bb22-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="2bb22-119">Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek ( <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia wątków), wątek musi obsłużyć <xref:System.Threading.ThreadAbortException> i wykonać dowolne końcowe przetwarzanie w `finally` klauzuli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2bb22-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="2bb22-120">Kod czyszczący musi znajdować się w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany przez system na końcu `finally` klauzuli lub na końcu `catch` klauzuli, jeśli nie ma `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2bb22-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="2bb22-121">Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="2bb22-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2bb22-122">Jednak należy to zrobić tylko wtedy, gdy własny kod spowodował <xref:System.Threading.ThreadAbortException> .</span><span class="sxs-lookup"><span data-stu-id="2bb22-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb22-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bb22-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="2bb22-124">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="2bb22-124">Using Threads and Threading</span></span>](using-threads-and-threading.md)
