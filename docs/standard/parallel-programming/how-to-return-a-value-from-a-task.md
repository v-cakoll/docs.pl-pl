---
title: 'Instrukcje: Zwracanie wartości z zadania'
description: Zobacz, jak używać typu System. Threading. Tasks. Task <TResult> do zwracania wartości z właściwości wynik w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767978"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="dfab9-103">Instrukcje: Zwracanie wartości z zadania</span><span class="sxs-lookup"><span data-stu-id="dfab9-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="dfab9-104">W tym przykładzie pokazano, jak za pomocą <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typu zwrócić wartość z <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dfab9-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="dfab9-105">Wymaga, aby folder C:\Users\Public\Pictures\Sample obrazy \ katalog istnieje i zawierał pliki.</span><span class="sxs-lookup"><span data-stu-id="dfab9-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfab9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="dfab9-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="dfab9-107"><xref:System.Threading.Tasks.Task%601.Result%2A>Właściwość blokuje wątek wywołujący do momentu zakończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="dfab9-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="dfab9-108">Aby dowiedzieć się, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do zadania kontynuacji, zobacz Tworzenie [łańcucha zadań przy użyciu zadań kontynuacji](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="dfab9-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfab9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfab9-109">See also</span></span>

- [<span data-ttu-id="dfab9-110">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="dfab9-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="dfab9-111">Wyrażenia lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="dfab9-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
