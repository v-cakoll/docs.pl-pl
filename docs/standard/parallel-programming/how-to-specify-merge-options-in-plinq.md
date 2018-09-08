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
ms.openlocfilehash: 8914d3c443971f73e6f3fa366c26567bae60dbe1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189469"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Porady: określanie opcji scalania w PLINQ
W tym przykładzie przedstawiono sposób Określanie opcji scalania, które będą stosowane do wszystkie kolejne operatory w zapytaniu PLINQ. Nie trzeba jawnie ustawić opcje scalania, ale może to poprawić wydajność. Aby uzyskać więcej informacji na temat opcji scalania, zobacz [opcji scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie opcji scalania w podstawowy scenariusz, nieuporządkowane źródła i stosuje kosztowna funkcja do każdego elementu.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 W przypadkach, gdzie <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcji powoduje niepożądanych opóźnienie przed pierwszym elementem jest uzyskane, spróbuj <xref:System.Linq.ParallelMergeOptions.NotBuffered> opcji umożliwiające uzyskanie wyniku elementów, szybciej i sprawniej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelMergeOptions>  
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
