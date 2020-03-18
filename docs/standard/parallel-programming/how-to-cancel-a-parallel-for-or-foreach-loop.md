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
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134244"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Porady: anulowanie równoległej pętli For lub pętli ForEach
Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i obsługują anulowanie za pomocą tokenów anulowania. Aby uzyskać więcej informacji na temat anulowania w ogóle, zobacz [Anulowanie](../../../docs/standard/threading/cancellation-in-managed-threads.md). W pętli równoległej <xref:System.Threading.CancellationToken> należy podać <xref:System.Threading.Tasks.ParallelOptions> do metody w parametrze, a następnie ująć wywołanie równoległe w bloku try-catch.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>jak anulować połączenie . Do wywołania <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> można zastosować to samo podejście.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Jeśli token, który sygnalizuje anulowanie jest tym <xref:System.Threading.Tasks.ParallelOptions> samym tokenem, który jest <xref:System.OperationCanceledException> określony w wystąpieniu, pętla równoległa spowoduje wyrzucenie pojedynczego podczas anulowania. Jeśli inny token powoduje anulowanie, <xref:System.AggregateException> pętla <xref:System.OperationCanceledException> będzie zgłaszać z jako InnerException.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
