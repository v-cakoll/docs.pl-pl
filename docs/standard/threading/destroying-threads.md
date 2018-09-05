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
ms.openlocfilehash: 5cd6e85dca7c4c32361b964573f318b165e8d683
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562940"
---
# <a name="destroying-threads"></a><span data-ttu-id="53ac5-102">Niszczenie wątków</span><span class="sxs-lookup"><span data-stu-id="53ac5-102">Destroying threads</span></span>
<span data-ttu-id="53ac5-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda jest używana do zatrzymywania wątków zarządzanych trwałe.</span><span class="sxs-lookup"><span data-stu-id="53ac5-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="53ac5-104">Gdy wywołujesz <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątek docelowy może przechwycić wątek docelowy.</span><span class="sxs-lookup"><span data-stu-id="53ac5-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="53ac5-105">Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53ac5-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53ac5-106">Jeśli wykonywany jest wątek niezarządzanego kodu podczas jego <xref:System.Threading.Thread.Abort%2A> metoda jest wywoływana, środowisko uruchomieniowe oznacza je <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53ac5-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53ac5-107">Wyjątek jest generowany, kiedy wątek wraca z kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="53ac5-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="53ac5-108">Gdy wątek jest przerwany, nie można uruchomić ponownie.</span><span class="sxs-lookup"><span data-stu-id="53ac5-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="53ac5-109"><xref:System.Threading.Thread.Abort%2A> Metoda nie powoduje, że wątek przerwać natychmiast, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonywanie dowolnych ilości kodu w `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="53ac5-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="53ac5-110">Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli musisz poczekać, aż wątek została zakończona.</span><span class="sxs-lookup"><span data-stu-id="53ac5-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="53ac5-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jest wywołania blokowania, która nie zwraca aż wątek faktycznie zatrzymała wykonywanie lub opcjonalny limit czasu upłynął.</span><span class="sxs-lookup"><span data-stu-id="53ac5-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="53ac5-112">Przerwanie wątku można wywołać <xref:System.Threading.Thread.ResetAbort%2A> metody lub wykonywania przetwarzania niepowiązanego w `finally` zablokować, więc jeśli nie określisz przekroczenie limitu czasu, czas oczekiwania nie gwarantuje zakończenia.</span><span class="sxs-lookup"><span data-stu-id="53ac5-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="53ac5-113">Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda może zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53ac5-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="53ac5-114">ThreadAbortException — Obsługa</span><span class="sxs-lookup"><span data-stu-id="53ac5-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="53ac5-115">Jeśli oczekujesz, że wątek przerwanie, w wyniku wywołania metody <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowywania domeny aplikacji, w którym wątek jest uruchomiony (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończenie wątków), wątek musi obsługiwać. <xref:System.Threading.ThreadAbortException> i wykonywać żadnego przetwarzania końcowego w `finally` klauzuli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="53ac5-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="53ac5-116">Twój kod czyszczenia musi znajdować się w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest zgłaszany ponownie przez system na końcu `finally` klauzuli lub na końcu `catch` klauzuli w przypadku nie `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="53ac5-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="53ac5-117">Można zapobiec systemu przez wywołanie metody ponowne generowanie wyjątku <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="53ac5-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="53ac5-118">Jednak zrobić, to tylko wtedy, gdy Twój własny kod spowodowało <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="53ac5-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ac5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53ac5-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="53ac5-120">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="53ac5-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
