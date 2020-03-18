---
title: 'Porady: zwracanie wartości z zadania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 495f68114bfe960b8182be4ab76b72043b2d0cc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141672"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="afa35-102">Porady: zwracanie wartości z zadania</span><span class="sxs-lookup"><span data-stu-id="afa35-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="afa35-103">W tym przykładzie pokazano, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> jak użyć <xref:System.Threading.Tasks.Task%601.Result%2A> tego typu, aby zwrócić wartość z właściwości.</span><span class="sxs-lookup"><span data-stu-id="afa35-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="afa35-104">Wymaga ona, aby katalog C:\Users\Public\Pictures\Sample Pictures\ zawierał pliki.</span><span class="sxs-lookup"><span data-stu-id="afa35-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afa35-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="afa35-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="afa35-106">Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje wątek wywołujący, dopóki zadanie nie zakończy.</span><span class="sxs-lookup"><span data-stu-id="afa35-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="afa35-107">Aby zobaczyć, jak przekazać <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> wynik jednego do zadania kontynuacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="afa35-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa35-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afa35-108">See also</span></span>

- [<span data-ttu-id="afa35-109">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="afa35-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [<span data-ttu-id="afa35-110">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="afa35-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
