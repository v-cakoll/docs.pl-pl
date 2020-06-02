---
title: 'Instrukcje: Odpakowywanie zadania zagnieżdżonego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288033"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="5432d-102">Instrukcje: Odpakowywanie zadania zagnieżdżonego</span><span class="sxs-lookup"><span data-stu-id="5432d-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="5432d-103">Można zwrócić zadanie z metody, a następnie zaczekać lub kontynuować z tego zadania, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5432d-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="5432d-104">W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest typu `string` ( `String` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5432d-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="5432d-105">Jednak w niektórych scenariuszach można utworzyć zadanie w innym zadaniu, a następnie zwrócić zagnieżdżone zadanie.</span><span class="sxs-lookup"><span data-stu-id="5432d-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="5432d-106">W takim przypadku załączane `TResult` zadanie jest zadaniem.</span><span class="sxs-lookup"><span data-stu-id="5432d-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="5432d-107">W poniższym przykładzie właściwość wynik jest `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5432d-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="5432d-108">Chociaż istnieje możliwość napisania kodu w celu odpakowania zewnętrznego zadania i pobrania oryginalnego zadania i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości, taki kod nie jest łatwy do zapisu, ponieważ należy obsługiwać wyjątki, a także żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="5432d-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="5432d-109">W tej sytuacji zalecamy użycie jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metod rozszerzających, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5432d-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="5432d-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>Metody mogą służyć do przekształcania dowolnego `Task<Task>` lub `Task<Task<TResult>>` ( `Task(Of Task)` lub `Task(Of Task(Of TResult))` w Visual Basic) na `Task` lub `Task<TResult>` ( `Task(Of TResult)` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5432d-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="5432d-111">Nowe zadanie w pełni reprezentuje wewnętrzne zagnieżdżone zadanie i zawiera stan anulowania oraz wszystkie wyjątki.</span><span class="sxs-lookup"><span data-stu-id="5432d-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5432d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5432d-112">Example</span></span>  
 <span data-ttu-id="5432d-113">Poniższy przykład ilustruje sposób używania <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metod rozszerzających.</span><span class="sxs-lookup"><span data-stu-id="5432d-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="5432d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5432d-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="5432d-115">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="5432d-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
