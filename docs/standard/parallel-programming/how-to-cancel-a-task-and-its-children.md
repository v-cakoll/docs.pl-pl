---
title: 'Porady: anulowanie zadania i jego elementów podrzędnych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 4e0e783a4dfe3bf3a55795d7baef461369d7405a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134203"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="84f87-102">Porady: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="84f87-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="84f87-103">W poniższych przykładach przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="84f87-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="84f87-104">Tworzenie i rozpoczynanie zadania możliwego do anulowania.</span><span class="sxs-lookup"><span data-stu-id="84f87-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="84f87-105">Przekaż token anulowania do delegata użytkownika i opcjonalnie do wystąpienia zadania.</span><span class="sxs-lookup"><span data-stu-id="84f87-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="84f87-106">Zwiaduj i odpowiedz na żądanie anulowania w pełnomocniku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84f87-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="84f87-107">Opcjonalnie należy zauważyć w wątku wywołującego, że zadanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="84f87-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="84f87-108">Wątek wywołujący nie powoduje wymuszenia zakończenia zadania; sygnalizuje jedynie, że wymagane jest anulowanie.</span><span class="sxs-lookup"><span data-stu-id="84f87-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="84f87-109">Jeśli zadanie jest już uruchomione, to do delegata użytkownika, aby zauważyć żądanie i odpowiednio odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="84f87-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="84f87-110">Jeśli odwołanie jest wymagane przed wykonaniem zadania, delegat użytkownika nigdy nie jest wykonywany, a obiekt zadania przechodzi w stan Anulowane.</span><span class="sxs-lookup"><span data-stu-id="84f87-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84f87-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="84f87-111">Example</span></span>  
 <span data-ttu-id="84f87-112">W tym przykładzie pokazano, jak zakończyć a <xref:System.Threading.Tasks.Task> i jego podrzędne w odpowiedzi na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="84f87-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="84f87-113">Pokazuje również, że gdy delegat użytkownika kończy <xref:System.Threading.Tasks.TaskCanceledException>się przez zgłaszanie , <xref:System.Threading.Tasks.Task.Wait%2A> wątek <xref:System.Threading.Tasks.Task.WaitAll%2A> wywołujący może opcjonalnie użyć metody lub metody, aby poczekać na zakończenie zadań.</span><span class="sxs-lookup"><span data-stu-id="84f87-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="84f87-114">W takim przypadku należy `try/catch` użyć bloku do obsługi wyjątków w wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="84f87-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="84f87-115">Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest w pełni zintegrowany z modelem <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> <xref:System.Threading.CancellationToken?displayProperty=nameWithType> anulowania, który jest oparty na i typów.</span><span class="sxs-lookup"><span data-stu-id="84f87-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="84f87-116">Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątków](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="84f87-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f87-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84f87-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="84f87-118">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="84f87-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="84f87-119">Dołączone i odłączone zadania podrzędne</span><span class="sxs-lookup"><span data-stu-id="84f87-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [<span data-ttu-id="84f87-120">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="84f87-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
