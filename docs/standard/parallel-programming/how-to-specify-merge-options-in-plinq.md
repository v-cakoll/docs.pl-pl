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
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588559"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Porady: określanie opcji scalania w PLINQ
W tym przykładzie pokazano, jak określić opcje scalania, które będą stosowane do wszystkich kolejnych operatorów w kwerendzie PLINQ. Nie trzeba ustawić opcje scalania jawnie, ale w ten sposób może poprawić wydajność. Aby uzyskać więcej informacji na temat opcji scalania, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zachowanie opcji scalania w scenariuszu podstawowym, który ma nieuiszczone źródło i stosuje kosztowną funkcję do każdego elementu.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 W przypadkach, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> gdy opcja powoduje wystąpienie niepożądanego opóźnienia przed uzyskaniem <xref:System.Linq.ParallelMergeOptions.NotBuffered> pierwszego elementu, spróbuj użyć opcji, aby uzyskać elementy wynikowe szybciej i płynniej.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelMergeOptions>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
