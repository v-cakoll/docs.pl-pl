---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138110"
---
# <a name="countdownevent"></a><span data-ttu-id="8d74f-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="8d74f-102">CountdownEvent</span></span>
<span data-ttu-id="8d74f-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> to element pierwotny synchronizacji, który odblokowuje oczekujące wątki po zasygnalizowaniu określonej liczby razy.</span><span class="sxs-lookup"><span data-stu-id="8d74f-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="8d74f-104"><xref:System.Threading.CountdownEvent> jest zaprojektowana dla scenariuszy, w których w przeciwnym razie należy użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> ręcznie zmniejszyć zmienną przed zasygnalizowaniem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8d74f-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="8d74f-105">Na przykład w scenariuszu rozwidlenie/łączenie można po prostu utworzyć <xref:System.Threading.CountdownEvent>, który ma liczbę sygnałów równą 5, a następnie rozpocząć pięć elementów roboczych w puli wątków i mieć każde wywołanie elementu pracy, <xref:System.Threading.CountdownEvent.Signal%2A> po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="8d74f-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="8d74f-106">Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1.</span><span class="sxs-lookup"><span data-stu-id="8d74f-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="8d74f-107">W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> będzie blokowane, dopóki liczba sygnałów nie będzie równa zero.</span><span class="sxs-lookup"><span data-stu-id="8d74f-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d74f-108">W przypadku kodu, który nie musi współdziałać ze starszymi interfejsami API synchronizacji .NET Framework, rozważ użycie obiektów <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub metody <xref:System.Threading.Tasks.Parallel.Invoke%2A> w celu uzyskania jeszcze łatwiejszego podejścia do wyznaczania równoległości przyłączania rozwidlenia.</span><span class="sxs-lookup"><span data-stu-id="8d74f-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="8d74f-109"><xref:System.Threading.CountdownEvent> ma następujące dodatkowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="8d74f-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="8d74f-110">Operację oczekiwania można anulować przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="8d74f-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="8d74f-111">Po utworzeniu wystąpienia można zwiększyć jego liczbę sygnałów.</span><span class="sxs-lookup"><span data-stu-id="8d74f-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="8d74f-112">Wystąpienia mogą być ponownie używane po zwróceniu <xref:System.Threading.CountdownEvent.Wait%2A>, wywołując metodę <xref:System.Threading.CountdownEvent.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d74f-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="8d74f-113">Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> do integracji z innymi interfejsami API synchronizacji .NET Framework, takimi jak <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d74f-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="8d74f-114">Podstawowe użycie</span><span class="sxs-lookup"><span data-stu-id="8d74f-114">Basic Usage</span></span>  
 <span data-ttu-id="8d74f-115">Poniższy przykład ilustruje sposób używania <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementami roboczymi.</span><span class="sxs-lookup"><span data-stu-id="8d74f-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="8d74f-116">CountdownEvent z anulowaniem</span><span class="sxs-lookup"><span data-stu-id="8d74f-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="8d74f-117">Poniższy przykład pokazuje, jak anulować operację oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="8d74f-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="8d74f-118">Wzorzec podstawowy jest zgodny z modelem dla ujednoliconego anulowania, który został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8d74f-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="8d74f-119">Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="8d74f-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="8d74f-120">Należy pamiętać, że operacja oczekiwania nie anuluje wątków, które je sygnalizujący.</span><span class="sxs-lookup"><span data-stu-id="8d74f-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="8d74f-121">Zazwyczaj anulowanie jest stosowane do operacji logicznej i może obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwają synchronizacja.</span><span class="sxs-lookup"><span data-stu-id="8d74f-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="8d74f-122">W tym przykładzie każdy element roboczy otrzymuje kopię tego samego tokenu anulowania, aby mógł on odpowiedzieć na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="8d74f-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d74f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d74f-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
