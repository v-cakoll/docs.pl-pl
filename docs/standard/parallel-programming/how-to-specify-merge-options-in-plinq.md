---
title: 'Instrukcje: Określanie opcji scalania w PLINQ'
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
ms.openlocfilehash: 947f3cb15b7eb372d20884ece73374114c48f472
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988848"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Instrukcje: Określanie opcji scalania w PLINQ
Ten przykład pokazuje, jak określić opcje scalania, które będą stosowane do wszystkich kolejnych operatorów w kwerendzie PLINQ. Nie trzeba jawnie ustawiać opcji scalania, ale może to poprawić wydajność. Aby uzyskać więcej informacji na temat opcji scalania, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje zachowanie opcji scalania w podstawowym scenariuszu z nieuporządkowanym źródłem i stosuje kosztowną funkcję do każdego elementu.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 W przypadkach, gdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcja odnosi się do niepożądanego opóźnienia przed zwróceniem pierwszego elementu, <xref:System.Linq.ParallelMergeOptions.NotBuffered> wypróbuj opcję, aby szybciej i bardziej płynnie dać elementy wynikowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelMergeOptions>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
