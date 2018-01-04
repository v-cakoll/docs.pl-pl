---
title: "Wstrzymywanie i wznawianie wątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4b87fbb51dbdcd5226a902e8b7ee5aeb7e126b7e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="c5557-102">Wstrzymywanie i wznawianie wątków</span><span class="sxs-lookup"><span data-stu-id="c5557-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="c5557-103">Najbardziej typowe sposoby synchronizowania działania wątków są bloku i wersji wątków lub obiektów blokady lub regiony kodu.</span><span class="sxs-lookup"><span data-stu-id="c5557-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="c5557-104">Aby uzyskać więcej informacji o tych blokowania i blokuje mechanizmów, zobacz [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="c5557-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="c5557-105">Może także zawierać wątków put samodzielnie w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="c5557-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="c5557-106">Gdy wątki są zablokowane lub uśpiony, można użyć <xref:System.Threading.ThreadInterruptedException> celu wyjścia ich stany oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="c5557-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="c5557-107">Metoda Thread.Sleep</span><span class="sxs-lookup"><span data-stu-id="c5557-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="c5557-108">Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda powoduje, że bieżący wątek natychmiast zablokować liczbę milisekund lub przedział czasu możesz przekazać do metody i daje w pozostałej części jej przedział czasu do innego wątku.</span><span class="sxs-lookup"><span data-stu-id="c5557-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="c5557-109">Po upływie tego przedziału, uśpiony wątku wznawia wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="c5557-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="c5557-110">Nie można wywołać jeden wątek <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="c5557-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="c5557-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>jest metodą statyczną, która zawsze powoduje, że bieżący wątek w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="c5557-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="c5557-112">Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> o wartości <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> powoduje, że wątek w stan uśpienia, dopóki nie zostanie przerwane przez inny wątek, który wywołuje <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w wątku uśpiony lub dopóki zostanie przerwany przez wywołanie do jego <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c5557-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="c5557-113">Poniższy przykład przedstawia obu metod przerwania uśpiony wątku.</span><span class="sxs-lookup"><span data-stu-id="c5557-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="c5557-114">Przerywanie wątków</span><span class="sxs-lookup"><span data-stu-id="c5557-114">Interrupting Threads</span></span>  
 <span data-ttu-id="c5557-115">Można przerwać wątek oczekiwania przez wywołanie metody <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w wątku zablokowanych, aby zgłosić <xref:System.Threading.ThreadInterruptedException>, która dzieli wątek poza blokowania wywołania.</span><span class="sxs-lookup"><span data-stu-id="c5557-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="c5557-116">Wątek powinien catch <xref:System.Threading.ThreadInterruptedException> i wykonaj niezależnie od jest kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="c5557-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="c5557-117">Jeśli wątek ignoruje wyjątek, środowisko uruchomieniowe przechwytuje wyjątek i zatrzymuje wątek.</span><span class="sxs-lookup"><span data-stu-id="c5557-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5557-118">Jeśli wątek docelowy nie jest blokowane podczas <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> jest wywoływana, wątek nie zostało przerwane aż bloki.</span><span class="sxs-lookup"><span data-stu-id="c5557-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="c5557-119">Jeśli wątek nigdy nie blokuje, można wykonać bez kiedykolwiek przerwane.</span><span class="sxs-lookup"><span data-stu-id="c5557-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="c5557-120">Jeśli oczekiwania jest zarządzany czas oczekiwania, następnie <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> oba niezwłocznie wake wątku.</span><span class="sxs-lookup"><span data-stu-id="c5557-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="c5557-121">Jeśli oczekiwania jest niezarządzany oczekiwania (na przykład platformę wywołanie wywołanie Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) funkcji), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> może przejąć kontrolę nad wątek, dopóki przywraca lub wywołania wewnątrz kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c5557-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="c5557-122">W kodzie zarządzanym zachowanie jest następujący:</span><span class="sxs-lookup"><span data-stu-id="c5557-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="c5557-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>Wznawia działanie wątku poza wszelkie oczekiwania może być w i powoduje, że <xref:System.Threading.ThreadInterruptedException> zostanie wygenerowany w wątek docelowy.</span><span class="sxs-lookup"><span data-stu-id="c5557-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="c5557-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Wznawia działanie wątku poza wszelkie oczekiwania może być w i powoduje, że <xref:System.Threading.ThreadAbortException> zostanie wygenerowany w wątku.</span><span class="sxs-lookup"><span data-stu-id="c5557-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="c5557-125">Aby uzyskać więcej informacji, zobacz [niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="c5557-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5557-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5557-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="c5557-127">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="c5557-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="c5557-128">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="c5557-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="c5557-129">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="c5557-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
