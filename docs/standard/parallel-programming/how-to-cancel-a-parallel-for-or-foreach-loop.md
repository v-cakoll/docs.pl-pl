---
title: "Porady: anulowanie równoległej pętli For lub pętli ForEach"
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
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Porady: anulowanie równoległej pętli For lub pętli ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody obsługują anulowania przy użyciu anulowanie tokenów. Aby uzyskać więcej informacji na temat anulowania ogólnie rzecz biorąc, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md). W pętli równoległej, możesz podać <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametr, a następnie umieść wywołanie równoległe w bloku try-catch.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób anulowania wywołania <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Możesz zastosować te same podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Jeśli token anulowania sygnały ma ten sam token określonym w <xref:System.Threading.Tasks.ParallelOptions> wystąpienia, a następnie równoległej pętli zgłosi pojedynczy <xref:System.OperationCanceledException> na anulowanie. Jeśli niektóre inne token spowoduje anulowanie, pętla będzie zgłaszać wyjątek <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako we właściwości InnerException.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
