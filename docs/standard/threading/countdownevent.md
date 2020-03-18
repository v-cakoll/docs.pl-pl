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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138110"
---
# <a name="countdownevent"></a><span data-ttu-id="75206-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="75206-102">CountdownEvent</span></span>
<span data-ttu-id="75206-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest prymitywem synchronizacji, który odblokowuje jego wątki oczekiwania po tym, jak został zasygnalizowany określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="75206-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="75206-104"><xref:System.Threading.CountdownEvent>jest przeznaczony dla scenariuszy, w których w <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> przeciwnym razie trzeba by użyć lub ręcznie zmniejszać zmienną przed zasygnalizowaniem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="75206-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="75206-105">Na przykład w scenariuszu rozwidlenie/sprzężenie można po prostu utworzyć, <xref:System.Threading.CountdownEvent> który ma liczbę sygnałów 5, a <xref:System.Threading.CountdownEvent.Signal%2A> następnie uruchomić pięć elementów roboczych w puli wątków i mieć każde wywołanie elementu pracy po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="75206-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="75206-106">Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1.</span><span class="sxs-lookup"><span data-stu-id="75206-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="75206-107">W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zostanie zablokowane, dopóki liczba sygnałów nie osiągnie zera.</span><span class="sxs-lookup"><span data-stu-id="75206-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75206-108">Dla kodu, który nie musi współdziałać ze starszymi <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> interfejsami <xref:System.Threading.Tasks.Parallel.Invoke%2A> API synchronizacji .NET Framework, należy rozważyć użycie obiektów lub metody dla jeszcze łatwiejszego podejścia do wyrażania równoległości sprzężenia rozwidliwego.</span><span class="sxs-lookup"><span data-stu-id="75206-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="75206-109"><xref:System.Threading.CountdownEvent>posiada następujące dodatkowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="75206-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="75206-110">Operację oczekiwania można anulować przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="75206-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="75206-111">Jego liczba sygnałów może być zwiększana po utworzeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75206-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="75206-112">Wystąpienia mogą być ponownie <xref:System.Threading.CountdownEvent.Wait%2A> używane po powrocie przez wywołanie <xref:System.Threading.CountdownEvent.Reset%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75206-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="75206-113">Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> do integracji z innymi <xref:System.Threading.WaitHandle.WaitAll%2A>interfejsami API synchronizacji programu .NET Framework, takimi jak .</span><span class="sxs-lookup"><span data-stu-id="75206-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="75206-114">Podstawowe użycie</span><span class="sxs-lookup"><span data-stu-id="75206-114">Basic Usage</span></span>  
 <span data-ttu-id="75206-115">W poniższym przykładzie pokazano, jak używać <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementami roboczymi.</span><span class="sxs-lookup"><span data-stu-id="75206-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="75206-116">Odliczanie zdarzenia z anulowaniem</span><span class="sxs-lookup"><span data-stu-id="75206-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="75206-117">W poniższym przykładzie pokazano, <xref:System.Threading.CountdownEvent> jak anulować operację oczekiwania przy użyciu tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="75206-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="75206-118">Podstawowy wzorzec następuje model ujednoliconego anulowania, który jest wprowadzany w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="75206-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="75206-119">Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="75206-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="75206-120">Należy zauważyć, że operacja oczekiwania nie anuluje wątków, które ją sygnalizują.</span><span class="sxs-lookup"><span data-stu-id="75206-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="75206-121">Zazwyczaj anulowanie jest stosowane do operacji logicznej i które mogą obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwa synchronizacja oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="75206-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="75206-122">W tym przykładzie każdy element pracy jest przekazywana kopia tego samego tokenu anulowania, dzięki czemu można odpowiedzieć na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="75206-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75206-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75206-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
