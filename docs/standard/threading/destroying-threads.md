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
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155935"
---
# <a name="destroying-threads"></a><span data-ttu-id="02df9-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="02df9-102">Destroying threads</span></span>

<span data-ttu-id="02df9-103">Aby zakończyć wykonywanie wątku, zwykle należy użyć [modelu anulowania współpracy](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="02df9-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="02df9-104">Czasami nie jest możliwe, aby zatrzymać wątek kooperatywnie, ponieważ uruchamia kod innej firmy nie przeznaczony do anulowania współpracy.</span><span class="sxs-lookup"><span data-stu-id="02df9-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="02df9-105">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> w .NET Framework może służyć do zakończenia wątku zarządzanego siłą.</span><span class="sxs-lookup"><span data-stu-id="02df9-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="02df9-106">Po wywołaniu <xref:System.Threading.Thread.Abort%2A>, common language runtime zgłasza <xref:System.Threading.ThreadAbortException> w wątku docelowego, które wątek docelowy może przechwycić.</span><span class="sxs-lookup"><span data-stu-id="02df9-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="02df9-107">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02df9-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="02df9-108">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02df9-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="02df9-109">Jeśli musisz zakończyć wykonywanie kodu innej firmy siłą w .NET Core, uruchom go <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>w oddzielnym procesie i użyj .</span><span class="sxs-lookup"><span data-stu-id="02df9-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="02df9-110">Jeśli wątek wykonuje kod niezarządzany, <xref:System.Threading.Thread.Abort%2A> gdy jego metoda jest <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>wywoływana, czas wykonywania oznacza go .</span><span class="sxs-lookup"><span data-stu-id="02df9-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="02df9-111">Wyjątek jest generowany, gdy wątek zwraca do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="02df9-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="02df9-112">Po przerwanie wątku nie można go ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="02df9-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="02df9-113">Metoda <xref:System.Threading.Thread.Abort%2A> nie powoduje wątku do przerwania natychmiast, ponieważ wątek <xref:System.Threading.ThreadAbortException> docelowy można przechwycić `finally` i wykonać dowolną ilość kodu w bloku.</span><span class="sxs-lookup"><span data-stu-id="02df9-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="02df9-114">Można wywołać, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jeśli trzeba poczekać, aż wątek zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="02df9-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="02df9-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołanie blokujące, które nie zwraca, dopóki wątek faktycznie przestał wykonywać lub opcjonalny przedział czasu upłynął.</span><span class="sxs-lookup"><span data-stu-id="02df9-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="02df9-116">Przerwana wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać przetwarzanie `finally` nieograniczone w bloku, więc jeśli nie określisz limitu czasu, oczekiwanie nie jest gwarantowane do końca.</span><span class="sxs-lookup"><span data-stu-id="02df9-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="02df9-117">Wątki, które oczekują na <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> wywołanie metody może być przerwane <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>przez inne wątki, które wywołają .</span><span class="sxs-lookup"><span data-stu-id="02df9-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="02df9-118">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="02df9-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="02df9-119">Jeśli oczekujesz, że wątek zostanie przerwane, albo <xref:System.Threading.Thread.Abort%2A> w wyniku wywołania z własnego kodu lub w wyniku<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zwalniania domeny aplikacji, w którym działa wątek (używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do zakończenia wątków), wątek musi obsługiwać <xref:System.Threading.ThreadAbortException> i wykonać wszelkie końcowe przetwarzanie w `finally` klauzuli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="02df9-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="02df9-120">Kod oczyszczania musi być w `catch` klauzuli `finally` lub klauzuli, <xref:System.Threading.ThreadAbortException> ponieważ jest rethrown przez `finally` system na końcu klauzuli lub na końcu `catch` klauzuli, jeśli nie `finally` ma klauzuli.</span><span class="sxs-lookup"><span data-stu-id="02df9-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="02df9-121">Można zapobiec system z ponownego wymuszenia wyjątku, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="02df9-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="02df9-122">Jednak należy to zrobić tylko wtedy, <xref:System.Threading.ThreadAbortException>gdy własny kod spowodował .</span><span class="sxs-lookup"><span data-stu-id="02df9-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02df9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02df9-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="02df9-124">Korzystanie z wątków i wątków</span><span class="sxs-lookup"><span data-stu-id="02df9-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
