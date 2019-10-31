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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134203"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="e04db-102">Porady: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="e04db-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="e04db-103">W poniższych przykładach pokazano, jak wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e04db-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="e04db-104">Utwórz i uruchom zadanie z możliwością anulowania.</span><span class="sxs-lookup"><span data-stu-id="e04db-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="e04db-105">Przekaż token anulowania do delegata użytkownika i opcjonalnie do wystąpienia zadania.</span><span class="sxs-lookup"><span data-stu-id="e04db-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="e04db-106">Zwróć uwagę i Odpowiedz na żądanie anulowania w oddelegowaniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e04db-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="e04db-107">Opcjonalnie Zwróć uwagę na wątek wywołujący, że zadanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="e04db-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="e04db-108">Wątek wywołujący nie wymusi zakończyć zadania; tylko sygnalizuje to żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="e04db-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="e04db-109">Jeśli zadanie jest już uruchomione, należy do delegata użytkownika, aby zwrócić uwagę na żądanie i odpowiednio odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="e04db-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="e04db-110">Jeśli przed uruchomieniem zadania zostanie wysłane żądanie anulowania, delegat użytkownika nigdy nie zostanie wykonany, a obiekt zadania przechodzi do stanu anulowane.</span><span class="sxs-lookup"><span data-stu-id="e04db-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e04db-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e04db-111">Example</span></span>  
 <span data-ttu-id="e04db-112">Ten przykład pokazuje, jak przerwać <xref:System.Threading.Tasks.Task> i jego elementy podrzędne w odpowiedzi na żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="e04db-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="e04db-113">Pokazuje również, że po zakończeniu delegata użytkownika przez wyrzucanie <xref:System.Threading.Tasks.TaskCanceledException>, wątek wywołujący może opcjonalnie użyć metody <xref:System.Threading.Tasks.Task.Wait%2A> lub metody <xref:System.Threading.Tasks.Task.WaitAll%2A>, aby poczekać na zakończenie zadań.</span><span class="sxs-lookup"><span data-stu-id="e04db-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="e04db-114">W takim przypadku należy użyć bloku `try/catch`, aby obsłużyć wyjątki w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="e04db-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="e04db-115">Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest w pełni zintegrowana z modelem anulowania opartym na typach <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e04db-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="e04db-116">Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="e04db-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04db-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e04db-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="e04db-118">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="e04db-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="e04db-119">Dołączone i odłączone zadania podrzędne</span><span class="sxs-lookup"><span data-stu-id="e04db-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [<span data-ttu-id="e04db-120">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="e04db-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
