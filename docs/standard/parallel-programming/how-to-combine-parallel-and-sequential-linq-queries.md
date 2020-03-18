---
title: 'Porady: łączenie równoległych i sekwencyjnych zapytań LINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134193"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Porady: łączenie równoległych i sekwencyjnych zapytań LINQ
W tym przykładzie pokazano, jak użyć <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metody do poinstruowania PLINQ do przetwarzania wszystkich kolejnych operatorów w kwerendzie sekwencyjnie. Mimo że przetwarzanie sekwencyjne jest zazwyczaj wolniejsze niż równoległe, czasami konieczne jest uzyskanie prawidłowych wyników.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jeden scenariusz, w którym jest wymagane, a mianowicie zachować kolejność, która została ustanowiona w poprzedniej klauzuli kwerendy.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować i uruchomić ten kod, wklej go do projektu PRÓBKI DANYCH `Main` [PLINQ,](../../../docs/standard/parallel-programming/plinq-data-sample.md) dodaj wiersz, aby wywołać metodę z , i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
