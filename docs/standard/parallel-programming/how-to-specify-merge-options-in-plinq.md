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
ms.openlocfilehash: 40abe2f101f6fa23d804ef30e27d642a36908196
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139269"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Porady: określanie opcji scalania w PLINQ
W tym przykładzie pokazano, jak określić opcje scalania, które będą stosowane do wszystkich kolejnych operatorów w kwerendzie PLINQ. Nie trzeba jawnie ustawiać opcji scalania, ale może to poprawić wydajność. Aby uzyskać więcej informacji na temat opcji scalania, zobacz [Opcje scalania w pliku PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zachowanie opcji scalania w podstawowym scenariuszu, który ma nieuporządkowane źródło i stosuje kosztowną funkcję do każdego elementu.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 W przypadkach, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> gdy opcja powoduje niepożądane opóźnienie przed pierwszym elementem jest <xref:System.Linq.ParallelMergeOptions.NotBuffered> plonowany, spróbuj opcji, aby uzyskać wynik elementów szybciej i bardziej płynnie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelMergeOptions>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
