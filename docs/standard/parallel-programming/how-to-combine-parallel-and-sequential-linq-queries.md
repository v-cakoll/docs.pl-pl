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
ms.openlocfilehash: 99c86e17c57a90d2268acb2a32c69bc4a693338a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588000"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Porady: łączenie równoległych i sekwencyjnych zapytań LINQ
W tym przykładzie <xref:System.Linq.ParallelEnumerable.AsSequential%2A> pokazano, jak użyć metody, aby poinstruować PLINQ do przetwarzania wszystkich kolejnych operatorów w kwerendzie sekwencyjnie. Chociaż przetwarzanie sekwencyjne jest zazwyczaj wolniejsze niż równoległe, czasami konieczne jest uzyskanie prawidłowych wyników.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia jeden <xref:System.Linq.ParallelEnumerable.AsSequential%2A> scenariusz, w którym jest wymagane, a mianowicie zachować kolejność, która została ustanowiona w poprzedniej klauzuli kwerendy.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować i uruchomić ten kod, wklej go do projektu [PLINQ Data Sample,](../../../docs/standard/parallel-programming/plinq-data-sample.md) dodaj wiersz, aby wywołać metodę z `Main`programu , i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
