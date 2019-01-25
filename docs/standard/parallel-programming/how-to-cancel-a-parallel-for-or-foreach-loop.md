---
title: 'Instrukcje: Anulowanie pętli Parallel.For lub ForEach'
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
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618081"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Instrukcje: Anulowanie pętli Parallel.For lub ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody obsługują anulowania przy użyciu tokenów anulowania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md). W pętli równoległej, możesz podać <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametru i następnie umieść wywołanie równoległe w bloku try-catch.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak anulować wywołanie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Można zastosować to samo podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Jeśli token, który sygnalizuje anulowania jest taka sama tokenu określonym w <xref:System.Threading.Tasks.ParallelOptions> wystąpienia, a następnie pętli równoległej zgłosi pojedynczej <xref:System.OperationCanceledException> na anulowanie. Jeśli niektóre inne tokenu powoduje unieważnienie, pętla będzie sygnalizować <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako wyjątek wewnętrzny.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
