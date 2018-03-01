---
title: "Porady: anulowanie zadania i jego elementów podrzędnych"
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
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ecccd5ddd3ff662b03ae7078aabaf58e397f7003
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="18ffb-102">Porady: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="18ffb-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="18ffb-103">Następujące przykłady przedstawiają sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="18ffb-103">These examples show how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="18ffb-104">Tworzenie i uruchamianie zadań można anulować.</span><span class="sxs-lookup"><span data-stu-id="18ffb-104">Create and start a cancelable task.</span></span>  
  
2.  <span data-ttu-id="18ffb-105">Przekaż token anulowania do pełnomocnika użytkownika i opcjonalnie wystąpienia zadania.</span><span class="sxs-lookup"><span data-stu-id="18ffb-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3.  <span data-ttu-id="18ffb-106">Zwróć uwagę i odpowiadać na żądania anulowania w pełnomocnika użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18ffb-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4.  <span data-ttu-id="18ffb-107">Opcjonalnie Zwróć uwagę na wątek wywołujący czy zadanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="18ffb-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="18ffb-108">Wątek wywołujący nie wymuszanie kończy zadanie; sygnalizuje tylko, że zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="18ffb-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="18ffb-109">Jeśli zadanie jest już uruchomiona, jest delegowanie użytkownika Zwróć uwagę, żądanie i reagowania.</span><span class="sxs-lookup"><span data-stu-id="18ffb-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="18ffb-110">Jeśli przed uruchomieniem zadania żądanie anulowania, delegat użytkownika nie został wykonany i obiekt zadania przechodzi do stanu Anulowano.</span><span class="sxs-lookup"><span data-stu-id="18ffb-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ffb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="18ffb-111">Example</span></span>  
 <span data-ttu-id="18ffb-112">W tym przykładzie pokazano, jak zakończyć <xref:System.Threading.Tasks.Task> i jego elementów podrzędnych w odpowiedzi na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="18ffb-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="18ffb-113">Także pokazanie, gdy użytkownik delegować przerwanie przez zgłaszanie <xref:System.Threading.Tasks.TaskCanceledException>, wątek wywołujący może opcjonalnie korzystać <xref:System.Threading.Tasks.Task.Wait%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody oczekiwania na zakończenie zadań.</span><span class="sxs-lookup"><span data-stu-id="18ffb-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="18ffb-114">W takim przypadku należy użyć `try/catch` bloku obsługi wyjątków w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="18ffb-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="18ffb-115"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy jest w pełni zintegrowana z modelem anulowania, na podstawie <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> typów.</span><span class="sxs-lookup"><span data-stu-id="18ffb-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="18ffb-116">Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="18ffb-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ffb-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18ffb-117">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [<span data-ttu-id="18ffb-118">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="18ffb-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [<span data-ttu-id="18ffb-119">Dołączone i odłączone zadania podrzędne</span><span class="sxs-lookup"><span data-stu-id="18ffb-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [<span data-ttu-id="18ffb-120">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="18ffb-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
