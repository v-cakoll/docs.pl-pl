---
title: 'Instrukcje: Dekodowanie zadania zagnieżdżonego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc468da70d3c62c139a98a6637e7a3c7990c378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602055"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="fbb8e-102">Instrukcje: Dekodowanie zadania zagnieżdżonego</span><span class="sxs-lookup"><span data-stu-id="fbb8e-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="fbb8e-103">Może zwracać zadanie z metody, a następnie poczekaj lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fbb8e-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="fbb8e-104">W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest typu `string` (`String` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fbb8e-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="fbb8e-105">Jednak w niektórych przypadkach warto utworzyć zadanie w ramach innego zadania, a następnie wróć zadania zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="fbb8e-106">W tym przypadku `TResult` otaczającej zadania jest zadaniem.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="fbb8e-107">W poniższym przykładzie jest właściwości wyniku `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="fbb8e-108">Chociaż istnieje możliwość napisać kod odpakowywanie zadania zewnętrznego i pobrać, oryginalnym zadaniem i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości takiego kodu nie jest łatwo zapisać, ponieważ musi obsłużyć wyjątki, a także żądań anulowania.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="fbb8e-109">W takiej sytuacji firma Microsoft zaleca, użyj jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="fbb8e-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody może służyć do przekształcania dowolne `Task<Task>` lub `Task<Task<TResult>>` (`Task(Of Task)` lub `Task(Of Task(Of TResult))` w języku Visual Basic) do `Task` lub `Task<TResult>` (`Task(Of TResult)` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fbb8e-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="fbb8e-111">Nowe zadanie pełni reprezentuje wewnętrzne zadanie zagnieżdżone, a obejmują stan anulowania i wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb8e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbb8e-112">Example</span></span>  
 <span data-ttu-id="fbb8e-113">Poniższy przykład pokazuje sposób użycia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fbb8e-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="fbb8e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbb8e-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="fbb8e-115">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="fbb8e-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
