---
title: 'Instrukcje: Zwracanie wartości z zadania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df928ec6494da6da368b3cef1f1d25a84a692aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741787"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="db0f2-102">Instrukcje: Zwracanie wartości z zadania</span><span class="sxs-lookup"><span data-stu-id="db0f2-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="db0f2-103">W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typu w celu zwrócenia wartości z <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="db0f2-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="db0f2-104">Wymaga czy C:\Users\Public\Pictures\Sample Pictures\ katalog istnieje i czy zawiera on pliki.</span><span class="sxs-lookup"><span data-stu-id="db0f2-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db0f2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="db0f2-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="db0f2-106"><xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość blokuje wątek wywołujący, aż do zakończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="db0f2-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="db0f2-107">Aby zobaczyć, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do kontynuacji zadania, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="db0f2-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0f2-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db0f2-108">See also</span></span>

- [<span data-ttu-id="db0f2-109">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="db0f2-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="db0f2-110">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="db0f2-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
