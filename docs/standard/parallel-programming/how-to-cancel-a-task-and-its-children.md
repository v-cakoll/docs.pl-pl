---
title: 'Instrukcje: Anulowanie zadania i jego elementów podrzędnych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08e5712db60fb09b48d6be9f35737c9a884d1ce8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324479"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="ed0c9-102">Instrukcje: Anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="ed0c9-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="ed0c9-103">Te przykłady przedstawiają sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="ed0c9-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="ed0c9-104">Tworzenie i uruchamianie można anulować zadania.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="ed0c9-105">Przekaż token anulowania w swoim delegacie użytkownika i opcjonalnie wystąpienia zadania.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="ed0c9-106">Zwróć uwagę, a odpowiedź na żądanie anulowania w swoim delegacie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="ed0c9-107">Opcjonalnie Zwróć uwagę na wątku wywołującym czy zadanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="ed0c9-108">Wątek wywołujący nie kończy wymuszone zadania; tylko sygnalizuje, że zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="ed0c9-109">Jeśli zadanie jest już uruchomiony, jest do pełnomocnika użytkownika Zwróć uwagę, żądania i odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="ed0c9-110">Czy zażądano anulowania przed uruchomieniem zadania, pełnomocnika użytkownika nigdy nie jest wykonywana, a obiekt zadania przechodzi do stanu Canceled.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0c9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed0c9-111">Example</span></span>  
 <span data-ttu-id="ed0c9-112">W tym przykładzie pokazano, jak zakończyć <xref:System.Threading.Tasks.Task> i jego elementy podrzędne w odpowiedzi na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="ed0c9-113">Pokazano także, czy po użytkownik delegować kończy się, zwracając <xref:System.Threading.Tasks.TaskCanceledException>, opcjonalnie możesz skorzystać z wątku wywołującego <xref:System.Threading.Tasks.Task.Wait%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metodę, aby czekać na zakończenie zadań.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="ed0c9-114">W takim przypadku należy użyć `try/catch` bloku obsługi wyjątków na wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="ed0c9-115"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy jest w pełni zintegrowana z anulowania, który jest oparty na <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> typów.</span><span class="sxs-lookup"><span data-stu-id="ed0c9-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="ed0c9-116">Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="ed0c9-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0c9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed0c9-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="ed0c9-118">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="ed0c9-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="ed0c9-119">Dołączone i odłączone zadania podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed0c9-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [<span data-ttu-id="ed0c9-120">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="ed0c9-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
