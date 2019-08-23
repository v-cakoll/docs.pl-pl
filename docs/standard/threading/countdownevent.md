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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac1f2283ad30499748511e6fed6d5ce98da7fd14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960108"
---
# <a name="countdownevent"></a><span data-ttu-id="b8906-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="b8906-102">CountdownEvent</span></span>
<span data-ttu-id="b8906-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest pierwotną synchronizacją, która odblokowuje oczekujące wątki po zasygnalizowaniu określonej liczby razy.</span><span class="sxs-lookup"><span data-stu-id="b8906-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="b8906-104"><xref:System.Threading.CountdownEvent>jest przeznaczony do scenariuszy, w których w przeciwnym razie trzeba będzie użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> ręcznie zmniejszyć zmienną przed zasygnalizowaniem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b8906-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="b8906-105">Na przykład w scenariuszu rozwidlenie/łączenie można po prostu utworzyć element <xref:System.Threading.CountdownEvent> , który ma liczbę sygnałów równą 5, a następnie rozpocząć pięć elementów roboczych w puli wątków i mieć każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> elementu pracy po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="b8906-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="b8906-106">Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1.</span><span class="sxs-lookup"><span data-stu-id="b8906-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="b8906-107">W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zostanie zablokowane, dopóki liczba sygnałów nie będzie równa zero.</span><span class="sxs-lookup"><span data-stu-id="b8906-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8906-108">W przypadku kodu, który nie musi współdziałać ze starszymi interfejsami API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> synchronizacji .NET Framework, <xref:System.Threading.Tasks.Parallel.Invoke%2A> Rozważ użycie obiektów lub metody dla jeszcze łatwiejszego podejścia do wyznaczania równoległości przyłączania do rozwidlenia.</span><span class="sxs-lookup"><span data-stu-id="b8906-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="b8906-109"><xref:System.Threading.CountdownEvent>ma następujące dodatkowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="b8906-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="b8906-110">Operację oczekiwania można anulować przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="b8906-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="b8906-111">Po utworzeniu wystąpienia można zwiększyć jego liczbę sygnałów.</span><span class="sxs-lookup"><span data-stu-id="b8906-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="b8906-112">Wystąpienia mogą być ponownie używane po <xref:System.Threading.CountdownEvent.Wait%2A> zwróceniu przez <xref:System.Threading.CountdownEvent.Reset%2A> wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="b8906-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="b8906-113">Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> integrację z innymi interfejsami API synchronizacji .NET Framework <xref:System.Threading.WaitHandle.WaitAll%2A>, takimi jak.</span><span class="sxs-lookup"><span data-stu-id="b8906-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="b8906-114">Podstawowe użycie</span><span class="sxs-lookup"><span data-stu-id="b8906-114">Basic Usage</span></span>  
 <span data-ttu-id="b8906-115">Poniższy przykład ilustruje sposób używania elementu <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementem roboczym.</span><span class="sxs-lookup"><span data-stu-id="b8906-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="b8906-116">CountdownEvent z anulowaniem</span><span class="sxs-lookup"><span data-stu-id="b8906-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="b8906-117">Poniższy przykład pokazuje <xref:System.Threading.CountdownEvent> , jak anulować operację oczekiwania przy użyciu tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="b8906-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="b8906-118">Wzorzec podstawowy jest zgodny z modelem dla ujednoliconego anulowania, który został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b8906-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="b8906-119">Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b8906-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="b8906-120">Należy pamiętać, że operacja oczekiwania nie anuluje wątków, które je sygnalizujący.</span><span class="sxs-lookup"><span data-stu-id="b8906-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="b8906-121">Zazwyczaj anulowanie jest stosowane do operacji logicznej i może obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwają synchronizacja.</span><span class="sxs-lookup"><span data-stu-id="b8906-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="b8906-122">W tym przykładzie każdy element roboczy otrzymuje kopię tego samego tokenu anulowania, aby mógł on odpowiedzieć na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="b8906-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8906-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8906-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
