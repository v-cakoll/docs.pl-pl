---
title: 'Porady: dekodowanie zadania zagnieżdżonego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106907"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="413be-102">Porady: dekodowanie zadania zagnieżdżonego</span><span class="sxs-lookup"><span data-stu-id="413be-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="413be-103">Można zwrócić zadanie z metody, a następnie poczekać lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="413be-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="413be-104">W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest `string` typu`String` (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="413be-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="413be-105">Jednak w niektórych scenariuszach można utworzyć zadanie w ramach innego zadania, a następnie zwrócić zagnieżdżone zadanie.</span><span class="sxs-lookup"><span data-stu-id="413be-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="413be-106">W takim przypadku `TResult` zadanie otaczające jest samo w sobie zadaniem.</span><span class="sxs-lookup"><span data-stu-id="413be-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="413be-107">W poniższym przykładzie Result właściwość `Task<Task<string>>` jest w `Task(Of Task(Of String))` języku C# lub w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="413be-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="413be-108">Chociaż istnieje możliwość zapisania kodu, aby rozpakować zadanie <xref:System.Threading.Tasks.Task%601.Result%2A> zewnętrzne i pobrać oryginalne zadanie i jego właściwość, taki kod nie jest łatwy do napisania, ponieważ należy obsługiwać wyjątki, a także żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="413be-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="413be-109">W tej sytuacji zaleca się użycie <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> jednej z metod rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="413be-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="413be-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody mogą służyć do przekształcania `Task<Task<TResult>>` `Task(Of Task)` dowolnego `Task(Of Task(Of TResult))` `Task<Task>` lub ( lub `Task<TResult>` w`Task(Of TResult)` języku Visual Basic) do lub ( w języku `Task` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="413be-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="413be-111">Nowe zadanie w pełni reprezentuje wewnętrzne zagnieżdżone zadanie i obejmuje stan anulowania i wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="413be-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="413be-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="413be-112">Example</span></span>  
 <span data-ttu-id="413be-113">W poniższym przykładzie pokazano, jak używać metod <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="413be-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="413be-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="413be-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="413be-115">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="413be-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
