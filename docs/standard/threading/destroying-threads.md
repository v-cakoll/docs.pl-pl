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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960089"
---
# <a name="destroying-threads"></a><span data-ttu-id="fc7fc-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="fc7fc-102">Destroying threads</span></span>
<span data-ttu-id="fc7fc-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda służy do trwałego zatrzymania wątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="fc7fc-104">Podczas wywoływania <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego <xref:System.Threading.ThreadAbortException> generuje w wątku docelowym, który wątek docelowy może przechwycić.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="fc7fc-105">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc7fc-106">Jeśli wątek wykonuje kod niezarządzany, gdy <xref:System.Threading.Thread.Abort%2A> Metoda jest wywoływana, środowisko uruchomieniowe go <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>oznaczy.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc7fc-107">Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="fc7fc-108">Po przerwaniu wątku nie można go ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="fc7fc-109">Metoda nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może <xref:System.Threading.ThreadAbortException> przechwycić i wykonać dowolne `finally` ilości kodu w bloku. <xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="fc7fc-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="fc7fc-110">Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> , jeśli musisz poczekać na zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="fc7fc-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="fc7fc-112">Przerwany wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać nieograniczone przetwarzanie `finally` w bloku, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="fc7fc-113">Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody mogą zostać przerwane przez inne wątki, które wywołują. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fc7fc-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="fc7fc-114">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="fc7fc-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="fc7fc-115">Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia wątków), wątek musi obsłużyć i wykonać wszelkie końcowe przetwarzanie `finally` w klauzuli, jak pokazano w poniższym kodzie. <xref:System.Threading.ThreadAbortException></span><span class="sxs-lookup"><span data-stu-id="fc7fc-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="fc7fc-116">Kod czyszczący musi znajdować `catch` się w klauzuli `finally` lub klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany `finally` przez system na końcu klauzuli lub na końcu `catch` klauzuli, jeśli nie `finally` ma klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="fc7fc-117">Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fc7fc-118">Jednak należy to zrobić tylko wtedy, <xref:System.Threading.ThreadAbortException>gdy własny kod spowodował.</span><span class="sxs-lookup"><span data-stu-id="fc7fc-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7fc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc7fc-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="fc7fc-120">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="fc7fc-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
