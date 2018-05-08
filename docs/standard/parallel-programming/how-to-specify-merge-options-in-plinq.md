---
title: 'Porady: określanie opcji scalania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1f30245b398ae894e7226d1e94046fc9111dcf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Porady: określanie opcji scalania w PLINQ
W tym przykładzie przedstawiono sposób Określanie opcji scalania, które będą stosowane do wszystkich kolejnych operatorów w zapytaniu PLINQ. Nie trzeba jawnie ustaw opcje scalania, ale może to zwiększyć wydajność. Aby uzyskać więcej informacji na temat opcji scalania, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie opcji scalania w scenariuszu podstawowe nieuporządkowaną źródła i stosuje funkcję kosztowne do każdego elementu.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 W przypadkach, gdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcja generuje niepożądanych czas oczekiwania przed pierwszym elementem jest zwróciło, spróbuj <xref:System.Linq.ParallelMergeOptions.NotBuffered> opcji umożliwiające uzyskanie wyniku elementy szybciej i bardziej gładko.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelMergeOptions>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
