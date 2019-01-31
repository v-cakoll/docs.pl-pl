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
ms.openlocfilehash: 1dc1b6a8a00141d05ded3c2443929463ca58ca15
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55480078"
---
# <a name="countdownevent"></a><span data-ttu-id="9b3ef-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="9b3ef-102">CountdownEvent</span></span>
<span data-ttu-id="9b3ef-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> jest elementem synchronizacji, który odblokowuje wątków oczekujących, po przeprowadzeniu sygnalizowane, ile razy.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="9b3ef-104"><xref:System.Threading.CountdownEvent> jest przeznaczona dla scenariuszy, w których w przeciwnym razie trzeba byłoby użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> i ręcznie dekrementacyjne zmienną przed sygnalizacja zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="9b3ef-105">Na przykład w scenariuszu rozwidlenia/scalania, po prostu utworzeniem <xref:System.Threading.CountdownEvent> zawierający sygnału liczbę 5, a następnie rozpoczęcia pięć elementów roboczych w wątku puli i mieć każdego wywołania elementu roboczego <xref:System.Threading.CountdownEvent.Signal%2A> po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="9b3ef-106">Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza sygnał liczba o 1.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="9b3ef-107">W głównym wątku, wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> blokuje, dopóki liczba sygnałów wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b3ef-108">Dla kodu, który nie ma do interakcji z starszej wersji .NET Framework synchronizacji interfejsów API, należy wziąć pod uwagę przy użyciu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub <xref:System.Threading.Tasks.Parallel.Invoke%2A> metoda jeszcze łatwiejsze podejścia do wyrażania równoległości rozwidlenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="9b3ef-109"><xref:System.Threading.CountdownEvent> ma te dodatkowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="9b3ef-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="9b3ef-110">Przy użyciu tokenów anulowania można anulować operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="9b3ef-111">Po utworzeniu wystąpienia można zwiększyć jego Liczba sygnałów.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="9b3ef-112">Wystąpienia mogą zostać ponownie użyte po <xref:System.Threading.CountdownEvent.Wait%2A> został zwrócony przez wywołanie metody <xref:System.Threading.CountdownEvent.Reset%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="9b3ef-113">Udostępnianie wystąpień <xref:System.Threading.WaitHandle> integrację z innymi API synchronizacji .NET Framework takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="9b3ef-114">Podstawowe użycia</span><span class="sxs-lookup"><span data-stu-id="9b3ef-114">Basic Usage</span></span>  
 <span data-ttu-id="9b3ef-115">Poniższy przykład pokazuje sposób użycia <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="9b3ef-116">CountdownEvent w przypadku anulowania</span><span class="sxs-lookup"><span data-stu-id="9b3ef-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="9b3ef-117">Poniższy przykład pokazuje, jak można anulować operacji oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu tokenu anulowania.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="9b3ef-118">Podstawowy wzorzec następuje modelu ujednoliconego anulowania, która została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3ef-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="9b3ef-119">Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="9b3ef-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="9b3ef-120">Należy pamiętać, operacji oczekiwania nie powoduje anulowania wątków, które są sygnalizowanie go.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="9b3ef-121">Zazwyczaj anulowania jest stosowany do operacji logicznej i który może zawierać oczekiwania na zdarzenie, a także wszystkie elementy robocze, które synchronizuje czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="9b3ef-122">W tym przykładzie każdy element roboczy jest przekazywany kopię tego samego tokenu anulowania, aby go mogą odpowiadać na żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="9b3ef-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3ef-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b3ef-123">See also</span></span>

- [<span data-ttu-id="9b3ef-124">EventWaitHandle, CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="9b3ef-124">EventWaitHandle, CountdownEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
