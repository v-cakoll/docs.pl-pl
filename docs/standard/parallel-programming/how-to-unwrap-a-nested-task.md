---
title: "Porady: dekodowanie zadania zagnieżdżonego"
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
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06d54efe5c8bac58746a1e01a194af55fde901b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="5a6d1-102">Porady: dekodowanie zadania zagnieżdżonego</span><span class="sxs-lookup"><span data-stu-id="5a6d1-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="5a6d1-103">Można zwrócić zadania przy użyciu metody, a następnie zaczekaj na lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5a6d1-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="5a6d1-104">W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest typu `string` (`String` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5a6d1-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="5a6d1-105">Jednak w niektórych scenariuszach, można utworzyć zadanie w ramach innego zadania, a następnie wróć zadania zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="5a6d1-106">W takim przypadku `TResult` otaczającego zadania jest zadanie.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="5a6d1-107">W poniższym przykładzie jest właściwość Result `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="5a6d1-108">Chociaż można napisać kod dekodowanie zadania zewnętrznego i pobrać oryginalnego zadania i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość, taki kod nie jest łatwa do zapisu, ponieważ musi obsłużyć wyjątki, a także żądań anulowania.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="5a6d1-109">W takiej sytuacji, firma Microsoft zaleca, użyj jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="5a6d1-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metod można użyć do przekształcania żadnego `Task<Task>` lub `Task<Task<TResult>>` (`Task(Of Task)` lub `Task(Of Task(Of TResult))` w języku Visual Basic) do `Task` lub `Task<TResult>` (`Task(Of TResult)` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5a6d1-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="5a6d1-111">Nowe zadanie w pełni reprezentuje wewnętrzny zadania zagnieżdżonego i obejmuje stan anulowania oraz wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a6d1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a6d1-112">Example</span></span>  
 <span data-ttu-id="5a6d1-113">W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="5a6d1-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="5a6d1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a6d1-114">See Also</span></span>  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [<span data-ttu-id="5a6d1-115">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="5a6d1-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
