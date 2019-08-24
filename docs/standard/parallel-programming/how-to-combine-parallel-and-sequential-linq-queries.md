---
title: 'Instrukcje: Łączenie równoległych i sekwencyjnych zapytań LINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 026c7d2be678c4b6aeed4e2e6f9eb43283cd04c1
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988455"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Instrukcje: Łączenie równoległych i sekwencyjnych zapytań LINQ
W tym przykładzie pokazano, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jak za pomocą metody poinstruować PLINQ, aby przetwarzać wszystkie kolejne operatory w kwerendzie sekwencyjnie. Chociaż przetwarzanie sekwencyjne jest ogólnie wolniejsze niż równoległe, czasami konieczne jest wygenerowanie poprawnych wyników.  
  
> [!WARNING]
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono jeden scenariusz, w <xref:System.Linq.ParallelEnumerable.AsSequential%2A> którym jest to wymagane, czyli zachowanie kolejności, która została ustanowiona w poprzedniej klauzuli zapytania.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować i uruchomić ten kod, wklej go do projektu [przykładu danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) , Dodaj wiersz do wywołania metody z `Main`, a następnie naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
