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
ms.openlocfilehash: 8e6eff0caa76349ce441a662428e37e25e2a6518
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582942"
---
# <a name="destroying-threads"></a><span data-ttu-id="41802-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="41802-102">Destroying Threads</span></span>
<span data-ttu-id="41802-103"><xref:System.Threading.Thread.Abort%2A> Metoda jest używana do zatrzymania wątku zarządzanego trwale.</span><span class="sxs-lookup"><span data-stu-id="41802-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="41802-104">Podczas wywoływania <xref:System.Threading.Thread.Abort%2A>, zgłasza środowisko uruchomieniowe języka wspólnego <xref:System.Threading.ThreadAbortException> w wątek docelowy wątek docelowy może catch.</span><span class="sxs-lookup"><span data-stu-id="41802-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="41802-105">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41802-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41802-106">Jeśli wykonuje wątku niezarządzanego kodu, gdy jego <xref:System.Threading.Thread.Abort%2A> metoda jest wywoływana, środowisko uruchomieniowe oznacza je <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41802-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41802-107">Wyjątek jest zgłaszany, gdy wątek powróci do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="41802-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="41802-108">Gdy wątek jest przerywana, nie można uruchomić ponownie.</span><span class="sxs-lookup"><span data-stu-id="41802-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="41802-109"><xref:System.Threading.Thread.Abort%2A> — Metoda nie powoduje, że wątek przerwania natychmiast, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonania dowolnego ilości kodu w `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="41802-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="41802-110">Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli należy poczekać, aż wątek została zakończona.</span><span class="sxs-lookup"><span data-stu-id="41802-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="41802-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> to wywołanie blokowania, która nie zwraca aż do wykonywania faktycznie zatrzymania wątku lub opcjonalne limit czasu upłynął.</span><span class="sxs-lookup"><span data-stu-id="41802-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="41802-112">Przerwanego wątku można wywołać <xref:System.Threading.Thread.ResetAbort%2A> metody lub niepowiązany przetwarzania w `finally` zablokować, jeśli nie określisz limit czasu, czas oczekiwania nie jest gwarantowana do końca.</span><span class="sxs-lookup"><span data-stu-id="41802-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="41802-113">Wątków, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> — metoda może zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41802-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="41802-114">Obsługa ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="41802-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="41802-115">Jeśli Twoje wątku zostać przerwane w wyniku wywołania metody <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub wyniku zwolnienie domeny aplikacji, w którym jest uruchomiony wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończenie wątków), musi obsługiwać Twoje wątku <xref:System.Threading.ThreadAbortException> i wykonywać żadnych końcowego przetwarzania w `finally` klauzuli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="41802-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="41802-116">Oczyszczanie kodu musi być w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest zgłoszony przez system na końcu `finally` klauzuli, lub na końcu `catch` klauzuli, jeśli istnieje nie `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="41802-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="41802-117">System uniemożliwia ponowne generowanie wyjątku przez wywołanie metody <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="41802-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="41802-118">Jednak należy wykonać tylko wtedy, gdy ich w swoim własnym kodem spowodowane <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="41802-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41802-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41802-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="41802-120">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="41802-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
