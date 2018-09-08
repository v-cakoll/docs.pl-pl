---
title: 'Porady: anulowanie równoległej pętli For lub pętli ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0ff4cbc343cfbc1c81b24aa4401fa00ecf4f4b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199391"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Porady: anulowanie równoległej pętli For lub pętli ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody obsługują anulowania przy użyciu tokenów anulowania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md). W pętli równoległej, możesz podać <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametru i następnie umieść wywołanie równoległe w bloku try-catch.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak anulować wywołanie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Można zastosować to samo podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Jeśli token, który sygnalizuje anulowania jest taka sama tokenu określonym w <xref:System.Threading.Tasks.ParallelOptions> wystąpienia, a następnie pętli równoległej zgłosi pojedynczej <xref:System.OperationCanceledException> na anulowanie. Jeśli niektóre inne tokenu powoduje unieważnienie, pętla będzie sygnalizować <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako wyjątek wewnętrzny.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
