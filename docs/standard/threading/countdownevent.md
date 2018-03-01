---
title: CountdownEvent
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
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 144bcde6c4c8fb227773fe613da8445f100ce66d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="countdownevent"></a><span data-ttu-id="5cdf8-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="5cdf8-102">CountdownEvent</span></span>
<span data-ttu-id="5cdf8-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest prymitywu synchronizacji, który odblokowuje wątków oczekiwania, po przeprowadzeniu sygnalizowane wiele razy.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="5cdf8-104"><xref:System.Threading.CountdownEvent>jest przeznaczony do scenariuszy, w których mogłyby w przeciwnym razie należy użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> i ręcznie dekrementacji zmiennej przed sygnalizowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="5cdf8-105">Na przykład w przypadku rozwidlenia/sprzężenia, po prostu utworzeniem <xref:System.Threading.CountdownEvent> mający sygnału liczbę 5, a następnie start pięć elementów roboczych w wątku puli i mieć każdego wywołania elementu roboczego <xref:System.Threading.CountdownEvent.Signal%2A> po zakończeniu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="5cdf8-106">Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczba sygnał o 1.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="5cdf8-107">W głównym wątku wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zablokuje dopóki liczba sygnałów wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cdf8-108">Kod, który nie ma na interakcję z starszej wersji .NET Framework synchronizacji interfejsów API, należy rozważyć użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub <xref:System.Threading.Tasks.Parallel.Invoke%2A> metody łatwiejsze podejścia do wyrażania równoległości rozwidlenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="5cdf8-109"><xref:System.Threading.CountdownEvent>ma następujące dodatkowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="5cdf8-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="5cdf8-110">Za pomocą tokenów anulowania można anulować operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="5cdf8-111">Po utworzeniu wystąpienia można odpowiednio licznika sygnału.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="5cdf8-112">Można ponownie użyć wystąpienia po <xref:System.Threading.CountdownEvent.Wait%2A> został zwrócony przez wywołanie metody <xref:System.Threading.CountdownEvent.Reset%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="5cdf8-113">Udostępnianie wystąpień <xref:System.Threading.WaitHandle> do integracji z innymi synchronizacji .NET Framework interfejsów API takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="5cdf8-114">Podstawowe sposoby użycia</span><span class="sxs-lookup"><span data-stu-id="5cdf8-114">Basic Usage</span></span>  
 <span data-ttu-id="5cdf8-115">W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="5cdf8-116">CountdownEvent z anulowania</span><span class="sxs-lookup"><span data-stu-id="5cdf8-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="5cdf8-117">Poniższy przykład przedstawia sposób anulowania operacji oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu token anulowania.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="5cdf8-118">Podstawowy wzorzec jest zgodna ze modelem ujednoliconego anulowania, która została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cdf8-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="5cdf8-119">Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="5cdf8-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="5cdf8-120">Uwaga operacji oczekiwania nie spowoduje anulowania wątków, które są sygnalizowania go.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="5cdf8-121">Zazwyczaj anulowania jest stosowany do operacji logicznych i który może zawierać oczekiwania na zdarzenie, a także wszystkie elementy robocze, które synchronizuje czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="5cdf8-122">W tym przykładzie każdy element roboczy jest przekazywany kopię tego samego token anulowania, dzięki czemu mogą odpowiadać na żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="5cdf8-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdf8-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cdf8-123">See Also</span></span>  
 [<span data-ttu-id="5cdf8-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="5cdf8-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
